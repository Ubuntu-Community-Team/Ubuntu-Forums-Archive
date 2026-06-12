---
title: "Help To Finish Installing LIRC please"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by bartoon on 2008-09-24
Hi,

I just installed LIRC but when I run irw nothing happen while pressing on some remote buttons:

```

bart@bart-desktop:~$ irw


```

Here are some outputs :


```

bart@bart-desktop:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 

```

sudo mode2 -d /dev/lirc0 :
```

space 16777215
pulse 406
space 263
pulse 2086
space 875
pulse 260
space 583
pulse 633
space 1220
pulse 572
space 842
pulse 1109

```

my config file (generated thanks to irrecord) is located in /home/bart/bench.conf

this is my /etc/lirc/hardware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Irman / UIR"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/home/bart/bench.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/home/bart/bench.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Serial Port Receiver"
RECEIVER_VENDOR="Generic"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="Linux Input Layer compatible Remote"
REMOTE_VENDOR="Generic"

```

(my IR receiver is home made connected to the serial port  and the remote control is a random remote i took in my living room the brand is 'bench')

Any ideas ?

Thank You!

---

