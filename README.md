# GroupDNA

GroupDNA turns a WhatsApp group chat export into a terminal-based group report. It summarizes who talks the most, when the group is most active, common words, response patterns, silent streaks, and a playful personality archetype for each member.

## What It Reports

- Total messages, members, date range, and busiest day/hour
- Messages per person with percentage breakdowns
- A 24-hour activity heatmap for each member
- Most frequently used words, excluding common filler words
- Media and deleted-message counts
- Fastest and slowest response patterns
- Longest silent streak for each member
- Fun archetypes such as `GROUP MOM`, `NIGHT OWL`, `STORYTELLER`, and `COMEDIAN`

## Requirements

- Python 3.8 or newer
- NumPy
- A WhatsApp chat export in plain-text format

## Installation

Create and activate a virtual environment if desired, then install the only external dependency:

```bash
python -m pip install numpy
```

## Usage

Keep the chat export in the project directory and name it `hostel_bois.txt`, or replace the filename in `groupdna.py`. Then run:

```bash
python groupdna.py
```

The report is printed directly to the terminal. It contains both a detailed overview and a compact final report.

## Input Format

The parser expects the common WhatsApp export format:

```text
01/04/24, 01:17 - Rahul: scene fix
01/04/24, 01:18 - Rahul: kya scene
```

It also recognizes:

- `<Media omitted>` as a media message
- `This message was deleted` as a deleted message
- Continuation lines belonging to the previous message
- System lines such as group creation and encryption notices

The current parser expects dates in `DD/MM/YY` format and times in 24-hour `HH:MM` format.

## Project Structure

```text
.
|-- groupdna.py       # Chat parsing and report generation
|-- hostel_bois.txt   # Example WhatsApp chat export
`-- README.md         # Project documentation
```

## Privacy

Chat contents are processed locally. The script does not upload or transmit the chat export. Since the report includes message-derived statistics and participant names, avoid committing private chat data to a public repository.

## Notes

- The analysis is heuristic and intended for entertainment and lightweight insight, not behavioral or psychological assessment.
- Word counts ignore a built-in list of common English and Hindi filler words.
- Archetypes are assigned by comparing each member's scores across the available categories, so each category is assigned at most once.
- The input file is currently configured directly in the script rather than through a command-line argument.

## License

This project is licensed under the MIT License.
