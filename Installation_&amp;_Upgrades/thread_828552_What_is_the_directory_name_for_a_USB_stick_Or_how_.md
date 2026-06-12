---
title: "What is the directory name for a USB stick? Or how can I figure it out?"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by crazyfish666 on 2008-06-13
Long story short I am installing Rosetta Stone (a language learning software) on a usb stick to make it portable AND able to run on Ubuntu. Thus I am also looking to install Wine on the usb stick. One problem. The way I know to do this involves me being in terminal and in the directory that I want to install Wine in (the usb stick) and I can't figure out what it is. *sigh*. I am sure this is obvious to someone who is good with linux but I am pretty new to it and have developed a strange splattering of understanding that is frequently lacking in some of the basics. So...

I know that a CD is /media/cdrom so what is a usb stick? Alternatively, how can I get a list of all accessable directories and then I could figure it out by process of elimination?

Sorry for being such a dumb *** :).

---

### Post by Pumalite on 2008-06-13
sudo fdisk -lu
You'llrecognize it for the small size

---

### Post by crazyfish666 on 2008-06-13
> **Pumalite said:**
> sudo fdisk -lu
You'llrecognize it for the small size

Hmmm. Yes. I did this and came back with it being /dev/sdb1 but "cd /dev/sdb1" doesn't work. Is this something to do with it being a USB?

Essentially what I am trying to do is to install Wine and Rosetta Stone on the USB stick so that I have Rosetta Stone in a portable format for Linux. However, I can't use "sudo apt-get install wine" to install it in the USB stick unless I am already in there. Is there another way to do this?

---

### Post by Pumalite on 2008-06-13
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Change the format according to your situation:
fat32=vfat

---

### Post by crazyfish666 on 2008-06-13
> **Pumalite said:**
> sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Change the format according to your situation:
fat32=vfat

I'm getting closer... :). But I did those and got myself into the directory (I didnt' change the format as I am not sure how) and then tried "sudo apt-get install wine" and it did everything and then said "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." which I assume is because I already have Wine on my computer. If this is the case then how do I get it to install onto the USB stick?

---

### Post by Pumalite on 2008-06-13
You have to make a bootable USB and then boot from it.
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)

---

### Post by crazyfish666 on 2008-06-13
> **Pumalite said:**
> You have to make a bootable USB and then boot from it.
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)

Ahhh. So it can't just have Wine on it and then have my computer connect with it from it's version of Ubuntu, the stick itself has to have Ubuntu on it? That kinda makes sense! How big is Hardy? Rosetta Stone is just under 2GB all together and my USB stick has 3.7GB total available. 

If I do set it up like this then would I have to shut down and boot back up to the USB stick every time I want to use Rosetta Stone (I imagine I would), or is there a way to make it accessible from an already booted up ubuntu?

If Hardy doesn't fit then do you think something like TinyLinux could deal with this fine?

---

### Post by Pumalite on 2008-06-13
You might make it with a 4 GB flash drive, but better 8 GB.

---

### Post by crazyfish666 on 2008-06-13
> **Pumalite said:**
> You might make it with a 4 GB flash drive, but better 8 GB.

4GB's the biggest I've got available and I don't have the cash to go and buy a bigger one. Do you think a smaller version of Linux would work? I suppose I can always try with Hardy and if it doesn't fit then all I have wasted is a little time.

P.S. Did I mention what a life saver you are? Seriously, thanks for all the help!

---

### Post by crazyfish666 on 2008-06-14
Right, I'm awake again now and ready to actually get this up and working. The two best bet tutorials I have found for getting my little 4GB bootable are [this]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-live-cd/") and [this]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/"). I'm planning on doing the from Linux one as I am staying at a friends and don't have any blank CDs with me, but are there any benefits to doing this from LiveCD that I should be aware of? I can't see any, but it does seem to be presented as the preferable method by the website.

---

### Post by Pumalite on 2008-06-14
You are doing fine. Post your results.

---

### Post by crazyfish666 on 2008-06-14
> **Pumalite said:**
> You are doing fine. Post your results.

Well, I was doing fine. I followed the instructions [here]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/"), but when I changed my BIOS Setup settings to boot from USB it went through the normal Dell part of the boot in which you can access BIOS, but it gave me an error message right after that that read something like "Error with operating system" (I'll check and post the exact message). And all I could do (hitting enter, esc, or F2 didn't do anything) was to hit the power button and go back into BIOS when I started it up again and change back to my normal boot. Sooo... I'm a little lost. What might be the error do you think?

---

### Post by Pumalite on 2008-06-14
Post: sudo fdisk -lu
(with your external connected, but not mounted)

---

### Post by crazyfish666 on 2008-06-14
> **crazyfish666 said:**
> (I'll check and post the exact message)

It is "Error loading operating system" and comes up exactly the same whether I am trying a one-time boot from USB or to set it as my normal preference (I didn't expect it to make a difference but I tried both anyway :) ). I'm contemplating wiping everything off of the USB and trying again as I did get interupted a few times in the process the first time by some little hicups I had to fix so it got done sort of piecemeal between reboots. Maybe I accidentally missed something important...

---

### Post by crazyfish666 on 2008-06-14
> **Pumalite said:**
> Post: sudo fdisk -lu
(with your external connected, but not mounted)

Somehow I managed to miss this post when you first posted it. But here it is:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455   107539109    53713327+  83  Linux
/dev/sda3       107539110   189068984    40764937+   5  Extended
/dev/sda4       189068985   195366464     3148740   db  CP/M / CTOS / ...
/dev/sda5       107539173   177855614    35158221   83  Linux
/dev/sda6       177855678   189068984     5606653+  82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbce0f5ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          48     1468559      734256    6  FAT16
/dev/sdb2         1468560     7829999     3180720   83  Linux


Also, I tried clearing the USB and redoing everything and the error is still the same.

---

### Post by Pumalite on 2008-06-14
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
Check and see if you have a 'boot' folder there.

---

### Post by crazyfish666 on 2008-06-15
> **Pumalite said:**
> Check and see if you have a 'boot' folder there.

How?

Really, I am a newbie!

---

### Post by Pumalite on 2008-06-15
Navigate to 'media' and look in sdb1

---

### Post by crazyfish666 on 2008-06-19
Okay, sorry about a bit of a delay here, work got crazy... Anyway, what I have decided to do is try the other approach, the Live CD one as opposed to doing it in Linux. So... I tried to download Xubuntu last night to put on my CD and I got this error message when I got back to it this morning

> /home/fae/Desktop/xubuntu-8.04-desktop-i386.iso.part could not be saved, because the source file could not be read.

Try again later, or contact the server administrator.


But I realised that at somepoint in the night internet had been lost (I'm using a sort of finickety wireless connection) so I am going to try again.

My main reason for trying this in the first place is because the bootable USB setup I did in Linux was incredibly quick with the longest step taking 45mins to an hour and usually when I upgrade to a new version of Ubuntu it takes about 4 or 5hours so I had a feeling it wasn't getting all of Xubuntu. The download for the Live CD is taking longer (it had been going for 3 hours when I went to bed and was nowhere near done) which is sort of promising, but then it has that error.

So, we'll see how the retry of the download goes while I am at work.

---

### Post by crazyfish666 on 2008-06-19
> **crazyfish666 said:**
> So, we'll see how the retry of the download goes while I am at work.

All went well with that. I know have a nice Xubuntu Live CD! Yay! :D. The issue at the moment is that I cannot access wireless (it just keeps trying to connect but never does) from the live CD so I am going to search around my host's house for a hard wire connection. Any ideas for the wireless if I can't find one?

I'll keep updated as things go on.

---

### Post by Pumalite on 2008-06-19
Open up all your repos; reload. Then:
sudo aptitude dist-upgrade
Post back with results.

---

### Post by crazyfish666 on 2008-06-20
> **crazyfish666 said:**
> All went well with that. I know have a nice Xubuntu Live CD! Yay! :D. The issue at the moment is that I cannot access wireless (it just keeps trying to connect but never does) from the live CD so I am going to search around my host's house for a hard wire connection. Any ideas for the wireless if I can't find one?

I'll keep updated as things go on.


Okay, I found a hardwire connection and followed the pendrivelinux instructions, but I am getting the same error when I try to boot from the USB as I was before.

I've got to head off to work now, but I will get back to this this evening and see what is up.

---

