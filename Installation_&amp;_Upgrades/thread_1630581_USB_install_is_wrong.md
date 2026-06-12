---
title: "USB install is wrong"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by anechoic on 2010-11-25
I wanted to do a clean install of 10.10 on my Dell netbook (SSD drive and no DVD or CD drive) so I made a LiveUSB by selecting '10.10_Live' using UNetbootin on the 10.04 system running on the netbook.

I made a backup of my '/home' partition and essentials on my '/' partition via Jungledisk

I did a sudo dpkg --get-selections > /home/user/package.selections
and made a 'save markings as' in Synaptic (which created a 0b doc - but that's another story) and copied my repositories file.

I got through the install in Ubuntu 10.10 but messed up on mounting my '/home' so I went back and corrected it on a second pass at a clean install

All went well except for a few minor annoyances and a modprobe error I got while booting - but I found a fix online which seemed to work

but it was when I tried to add newer kernels (in an attempt to fix the modprobe error mentioned above) and found that none of them were showing up in the list in Startup-Manager app that caused me to check the version of GRUB I was using.

I found that I was still using GRUB and not GRUB2.

So my questions are as follows:
- is there a known issue (I Googled and didn't find anything) about the Live USB created with UNetbootin using an old 10.10 iso?
    -- I will download a newer iso and reinstall to see if this fixes things
- is there an easy way to just upgrade from GRUB to GRUB2?
   -- all the methods I found were confusing and unclear - maybe someone can point me to a quintessential 'HOW TO upgrade to GRUB2' post somewhere?

thanks in advance!!
:)
KC

---

### Post by sikander3786 on 2010-11-25
> I found that I was still using GRUB and not GRUB2.

A clean install of 10.10 should definitely install Grub2 and not the Grub Legacy. I feel you chose the option not to install Grub somehow. But then how would you be able to boot that successfully :-k

How did you know that you are running Grub Legacy and not Grub2?

> is there a known issue (I Googled and didn't find anything) about the Live USB created with UNetbootin using an old 10.10 iso?

None to my knowledge until you use the latest version of unetbootin.

> I will download a newer iso and reinstall to see if this fixes things

Instead of that, run an MD5SUM on the existing image and if it is corrupt, you'll definitely need to re-download. But if ok, it mean it is OK.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> is there an easy way to just upgrade from GRUB to GRUB2?

We first need to make sure which version of Grub are you currently running. You can help us know that by posting the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything related to boot and Grub and therefore we'll be able to advise accordingly. Please wrap your output with proper code tags # from the post menu. [/code] at the end and [code] at the beginning.

> all the methods I found were confusing and unclear - maybe someone can point me to a quintessential 'HOW TO upgrade to GRUB2' post somewhere?

Easiest one here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But if you post the output of bootinfoscript, we'll be able to give you the exact commands and then you can just copy/paste them in your terminal.

---

### Post by itang sanjana on 2010-11-25
Are you sure about this legacy grub? try ```
sudo grub-install -v
``` GRUB 2 should display a version number of 1.96 or later. Legacy GRUB is version 0.97.

> **anechoic said:**
> ..
- is there an easy way to just upgrade from GRUB to GRUB2?
..

See [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202) pretty much clear there.

HTH

---

### Post by anechoic on 2010-11-25
I did a grub-install -v 

which is how I found out I was running a legacy version

and no I didn't do anything wrong on the install

since IIRC the Ubuntu install for 10.10 doesn't give you any options to install a legacy version of GRUB
:)

---

### Post by anechoic on 2010-11-25
thanks to all who pointed me to the simple and easy 
Synaptic grub-pc install
although finding the right kernel and Broadcom wireless driver combination took a while after that
thanks again!
:)

---

