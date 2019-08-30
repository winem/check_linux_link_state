# check_linux_link_state
Nagios and Icinga2 plugin to check the link state of any network interface on a Linux host

## Dependencies
This plugin requires:
  - Python3

## How it works
The plugin reads the link state from /sys/class/net/<interface-name>/operstate. An alarm is raised if the link state (up/down) does not match the desired state.

## Performance data
This plugin provides the following metrics: 
  - link_state: values match the exit code of the plugin (0: state == desired state; 2: state != desired state)

## Usage
See the examples below or execute the plugin with -h/--help.

## Examples
Raise an alarm if eth0 is down: 
```
./check_linux_link_state -d eth0 -s up
eth0 LINK STATE OK - Device eth0 link is up. | link_state=0
```
 
The default of the desired state is up. So the state argument can be omitted and the command above is equivalent to:
```
./check_linux_link_state -d eth0
eth0 LINK STATE OK - Device eth0 link is up. | link_state=0
```

Raise an alarm if eth0 is up: 
```
./check_linux_link_state -d eth0 -s down 
eth0 LINK STATE CRTITCAL - Device eth0 link is up | link_state=2
```
