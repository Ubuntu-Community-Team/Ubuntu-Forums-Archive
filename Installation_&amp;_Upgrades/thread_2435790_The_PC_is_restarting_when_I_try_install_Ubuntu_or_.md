---
title: "The PC is restarting when I try install Ubuntu or Try Ubuntu without installing it"
date: 2020-01-26
forum: Installation &amp; Upgrades
---

### Post by ghunterstar1234 on 2020-01-26
Hello,I had tried to install on a old PC that has 2GB ram ,Pentium 4, 200GB HDD and a AMD GPU(and it s 32bit).It had worked before,but since I changed the case of the computer and format the HDD is restarting when I try to install.I had tried everything: I have changed the USB drive and they are working fine on other computers,I had tried old versions of Ubuntu,I had tried to format the usb from FAT32 to FAT16 ,but nothing happend and I tried Lubuntu and other lightweight operating systems.Can someone help me?

---

### Post by guiverc on 2020-01-26
I have a pentium IV system I still use for testing (mainly Lubuntu & Xubuntu).

I would firstly confirm your ISO was perfect,

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

 then validate your install media write ie. 

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

where CD refers to whatever media you use, be it CD/DVD/hdd/ssd/thumb-drive

Other alternative links :
[https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)

If you have trouble testing your media on that box; I'd use another box to test it, if you don't get a pass on either box - consider the media as failed (bad write to install media).

Assuming both ISO & media passes the following are my thoughts (I suspect it's a the ISO wasn't written to your media firstly)

If you just changed case; I'd probably re-seat cables & other hardware stuff (assuming you did a cap-check on motherboard etc) just in case dust got caught inside connectors during move.

My hp dx6120mt (mini-tower, pentium 4 dual core, 3gb, winfast clone of nvidia 7600gt) has had installed Lubuntu up to 19.04, Xubuntu up to 19.04, other flavors up to 18.04.4 (and even had a Lubuntu 19.04 bumped to 19.10) so I'd be suspicious of your hardware change personally.  Also my memory increase was only semi-recent; most of the testing was done using 1.5gb ram.

---

### Post by hk42 on 2020-01-26
Hi
That old PC had an original OS is it still working ?
Linux can't be expected to work miracles .
Keeping the original OS on any device is the only way to expect
servicing of it.
It is a very good way to sort hardware from software problems.

---

### Post by CatKiller on 2020-01-26
> **ghunterstar1234 said:**
> It had worked before,but since I changed the case of the computer and format the HDD is restarting when I try to install.

It sounds most like you had problems with the assembly. Checking that you've got the motherboard standoffs in the right place, reseating everything, and blowing out any metal shavings from screws would be my first steps.

---

### Post by mörgæs on 2020-01-26
> **hk42 said:**
> 
Keeping the original OS on any device is the only way to expect servicing of it.


What? The main reason for running this website is that people want to use something else than the original OS.

---

### Post by ghunterstar1234 on 2020-01-27
Thanks everyone for the advices.I had taken out the mother board the case and it worked!!

---

### Post by CelticWarrior on 2020-01-27
> **mörgæs said:**
> What? The main reason for running this website is that people want to use something else than the original OS.

Quite true, sir.

But it's also true that almost all customer support of the major brands refuse to troubleshoot/service without the original OS. In this case, if still in warranty, and trying to reinstall the original OS would probably have the same result so they would have to service it anyway.

It also happens the other way around: Many years ago I had an Acer notebook affected by the infamous bulging capacitors industry wide problem. Having a dual-boot with Linux actually saved me a lot of time in the call because - lucky me - the agent understood immediately that a problem occurring in Windows and Linux wasn't software/OS related and proceeded to schedule the pick up. I wonder how long the call would have been if I had only the original OS and the agent following their "script" of, in this case, useless diagnostics.

---

### Post by hk42 on 2020-01-28
> **mörgæs said:**
> What? The main reason for running this website is that people want to use something else than the original OS.
If you need any kind of servicing on a device where you totally removed the original software
i wish you luck.
Even if you installed W10 on a W7 computer.
But Linux allowed multi-boot since the beginning.
Even flashing the Bios on a PC can be impossible without the original software.
Destroying the original software is stupid as you paid for it and won't get your money back.

---

### Post by mörgæs on 2020-01-29
The guarantee for a Pentium 4 ran out many years ago so there will not be any support. It was probably born with Windows 2000 or XP so plenty of reasons to get rid of them.

Original poster, please mark the thread solved.

---

