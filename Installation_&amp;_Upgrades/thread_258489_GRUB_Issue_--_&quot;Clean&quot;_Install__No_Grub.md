---
title: "GRUB Issue -- &quot;Clean&quot; Install | No Grub"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by Roger Mudd on 2006-09-16
Decided to rid my system of Windows XP and install Dapper (Ubuntu) as the sole OS on my desktop. Backed up all my data to an external USB drive and loaded up the install CD. Installation seemed to go fine, however, when I reboot after the install I get "Error 17" instead of the GRUB bootloader.
My research on "Error 17" indicates that GRUB is essentially looking for itself but failing to find the necessary information. I tried reinstalling GRUB from the live CD to no avail.

"find /boot/grub/stage1" resulted in this:

```
(hd1,0)
```

"root (hd0,1)" resulted in this:
```

Error 22: No such partition
```

Result of "fdisk -l":

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
```

I have three hard drives in this machine:

A 160 GB internal SATA drive on which I've attempted to install Ubuntu (listed as sdb1 above -- I believe).
A 250 GB external USB drive listed as sdb above
A 60 GB internal IDE drive which is still formatted as NTFS. Not listed above for some reason.

Any help is greatly appreciated.

---

### Post by orb9220 on 2006-09-16
Check the bios on your system. When you add a sata and ide sometimes the  bios chose one over the other.

Also did you let it install to the mbr? Which is the first disk.

---

### Post by Roger Mudd on 2006-09-16
Thanks for the reply. Are you referring to boot order or IDE number? I have the SATA drive -- on which Ubuntu is installed -- selected as the initial boot device even though it is listed as IDE 4. The 60 GB internal IDE drive is listed as IDE 1. I don't think I can change the IDE numbers, however. If it matters, I'm using an ABIT IC7-G motherboard.
Also, despite getting the GRUB Error 17, there is no instance of GRUB in /boot. Does that seem strange to anybody else?

---

### Post by pradeepadapa on 2006-09-16
hi roger,

    actually try these steps from ur UBUNTU DAPPER LIVE CD to restore the GRUB nd solve the problem,

boot into the live cd nd enter the terminal,nd enter as the root in the terminal by typing           

$sudo -i

then just type grub at the prompt

#grub

then u wll see the grub prompt like this

grub>

then

grub>find /boot/grub/stage1

then u will get something like (hd0,0) ,, in ur case it is (hd1,0), so next type

grub>root (hd1,0)

next type

grub>setup (hd1,0)

then type quit nd RESTART the system nd ur GRUB will be RESTORED.

hope this works fr u,

bye.

---

### Post by Roger Mudd on 2006-09-16
A.Pradeep,

Thanks for the input, but I have already tried that with no success (see original post). I received a "No such partition" error after issuing the command "root (hdx,x)." Should I go ahead with "setup (hdx,x) even though I received the "No such partition" error?"

---

### Post by pradeepadapa on 2006-09-16
hi roger,

        actually when u tupe find /boot/grub/stage1 , u said that u got an ans like (hd1,0),
bt in the next step u told that u gav the command as "root (hd0,1)" but u hav to give " (hd1,0) " nd then it wll work fine, since u gav (hd0,1) it gav u an error message, try to do as i instructed, it wll work yaar,

bye.

---

### Post by randell6564 on 2006-09-16
> **Roger Mudd said:**
> 
"find /boot/grub/stage1" resulted in this:
(hd1,0)
"root (hd0,1)" resulted in this:
Error 22: No such partition


Not sure in this situation, but I believe you got that error because you should have entered, after the 'find /boot/grub/stage1' exactly what it found.,'hd1,0' and not 'hd0,1'.

---

### Post by Roger Mudd on 2006-09-16
Okay. Thanks for catching my typo. That seemed to seemed to work aside from a failure to "imbed" something (although the message indicated this failure was not fatal. Rebooted to the same *Error 17*, however. Any ideas?

---

### Post by Roger Mudd on 2006-09-16
Very strange. Shouldn't there be some instance of GRUB in /boot? Because there isn't...

---

### Post by Roger Mudd on 2006-09-16
Wait a second...
Booting up from the Live CD and opening up GParted shows that the actual drive (160 GB internal SATA -- see attached screenshot) on which Ubuntu is installed is not recognized by the command *fdisk -l*. What's that all about? The only drive shown by *fdisk -l* is my external USB drive, which is formated NTFS.
This is very strange and above my grade level. Any ideas?
Thanks!

---

### Post by confused57 on 2006-09-16
Is there a drop-down menu in the upper right corner of gparted for your other hard drive?

---

### Post by Roger Mudd on 2006-09-16
I'm spamming the heck out of my own thread and I apologize for that. Just want to provide those who are willing and able to help with what I deem to be pertinent information.
Further noodling around with GParted revealed something interesting. Could the problem lie in the "Disk Label Type?" All three of my drives are labeled "msdos," which is not surprising as Windows was installed on this PC at one time. Is this data written in the MBR of each of the disks? Could that be what's preventing GRUB from installing? Attached are GParted screenshots of the current state of each of my drives.
Thanks for your help (and putting up with my antics).

---

### Post by Roger Mudd on 2006-09-17
Any takers? I'm going on 22-hour install of Ubuntu now. And people gripe about the duration of an XP install/update-fest? ;-)

---

### Post by jadacyrus on 2006-09-17
I'm also receiving the same problem. I've tried installing Xubuntu and Ubuntu Edgy Eft Knot 3 and both installations failed to install GRUB properly, however installing OpenSuse or any other linux distribution installed the bootloader correctly. Why does ubuntu fail to completely install the bootloader. Both times the /boot directory contains no instances of GRUB. This must be a bug..? PLease help.

---

### Post by Roger Mudd on 2006-09-17
Jadacyrus,
I sympathize with you. I actually spent the day installing Debian Etch, OpenSuse 10.1 and Fedora Core 5. Same GRUB *Error 17* on each. That would seem to indicate a hardware issue of some sort.
I'm wondering if each attempt is detecting a previous install of GRUB on the MBR of my secondary IDE hard drive -- which I thought I wiped clean (see middle thumb attached to post 12 above). That's strange though, because I explicity requested that FC5 install GRUB on the MBR of my SATA drive (sda). Still didn't work, though.
I'm 24 hours into this ordeal and contemplating breaking out my XP install CD and returning to the dark side. I've done a lot of research and tried just about everything that's been suggested in these forums and elsewhere. Unfortunately, I'm reliant upon Google and the good will of others as I'm relatively new to Linux.
Seems a bit ironic that I never had this problem with a dual-boot install. Only when I made the concious effort to dump Windows altogether did these problems arise.

---

### Post by randell6564 on 2006-09-17
> **Roger Mudd said:**
> Wait a second...
Booting up from the Live CD and opening up GParted shows that the actual drive (160 GB internal SATA -- see attached screenshot) on which Ubuntu is installed is not recognized by the command *fdisk -l*. What's that all about? The only drive shown by *fdisk -l* is my external USB drive, which is formated NTFS.
This is very strange and above my grade level. Any ideas?
Thanks!
Read [this]("http://linuxmafia.com/faq/Hardware/sata.html") regarding SATA and Linux

---

### Post by LeftyMills on 2006-09-17
I tried to install Ubuntu 6.06 on a Win98 computer to dual boot.  After installation, I rebooted and got the message
"GRUB loading stage 1.5
GRUB loading, please wait.
Error 17"

At that point, my computer just hangs.
What do I do now?
(Luckily, I have another computer in the house so I can send this email.)

L.

---

### Post by Roger Mudd on 2006-09-17
Randell6564,

I looked at the link you provided and I think they're talking about poor SATA support in kernels prior to 2.4.x. As stated before, I'm using an Abit IC7-G. This motherboard features ICH5 SATA control. [Here]("http://linuxmafia.com/faq/Hardware/sata.html#intel-ich5") are the comments on that particular chip from the link you provided.
I think my SATA drive is recognized by Ubuntu as it is able to partition and install the OS. I can read and write that data from the Live CD as well. I believe the real issue lies within the MBR.
I may be mistaken, though. Please correct me if I'm not seeing the light.
32 hours and counting...

---

### Post by indulis on 2006-09-17
OK I have had to do some playing around with SATA boot on my Promise RAID chipset.  The bad news is that GRUB doesn't seem to be able to recognise SATA devices.

The reason you can partition etc from the Ubuntu install disk is that when you are running the install, you have booted to CD, and are running a full Linux kernel from CD with lots of nice device drivers so it can see all the hardware and knows how to talk to all of the myriad of SATA chipsets.

When you boot from hard disk, the BIOS starts up the Grub stage 1 from the MBR ('cos the BIOS knows how to do this).  Then Grub starts running, and can't see any SATA devices, becaues it does not know how to talk to the SATA chipsets.  I think there are so many SATA chipsets that unlike serial ports and IDE drives, Grub can't know how to talk to them all.

That's my opinion, from experimenting around with my system.  It may or may not be right.

A workaround is to create a boot CD or USB drive with Grub and a /boot with kernels on it.  It is horrible, but as Ubuntu is pretty stable, you probably won't have to use it that often.  It only has to be 256MB to hold Grub and your kernel images (OK maybe even as low as 64MB).  As a USB drive, you could even put it on the back of the computer, or inside your case (if you have an internal USB port).

Copy the /boot filesystem onto a hard drive as well, you can always then use rescue CD to recreate another floppy/CD/USB image.  I always set up mny hard disk with a /boot as the 1st partition (EXT2 filesystem), and  SWAP as the 2nd partition, then I do LVM for the rest.  Logical volume manager has the same issue as SATA, as Grub does not know how to access it, so you have to get an LVM-enabled kernel up and running before you can access the rest of the disks.

I've heard some newer motherboards with SATA have an "IDE compatibility" mode in the BIOS, so you can make the SATA drives look like IDE drives via the BIOS.  You should check around in your BIOS settings and see if this exists.

Good luck!

Indulis
PS there is a new Grub in development, this might be better, but I never figured out how to create my own Grub2 boot CD, and my floppy dreive is out of action due to dumb case design coupled with dumb power supply design so the power doesn't reach

---

### Post by Roger Mudd on 2006-09-17
Thanks to all for your help. I'd have to agree with the general sentiment that GRUB does not play nice with SATA drives.
In an effort to get back on-line I switched my IDE drive to the boot drive in the BIOS, installed Ubuntu to this drive (hda) with the intention of using the larger and faster SATA drive for multimedia storage. Not ideal, but it worked.
Here's the funny part. When booting into the new installation, the boot stalled after the BIOS loaded. I switched my first boot drive back to the SATA and it booted right up. How's that for a 42-hour kick in the pants?
Oh well. Maybe this will get sorted out in time. At least I'm up and running.
Thanks again for your concern.

---

