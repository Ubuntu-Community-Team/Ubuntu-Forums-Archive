---
title: "Lirc is sloooowwww in 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by tcchris on 2010-10-13
I just upgraded my htpc to 10.10 minimal with xfce .
I use boxee on this box and since I upgraded the remote is very slow to respond sometimes . This is not boxee because even in irw it does it .
Sometimes the remote responds instantly , sometimes just a little slow , like windows , and sometimes you have to hit a button 5 or 6 times before it responds . I changed the batteries , the red light on the reciever lights each time you hit a button , it just doesn't always respond in linux .
This setup worked perfectly before I did the new install . 
MCE remote from a hvr 1600

---

### Post by tcchris on 2010-10-13
Is anyone else having problems with their remote in 10.10 ?

---

### Post by aliquis on 2010-11-07
Yeah, I'm experiencing the same issue. Ubuntu 10.10 clean install, MCE Remote is slow. Can't find out why? Any ideas anyone?

---

### Post by discoverpc on 2010-11-08
[http://forum.xbmc.org/showthread.php?p=627326](http://forum.xbmc.org/showthread.php?p=627326)
this helped me out with the 10.10 lirc issue 


Quote:
sudo dpkg-reconfigure lirc
then select
Quote:
Linux input layer (/dev/input/eventX)
on "IR transmitter" i picked none.

on "Custom event interface for your dev/input device: " open a new shell and run:

Quote:
cat /proc/bus/input/devices
you will face somethig like this:
Quote:
I: Bus=0003 Vendor=15c2 Product=0038 Version=0001
N: Name="iMON Remote (15c2:0038)"
P: Phys=usb-0000:00:0b.0-6/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/rc/rc0/input5
U: Uniq=
H: Handlers=kbd mouse1 event5
B: EV=100007
B: KEY=fff 0 0 400000 108c0320 2d50082 0 0 30000 4 119000 4196 14100801 809e1680 0 2000000 10004002
B: REL=103
select the event you want lirc to listen, in my case:
Quote:
/dev/input/event5
this enables IMON input driver to notify lirc the events, but i still don't understand how to let imon module listen rc6 and act as a mceusb module for my harmony-rc6 configured remote.
Last edited by lyka; 2010-10-16 at 02:42. 

then i restarted and did 

sudo dpkg-reconfigure lirc

and selected the mce remote again.

looks like the issue was in 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="-r"

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

now when i run /etc/init.d/lirc restart 
it works with no errors.

---

### Post by wjanik on 2010-11-08
Similar problem here.  I'm using the MCE USB receiver and one of the old TiVo "peanut" remotes.  Worked great in 10.04.

In my case, it's not that the response is slow but that it seems to drop a good number of events in MythTV (maybe this is how MythTV deals with slowness).  Sometimes it works great, others it just seems to do nothing unless I hit a button repeatedly.

This is not a clean install, but an upgrade from 10.04 on an nVidia ION.  dpkg-reconfigure didn't seem to help my case.

---

### Post by the_pod on 2010-11-22
Same issues.  Last two days I upgrades from 9.4 to 9.10 to 10.4 to... what the hey, everything is working well - 10.10.

Now remote is virtually worthless.

---

### Post by wilma92010 on 2010-11-29
Me too.

I am wondering whether there is a difference between 0.8.7 final release of lirc and 0.8.7~pre3-0ubuntu that is evidently installed with 10.10?

How would I upgrade?

Wilma

---

### Post by mitchell2345 on 2010-12-05
same problem here.  My remote that was great in 10.04 is SLOW in 10.10



mitchellisregreatingupgradedingto10.10.24

---

### Post by tcchris on 2010-12-05
I bought a harmony that seems to work fine , but the mce remote is still slow

---

### Post by tech_eric on 2010-12-27
I'm experiencing the same issues after upgrading to 10.10.  I've scoured the 'net and learned a lot about the new lirc maintainer, a few other posts with suggestions that just don't help, etc.

My issue seems to be limited to the TiVo peanut remote commands.  irw indicates that lirc just stops receiving events (from any remote) after hitting a few buttons on the TiVo remote, then comes back to life at random intervals.

I've tailed every log file for clues but nothing seems to be showing up.  I really don't want to go back to 10.04 (based on principle at this point)....

Anyone?

---

