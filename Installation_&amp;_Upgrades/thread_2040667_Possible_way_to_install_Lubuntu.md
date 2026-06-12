---
title: "Possible way to install Lubuntu?"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by slooksterpsv on 2012-08-11
I'm trying to get Lubuntu onto an old computer (AMD Duron 725MHz, 320MB RAM) and I was wondering if you guys think this would work. (CDROM drives are bad)

(Maybe not have to do this) 1. Install Grub4Dos to have a grub like bootloader
2. Partition down Windows and have 1GB allocated to where I could use an old version of unetbootin to install Lubuntu to the 1GB Partition.
3. Boot off said partition and have it install and clear out the Windows partition.

Guess that's pretty much it, think it would work? The only reason I say Grub4Dos is cause I don't remember if doing a Unetbootin to the HDD will install the bootloader to where I could boot directly to Lubuntu install.

Also there is no USB booting and I don't have floppy disks.

---

### Post by cwsnyder on 2012-08-11
Have you considered simply connecting your hard drive temporarily to another computer and installing your new OS from there?

---

### Post by Doj on 2012-08-11
My laptop has a messed cdrom, so what I did was put the plop boot manager on my windows partition and use a usb drive to install Lubuntu from. My laptop can't boot straight from usb because no option in bios... Good luck.

---

### Post by slooksterpsv on 2012-08-11
I'll look into plop.

Also, no the computer uses IDE and I only have a laptop and no external drive. So yeah.

---

### Post by cwsnyder on 2012-08-11
Okay, second thought.  You still have a working USB port?  An external DVD-ROM which connects only to your USB port costs about $40.

---

### Post by slooksterpsv on 2012-08-11
> **cwsnyder said:**
> Okay, second thought.  You still have a working USB port?  An external DVD-ROM which connects only to your USB port costs about $40.

BIOS is so old it won't allow booting from USB.

---

### Post by cwsnyder on 2012-08-11
Plop would work with either the external USB CD/DVD drive or a thumb drive.

---

### Post by pierceTN on 2012-08-11
> **cwsnyder said:**
> Have you considered simply connecting your hard drive temporarily to another computer and installing your new OS from there?
 I would try this. Do you have another computer you can put this hard drive into then switch them back after they are installed?

---

### Post by slooksterpsv on 2012-08-11
Can't find my USB stick, where the heck it went I have no clue (probably put it in the box in my closet that's in the corner buried under 10 other boxes lol). No other external storage medium. And I don't have another computer, only my HP laptop.

---

### Post by slooksterpsv on 2012-08-12
Ok so the computer is running windows xp and here's how I'm doing it (not done yet but I'll post results):

1. Using HP Laptop and a CAT5 cable (Ethernet) I did a network bridge under Windows 7 and manually set the IP address of the Compaq 700MHz computer.
2. Checked to see if internet worked.
3. Tried Samba file sharing - it'd take a lot of work to get XP to share with Windows 7 so that idea was out. So I used Xampp and setup a faux web server, put the files in I needed to copy to the compaq and had firefox download said files.
4. Using EaseUS Partition Manager I'm repartitioning the Fat32 drive down by 1GB to rip the ISO file using Unetbootin.

So far I'm here

5. Using Unetbootin version 4.9.4 I'm having it use the Lubuntu iso to rip it to the 1GB drive.
6. Attempting a reboot to see if grub will load Lubuntu, if it won't I'll have to install Grub4Dos and boot that way.
7. Start installing Lubuntu with Manual partition editing as to make sure I have enough swap and leave the Lubuntu install partition alone.
8. Reboot into Lubuntu and no more XP

(Waiting to do steps 5-8)

---

### Post by Cheesemill on 2012-08-12
You could always set up another machine (Linux or Windows) as a PXE / TFTP server and then boot the laptop from the network.

That way the installer runs just as if you've booted from a CD, no need to mess about with creating temporary partitions to boot from.

---

### Post by slooksterpsv on 2012-08-12
> **Cheesemill said:**
> You could always set up another machine (Linux or Windows) as a PXE / TFTP server and then boot the laptop from the network.

That way the installer runs just as if you've booted from a CD, no need to mess about with creating temporary partitions to boot from.

The duron is a desktop, my laptop I have what I need on it. PXE may be an option I'll have to look into.

---

