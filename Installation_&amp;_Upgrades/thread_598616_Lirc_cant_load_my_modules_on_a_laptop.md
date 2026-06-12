---
title: "Lirc cant load my modules on a laptop"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by gillis on 2007-10-31
Hello. 
i spend almost one week with installing lirc on ubuntu gutsy.
so far without a result.
today i did a ubuntu reinstall, unfortunately i still cant get it working.

I have a hp nc8000 laptop with a build in infrared.
i followed the gutsy lirc install guide. 
basically i did 
$ DEBIAN_FRONTEND=gnome sudo apt-get install lirc
and i downloaded a lircd.conf file for my remote control.

when i try to start lirc i get the following error:

g@nc8000:~$ sudo /etc/init.d/lirc restart
Stopping lirc daemon: lircmd lircd.
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

i have the following lines in hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SIR IrDA (built-in IR ports)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_sir"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""


why is lirc_dev lirc_sir not loading properly?

dmesg | grep -i lirc  give me the following information:

[ 1040.292000] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1040.292000] lirc_sir: i/o port 0x03e8 already in use.
[ 1040.328000] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1040.328000] lirc_sir: i/o port 0x03e8 already in use.
[ 1040.368000] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1040.368000] lirc_sir: i/o port 0x03e8 already in use.
[ 1040.404000] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1040.404000] lirc_sir: i/o port 0x03e8 already in use.
..............
.....

---

