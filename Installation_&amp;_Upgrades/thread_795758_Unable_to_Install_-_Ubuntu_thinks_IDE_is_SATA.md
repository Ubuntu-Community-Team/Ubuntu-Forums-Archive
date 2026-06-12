---
title: "Unable to Install - Ubuntu thinks IDE is SATA?"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Dedalus14 on 2008-05-15
OK I am very new to Linux so I apologize if I'm asking noob questions.  Having said that, I'm finding it impossible to install Ubuntu 8.04.  I have no other operating systems installed, and I have two hard drives: 
-One SATA 1+0 Stripe (RAID something or other, I don't understand it) with a single NTFS partition that contains the files I wanted to save before deleting Windows XP.
-And one IDE drive (set as master IDE drive in BIOS, and second boot priority after DVD-RW drive).

The IDE drive is completely empty, and I am attempting to install Ubuntu 8.04 on it, and the install is confusing the hell out of me; It is calling my SATA drive (which my BIOS doesn't even recognize) sda, and my IDE drive sdb, even though it's not a SATA SCSI drive at all.

I tried all the different partitioning methods including essentially every possible combination of /boot, /, /home, logical, primary manual partitions in order to get Ubuntu working, but none of them worked.  It runs perfectly from the LiveCD, but whenever I try to install it appears to work, but when I reboot and remove the CD it **does not boot**.  It gives me Error 17: Cannot Mount Partition and refuses to boot.  I'm guessing there's something wrong with GRUB or something, but I searched all over and couldn't find anyone with this same problem.

So does anyone have any suggestions of things I could try to make it boot from the IDE drive, or even get Ubuntu to recognize that it *is* an IDE drive?

Thanks.

---

### Post by Pumalite on 2008-05-15
Have you tried changing the boot order in BIOS? I don't know anything about Raids, so you might not even be able to boot from the other drive.

---

### Post by Dedalus14 on 2008-05-15
> **Pumalite said:**
> Have you tried changing the boot order in BIOS? I don't know anything about Raids, so you might not even be able to boot from the other drive.
In my BIOS the IDE drive is second, after my DVD-RW drive (which I'm running the LiveCD version off of now).  The actual SATA drive isn't on the list at all; Floppy was first for some reason and I changed that because I read somewhere it might help, but it didn't change anything.

Right now when I try to boot I get an error message saying GRUB is loading stage1.5, and then Error 17.

---

### Post by iaculallad on 2008-05-15
Try this [link]("http://www.justlinux.com/forum/showthread.php?threadid=149484"). Hope it would help

---

### Post by Dedalus14 on 2008-05-16
OK I was finally able to boot it by hitting enter after error 17 came up and using a command prompt and writing "find /boot/grub/stage1" the results surprised me, and when I replaced what was there with the first result (hd0,0) it booted.  

So now I can boot it by doing this, so I'm wondering how exactly I'd go about being able to boot without having to do this each time?

--It looks like GRUB is based solely on the BIOS boot settings, so it actually makes sense that it would be (hd0,0).  However, Ubuntu still thinks this drive is a SATA and calls it sbd1.

---

### Post by RTucker on 2008-05-16
To put it incredibly simply, RAID is the process of using multiple physical hard drives to create one single logical drive. The simplest forms being:

RAID 0 (Striped) = 2 or more physical drives appearing as a single drive with a size equal to the total of the physical drives. eg. 2x200GB drives show up as a single 400GB drive.

RAID 1 (Mirrored) = 2 drives which constantly maintain an exact mirror of each other and appear as a single drive with a size equal to ONE of the physical drives. Used to create redundancy, ie. if one HDD dies, your system boots as normal and you simply replace the drive. eg. 2x200GB driver show up as a single 200GB drive.

So, if you only have 2 drives, one SATA and one IDE, you aren't using RAID.

I suspect that your motherboard probably uses a third party SATA controller (which would actually be a SATA RAID controller), which is why it dosen't show up in the normal bios boot order. If you watch the options during the POST (when the system is first starting up) you may be able to get in to the BIOS of the SATA RAID controller it self and change the boot order, or disably booting from those drives. If not there should be the option to remove the SATA RAID as a boot device (change the mode of it)  somewhere in the normal system BIOS (possibly in 'standard settings').

---

### Post by confused57 on 2008-05-16
> **Dedalus14 said:**
> OK I was finally able to boot it by hitting enter after error 17 came up and using a command prompt and writing "find /boot/grub/stage1" the results surprised me, and when I replaced what was there with the first result (hd0,0) it booted.  

So now I can boot it by doing this, so I'm wondering how exactly I'd go about being able to boot without having to do this each time?

--It looks like GRUB is based solely on the BIOS boot settings, so it actually makes sense that it would be (hd0,0).  However, Ubuntu still thinks this drive is a SATA and calls it sbd1.
If you want to make it permanent, boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), enter(copy & paste one line at a time, press enter after each line):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Change the root line(s) to (hd0,0)...also, change the line with #groot to (hd0,0)...leave the # in front of groot.
Quit & save.

---

