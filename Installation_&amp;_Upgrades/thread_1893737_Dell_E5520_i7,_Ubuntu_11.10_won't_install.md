---
title: "Dell E5520 i7, Ubuntu 11.10 won't install"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by maghajan on 2011-12-10
Hi,

I have a Dell E5520 laptop with the Intel i7 processor. I am trying to install Ubuntu 11.10 amd64 but it won't work. I have tried installing off of a USB stick as well as a CD, but neither work. After the computer goes through the POST messages, the Ubuntu install screen appears for a few seconds and then the screen turns black with just a cursor blinking in the top left hand corner. I updated the computers BIOS because the computer has Windows 7 currently installed. Any help is appreciated!

---

### Post by fantab on 2011-12-10
> **maghajan said:**
> Hi,

I have a Dell E5520 laptop with the Intel i7 processor. I am trying to install Ubuntu 11.10 amd64 but it won't work. I have tried installing off of a USB stick as well as a CD, but neither work. After the computer goes through the POST messages, the Ubuntu install screen appears for a few seconds and then the screen turns black with just a cursor blinking in the top left hand corner. I updated the computers BIOS because the computer has Windows 7 currently installed. Any help is appreciated!

First of all CHECK your downloaded .iso. If possible re-download the .iso as torrent. Then burn the .iso to the CD at the lowest possible speed. And TRY AGAIN. 

Also post the screen shot of the Partition Scheme.

---

### Post by maghajan on 2011-12-11
> **fantab said:**
> First of all CHECK your downloaded .iso. If possible re-download the .iso as torrent. Then burn the .iso to the CD at the lowest possible speed. And TRY AGAIN. 

Also post the screen shot of the Partition Scheme.

Hi fantab, I MD5'd the image and it is fine. I am actually trying to install from a USB stick using the package "usb-creator" on my Ubuntu desktop computer, so I'm pretty sure that part is fine. Can you tell me exactly what you mean by "post the screen shot of the Partition Scheme"? Thank you for helping me with this.

---

### Post by fantab on 2011-12-11
> **maghajan said:**
> Hi fantab, I MD5'd the image and it is fine. I am actually trying to install from a USB stick using the package "usb-creator" on my Ubuntu desktop computer, so I'm pretty sure that part is fine. Can you tell me exactly what you mean by "post the screen shot of the Partition Scheme"? Thank you for helping me with this.

I have had problems earlier with the downloaded .iso in spite of positive MD5. On the face of it the issue seems to be of missing files on .iso image you've created. 

I might help us if we know how you partitioned your hard drive. Though it doesn't seem that you may have issues with Partitions, yet it will be better to rule it out.

---

### Post by maghajan on 2011-12-12
> **fantab said:**
> I have had problems earlier with the downloaded .iso in spite of positive MD5. On the face of it the issue seems to be of missing files on .iso image you've created. 

I might help us if we know how you partitioned your hard drive. Though it doesn't seem that you may have issues with Partitions, yet it will be better to rule it out.


I will try re-downloading the ISO and let you know what happens. I made the USB stick using usb-creator-kde which I have done before and it's worked fine on other PC's. 

As for the harddrive partition, there is a Windows 7 installation on the harddrive right now. I am hoping to partition the harddrive once I can get the Ubuntu install to reach that part, but right now I am not able to get to that part of the installation. Does this make sense?

---

### Post by maghajan on 2011-12-12
> **fantab said:**
> I have had problems earlier with the downloaded .iso in spite of positive MD5. On the face of it the issue seems to be of missing files on .iso image you've created. 

I might help us if we know how you partitioned your hard drive. Though it doesn't seem that you may have issues with Partitions, yet it will be better to rule it out.

Just tried an Ubuntu 9.10 AMD 64 disk as well, same problem: Few seconds after the POST messages and initial Ubuntu screen, just a black screen with cursor in the corner.

---

### Post by fantab on 2011-12-12
See this [**webpage**]("http://www.ubuntu.com/certification/hardware/201011-6894").

The linked webpage quotes > "Standard images of Ubuntu may not work at all on the system or may not  work well, though Canonical and computer manufacturers will try to  certify the system with future standard releases of Ubuntu".**Download Ubuntu from the above webpage** and it is 32bit.

Also call Dell Customer Care, and hear out what they have to say.

---

### Post by jnguyen on 2011-12-12
Hi maghajan,

I had the same problems before. The culprit is the new bios . Just go back to the last version to fix it.

jn

---

### Post by maghajan on 2011-12-12
> **jnguyen said:**
> Hi maghajan,

I had the same problems before. The culprit is the new bios . Just go back to the last version to fix it.

jn

Thank you for the suggestion jn! I went to the Dell page to download the BIOS for this product, but it only allows me to download the latest BIOS, which I am sure does not work cause that is the one I have installed right now. Any ideas where to download older Dell BIOSes?

---

### Post by darkod on 2011-12-12
This might be video related too. Try this:
As soon as the first purple screen shows (before the ubuntu menu shows) press Esc. That should load the older type of the main menu. You can press F6 for advanced options, and select the nomodeset option (you select with up/down and pressing Space to show a tick mark).
After that select Try Ubuntu from the main menu.

First see if the live mode loads fine before continuing to install.

You should also post the type of your video card, someone else with the same card might know a solution.

---

### Post by maghajan on 2011-12-12
> **jnguyen said:**
> Hi maghajan,

I had the same problems before. The culprit is the new bios . Just go back to the last version to fix it.

jn

Hi jn, nevermind, was able to find the A02 BIOS. Any idea why the new BIOS wouldn't work? Is there a chance that non of the subsequent BIOS revisions will work? Do you know if there is another Linux Distro that will work with the latest BIOS and be able to use all the features of the laptop? Thanks to you and everyone else who have offered suggestions!

---

### Post by jnguyen on 2011-12-12
The new bios has a big bug in it and Dell is working on it to fix the issue. When I ran the onboard Diagnostic within the bios, I got many issues such as storage, video and lcd cable. There was so many users like us complaint to Dell already, but I'm so supprise that it still there and allow people to download and get crashes. 
I guess we just have to wait for Dell to wave their magic wand.
jn

---

### Post by James B Davis on 2012-03-12
This is still a problem - no fix yet. I got the latest bios for my i5 E5520 and can't get an install to complete (using the same setup as I had on previous laptops - boot grub w/windows as a second os. Nothing fancy in that setup. Can't install centos or mint either so I'm sure the bios is an issue with the current kernel(s).

---

