---
title: "XP dual-boot problem (with log)"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by ButtBuntu on 2012-06-19
[]("http://paste.unbuntu.com/1049700")Appreciate any help.  Installed Ubuntu on top of XP a few months ago and it initially worked, but somewhere along the line XP stopped booting completely (system reboots after the XP load screen).

[http://paste.ubuntu.com/1049700](http://paste.ubuntu.com/1049700)

---

### Post by wilee-nilee on 2012-06-19
If you have a XP disc run a chkdsk /r from it, it should run on a boot to it hopefully.

It will probably ask from the terminal on the XP disc if you want it run on startup say yes.

This is assuming XP is not broke in some other way.

You may need to reload the MS bootloader to to the mbr as well to get a clean boot with the chkdsk and to check the XP boot in general, from the XP terminal on the booted cd.
```
/fixmbr
```

---

### Post by ButtBuntu on 2012-06-26
> **wilee-nilee said:**
> If you have a XP disc run a chkdsk /r from it, it should run on a boot to it hopefully.

It will probably ask from the terminal on the XP disc if you want it run on startup say yes.

This is assuming XP is not broke in some other way.

You may need to reload the MS bootloader to to the mbr as well to get a clean boot with the chkdsk and to check the XP boot in general, from the XP terminal on the booted cd.
```
/fixmbr
```


Hey thanks for the input.  I did what you said and now my HD is borked and I can't even get into Ubuntu anymore.

Operating system is missing

That is my new error after attempting to run Boot Repair off Ubuntu Live CD.  

I am now running off Ubuntu Live CD exclusively trying to fix this problem as my HD has a ton of very important data that I need to retrieve.

How can I force the old boot sector data back into the current boot sector and at least get back to the point where I can boot into Ubuntu so I can retrieve my files?

EDIT:  Here is the updated Pastebin:

[http://paste.ubuntu.com/1059957/](http://paste.ubuntu.com/1059957/)

---

### Post by oldfred on 2012-06-26
It looks like your partition table got totally erased. Did you try to run chkdsk on the Linux partitions or start a system restore (which erases partitions first)?

Fortureately you have the table documented from your first run of boot script.
```

Drive: sda ________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS
/dev/sda2         268,414,974   272,711,679     4,296,706   5 Extended
/dev/sda5         268,414,976   272,711,679     4,296,704  82 Linux swap / Solaris
/dev/sda3         272,711,680   311,773,183    39,061,504  83 Linux
/dev/sda4         311,773,455   546,306,389   234,532,935  83 Linux

```

I would try testdisk first as it may automatically rebuild partition table.

But you could manually rebuild it from above info if we have to.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by ButtBuntu on 2012-06-27
> **oldfred said:**
> It looks like your partition table got totally erased. Did you try to run chkdsk on the Linux partitions or start a system restore (which erases partitions first)?

Fortureately you have the table documented from your first run of boot script.
```

Drive: sda ________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 NTFS / exFAT / HPFS
/dev/sda2         268,414,974   272,711,679     4,296,706   5 Extended
/dev/sda5         268,414,976   272,711,679     4,296,704  82 Linux swap / Solaris
/dev/sda3         272,711,680   311,773,183    39,061,504  83 Linux
/dev/sda4         311,773,455   546,306,389   234,532,935  83 Linux

```I would try testdisk first as it may automatically rebuild partition table.

But you could manually rebuild it from above info if we have to.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Hey oldfred, testdisk worked great.  I ran it and wrote a new table, and the good news is that I can now access my data on my old HD via Ubuntu Live CD.  The bad news is that I'm back to where I started the beginning of this thread.

After I ran testdisk and rebooted, it ran me straight into the XP load screen without giving me an option to dual boot.  Then XP ran chkdsk and deleted a few things and rearranged a few things.  Upon chkdsk completing, it rebooted and then XP got to the load screen before BSODing as it previously was doing.

The only difference now is that I'm not getting a dual boot option.  It's just booting straight into XP and failing.  I'll run a boot repair again to see what's changed.

If Microsoft still supported XP, I would just copy my good data off the HD and reformat everything, but I read that I won't be able to update my old XP SP1 disc to SP3 if I do that.  I'd really like to have XP SP3 available still for gaming purposes (and I'd rather not spend all the time reinstalling).   Thoughts?

---

### Post by oldfred on 2012-06-27
I thought you could still get the service packs.
XP Service Packs
[http://support.microsoft.com/kb/322389](http://support.microsoft.com/kb/322389)

Have you rerun chkdsk, fixboot and other repairs? It probably installed the Windows boot loader to the MBR but until you get it fixed best to leave it. When you want Ubuntu again reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you prefer a gui way:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by ButtBuntu on 2012-07-01
> **oldfred said:**
> I thought you could still get the service packs.
XP Service Packs
[http://support.microsoft.com/kb/322389](http://support.microsoft.com/kb/322389)

Have you rerun chkdsk, fixboot and other repairs? It probably installed the Windows boot loader to the MBR but until you get it fixed best to leave it. When you want Ubuntu again reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

If you prefer a gui way:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Ok oldfred, thanks for your assistance and patience.  I seem to be in a rough spot.  After attemping to repair XP via the install disc, I was given the same error as before.  At this point, I think my XP install is corrupted somehow even though I had done nothing in XP after I installed Ubuntu for the first time.  The only thing I had done related to Windows was install WINE in Ubuntu and move a couple of game-related files between partitions.  I'm not sure if this is enough to corrupt XP or what.

Boot-Repair does not seem to be working as we want.  It initially just ruined the partition table again and caused a bunch of wingdings or other random characters to pop up where "Missing operating system" was popping up earlier.

A bit stumped.  I had initially been okay with just reformatting but after looking through my files, I realize I have about 40 GB of video data that I want to save, which makes reformatting an absolute last option now.

We need to get XP back up and running, but it appears /fixboot /fixmbr is not a viable strategy now.

---

### Post by oldfred on 2012-07-01
I do not like the default settings of Linux in NTFS partitions as it shows all the normally hidden system files & folders. I normally suggest resetting to read only. When I ran XP I used to always turn on visibility of the hidden files, but often broke system by click and accidentally dragging some vital file or folder to another place. I learned I did that and often was able just to move folders back and it would then work.

Normally chkdsk run until no errors & the fixBoot, fixMBR solve Windows boot problems. 

If you want to boot Ubuntu, you have to reinstall the grub2 boot loader to the MBR and then you should be able to boot it. If chkdsk has cleared the needs chkdsk flag then Ubuntu should be able to mount your XP NTFS partition to let you copy data.

Either boot repair or the links I posted before should let you reinstall grub.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct Yours is sda3 or sda4?:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by YannBuntu on 2012-07-01
Hello

> **ButtBuntu said:**
> It initially just ruined the partition table

The partition table was ok after the first Boot-Repair use (as shown in the [post#1 log]("http://paste.ubuntu.com/1049700/")) and was broken before the 2nd Boot-Repair use (as shown in the [post#3 log]("http://paste.ubuntu.com/1059957/")).
So it was broken by the operations performed in between (post#3: /fixmbr only?).

If you haven't formatted your disk, you can obtain the original partition table via the Boot-Repair -> Advanced options -> Backup partition tables button. Save the ZIP file somewhere and send it by email (yannubuntu ATT gmail DOTcom) or attach it to your reply in this thread. We will tell you how to recover the table, then you can try the /fixboot.

---

### Post by ButtBuntu on 2012-07-11
> **oldfred said:**
> I do not like the default settings of Linux in NTFS partitions as it shows all the normally hidden system files & folders. I normally suggest resetting to read only. When I ran XP I used to always turn on visibility of the hidden files, but often broke system by click and accidentally dragging some vital file or folder to another place. I learned I did that and often was able just to move folders back and it would then work.

Normally chkdsk run until no errors & the fixBoot, fixMBR solve Windows boot problems. 

If you want to boot Ubuntu, you have to reinstall the grub2 boot loader to the MBR and then you should be able to boot it. If chkdsk has cleared the needs chkdsk flag then Ubuntu should be able to mount your XP NTFS partition to let you copy data.

Either boot repair or the links I posted before should let you reinstall grub.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct Yours is sda3 or sda4?:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub


OKAY!  Good progress here.  This worked and got me back to square one.  I can boot into Ubuntu again as before.  It gives me the same long list of choices at bootup, and my Ubuntu partition works.  

I would still like to get XP working.  Would transferring all my data to a Linux partition and then reinstalling XP work?  What would be the best way to go about that without running into booting problems?

---

### Post by oldfred on 2012-07-12
If you can boot Ubuntu or a liveCD, can you mount the NTFS partition? 
If it needs chkdsk or is hibernated, Ubuntu will not mount it to prevent further damage. Otherwise you should just be able to copy all your files with Nautilus  file manager. It should auto mount it. 

Often in left panel it is just shown as the size. I always try to label every partition with gparted when I create them or using Disk Utility when I have forgotten. With labels then you see the label which you then know what it is in Nautilus.

---

### Post by ButtBuntu on 2012-07-12
> **oldfred said:**
> If you can boot Ubuntu or a liveCD, can you mount the NTFS partition? 
If it needs chkdsk or is hibernated, Ubuntu will not mount it to prevent further damage. Otherwise you should just be able to copy all your files with Nautilus  file manager. It should auto mount it. 

Often in left panel it is just shown as the size. I always try to label every partition with gparted when I create them or using Disk Utility when I have forgotten. With labels then you see the label which you then know what it is in Nautilus.


I can mount NTFS and move files.  What I am wondering is, do I just format the first 137 GB where XP resides, then reinstall XP as normal?  Will this give me anymore boot problems?  I'm wary of XP overwriting the boot block again.

Last time, I installed Ubuntu after installing XP on the first 137 GB of the HD.  I had no problems dual booting for a few weeks that way.  I'm still not even sure how XP got corrupted.

Running a CHKDSK off the XP CD says there are unrecoverable problems.  I'd like to think that's not the case, but I'm willing to just format and get on with things at this point now that I can retrieve my data.

---

### Post by oldfred on 2012-07-12
All Windows installs over write the MBR and you have to reinstall grub2's boot loader to the MBR.

If you want a gui:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Or just reinstall:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

