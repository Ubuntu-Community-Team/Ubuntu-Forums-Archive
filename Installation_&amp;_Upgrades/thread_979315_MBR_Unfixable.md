---
title: "MBR Unfixable?"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by kook44 on 2008-11-11
Hi-
I have 2 drives - sda and sdb.  sda is my XP installation.  I was trying to install 8.10 on sdb and in doing so, rendered my XP installation unbootable.  (side note: the 8.10 installation has gone too far to the school of Gates. By oversimplifying and dumbing-down the process, details and control are lost.  The installation program never asked me where I wanted to install GRUB, where previous versions had.  It just assumed I wanted to dual boot and overwrote the MBR on my first drive.  I had planned on using the BIOS to selectively boot.  But I digress..)
I should note that the drive is completely mountable on the filesystem in ubuntu (I've already backed up my data using the live CD), and gparted and fdisk seem to recognize the partition fine.
When I use the XP recovery disk and run FIXMBR, I get no response, just a blank line, then the prompt.  Doesn't seem to do anything.

If I boot to the second drive and select the windows installation on hd0, I get Error 13 : "Inconsistent filesystem structure"
Doesn't sound to good.

I'm not terribly excited about weeks of reinstalling windows apps.  Is there any way I can make this disk bootable?

Thanks

---

### Post by oilchangeguy on 2008-11-11
"When I use the XP recovery disk and run FIXMBR, I get no response, just a blank line, then the prompt. Doesn't seem to do anything."

is this a factory restore cd, or a true xp cd?

---

### Post by kook44 on 2008-11-11
> **oilchangeguy said:**
> "When I use the XP recovery disk and run FIXMBR, I get no response, just a blank line, then the prompt. Doesn't seem to do anything."

is this a factory restore cd, or a true xp cd?

Factory restore CD.

---

### Post by mr.v. on 2008-11-11
> **kook44 said:**
> (side note: the 8.10 installation has gone too far to the school of Gates. By oversimplifying and dumbing-down the process, details and control are lost.  The installation program never asked me where I wanted to install GRUB, where previous versions had.  It just assumed I wanted to dual boot and overwrote the MBR on my first drive. I had planned on using the BIOS to selectively boot.  But I digress..)


On one of the install tabs during the 8.10 installer is an "Advanced" button which allows you to specify where you want grub installed to. You can also manually partition the drives. I have this same configuration and was able to select my second hard drive to install grub to and use bios to boot from disk 2.

As for your main problem. Try the following. Disable the drive with ubuntu on it (drive 2) and try booting and see what happens. If that doesn't work you have two options. Leave ubuntu drive disabled and boot with the XP recovery CD. Type ```
fdisk /mbr
``` then ```
fixmbr
``` and try rebooting to see if you can boot from the drive. If you can't download the Ultimate Boot CD from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) it's free. Then when you boot to a dos prompt type ```
fdisk /mbr
``` on the XP/Vista drive. That should repair it and make it bootable. Then redo the ubuntu installer and look for the Advanced button.

---

### Post by oilchangeguy on 2008-11-11
> **kook44 said:**
> Factory restore CD.

probably won't work. depends on the cd. some just restore to factory settings (all apps) and some use several cd's (windows on one and drivers, etc. on another). if yours only has windows, follow the prompts to enter the repair console. at the c:> prompt enter the admin password, if none press enter to bypass the prompt. then type fixboot and press enter, type fixmbr and press enter type exit and press enter. the computer should now boot into windows.

---

### Post by oilchangeguy on 2008-11-11
> **mr.v. said:**
> On one of the install tabs during the 8.10 installer is an "Advanced" button which allows you to specify where you want grub installed to. You can also manually partition the drives. I have this same configuration and was able to select my second hard drive to install grub to and use bios to boot from disk 2.

As for your main problem. Try the following. Disable the drive with ubuntu on it (drive 2) and try booting and see what happens. If that doesn't work you have two options. Leave ubuntu drive disabled and boot with the XP recovery CD. Type ```
fdisk /mbr
``` then ```
fixmbr
``` and try rebooting to see if you can boot from the drive. If you can't download the Ultimate Boot CD from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) it's free. Then when you boot to a dos prompt type ```
fdisk /mbr
``` on the XP/Vista drive. That should repair it and make it bootable. Then redo the ubuntu installer and look for the Advanced button.

fdisk /mbr is a command used in windows 95, 98, and ME. while it may work with 200, xp and vista, it's not the correct way. see post #5 for the correct steps.

---

### Post by cdtech on 2008-11-11
To fix the boot sector of a NTFS partition, you could use the program "testdisk".
```
sudo apt-get install testdisk
```
Start "testdisk"
```
sudo testdisk
```
Choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the NTFS partition you want to fix, choose "boot", then choose "Backup BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". 

That should fix the boot sector of that NTFS partition.

Hope this helps ya....

---

### Post by mr.v. on 2008-11-11
> **oilchangeguy said:**
> fdisk /mbr is a command used in windows 95, 98, and ME. while it may work with 200, xp and vista, it's not the correct way. see post #5 for the correct steps.

I'm fairly certain that the MBR for Windows up to and including XP is the same so fdisk /mbr should work to boot XP just as well as previous versions. It just directs the drive to boot the active partition. You may be correct in that the Vista MBR does differ in some way compared to previous versions. For vista you must run the bootsect.exe program in the Vista recovery console and specify /fixmbr and /fixboot and something else I think.

---

### Post by lisati on 2008-11-11
> **oilchangeguy said:**
> probably won't work. depends on the cd. some just restore to factory settings (all apps) and some use several cd's (windows on one and drivers, etc. on another). if yours only has windows, follow the prompts to enter the repair console. at the c:> prompt enter the admin password, if none press enter to bypass the prompt. then type fixboot and press enter, type fixmbr and press enter type exit and press enter. the computer should now boot into windows.

<aside>My COMPAQ desktop came with a recovery partition. When using the "fixmbr" approach with a Windows setup CD, I had to use "fixmbr C:" instead,.</aside>

---

### Post by kook44 on 2008-11-11
Many thanks for everyone's help.  OK - let me run down the various things Ive tried

- I enabled multiverse and universe, and apt can't find the 'testdisk' package.

- I booted to the recovery mode and ran fixboot. I was prompted with "Bootsector successfully written" then I tried fixmbr, fixmbr C:, fixmbr c:\, etc.  All with the same result - no dialogue, just a blank line then the prompt again.

- I have an old WIN95 boot disk that I fired up to run fdisk.  When I start it up, it says "Current Fixed Drive: 2".  I thought this was peculiar, I would think it would be 1.  When I view the partition information on that drive the table has 1 entry in it - partition:1, status:A, type:NTFS, mbytes:15258, system:6, usage:100%.  All typical I'd think.
Now, if I try to change the fixed drive to 1, I get an error message saying "Unable to access drive 1"
If I run fdisk /mbr from the prompt, I get "The master boot code has NOT been updated"

I remember once before I had an MBR problem from an ubuntu install, and it if I recall correctly, it was fixed rather easily by booting to the recovery console and running fixmbr.

I have no idea what's going on here.

Also - I forgot to mention that when I disable the second drive and boot directly to the windows drive, I get "Stage 1.5 GRUB loading, please wait... Error 25" I looked it up and that's a "Disk Read" error.  Now, I can't tell if that's because it's trying to chain to the GRUB on hd1, or if there is a read error in the MBR on hd0

Thanks again for all your help.  I'm hesitant to just throw in the towel on this one, especially because the drive is fine otherwise.

---

### Post by mr.v. on 2008-11-12
kook--

keep the linux drive disabled (or even unplugged) just so it's a non-issue. Then download the ultimate boot cd and boot with it to dos. Then run fdisk /mbr from it. Also run fdisk to ensure that the windows partition is active and bootable (and if not, make it active/bootable). There will only be one disk that will get fdisked if the other one is unplugged.

Then try booting. It should fix the problem. Then from there replug in the other drive and retry the install process.

Please note with your config you will have to manually edit your menu.lst grub file if you're going to have the slave drive boot first to get windows to boot. But that'll be a different story after you get your system back online.

---

### Post by kook44 on 2008-11-12
> **mr.v. said:**
> keep the linux drive disabled (or even unplugged) just so it's a non-issue. Then download the ultimate boot cd and boot with it to dos. Then run fdisk /mbr from it. Also run fdisk to ensure that the windows partition is active and bootable (and if not, make it active/bootable). There will only be one disk that will get fdisked if the other one is unplugged.


Ok - so when I run fdisk /mbr from the ubcd, I get "Invalid drive specification", Same if I try to view all partitions.  If I run any of the included hard drive diagnostic utilities, they all say "No disks found" or something to that effect.  Is this becasue my drive is SATA (not IDE)?

Also - regarding making a partition active, when I ran fdisk from a win95 boot disk (see my previous post), it listed the partition on disk 2 with status="A".  I guess that means active, but when I tried to make it specifically active, I got a message saying "Only partitions on drive 1 may be made active"

---

### Post by mr.v. on 2008-11-12
> **kook44 said:**
> Is this becasue my drive is SATA (not IDE)?


Certainly is possible. Frequently BIOS will have an option to take the drive from enchanced mode and place the drive in compatibility mode/IDE mode which should let the drives be accessible.

If it doesn't support that feature, then you're going to have to use the XP recovery console to fix it and you'll need to load the SATA drivers for XP first.

---

### Post by psusi on 2008-11-12
fdisk is an MSDOS utility, so it does not exist in non dos based windows.  The FIXMBR command in the 2000/xp/vista recovery console does the same thing that fdisk /mbr did, which is to say, rewrites the MBR with dos boot code.

It sounds like you either didn't run FIXMBR, or it didn't work.  The recovery console DID recognize your windows drive didn't it?

---

### Post by cdtech on 2008-11-12
You can't find the "testdisk" ?

Make sure you have the hardy/universe repository enabled. This will give you "testdisk". Fast and easy fix.

---

### Post by kook44 on 2008-11-12
> **mr.v. said:**
> Certainly is possible. Frequently BIOS will have an option to take the drive from enchanced mode and place the drive in compatibility mode/IDE mode which should let the drives be accessible.

If it doesn't support that feature, then you're going to have to use the XP recovery console to fix it and you'll need to load the SATA drivers for XP first.
Hmmm, my bios has various raid/ahci options, and one sata/pata option.  (not exacty sure -I'm at work now, I'll verify when I get home.

> **psusi said:**
> fdisk is an MSDOS utility, so it does not exist in non dos based windows.  The FIXMBR command in the 2000/xp/vista recovery console does the same thing that fdisk /mbr did, which is to say, rewrites the MBR with dos boot code.

It sounds like you either didn't run FIXMBR, or it didn't work.  The recovery console DID recognize your windows drive didn't it?
Yes, the recovery console does recognize the drive, if i run the DISKPART program (a trimmed-down FDISK), It recognizes one NTFS partition the size of the whole drive.  FIXMBR doesn't seem to work, but it doesn't give me any specific failure message. 

> **cdtech said:**
> You can't find the "testdisk" ?

Make sure you have the hardy/universe repository enabled. This will give you "testdisk". Fast and easy fix.
This was the 8.10 live CD (Intrepid Ibex, I believe)

Now I'm wondering - even if I did nuke the drive and reinstall from scratch, if all of these tools can't write to the MBR, why would the windows installer be able to?  Is it possible I have bad (unrepairable) sectors in my MBR?

---

### Post by cdtech on 2008-11-12
I know, but if you ADD the gutsy/universe repository you can install testdisk.

I had hardy on the first but its available on the gutsy as well.

---

### Post by Coreigh on 2008-11-12
[admission: I glossed over most of the posts, I am sorry if this has been tried already.]

I prefer the Win95/98 floppy with fdisk and "fdisk /MBR" command, and have used it many times to re-enable a windows partition. However I see that you have tried the FIXMBR on the 2k/XP install CD. Have you tried the FIXBOOT command?

With only the Windows hard drive installed as the primary disk (hda sda or C: how ever you like to think of it) boot the XP install cd and issue:
```
FIXBOOT C:
```

More information on FIXBOOT and the recovery console can be found with a Google search.

---

### Post by kook44 on 2008-11-12
GOT IT!!!!!!!!!!!!!!!

TESTDISK on the ultimate boot CD was the ONLY thing that was able to write to the MBR.  FYI - I had switched to combination SATA/PATA mode in my BIOS beforehand.  Don't know if this had anything to do with it - I never tried testdisk in regular mode.

Thanks for all your help!!!

:guitar:

---

### Post by cdtech on 2008-11-12
Congrats to you....:guitar:

---

