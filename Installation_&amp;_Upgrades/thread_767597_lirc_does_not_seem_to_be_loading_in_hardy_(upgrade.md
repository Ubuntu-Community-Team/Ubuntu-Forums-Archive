---
title: "lirc does not seem to be loading in hardy (upgrade from gutsy)"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2008-04-25
I just upgraded from Gutsy to Hardy.

Lirc doesn't seem to want to load/run.  

```
[   46.412902] lirc_dev: disagrees about version of symbol struct_module
[   46.413591] lirc_i2c: disagrees about version of symbol struct_module
[  150.498761] lirc_dev: disagrees about version of symbol struct_module
[  150.505809] lirc_dev: disagrees about version of symbol struct_module
[  150.508594] lirc_i2c: disagrees about version of symbol struct_module

```


It sounds like the following error occurs when the headers do not match the kernel?  It that correct?
Could this be a problem with the repositories?

I don't know what to do from here.  Any suggestions?  

Thanks.

---

### Post by ozite on 2008-04-26
I am experiencing the same problem.  Did you happen to find a solution?

dmesg | grep -i lirc 
[   47.438608] lirc_dev: disagrees about version of symbol struct_module
[   47.466036] lirc_i2c: disagrees about version of symbol struct_module
[  465.284937] lirc_dev: disagrees about version of symbol struct_module
[  465.291459] lirc_dev: disagrees about version of symbol struct_module
[  465.292111] lirc_i2c: disagrees about version of symbol struct_module

---

### Post by dentaku65 on 2008-04-27
You must add lirc_dev under MODULES in /etc/lirc/hardware.conf
```
MODULES="lirc_i2c"
```
became
```
MODULES="lirc_dev lirc_i2c"
```

In my case (upgraded from Gutsy to Hardy) was necessary to remove this package too:
```
sudo apt-get --purge remove dkms
```

---

### Post by kacheng on 2008-04-27
Thanks!  This seems to help.

I no longer get the 'disagrees about version of symbol struct_module' errors after uninstalling dkms and rebooting.

However, the remote still does not work.  

$ sudo lircd
lircd: WARNING: config file contains no valid remote control definition

BUT

[B]# /etc/lirc/hardware.conf
[/B]#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
:
:

[B]# /etc/lirc/lircd.conf 
[/B]# Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

[B]# /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge
[/B]#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and
# original Hauppauge TV cards !!!
#
<remote code definitions>
:
:

Any ideas?

---

### Post by dentaku65 on 2008-04-27
Hi,
your hardware.conf seems incomplete; did you re-run:
```
sudo dpkg-reconfigure lirc
```
Anyway this is my hardware.conf (Hauppauge too):
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc"
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Command IR : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc/1"
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```
As you can see (at least in my case) the REMOTE_DEVICE and the TRANSMITTER_DEVICE changed the dev position

More strange: lirc is working, but during the bootup give me "fail" as daemon, but in KDE I create an Autostart entry for "irexec"
```
sudo ln -s /usr/bin/irexec ~/.kde/Autostart/irexec
```
and it works! Despite the error in the bootup process.

In any case the lirc is there on my box:
```
dmesg |grep lirc
```
```

[   48.889995] lirc_dev: IR Remote Control driver registered, at major 61
[   49.021645] lirc_i2c: chip 0x10005 found @ 0x18 (Hauppauge IR)
[   49.021672] lirc_dev: lirc_register_plugin: sample_rate: 10
[   49.163904] lirc_dev: lirc_register_plugin: sample_rate: 20
[   49.165676] lirc_cmdir: freq set to 38000Hz

```

---

### Post by kacheng on 2008-04-27
Thanks. I tried to run the command you suggest:

```
**$ sudo dpkg-reconfigure lirc**
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC       .conf                   [fail]
 * Reloading kernel event manager...                                     [ OK ]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

Checking /etc/lirc/hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
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

```

And it doesn't looks like lirc is running at all. 
```
**dmesg | grep lirc**
``` 
gives nothing.

Everything seems like it's in order?

---

### Post by dentaku65 on 2008-04-27
What is the output of:
```
ls -al /dev/lirc*
```

---

### Post by kacheng on 2008-04-27
I get:

```
**$ ls -al /dev/lirc***
srw-rw-rw- 1 root root 0 2008-04-27 04:50 /dev/lircd

```

---

### Post by dentaku65 on 2008-04-27
So, as I wrote above the REMOTE_DEVICE is changed; replace the entry in hardware.conf:
```
REMOTE_DEVICE="/dev/lirc0"

```
into
```
REMOTE_DEVICE="/dev/lirc/0"
```
Then reload lirc
```
sudo /etc/init.d/lirc restart
```

Is the output ok?

---

### Post by kacheng on 2008-04-27
Hmm,

I made the change, and tried:

REMOTE_DEVICE="/dev/lirc/0"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_DEVICE="/dev/lircd"
REMOTE_DEVICE="/dev/lircd/0"

but there is no change in output of
```
**$sudo /etc/init.d/lirc restart**
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
**$ dmesg | grep lirc**
<no output>

```

Anything else I should check?

---

### Post by dentaku65 on 2008-04-27
Can you post your actual hardware.conf file? There shold not exist /dev/lircd/0 but only /dev/lirc/0 as remote.

---

### Post by kacheng on 2008-04-27
Here you are:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
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
```

---

### Post by dentaku65 on 2008-04-27
AFAIK seems correct the .conf file; I do not understand where you put the /dev/lircd/0 entry as you said before.

You can try a raw test:
```
sudo killall -9 lircd
```
```
sudo killall -9 lircmd
```
```
sudo /usr/sbin/lircd --device=/dev/lirc/0
```
```
sudo /usr/sbin/lircmd
```
```
irw
```
Noy you can push some buttons on IR and the output should be on the console something like this:
```
0000000000001f95 00 DOWN grayHauppauge
0000000000001f95 01 DOWN grayHauppauge
0000000000001f95 02 DOWN grayHauppauge
0000000000001f95 00 DOWN grayHauppauge

```
CTRL-C to terminate

If so, the lirc + device is working; we have to understand what is wrong in the hardware.conf.

---

### Post by kacheng on 2008-04-27
Ah sorry if I was not clear.  I tried each of those four options
 REMOTE_DEVICE="/dev/lirc/0"
 REMOTE_DEVICE="/dev/lirc0"
 REMOTE_DEVICE="/dev/lircd"
 REMOTE_DEVICE="/dev/lircd/0"
one at a time - partly because I am unsure of the syntax for the lirc devicenames.


So here is what I've done and the output:

```
$ sudo killall -9 lircd
lircd: no process killed
$ sudo killall -9 lircmd
lircmd: no process killed
$ sudo /usr/sbin/lircd --device=/dev/lirc/0
$ sudo /usr/sbin/lircmd
$ irw
connect: Connection refused
$ sudo killall -9 irw
irw: no process killed
$ irw
connect: Connection refused
$ dmesg | grep lirc
<no output>
$
```

What are your thoughts?

---

### Post by dentaku65 on 2008-04-27
mmm... we can try mode2
```
sudo mode2 -d /dev/lirc/0
```
and push a few buttons on the remote, if everything is working, you should see something like:
```
 code: 0x17a5
 code: 0x17a5
 code: 0x1fa5
 code: 0x1fa5
```
CTRL-C to stop

---

### Post by kacheng on 2008-04-27
Okay <big sigh>

```

$ sudo mode2 -d /dev/lirc/0
mode2: error opening /dev/lirc/0
mode2: No such file or directory
$ sudo /etc/init.d/lirc restart
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

What's up with the LIRC kernel modules?

---

### Post by dentaku65 on 2008-04-27
> **kacheng said:**
> Okay <big sigh>

```

$ sudo mode2 -d /dev/lirc/0
mode2: error opening /dev/lirc/0
mode2: No such file or directory
$ sudo /etc/init.d/lirc restart
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

What's up with the LIRC kernel modules?

BTW, what exatly you have under /dev/lirc ?
```
ls -ali /dev/lirc*
```

Seems that the you don't have devices for IR on our box; I'm afraid you must reconfigure lirc
```
sudo dpkg-reconfigure lirc
```
Choosing Hauppauge TV card as REMOTE and Command IR : Direct TV Receiver as TRANSMITTER
then you can check the hardware.conf file generated on your box with this working one:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc"
MODULES="lirc_dev lirc_i2c"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Command IR : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_cmdir"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc/1"
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

---

### Post by kacheng on 2008-04-27
```
$ ls -ali /dev/lirc*
21441 srw-rw-rw- 1 root root 0 2008-04-27 08:44 /dev/lircd
20279 prw-r--r-- 1 root root 0 2008-04-27 08:29 /dev/lircm

```

```
$ sudo dpkg-reconfigure lirc
[sudo] password for kacheng:
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Reloading kernel event manager...                                     [ OK ]
 * Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

I changed the configuration to some other receiver and saved it, then re-ran it and changed the configuration back to Hauppauge TV Card.  
Note that the REMOTE_DEVICE line is changed back to /dev/lirc0 from /dev/lirc0.
The resulting hardware.conf is:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
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

```


I'm not sure, but [this unhelpful bug report]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/216781") shows a similar problem.
If I were to purge and reinstall all related packages, perhaps that will help?  What do I need to purge? lirc, lirc-x, anything else?

I'm also not sure about [this bug report]("http://https://bugs.launchpad.net/mythbuntu/+bug/206609"), but here is my lirc.conf file for a look-see.

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

#Configuration for the Hauppauge TV card remote:
include /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

```


I've rebooted the box and there doesn't seem to be any change.  Everything looks alright doesn't it?

---

### Post by dentaku65 on 2008-04-27
The result of ls -ali /dev/lirc* shows that you don't have devices there, not /dev/lirc0 nor /dev/lirc/0 
These devices are created when you do the "dkpg-reconfigure lirc" operation 

Maybe reinstall packages first:
```
sudo  apt-get --reinstall install ncurses-dev lirc
```

---

### Post by ozite on 2008-04-27
I am having the same difficulties and observed the same errors as the original poster.  I found that 
```
dpkg -l | grep lirc
```
gave the following:
[HTML]ii  liblircclient0                             0.8.3~pre1-0ubuntu7                                LIRC client library
ii  lirc                                       0.8.3~pre1-0ubuntu7                                Linux Infra-red Remote Control support
ii  lirc-modules-2.6.17-10-generic             0.8.0-9ubuntu0unofficial1+2.6.17.1-10.34           Linux Infra-red Remote Control support (bina
ii  lirc-modules-2.6.17-11-generic             0.8.0-9ubuntu0unofficial1+2.6.17.1-11.35           Linux Infra-red Remote Control support (bina
ii  lirc-modules-2.6.20-15-generic             0.8.1+cvs20070310-0ubuntu2+2.6.20-15.27            Linux Infra-red Remote Control support (bina
ii  lirc-modules-2.6.20-16-generic             0.8.1+cvs20070310-0ubuntu2+2.6.20-16.28            Linux Infra-red Remote Control support (bina
ii  lirc-modules-2.6.22-14-386                 0.8.2-0ubuntu8+2.6.22-14.46                        Linux Infra-red Remote Control support (bina
ii  mythbuntu-lirc-generator                   0.20-0ubuntu1                                      Mythbuntu Lirc Configuration Generator
[/HTML]

I'm a beginner, so I don't quite understand why it switched from *-generic to *-386.

Any ideas on how to solve this?

---

### Post by ozite on 2008-04-27
I forgot to mention, ```
uname -r
``` gives 2.6.24-16-generic.

---

### Post by uvahaole on 2008-04-27
kacheng, I was experiencing the same problem.  I only had device /dev/lircd present (no /dev/lirc0).  Initially, running ```
sudo dpkg-reconfigure lirc
``` did not fix the issue.  However, I then deleted /etc/lirc/lircd.conf, reran ```
sudo dpkg-reconfigure lirc
```and now my devices and lircd.conf are generated correctly and the remote works once again.

---

### Post by kacheng on 2008-04-27
dentaku65,
Thanks for all the guidance.  However, the last one, reinstalling those suggested packages, didn't seem to affect anything.

uvahaole,
Thanks for the tip, I had to delete both /etc/lirc/lircd.conf and /etc/lirc/hardware.conf to get the file to regenerate.  Now the modules seem to load.  

```
$ sudo dpkg-reconfigure lirc
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Reloading kernel event manager...                                     [ OK ]
 * Starting remote control daemon(s) : LIRC                              [ OK ]
 * Starting remote control mouse daemon : LIRCMD                         [ OK ]

```

However, I still do not get devices created, nor do I see anything in dmesg about lirc. irw still gives 'connection refused'.  Am I going crazy?

In the meantime, I'll try some of dentaku65's earlier suggestions again, to try to see if I can get lircd running manually.

---

### Post by kacheng on 2008-04-27
Still no love.  
It looks like executing irw is killing the lircd daemon?


```
$ sudo /usr/sbin/lircd --device=/dev/lirc/0
$ irw
$ irw
connect: Connection refused

```

---

### Post by uvahaole on 2008-04-30
kacheng, if a device is not generated, irw is not going to work. I am guessing you also are not getting anything if you type 
```
lsmod | grep -i lirc
```
Does /etc/udev/rules.d/ contain any files related to lirc?  I have 85-lirc.rules with 544 permissions.  The contents are
```
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"
```
If you do not have that file, try creating it and restarting. If you do have that file, try manually adding the device.
```
mknod /dev/lirc0 c 61 0
```

---

### Post by kacheng on 2008-05-01
You are correct in that there is no result from

```
lsmod | grep -i lirc
```

I do have /etc/udev/rules.d/85-lirc.rules.  It also has:

```
ACTION=="add", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc restart udev"
ACTION=="remove", KERNEL=="lirc[0-9]", RUN="/etc/init.d/lirc stop udev"
```

So I tried manually adding the device as suggested and here are my results:
```
~$ sudo mknod /dev/lirc0 c 61 0
~$ lsmod | grep -i lirc
~$ ls /dev/lirc*
/dev/lirc0  /dev/lircd  /dev/lircm
~$ dmesg|grep lirc
~$ irw
connect: Connection refused
~$ sudo irw
connect: Connection refused

```

---

### Post by uvahaole on 2008-05-01
Try this sequence, so you run lirc daemon after creating the device.
```
~$ sudo mknod /dev/lirc0 c 61 0
~$ sudo /usr/sbin/lircd --device=/dev/lirc0
~$ lsmod | grep -i lirc
~$ dmesg | grep -i lirc
~$ irw

```

---

### Post by kacheng on 2008-05-01
I'm not sure if we're making progress or not...

```
~$ sudo mknod /dev/lirc0 c 61 0
mknod: `/dev/lirc0': File exists
~$ sudo /usr/sbin/lircd --device=/dev/lirc0
~$ lsmod | grep -i lirc
~$ dmesg | grep -i lirc
~$ irw
~$ irw
connect: Connection refused
```

---

### Post by uvahaole on 2008-05-01
No progress. Anything with the following?
```
~$ sudo modinfo lirc_i2c
```

---

### Post by muldy on 2008-05-01
Same problem here, but with a mac mini remote.

After upgrading remote stopped working.

Same problems.
:confused:

my hardware.conf (generated by lirc reconfigure)
```

REMOTE="Apple Mac mini USB IR Receiver"
REMOTE_MODULES=""
REMOTE_DRIVER="macmini"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="apple/lircd.conf.macmini"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"


```

and lircd.conf:

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

#Configuration for the Apple Mac mini USB IR Receiver remote:
include /usr/share/lirc/remotes/apple/lircd.conf.macmini


```

---

### Post by muldy on 2008-05-01
Only thing that reacts to remote button presses is:

```

sudo cat /dev/hidraw3

```

Starts printing weird chars for each button press.

---

### Post by kacheng on 2008-05-01
@uvahaole

```
~$ sudo modinfo lirc_i2c
modinfo: could not open /lib/modules/2.6.24.16-generic/updates/dkms/lirc_i2c.ko: No such file or directory
```

> **uvahaole said:**
> No progress. Anything with the following?
```
~$ sudo modinfo lirc_i2c
```

---

### Post by uvahaole on 2008-05-02
The kernel still thinks lirc_i2c.ko is in /lib/modules/2.6.24.16-generic/updates/dkms.  That directory is probably empty since you removed dkms early in this thread. Module dependencies need to be rebuilt:
```
$ sudo depmod
```
FYI, the location of my lirc_i2c.ko is /lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_i2c.ko

---

### Post by kacheng on 2008-05-02
Yippee, we are moving forward again!

So rebuilding the dependencies has worked to get lirc_i2c.ko linked correctly.

After restarting lirc, I see that the lsmod and dmesg are finally showing entries!
modinfo shows the correct entry now.
Now we just need to get irw working!

What shall I do next?

```
$ sudo depmod
$ sudo /etc/init.d/lirc restart
 * Stopping remote control mouse daemon: LIRCMD                          [fail]
 * Stopping remote control daemon(s): LIRC                               [fail]
 * Starting remote control daemon(s) : LIRC                              [ OK ]
 * Starting remote control mouse daemon : LIRCMD                         [ OK ]
$ lsmod | grep -i lirc
lirc_dev               15732  0
$ dmesg | grep -i lirc
[96316.930489] lirc_dev: IR Remote Control driver registered, at major 61
$ sudo modinfo lirc_i2c
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/input/misc/lirc_i2c.ko
license:        GPL
author:         Gerd Knorr, Michal Kochanowicz, Christoph Bartelmus, Ulrich Mueller, Stefan Jahn, Jerome Brock
description:    Infrared receiver driver for Hauppauge and Pixelview cards (i2c stack)
srcversion:     BD764D95FF7997B3F7B4F3E
depends:        i2c-core,lirc_dev
vermagic:       2.6.24-16-generic SMP mod_unload 586
parm:           minor:Preferred minor device number (int)
parm:           debug:Enable debugging messages (bool)
$ irw
connect: Connection refused

```

---

### Post by uvahaole on 2008-05-03
Only lirc_dev is getting loaded when you start the daemon; lirc_i2c is not.  Try 
```
$ sudo modprobe lirc_i2c
```
If that helps, do you have both lirc_dev and lirc_i2c listed in /etc/lirc/hardware.conf?

---

### Post by kacheng on 2008-05-04
We're in business!

So 'sudo modprobe lirc_i2c' seems to get lirc_dev running.

```
$ sudo modprobe lirc_i2c
$ dmesg | grep -i lirc
[96316.930489] lirc_dev: IR Remote Control driver registered, at major 61
[242744.936685] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[242744.936714] lirc_dev: lirc_register_plugin: sample_rate: 10
$ irw
00000000000017c1 00 1 hauppauge_pvr
00000000000017c2 00 2 hauppauge_pvr
00000000000017c3 00 3 hauppauge_pvr
00000000000017c4 00 4 hauppauge_pvr
00000000000017c4 01 4 hauppauge_pvr
00000000000017c5 00 5 hauppauge_pvr
00000000000017c6 00 6 hauppauge_pvr
00000000000017c7 00 7 hauppauge_pvr
00000000000017c8 00 8 hauppauge_pvr
00000000000017c9 00 9 hauppauge_pvr
00000000000017c9 01 9 hauppauge_pvr
00000000000017c0 00 0 hauppauge_pvr
00000000000017c0 01 0 hauppauge_pvr
00000000000017c0 02 0 hauppauge_pvr
00000000000017e0 00 Ch+ hauppauge_pvr
00000000000017e1 00 Ch- hauppauge_pvr
00000000000017e1 01 Ch- hauppauge_pvr
00000000000017d0 00 Vol+ hauppauge_pvr
00000000000017d1 00 Vol- hauppauge_pvr
```

And to answer your question, yes both lirc_dev and lirc_i2c are in /etc/lirc/hardware.conf.

```
$ more /etc/lirc/hardware.conf
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```


Great so far!  
Ok, so how do I ensure that both modules load at startup?
And how did the upgrade from Gutsy to Hardy break this?

Thanks again.

---

### Post by kacheng on 2008-05-07
Got it working!
Minor change needed in the /etc/lirc/hardware.conf file:
/dev/lirc0 needed to be /dev/lirc/0

Thanks everyone for all your help.

$ cat /etc/lirc/hardware.conf
```

REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

---

### Post by tkoopa on 2008-07-27
thanks everyone, I also had the problem after upgrading and editing hardware.conf to replace REMOTE_DEVICE="/dev/lirc0"
 by REMOTE_DEVICE="/dev/lirc/0" fixed it for me

---

