---
title: "Netbook will not boot from USB"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Last Tango on 2009-12-28
I have no idea what the problem is.  It can read the USB stick fine from both Windows XP and the Jolicloud installation I've installed on it, but it won't read it when I boot the computer up.  When I turn off all boot devices except for USB it doesn't read it (likewise for when USB is set to 1st priority).  When I run wubi.exe and try to install the thing that says something like 'help me boot from USB' it gets an error at the very end about not being able to extract something or another.  I get the exact same problem with Moblin too.  All of this used to work flawlessly, but for some reason it stopped.  Any ideas?

---

### Post by Charlietje on 2009-12-28
How have you installed it on the usb stick?
Is the usb partition active and bootable?

Try the next thing.
If you have already on an other pc ubuntu running, copy the ISO to that machine.
Then use the **USB Startup Disk Creater** from the **System - Administration** menu

Then choose your ISO and Ubuntu will format it the right way and copy the contents of the ISO the right way.


greetings

---

### Post by Last Tango on 2009-12-28
> **Charlietje said:**
> How have you installed it on the usb stick?
Is the usb partition active and bootable?

Try the next thing.
If you have already on an other pc ubuntu running, copy the ISO to that machine.
Then use the **USB Startup Disk Creater** from the **System - Administration** menu

Then choose your ISO and Ubuntu will format it the right way and copy the contents of the ISO the right way.


greetings
I installed it using my Xubuntu desktop computer and the USB Startup Disk Creator.  Is there something outside of that I need to do to make the partition on the USB stick active and bootable?  I don't recall ever having had to do that before...

---

### Post by presence1960 on 2009-12-28
> **Last Tango said:**
> I installed it using my Xubuntu desktop computer and the USB Startup Disk Creator.  Is there something outside of that I need to do to make the partition on the USB stick active and bootable?  I don't recall ever having had to do that before...

some people complain about unetbootin failing to make bootable USBs, but my experience is the Startup Disk Creator makes way more unbootable USBs than unetbootin does. Why not try unetbootin you can install it from terminal ```
sudo apt-get install unetbootin
```

---

### Post by Last Tango on 2009-12-28
I tried unetbootin as well, with exactly the same results.  I don't think the USB drive is the problem (although I could be wrong), but that for some reason my laptop doesn't like booting from the USB port anymore.  I also tried to do the thing with 'plop' here
[https://help.ubuntu.com/community/Installation/FromUSBStick#Cannot%20Boot%20the%20Computer%20From%20USB?](https://help.ubuntu.com/community/Installation/FromUSBStick#Cannot%20Boot%20the%20Computer%20From%20USB?)
but when I tried to run the .exe file, it said something about the .bin file being fragmented, and when I downloaded and ran the thing which was supposed to fix the .bin, it said that it couldn't defrag the .bin.

---

### Post by Charlietje on 2009-12-29
Did you try another USB stick?
Not all stick are capable of making them bootable...

Just a thought...

---

### Post by Ganymedes on 2009-12-29
I have tried with several distros, mostly with Ubuntu and Puppy Linux.

Most 1-2 Gb USB flash disks do boot. Most of 8 GB / 16 GB do NOT boot.

With 4 Gb disks it is a 50/50 chance - however, even with some Kingston 4 Gb disks which "look" the same, some of them do boot and some do not.

---

### Post by presence1960 on 2009-12-29
> **Ganymedes said:**
> I have tried with several distros, mostly with Ubuntu and Puppy Linux.

Most 1-2 Gb USB flash disks do boot. Most of 8 GB / 16 GB do NOT boot.

With 4 Gb disks it is a 50/50 chance - however, even with some Kingston 4 Gb disks which "look" the same, some of them do boot and some do not.

I just remembered something. I have a Biostar mobo and sometimes for reason(s) I have not figured out yet some bootable flash disks show up in my hard disk boot order in BIOS. I have to go into BIOS and make them the first hard disk to boot. Maybe that is what is happening to you. If they are listed in your hard disk boot order and you do not switch them to be first to boot in hard disk boot order they will not boot.

---

### Post by Ganymedes on 2009-12-29
Thanks! I have tried this on many computers, in the end they have booted from some usb stick without me changing the boot order.

I have to keep on eye on this matter - this may well be the explanation in some cases. Now that you mention this, I do remember that the boot order had some effect in one case.

---

### Post by Last Tango on 2009-12-29
> **Charlietje said:**
> Did you try another USB stick?
Not all stick are capable of making them bootable...

Just a thought...
I haven't, but it's the same USB I used to install every other linux distro I've tried.  Is it possible that some part of the stick is corrupted, and that's causing the problem?  I've no evidence to point to that being the case, but I've installed linux on the laptop before, with the same USB stick, so at this point I'm pretty much assuming that some small bit of code got broken.

---

### Post by nooby on 2010-01-02
This happens to me too. The Linux Mint 8.0 does boot up but the Ubuntu 9.10 does not. Both created using Unetbootin on a 2GB Kingston. 

I have also seen this BIOS list the Kingston data traveller so there is something going on there that goes wrong? 

Edit. It has happen with other distros too but I am not good at writing it down. I test every distro I find so not motivated to log every detail about those that fails.

---

### Post by Charlietje on 2010-01-02
Is it the last release of NBR?
I remember that I tries to install 9.04 NBR and it didn't work on my netbook.
It booted, but in the boot process it crashed

With the latest release 9.10 it installed like a charm, and I must say the interface is better too.

---

### Post by nooby on 2010-01-02
The version I had was a remastering of Karmic Koala 9.10 with Swedish translation to help those even more challenged by english than I am. 

So something could have goon bad there but his remaster of Linux Mint worked very well

---

### Post by Last Tango on 2010-01-02
> **Charlietje said:**
> Is it the last release of NBR?
I remember that I tries to install 9.04 NBR and it didn't work on my netbook.
It booted, but in the boot process it crashed

With the latest release 9.10 it installed like a charm, and I must say the interface is better too.
It is 9.10 that I'm trying to install, so yes.

---

### Post by pietpaardebloem on 2010-01-07
I recognize the problem. bought an eeepc today and was struggling in the same way to get UNR installed (karmic). 
Till i found out that besides the boot device priority sequence, there also appears a hard disks drives option (in the BIOS under the boot device priority). this submenu; I quote *specifies the boot device priority sequence from available hard drives.*
it appeares when starting the computer while the usb drive is connected and it lists my usb drive as a _hard drive_, but as the 2nd drive. after changing it to the 1st drive booting went perfect! :D
note: this hard disks drive option did not appear in the BIOS menu when starting the computer without the usb drive connected! making it difficult to find.

you might give it a try.

Piet Paardebloem

---

### Post by pietpaardebloem on 2010-01-09
Found another option (at least for my eeepc 1005ha).
put your usb device in the computer, switch it on and
hit the escape buton (instead of the f2 for entering the BIOS), then you get a small window where you can choose from which device you want to boot.
maybe it works on other netbooks too

Piet

---

### Post by MayaMouse on 2010-07-09
> **pietpaardebloem said:**
> Found another option (at least for my eeepc 1005ha).
put your usb device in the computer, switch it on and
hit the escape buton (instead of the f2 for entering the BIOS), then you get a small window where you can choose from which device you want to boot.
maybe it works on other netbooks too

Piet
Piet, you save me a lot of time. I am sure I would have spent hours restarting the netbook trying to get it to boot from the USB. Thanks a million.

---

