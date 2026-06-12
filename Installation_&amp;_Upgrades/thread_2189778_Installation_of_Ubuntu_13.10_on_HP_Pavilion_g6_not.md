---
title: "Installation of Ubuntu 13.10 on HP Pavilion g6 notebook w/ Windows 7"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by Remember2Wipe on 2013-11-24
Hello, first post here.

PC Stuff (don't know which are necessary to know for this problem, so I'm just dumping):

OS: Windows 7 Ultimate SP 1
System Type: 64 bit Operating System
Processor Type: AMD AG-4400 M APU with Radeon ND Graphics
Processor Speed: 2700 MHz
RAM: 4 GB


So I've been trying to install Ubuntu off and on all afternoon. I've tried making a bootable USB, didn't work. Tried booting from a CD, didn't work.
Both resulted in just booting up to a black screen with the under score thingy (obvious pc expert here) blinking. I've left it at that for 20 minutes just to see if anything would happen. I did boot into Ubuntu and tried it off of a CD a couple of months ago. I don't know what I did differently. 

I'm using Imgburn for the CD.

I could list all of the things I've done wrong, but it would be far too long. 


Could someone give a step by step instruction on how to boot through either CD or USB?
Too much information is much better than too little

Find screenshot of boot options in bios attached.

Thanks in advance.


I'll be here for about an hour and a half more then I'm going to bed. I'll be here tomorrow though

---

### Post by Bucky Ball on 2013-11-24
Welcome.

I have attached your screen shot. Please attach them rather than including in body of post by 'Go Advanced' and using the paperclip icon. Thanks. ;)

You have UEFI and Legacy boot order in the screenshot. I notice the UEFI order is not set to CD first. That might be it. There are differences in installing in either UEFI or Legacy, though, which I know little about, but you could try changing the UEFI boot order and see if that makes a difference.

* Ah, further to that, after having another look, the UEFI boot order seems to be set to 'OS boot manager'. You might want to do some research on installing in UEFI, GPT, or Legacy or hope someone that knows about these things jumps on here.

This is an internal optical drive you are using? Also, you might try the known, stable 12.04 LTS to make sure this is not specific to 13.10.

You have checked the disk for errors before commencing?

---

### Post by fantab on 2013-11-24
AFAIK, there are a very few machines with Windows7 that boot in UEFI. A screen-shot of your HDD showing all partitions from Windows Disk Manager will help to identify if its UEFI or Legacy.

Perhaps this is a typo on your part, but Ubuntu will NOT fit on a CD you will need a DVD.
To be able to boot from USB you have to set the 'Boot Order' to boot USB -Hard disk first. Or choose this from BIOS boot menu.
IMO 13.10 is good. Just check the integrity of Downloaded ubuntu.iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by Bucky Ball on 2013-11-24
> **fantab said:**
> AFAIK, there are a very few machines with Windows7 that boot in UEFI. A screen-shot of your HDD showing all partitions from Windows Disk Manager will help to identify if its UEFI or Legacy.


The photo of the screen in the first post shows the BIOS with 'UEFI Boot Order' and 'Legacy Boot Order'. 

The UEFI one is not set to CD/DVD, but 'OS Boot Manager'.

---

### Post by Remember2Wipe on 2013-11-24
First off, thanks for the help guys.

Yep. Typo. I'm using a 4.5 GB DVD.

Will try changing UEFI boot order. I think I already did try this at one point, but I'll have at it another time.

Also, I'm trying the MD55um check. Can someone explain how to use it? I clicked [http://releases.ubuntu.com/13.10/](http://releases.ubuntu.com/13.10/) but all the page is doing is loading. Been doing this for about a minute now. I refreshed the page twice

---

### Post by Bucky Ball on 2013-11-24
That page pops straight up for me. :-k

As for the hash check, how are you trying to do it? All the hash numbers are here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Remember2Wipe on 2013-11-24
Alright. Changed my UEFI boot order. When I booted from the DVD, it flahed for a split second and said something about Linux ISO being corrupt or something (flashed for literally less than a second). Redownloading an I'll try it again

---

### Post by oldfred on 2013-11-24
We really need to know if you have Windows in UEFI or BIOS boot mode. 
Ubuntu needs to be installed in the same boot mode.
If Windows is BIOS mode then drive is partitioned with MBR(msdos) and Ubuntu can only be installed in BIOS boot mode.
If Windows is UEFI, then drive is gpt partitioned and Ubuntu will install in BIOS or UEFI, but you only can easily dual boot if Ubuntu is UEFI. If Windows is UEFI and Ubuntu BIOS you only can boot from UEFI menu and may have to turn on/off UEFI boot to match system booting.

Post this from live installer once you get it working.
sudo parted -l

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Remember2Wipe on 2013-11-24
[http://i.imgur.com/WS6SbdJ.jpg](http://i.imgur.com/WS6SbdJ.jpg)

I think it's in BIOS

---

### Post by oldfred on 2013-11-24
You would have an efi partition if UEFI and gpt.

So be sure to boot Ubuntu installer in BIOS boot mode as how you boot installer is how it installs.
You should get purple accessibility screen in BIOS mode, not standard grub menu when in UEFI mode.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Remember2Wipe on 2013-11-24
Well I just redownloaded the ISO, this time via torrent, and it booted up fine

Now for the installation...

---

### Post by Bucky Ball on 2013-11-25
Good news. Corrupt disk after all that by the sounds.

Post a new thread if you have any other issues. Enjoy! 

PS: Torrent is the most reliable way of getting the ISO as checksum is done during the download. ;)

---

