---
title: "How to: Set up a Dial-up connection"
date: 2004-12-26
forum: Installation &amp; Upgrades
---

### Post by yaro on 2004-12-26
The Ubuntu Live CD installs without problems, how do I set up a modem dial-up connection?
Any help appreciated

Yaro

---

### Post by FXWGBill on 2004-12-26
Yeah, this is the same problem I have. I followed the procedure for PPPconfig and it doesn't autodetect my modem.  Then when I manually set it, it appears there is no support for the com ports, which I totally don't understand.  I would think that should be a pretty standard feature in any OS.  I guess a lot of folks have gone to using the USB port, but I bet the bulk of folks that are contemplating this sort of move have older machines.  

I am also very curious if the full version has any support for the com ports.  I was planning on doing a full install of Abuntu after the first of the year, but if there is no easy way for me to get this going, I may have to look into something else.  I have looked and looked through the entire forum and a couple others also, and I don't see this issue addressed anywhere...  


Anyway...  Let's see what happens... I guess it's quite possible  it's my machine...

FX

---

### Post by az on 2004-12-26
Windows calls them com ports.  The rest of the world calls them serial ports.  Whatever.

Com1 = /dev/ttyS0
Com2 = /dev/ttyS1
Com3 = /dev/ttyS3
and so forth...

In Unix, everything is a file.  You have the ability to access hardware as though it were a file.

The problem here is that you may have a software modem (winmodem)  Many winmodems have linux support.  Most of this support is non-free (either you have to pay, or the provided drivers are not distributed with the source code or a free licence).  See the how-to forums for more...  Look for linmodem.

---

### Post by FXWGBill on 2004-12-27
I understand this.... /dev/ttyS2   in my case.....    You missed the whole point though...  It doesn't work.   I do NOT have a winmodem.... the modem is on ttyS2 and an IRQ of  10.   I am trying to remember exactly how it was worded; I'll  have to boot it back up to get it just right, but basically it acted like it didn't have a clue what I was talking about.  It was like something software wise was missing.   I tried the other ports and got the same response...  I will boot up Ubuntu here in a minute and get exactly what it is saying...  


FX

---

### Post by az on 2004-12-27
I do not understand what you say your problem is.  Your machine does not recognise your modem?

Show the output of
sudo lspci

Also, how did you configure your modem?  The networking app or the command line (pppconfig)?

---

### Post by rduch on 2004-12-27
I am having issues here as well. I have a US Robotics 5610B internal modem that is supposed to be compatible with any Linux kernal 2.3 or newer.  I set up my dial-up connection with gnome-ppp. The modem is listed in the device manager but gnome-ppp looks for the modem in the/dev/modem folder. There was no modem folder in /dev so I created one but I do not know how to get the data into the right place. It just occured to me... is /dev/modem a file or a folder? Does the modem need to be mounted somehow? I am slowly learnig this stuff so be gentle.

---

### Post by rduch on 2004-12-28
Well.. I am getting closer. I must be getting tired or stupid but all I needed to do was to click on the search button in gnome-ppp and it found my modem and completed the setup. The modem dialed out to the ISP server just fine but they were unable to complete a viable connection. 

The ppp log showed (abridged):
Do not support Terminal Server, please use PPP
PPP not enabled
sending ppp
...repeated several times

starting pppd
unable to run /usr/sbin/pppd
check permissions or specify a pppd path option in wvdial.conf
...repeated many times

I am stumped as to how or what to correct in the configuration file so that I can complete this set-up

Thanks to everyone again for this helpful forum.

---

### Post by az on 2004-12-28
/dev/modem should be a symlink to your real modem device.  It is put there by an installer that has detected your modem.  The ubuntu installer does not do this.

For your other issues, see:
[http://www.ubuntuforums.org/showthread.php?t=6319](http://www.ubuntuforums.org/showthread.php?t=6319)

---

### Post by 1016 on 2005-01-20
hi, I have a similar problem with a usb modem.
I have loaded the cdc-acm module and then build the device entry with mknod.
I have tried calling it /dev/usb/ttyACM0 as I've found in a forum 
and then and I've tried /dev/ttyACM0 too but in both cases it 
seems to be disconnected from the module.
there's something else I have to do ??  please help me.

---

