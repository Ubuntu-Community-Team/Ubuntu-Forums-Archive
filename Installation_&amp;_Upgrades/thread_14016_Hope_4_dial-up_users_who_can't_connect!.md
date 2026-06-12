---
title: "Hope 4 dial-up users who can't connect!"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by thestarman on 2005-02-04
There's still hope for all (hardware) dial-up modem users who haven't been able to connect! ;-)
I had read all of the comments here, tried many of the suggestions, but nothing seemed to work!  Today, while looking through the **/etc/wvdial.conf** file, for some odd reason instead of seeing the "*ttyS4*" that my Analog (or *Hardware-type*) US Robotics 56Kbps Internal Modem had been assigned under my RedHat 9.0 installation, it said: "**ttyS14**" (14?).  I confirmed this was true by running the command:

[FONT=Fixedsys][B]root@ubuntu:/home/starman # dmesg |grep ttyS
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS14 at I/O 0xe800 (irq = 10) is a 16550A[/B][/FONT]

which showed me that at boot-up, Ubuntu was indeed using **ttyS14** for my modem, because I knew it was also on IRQ 10 beginning at 0xE800. (The **dmesg** command will show you almost everything that Ubuntu spits out to the screen at boot-up, and the " |grep ttyS " part means to display only the lines with the phrase "ttyS" in them!)

  After doing a bit of playing around with the "wvdial" command, I found that one of the modem strings had been causing errors and deleted it from the "wvdial.conf" file.  You can edit that file with this command:
**pico /etc/wvdial.conf** and following the instructions at the bottom of the screen after making changes; "**pico**" is an easier text editor to use than "**vi**" for most new Linux users.  Anyway, once I'd gotten rid of the offending "AT" string, I was able to enjoy the following interaction between my modem and ISP:
[FONT=Fixedsys]
root@ubuntu:/home/starman # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATM0 **[ATM0** will SILENCE most modem speakers**!]**
ATM0
OK
--> Modem initialized.
--> Sending: ATDTnnnnnnn
--> Waiting for carrier.
ATDTnnnnnnn
CONNECT 53333/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
UQKT2 xxxxx.xxxxx.xxxx.xxxxxxxxxx.com
login:
--> Looks like a login prompt.
--> Sending: [[[[My username]]]]
password:
--> Looks like a password prompt.
--> Sending: (password)
Connected
Exiting shell, and starting PPP session.
~[7f]}#@!}!}!} }<}!}$}%\}"}&} }*} } }%}&aW;a}'}"}(}"}1}$}%bz}4~
--> PPP negotiation detected.
--> Starting pppd at Fri Feb  4 05:10:09 2005
--> pid of pppd: 4124
--> Using interface ppp0
--> pppd: e[/FONT]
[[[etc. etc. it's still running right now!]]]

After that, I installed the "**Modem Lights**" applet (just right-click in any blank spot and choose "**+Add**" for a whole bunch of things!) and configured it to "ttyS14" instead of "ttyS4" and the lights immediately started flashing! Yeah!  Now I need to set it up so I don't need to enter that wvdial command everytime; I think the applet might be able to do that, but don't want to lose this posting before testing that! :-)

The Starman.

---

### Post by thestarman on 2005-02-04
:D  Yes, things are working out just fine today!  I went back to the selection: "Computer" ---> "System Configuration" ---> "Networking" and after entering S14 instead of S4 and closing the window, it started dialing and connecting again. If I can use "Modem Lights" to disconnect/connect from now on, then I'll be done with this and move on to my next project.  The Starman.

---

### Post by thestarman on 2005-02-04
PLEASE help:  OK, now that I'm connected.... I can't use "Modem Lights" to disconnect!  Funny!
Should there really be only "pon" and "poff" in those confg. boxes or something else?  What possible '.conf' file(s) might they control?  So, for now, I have to open the Networking configuration program again and turn things off and on from there I guess.  The Starman.

---

