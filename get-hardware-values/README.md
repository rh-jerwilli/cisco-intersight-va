get-hardware-values

This role queries Cisco Intersight for UCS hardware information and generates host-related variables used to populate OpenShift installation inputs.

It is designed to run in Ansible Automation Platform using a custom credential for Intersight authentication and optional host targeting.

The role discovers blades, identifies assigned server profiles, retrieves vNIC MAC addresses, and builds host data structures suitable for rendering into a values or vars file.

Requirements

Ansible core 2.15 or newer is required.

The cisco.intersight collection version 2.12.0 must be installed.

An AAP custom credential must provide the Intersight API key ID and private key. The private key must be provided as PEM content.

Inputs

Authentication values are expected from environment variables injected by AAP.

The hostname may be provided either through a variable or through the credential as a default.

If no hostname is provided, the role will discover blades and process all matching systems.

Outputs

The role generates structured host data including MAC addresses derived from vNICs.

Output files are written to the configured output directory and can be consumed by downstream OpenShift installation workflows.

Usage

The role is intended to be executed from a simple play that targets localhost and includes this role.

Configuration values may be overridden using inventory variables, surveys, or vars files.

Notes

BMC credentials and host IP addresses are not sourced from Intersight and must be provided separately if required by the installation process.

This role focuses on removing the hardware team dependency for hardware discovery and network identity generation.