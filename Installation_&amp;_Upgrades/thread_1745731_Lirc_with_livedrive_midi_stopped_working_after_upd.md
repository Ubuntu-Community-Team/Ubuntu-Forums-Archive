---
title: "Lirc with livedrive_midi stopped working after update to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by n0rbi666 on 2011-05-01
Hi

I've got small problem.
On 10.10 everything was working ok, but after update to 11.04 lirc stopped working - irw does not recognize any keys :(
Tried reinstalling lirc, but it still does'nt work.
my hardware.conf :
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Creative LiveDrive midi"
REMOTE_MODULES=""
REMOTE_DRIVER="livedrive_midi"
REMOTE_DEVICE="/dev/snd/midiC0D1"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="creative/lircd.conf.livedrive"
REMOTE_LIRCD_ARGS="-d /dev/snd/midiC0D1 -H livedrive_midi"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

I've had simillar problem on Gentoo, after system recompiling : so it might be lirc compiled with new kernel ? Dunno :(

--add--

Oh, i forgot : cat /dev/snd/midiC0D1 shows some output, when I'm pressing keys on remote, so it's definitly not hardware problem, but problem with LIRC.

---

### Post by gunnarflax on 2011-05-10
Hi, I have the same problem. I posted about it [here]("http://ubuntuforums.org/showthread.php?t=1746059") and [here.]("http://forum.xbmc.org/showthread.php?t=100438") Let me know if you find a solution!

---

### Post by n0rbi666 on 2011-05-14
> **gunnarflax said:**
> Hi, I have the same problem. I posted about it [here]("http://ubuntuforums.org/showthread.php?t=1746059") and [here.]("http://forum.xbmc.org/showthread.php?t=100438") Let me know if you find a solution!

Do you have livedrive, too ?

---

### Post by bokkertoff on 2011-05-16
Hi. I solved this problem.

Here are the steps that you need to do to get it working.

It seems like the lirc livedrive_midi code has some problems with the gcc 4.5.2 compiler that ships with ubuntu 11.04.

I installed gcc 4.4.5 (sudo apt-get install gcc-4.4)

Next change to some directory where you can build the new package.

Next get the source: sudo apt-get source lirc

Change to the lirc directory: cd lirc-0.8.7

Set the CC evironment variable to gcc-4.4
In bash/sh "export CC=gcc-4.4".
In tcsh/csh "setenv CC gcc-4.4".

Try to build the package: dpkg-buildpackage -us -uc -nc

This will probably fail with dependency problems. The build environment has a lot of dependencies. On my system I had to add the following as well:

sudo apt-get install debhelper libusb-dev libasound2-dev libice-dev libsm-dev libirman-dev libftdi-dev autotools-dev portaudio19-dev devscripts quilt libxt-dev po-debconf

If there are any other dependencies, simply install them the same way as above.

Rerun "dpkg-buildpackage -us -uc -nc". If all goes well, you can do "cd .."
There should now be a few new packages in the current directory.

You can install it by doing "sudo dpkg -i lirc_0.8.7-0ubuntu4.1_amd64.deb". It should not be necessary to install the other packages.

My /etc/lirc/ hardware.conf looks like this:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Creative LiveDrive midi"
REMOTE_MODULES=""
REMOTE_DRIVER="livedrive_midi"
REMOTE_DEVICE="/dev/snd/midiC0D1"
REMOTE_LIRCD_CONF="creative/lircd.conf.livedrive"
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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""

```

Hope this works for you as well.

---

### Post by bokkertoff on 2011-05-16
Hi. I solved this problem.

Here are the steps that you need to do to get it working.

It seems like the lirc livedrive_midi code has some problems with the gcc 4.5.2 compiler that ships with ubuntu 11.04.

I installed gcc 4.4.5 (**sudo apt-get install gcc-4.4**)

Next change to some directory where you can build the new package.

Next get the source: [B]sudo apt-get source lirc
[/B] 
Change to the lirc directory: **cd lirc-0.8.7**

Set the CC evironment variable to gcc-4.4
In bash/sh "**export CC=gcc-4.4**".
In tcsh/csh "setenv CC gcc-4.4".

Try to build the package: **dpkg-buildpackage -us -uc -nc**

This will probably fail with dependency problems. The build environment has a lot of dependencies. On my system I had to add the following as well:

[B]sudo apt-get install debhelper libusb-dev libasound2-dev libice-dev libsm-dev libirman-dev libftdi-dev autotools-dev portaudio19-dev devscripts quilt libxt-dev po-debconf
[/B] 
If there are any other dependencies, simply install them the same way as above.

Rerun "**dpkg-buildpackage -us -uc -nc**". If all goes well, you can do "**cd ..**"
There should now be a few new packages in the current directory.

You can install it by doing "**sudo dpkg -i lirc_0.8.7-0ubuntu4.1_amd64.deb**". It should not be necessary to install the other packages.

My /etc/lirc/ hardware.conf looks like this:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Creative LiveDrive midi"
REMOTE_MODULES=""
REMOTE_DRIVER="livedrive_midi"
REMOTE_DEVICE="/dev/snd/midiC0D1"
REMOTE_LIRCD_CONF="creative/lircd.conf.livedrive"
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
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""

```Hope this works for you as well.

---

### Post by n0rbi666 on 2011-05-17
Hahaha it worked xD OMG I'm so happy xD
Thanks ! Big thanks !

BTW I've had to do :
```
rm /usr/bin/gcc
ln -s /usr/bin/gcc-4.4 /usr/bin/gcc
```
because export did'nt worked. 

Thanks once again !

---

