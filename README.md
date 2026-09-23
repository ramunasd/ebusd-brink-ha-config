# Brink / ebusd / Home Assistant Configuration

Configuration files for integrating the **Brink** heat recovery units (HRU) with **Home Assistant** using **ebusd** interface .

## What's Inside

- **ebusd configuration** – split into separate files per device/feature for easier maintenance and versioning.
- **Home Assistant MQTT config** – fixed and improved ebusd MQTT config.

## ebusd Config

The ebusd configuration is organised as **multiple files** (one per logical section) rather than a single monolithic config. This makes it straightforward to:

- diff and review changes in git,
- enable/disable individual sections without touching unrelated parts,
- keep the config readable as the unit's supported registers grow.

## Data Quality

- **Proper data types** are declared for every register so values are interpreted correctly downstream.
- **Numeric field ranges** (`min` / `max`) are defined wherever the hardware documentation specifies valid limits, preventing out-of-range values from propagating into Home Assistant.

## Compatibility

All configuration files have been **checked and tested against the latest released versions of ebusd**. If you run into issues, please make sure your ebusd build is current before filing a bug.

## Getting Started

1. Clone this repository.
2. Copy the relevant ebusd config files into your ebusd `config/` directory (or symlink them).
3. Add the Home Assistant integration files to your HA configuration.
4. Restart ebusd, then reload the MQTT integration in Home Assistant.

> **Tip:** Because the ebusd config is split per section, you can cherry-pick only the files you need (e.g. temperature sensors without the fan-control section).

## Contributing

PRs welcome — especially for:
- additional register mappings,
- corrected ranges / data types,

## Credits

* ebusd MQTT config - https://github.com/john30/ebusd/blob/master/contrib/etc/ebusd/mqtt-hassio.cfg
* Excellent 300 config - https://github.com/dstrigl/ebusd-config-brink-renovent-excellent-300

## License

MIT (or whatever licence applies to your project — adjust as needed).
