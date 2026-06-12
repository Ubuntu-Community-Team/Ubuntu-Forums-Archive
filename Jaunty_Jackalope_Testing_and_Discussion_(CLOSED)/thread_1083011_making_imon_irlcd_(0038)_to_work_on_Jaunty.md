---
title: "making imon ir/lcd (0038) to work on Jaunty"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nirro on 2009-02-28
Hi Guys,

I'm trying to make my imon remote and LCD to work on Jaunty.
Jaunty has lirc 0.8.4a, which supposed to support this device.

I did :
```
sudo apt-get install lirc
sudo dpkg-reconfigure lirc

```
I choose "Soundgraph iMON IR/LCD"
In IR-Transmitter I choose None for now.

The output is :
```
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Reloading kernel event manager...                                     [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 

```

Then I do :
```
ls /dev/lirc*
```
and I see : /dev/lircd  /dev/lircd1

I need to see /dev/lirc0 and /dev/lirc1
but they are missing.

Can someone help me what am I doing wrong ?

Thanks,
Nir.

---

### Post by Nirro on 2009-03-01
bump.

lirc_mceusb2 on the same system works fine.

---

### Post by Nirro on 2009-03-14
Hi, 

I'm still interested in setting up the iMon LCD,
so I'm bumping...

Thanks.

---

### Post by Nirro on 2009-03-15
Information :

/etc/lirc/hardware.conf
```

# /etc/lirc/hardware.conf

#Chosen Remote Control
REMOTE="custom"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Custom"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

```

I changed LOAD_MODULES to "false" because it fails to start otherwise, and anyways the modules are loaded without it, (lirc_mceusb2, not lirc_imon). when I modprobe lirc_imon, it is loaded, but lirc doesn't seem to know about it.

/etc/lirc/lircd.conf
```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

include "/usr/share/lirc/remotes/imon/lircd.conf.imon"
include "/usr/share/lirc/transmitters/hot/general.conf"

```

cat /proc/bus/usb
```

T:  Bus=03 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0038 Rev= 0.01
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

kernel:
Linux htpc 2.6.28-9-generic #31-Ubuntu SMP Wed Mar 11 15:43:49 UTC 2009 x86_64 GNU/Linux

lirc: 
0.8.4a-0ubuntu4~ppa2   (from [https://launchpad.net/~ubuntu-kennynet/+archive/ppa](https://launchpad.net/~ubuntu-kennynet/+archive/ppa))


Thanks,
Nir.

---

### Post by moptop on 2009-03-28
hard for me to tell from your latest, did you manage to make it work at all?  i'm trying now with a brnad-new jaunty install,  no luck yet...

matt

---

### Post by moptop on 2009-03-30
Hi,

status update:  after rebooting I *do* get /dev/lirc0 and /dev/lirc1, this with kenny's ppa lirc and lirc-modules-source packages.  

however: if I reload /etc/init.d/lirc, I get an error about the kernel modules:

matt@tehanu:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC              [fail] 
 * Loading LIRC modules                                 [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
----
also, 
irw refuses to connect.
Do you have nay suggestions?  this is  frustrating, and I feeel it's so close...  

thanks,

matt

---

### Post by levedge on 2009-03-30
I am at the same point with kenny's ppa modules on jaunty

Kernel version  2.6.28-11-generic 


root@ginaz:/# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 15c2:0038 SoundGraph Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@ginaz:/# ls -1 /dev/lirc*
/dev/lirc0
/dev/lirc1
/dev/lircd


Work:

Remote (didn't test the control pad yet)

Doesnt work

- knob
- LCD

Ill keep this post updated if I find something

Tks

SP

---

