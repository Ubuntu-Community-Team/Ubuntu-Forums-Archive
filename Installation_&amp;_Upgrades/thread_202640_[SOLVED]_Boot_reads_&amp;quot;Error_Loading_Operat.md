---
title: "[SOLVED] Boot reads &amp;quot;Error Loading Operating System&amp;quot;"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by stalker145 on 2006-06-23
Greetings, all. I have finally decided to try out a Dapper install on my server. I tried the Live CD and it did everything that I needed... for now. I ran through the install seamlessly, removed the CD, changed my BIOS to boot only from Primary IDE Master and was greeted with "Error Loading Operating System". No GRUB, no Ubuntu, just hate and discontent.

My setup is an AMD 2600+, 768MB RAM, 128 MB GPU, 2 HDD's on the primary IDE, 1 DVD on the secondary IDE, and 4 HDD's hanging off a PCI IDE controller card. 

I was able to successfully mount and umount all of the HDD's from the Live CD and, upon being met with this error, was able to get back into the Live CD and verify that files that looked like a Linux install to me were, in fact, loaded onto the primary IDE master.

Now, here's a big question: for some reason, Ubuntu reads my primary IDE master as /hde1. Is this a problem? I'm grasping at straws here since it seems (to me, at least) that the letter 'e' is a little way from the first letter in the alphabet.

I know that the CD is good as it's the same one that I used on my laptop a few weeks ago. I have also tried installing Ubuntu Server and was met with the same error.

---

### Post by Joeb on 2006-06-23
It sounds like Dapper is detecting your add-on IDE controller before your on-board IDE controller, which would explain why your primary is /dev/hde.  I am assuming you are seeing this whil in the live CD.

If that is the case, the fix may be as simple as editing the /boot/grub/menu.lst located on your primary drive.  If during the install it was detected as /dev/hde and when booting it is /dev/hda, then the menu.lst has the wrong info.

Assuming your Dapper install is on the first partition, then you would want the line begining with "root" under the title "Ubuntu" to be (hd0,0).  If it is a different partition than the first, set the second number to one less than the partition (ie, the 3rd partition would be hd0,2).

Most likely your line says (hd4,0) since it thinks it is /dev/hde.  Anyway, after that change, you should be able to reboot.

---

### Post by stalker145 on 2006-06-23
joeb, Sounds like an easy fix. Now how would I go about editing GRUB if I don't have an OS to boot into? Would I simply need to boot to the Live CD, mount the HDD and edit it there? Please tell me it's that easy and I will never stray from the ways of Linus;)

---

### Post by Joeb on 2006-06-23
[QUOTE=stalker145]joeb, Sounds like an easy fix. Now how would I go about editing GRUB if I don't have an OS to boot into? Would I simply need to boot to the Live CD, mount the HDD and edit it there? Please tell me it's that easy and I will never stray from the ways of Linus;)[/QUOTE]

Yes, you would boot from the Live CD and mount the drive.  If you did it all in Gnome, then you could just use Nautilus to drill down to the menu.lst and edit it with a text editor.  Then, just reboot and that should take care of it.


EDIT:  menu.lst will be found under /boot/grub/menu.lst on whatever drive you installed linux to.
EDIT2: In the menu.lst file, lines that begin with # are comments and include examples. You will want to change the ones further down the file that pertain to the boot menu displayed when you boot your computer.

---

### Post by stalker145 on 2006-06-23
joeb, Thank you for the help. 

All three of the hd(4,0) have been changed to read (0,0) but it's still not working. Two questions: first, does it matter that the mount point is still reading /hde1? Second, is there a config file somewhere that I should change? What I'm asking is did I inadvertantly cause a conflict when I changed the root HDD in GRUB and need to fix it elsewhere?

I'll continue to poke around and see if something might fall into my lap, but I will *definitely* be checking back here until it's done... no matter how late it is ;)

---

### Post by stalker145 on 2006-06-24
Success!!:D 
For anyone out there with a bizarre setup like mine, here's what I did to fix it. 

Booting is performed via the Live CD. You must mount the drive to which you've installed ubuntu (it's as easy as **sudo mount /dev/hde1 /dev/linux** where hde1 is the drive you wish to mount (Linux file system) and /linux is your desired mount point

It took removing my controller card and installing each piece one at a time while checking the files /boot/grub/menu.lst and /boot/grub/devices.map. 
I started out with a fresh install with only my motherboard's IDE devices hooked up (IDE0 master/slave and IDE1 master/slave). Checking the devices.map and menu.lst files (by the way, this install worked perfectly) i got a baseline for what those two files *should* look like.

devices.map looked like this:
hd0 /dev/hda
hd1 /dev/hdb

menu.lst looked like this for the boot devices:
#kopt=root=/dev/hda1 ro

#groot=(hd0,0)

*and further down all kernels contained*

root (hd0,0)

root-/dev/hda1

In running **fdisk -l** I observed (as should be) that my Primary master and slave IDE chaim were at hda and hdb, respectively.

Upon the installation of the primary IDE chain of my controller card, I noticed that [B]fdisk -l{/B] had changed to hda being my primary master on the controller card, hdb was the primary slave on the controller card, and hde and hdf were my primary IDE for the mobo, master and slave respectively (in other words, my desired boot device).

With that said, I looked up the devices.map and menu.lst files and observed that the notations remained referenced to hda and hdb event though the drives were now recognized and hde and hdf.

I changed the aforementioned hda and hdb references to hde and hdf, performed a reboot, and it worked. IT FRIGGIN' WORKED!!

I installed the secondary chain for the controller card, booted, and this worked as well. I guess once I got the boot device recognized by GRUB, all was well.

That's my story and I'm sticking to it.

---

### Post by markvanh on 2007-02-03
Hi all, my first post here. Looking to finally make the switch from Windows; I'm new to Linux.  Downloaded Ubuntu 6.10 Desktop amd64.

The install had completed, with out any cues for Grub. (Installed on it's own HD, i have 2 other WinXP HDs). But at end when it ejected the CD and instructed to remove it and close the bay, press enter to reboot...   it froze and would not reboot.   I manually shut down and booted with the new Linux drive first priority boot, but it won't boot-- I just get a black screen.  

I don't quite understand how/where to type the command, "sudo mount /dev/hde1 /dev/linux".   Could i also use the Install CD or will I need to download the LiveCD?  

I verified my Install CD .iso was checksum accurate, burned it slow, and it passed the Disk integrity check utility in the Install CD launch menu.  (second time was the charm)

Also i don't quite understand the details of what files & how to edit them..   I hoped the install would be automatic.  

Could I re-do the install after disconnecting my other 2 HDs, to avoid confusion?  Is it possible some hardware or driver issue is complicating a 'automatic' install? 

Thanks for any advice,
mark

ASUS A8N-SLI Deluxe
ATHLON 64 X2 4400+
ATI X1800XL PCI-E
HD 200G|WD 7K 8M SATA2
1Gx2|CORSAIR Twinx2048-3200c2pt

---

### Post by markvanh on 2007-02-04
I unplugged my 2 ntfs HDs and successfully installed ubuntu.  It immediately prompted me for 114 updates, which it downloaded and installed then rebooted.

However, when I reconnected the other 2 ntfs drives (set bios to boot to Linux one).. bomb.
Screen shows:

"BusyBox v1.13 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
/bin/sh:  can't access tty; job control turned off
(initrmafs)"

Any suggestions on how to fix this, so ubuntu will load while other ntfs drives connected? 

P.S. Typing from inside WinXP again; the Linux hard drive isn't 'readable' in Win file Explore.  Instead i see a 3rd CD/ROM drive, when i only have 2.  Some tip to make Linux drives/files viewable from inside Windows?  

Thanks,  mark

---

