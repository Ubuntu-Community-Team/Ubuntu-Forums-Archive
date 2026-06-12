---
title: "Vodacom 3G Card install"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by agentpt on 2005-05-06
I have just said cheers to Windows and  installed Ubuntu 5.04 on my laptop....installation looks successful. I'm a TOTAL newbie to Linux, but need to get my Option 3G datacard going so I can have webaccess. Does anyone know how to this? Also if there are any suggestions on a good place to go for first steps for beginners, I'll appreciate it greatly.. :smile:

---

### Post by sudhashen on 2005-05-16
Hiya

I've been at this forum to get my card working and have managed to do so but need to know if the card you have is a Novatel card?  I can see on the Vodacom site in SA that this is the case - if so ur in luck.

Procedure :
1) insert card and then open terminal and type tail /var/log/syslog - you can also do dmesg
my output :

May 16 21:40:37 localhost cardmgr[5800]: executing: 'modprobe -r serial_cs'
May 16 21:40:37 localhost udev[9507]: creating device node '/dev/ttyS2'
May 16 21:41:20 localhost cardmgr[5800]: socket 0: Serial or Modem
May 16 21:41:20 localhost cardmgr[5800]: executing: 'modprobe serial_cs'
May 16 21:41:21 localhost udev[9612]: removing device node '/dev/ttyS2'
May 16 21:41:21 localhost cardmgr[5800]: executing: './serial start ttyS2'
May 16 21:41:21 localhost kernel: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
May 16 21:41:21 localhost udev[9621]: creating device node '/dev/ttyS2'

if you do a sudo cardctl info or status you will get info on the card. Can't understand why theres no info on what's being done with the above output.

Anyways - now you know the device can is at /dev/ttyS2 - check in your instance what this will be.  You then then need to configure ppp for dialup.  Easiest way to do this is to sudo apt-get install gnome-ppp which is an interface for wvdial.  once that is downloaded and installed, execute gnome-ppp.

I don't know what your username,password is - you will need to find this out.
For all networks that I know off, dialup number is *99***#.
You then click on setup and choose where your device is mapped to ie mine is /dev/ttyS2 .  
Choose type as usb modem. 
Speed for 3g is 38400.
Click on init string - fill in this: AT+CGDCONT=1,"IP","(your network apn)", 

And then you are ready to connect!

btw - to safely eject ur card just sudo cardctl eject

There are some other funky init strings/configurations that allow you to choose 3g preferred but allow gprs etc and I'm busy investigating this - will update this when I can.

Good Luck!

---

### Post by thejonesfactor on 2005-09-01
hi there

i have followed these instructions up to the point of needing to instal gnome-ppp, but it does not appear to be on my Ubuntu CD, where can I download this from, or what is my next step

here are the commands and results so far:

craig@CraigLaptop:~$ tail /var/log/syslog
Sep  1 10:36:52 localhost cardmgr[6327]: executing: 'modprobe serial_cs'
Sep  1 10:36:52 localhost udev[8686]: removing device node '/dev/ttyS2'
Sep  1 10:36:52 localhost cardmgr[6327]: executing: './serial start ttyS2'
Sep  1 10:36:52 localhost kernel: ttyS2 at I/O 0x3e8 (irq = 3) is a 16550A
Sep  1 10:36:52 localhost udev[8695]: creating device node '/dev/ttyS2'
Sep  1 10:50:40 localhost -- MARK --
Sep  1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost synchronization, throwing 4 bytes away.
Sep  1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost sync at byte 1
Sep  1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 l ost sync at byte 1
Sep  1 10:50:57 localhost kernel: psmouse.c: TouchPad at isa0060/serio1/input0 -  driver resynched.
craig@CraigLaptop:~$ sudo cardctl info
Password:
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="Novatel Wireless"
PRODID_2="Merlin UMTS Modem"
PRODID_3="U630"
PRODID_4=""
MANFID=00a4,0276
FUNCID=2
craig@CraigLaptop:~$ sudo apt-get install gnome-ppp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-ppp
craig@CraigLaptop:~$


thanking you in advance

thejonesfactor

---

### Post by Divan Santana on 2008-06-20
simply install the vodafone "official" software from:
[https://forge.betavine.net/frs/?group_id=12&release_id=11](https://forge.betavine.net/frs/?group_id=12&release_id=11)

I used the 2.0 beta3 and it worked on a few laptops I tried! :)

---

