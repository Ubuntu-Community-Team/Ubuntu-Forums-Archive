---
title: "Grub does not detect Windows 7"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by nycazncarguy on 2010-05-11
Hey, i did a fresh install of 10.04 on my asus 1005ha netbook (first-gen 1005ha, if it matters), and it works great.  However, grub does NOT detect my windows partition.  In gparted, the partition is recognized as "unknown".  I can't mount it in ubuntu.

This is what fdisk gives me:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b72c79b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290903+  ee  GPT





Any clue?  I honestly don't mind reinstalling 7, but my biggest problem is that i need to grab the files from the partition.  if i cant even mount it, i honestly dont know what's wrong.

My windows 7 is not corrupted.  it is also not virus-infected.  I know what i am doing, and i know my windows is fine.  it has been running fine prior to installing ubuntu.  I'm just saying this becuz i noticed that viruses are a common response to similar problems like this.  However, i did not come across a thread with an issue like mine, or maybe i just missed it.  i dunno.

thanks in advance!

---

### Post by lechien73 on 2010-05-11
The clue comes from the fact that it's a GPT partition. Are you running Windows 7 64-bit? You could try installing gparted:

```
sudo apt-get install gparted
```

Then:

```
sudo gparted
```

If you then see an NTFS partition listed, then try mounting it as normal:

```
mkdir /mnt/win7
sudo mount /dev/sdaX /mnt/win7
```

Where "X" in sdaX is the number of the NTFS partition.

---

### Post by darkod on 2010-05-11
Fix for Grub2 when you have GPT partition table:
[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)

---

### Post by nycazncarguy on 2010-05-11
ohhhh, i think that was from when i was installing osx. that's probaby whyits in gpt. i'll try the stuff from the link soon.

@lechien73
i already tried gparted, as i mentioned above. shows up as unknown *shrugs*.

---

### Post by darkod on 2010-05-11
> **nycazncarguy said:**
> ohhhh, i think that was from when i was installing osx. that's probaby its in gpt. i'll try the stuff from the link soon.

@lechien73
i already tried gparted, as i mentioned above. shows up as unknown *shrugs*.

Actually Gparted reporting it as unknown is getting me worried. That fix is for grub2 only, Gparted should still see the partition OK. I hope you don't have another issue.

---

### Post by nycazncarguy on 2010-05-11
> **darkod said:**
> Actually Gparted reporting it as unknown is getting me worried. That fix is for grub2 only, Gparted should still see the partition OK. I hope you don't have another issue.

Yeah, just tried the fix, and i just realized. Gparted still shows it as unknown =(.

Anybody have any idea why?  It (windows 7) was working fine and speedy right before.  I don't use 64bit, since this is a netbook here.

---

### Post by darkod on 2010-05-11
> **nycazncarguy said:**
> Yeah, just tried the fix, and i just realized. Gparted still shows it as unknown =(.

Anybody have any idea why?  It (windows 7) was working fine and speedy right before.  I don't use 64bit, since this is a netbook here.

In Gparted if you right-click the win7 partition and select Check it might tell you more.

There are other ways to try and do the windows diskcheck, if nothing else works.

Depending what the gparted check tells you, you can consider putting a windows MBR on the hdd, and try if win7 boots and works fine. Maybe it got corrupted you just don't know it yet. :)

Note: I just remembered, you might need to install the ntfs-progs package for gparted to be able to do a check on ntfs partition.

---

### Post by oldfred on 2010-05-11
gparted is smart enough to know that the drive is gpt and does not edit it because it is not updated yet to handle gpt partitions.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

do you have a BIOS boot partition?
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

---

### Post by nycazncarguy on 2010-05-14
> **darkod said:**
> In Gparted if you right-click the win7 partition and select Check it might tell you more.

There are other ways to try and do the windows diskcheck, if nothing else works.

Depending what the gparted check tells you, you can consider putting a windows MBR on the hdd, and try if win7 boots and works fine. Maybe it got corrupted you just don't know it yet. :)

Note: I just remembered, you might need to install the ntfs-progs package for gparted to be able to do a check on ntfs partition.

GParted just tells me its unknown format.  It doesnt know anything else.

> **oldfred said:**
> gparted is smart enough to know that the drive is gpt and does not edit it because it is not updated yet to handle gpt partitions.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)

do you have a BIOS boot partition?
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

I am not sure what all that stuff meant lol.  I was reading through the links and i got lost.  Can you explain to me what I should do?  And how do i check if i have a BIOS boot partition?


Btw, the reason my hdd is gpt partition is because i installed osx.  So no, I can't change it to mbr or something, cuz my osx wont work anymore.

---

### Post by darkod on 2010-05-14
I'm confused. At the beginning you mentioned only booting win7 is a problem. Then later you say you also have osx. Can you boot it fine?

I believe the process to boot all three different systems on the same hdd is different than just dual booting ubuntu/windows.

Otherwise, the second link oldfred provided basically says you could create a bios boot partition yourself if you don't have one.

If you could post a screenshot of Gparted that would help to get an idea which partitions you have. And if you can write short explanation which partition is what.

Otherwise the idea would be to create a small 64KB or 128KB partition before you install ubuntu. Note that this has nothing to do with the ubuntu /boot partition.

After that you can just set it as bios boot with the command in the link:
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

Then grub2 knows where to go and there is no confusion with using GPT.

---

### Post by nycazncarguy on 2010-05-15
> **darkod said:**
> I'm confused. At the beginning you mentioned only booting win7 is a problem. Then later you say you also have osx. Can you boot it fine?

I believe the process to boot all three different systems on the same hdd is different than just dual booting ubuntu/windows.

Otherwise, the second link oldfred provided basically says you could create a bios boot partition yourself if you don't have one.

If you could post a screenshot of Gparted that would help to get an idea which partitions you have. And if you can write short explanation which partition is what.

Otherwise the idea would be to create a small 64KB or 128KB partition before you install ubuntu. Note that this has nothing to do with the ubuntu /boot partition.

After that you can just set it as bios boot with the command in the link:
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

Then grub2 knows where to go and there is no confusion with using GPT.

Yes, osx boots. I'm not sure what different process you're talking about, as I quad-boot my regular laptop, osx included, and all 4 work fine.  Then again, my grub on my laptop is still 1.5, even though im using 10.04. *shrugs*   Grub2 is screwing with everything lol.  I'm sure theres reasons why grub2 is better, so no need to defend it.

I will post a screenshot soon.

---

### Post by nycazncarguy on 2010-07-17
Hey, sorry about the long delay, i've been really busy. then again, the delay is more hurtful towards myself than to you guys, most likely, so iono why im saying sorry lol.

anyway, i posted two screenshots. one is of fdisk, and the other is of gparted.  the highlighted partition in gparted is the windows partition, which is supposed to be ntfs.

---

### Post by nycazncarguy on 2010-08-21
Okay, so i guess nobody knows?  It's been a while...

Well, anyway, I currently give up on trying to make this work with the GUID thing.  I'm just gonna reformat the drive and reinstall everything.  However, before I do that, is there ANY way I can boot into windows right now?  Or at least access that partition? I just wanna grab some important files before I wipe.  I'm hoping that an approach to this is easier than getting grub2 to play cooperatively with GUID.

thanks in advance!

---

### Post by oldfred on 2010-08-22
If one drive is gpt and the other is MBR (msdos)

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by nycazncarguy on 2010-08-22
> **oldfred said:**
> If one drive is gpt and the other is MBR (msdos)

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)


Well, all this is actually on a single drive, so I'm not sure if those steps still apply.  I tried it anyway.

It seems that I've tried this method before, but it did not work.  After adding the GRUB_PRELOAD_MODULES thing, nothing changed.  I tried the grub-install thing, but it said something about how its bad to write grub2 to a partition instead of the mbr, and that i would have to use --force to make it work with blocklisting.  I tried that too, but still nothing changed.  Grub2 never even listed Windows as an option to boot into since I first installed Ubuntu.

I'm not all too sure what else to do.  Like i mentioned in a previous post, I'm ready to just reinstall everything, but I need to back that stuff out of my Windows first =/

EDIT
to top it off, windows 7 installer doesnt even boot on the netbook.  I have the contents of the disc copied to a external hard disk.  I know its not the disk, because it boots and runs on all the other computers i've tried it on.  So I cant even try the repair thing. =/

---

### Post by srs5694 on 2010-08-23
First, concerning accessing the partition in Linux, try posting this command's output:

```

blkid /dev/sda3

```

This won't fix anything, but the output should tell you whether Linux can detect a filesystem on the partition. The output on an NTFS partition should look something like this:

```

/dev/sda3: UUID="4C3C7DCA2046A466" TYPE="ntfs"

```

Your UUID value may be different, but the type should be "ntfs". If it's not, or if the blkid program produces no output at all, then the partition's contents may be corrupted. In that case, you might need to resort to something like [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) to do the data recovery.

If blkid shows the partition as NTFS, then it's conceivable it's not showing up properly because of a mis-set partition type code -- although Linux generally ignores these, so this seems like a long shot to me. The main thing going for this hypothesis is that GParted is saying the "boot flag" is set; the last I checked, that meant the type code is that for an EFI System Partition, which is the wrong type code for an NTFS data partition. You can view and change the type code using my [GPT fdisk](http://www.rodsbooks.com/gdisk/) (aka gdisk) program. The type code should be "0700", as reported by GPT fdisk, as in:

```

gdisk -l /dev/sda
{...stuff snipped for brevity...}
Number  Start (sector)    End (sector)  Size       Code  Name
   3            2048        31576030   15.1 GiB    0700  Linux/Windows data

```

Note the "Code" column in the output. If it's not "0700", then you can launch gdisk without the "-l" option (note that's a lowercase "L", not a digit "1"), use the "t" command to change the type code, and then use "w" to write the changes out to disk.

You can also use GPT fdisk to create a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which might enable Windows to boot again. You'd use the "h" option on the recovery & transformation menu. Put the Windows partition, as well as any other partition(s) to which Windows should have access, in the MBR. Hybrid MBRs are, however, flaky and dangerous. Unfortunately, they're the easiest way to accomplish certain multi-booting tasks, thanks to Microsoft's dragging its heels over GPT support.

Good luck!

---

### Post by nycazncarguy on 2010-08-23
> **srs5694 said:**
> First, concerning accessing the partition in Linux, try posting this command's output:

```

blkid /dev/sda3

```

This won't fix anything, but the output should tell you whether Linux can detect a filesystem on the partition. The output on an NTFS partition should look something like this:

```

/dev/sda3: UUID="4C3C7DCA2046A466" TYPE="ntfs"

```

Your UUID value may be different, but the type should be "ntfs". If it's not, or if the blkid program produces no output at all, then the partition's contents may be corrupted. In that case, you might need to resort to something like [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) to do the data recovery.

If blkid shows the partition as NTFS, then it's conceivable it's not showing up properly because of a mis-set partition type code -- although Linux generally ignores these, so this seems like a long shot to me. The main thing going for this hypothesis is that GParted is saying the "boot flag" is set; the last I checked, that meant the type code is that for an EFI System Partition, which is the wrong type code for an NTFS data partition. You can view and change the type code using my [GPT fdisk](http://www.rodsbooks.com/gdisk/) (aka gdisk) program. The type code should be "0700", as reported by GPT fdisk, as in:

```

gdisk -l /dev/sda
{...stuff snipped for brevity...}
Number  Start (sector)    End (sector)  Size       Code  Name
   3            2048        31576030   15.1 GiB    0700  Linux/Windows data

```

Note the "Code" column in the output. If it's not "0700", then you can launch gdisk without the "-l" option (note that's a lowercase "L", not a digit "1"), use the "t" command to change the type code, and then use "w" to write the changes out to disk.

You can also use GPT fdisk to create a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which might enable Windows to boot again. You'd use the "h" option on the recovery & transformation menu. Put the Windows partition, as well as any other partition(s) to which Windows should have access, in the MBR. Hybrid MBRs are, however, flaky and dangerous. Unfortunately, they're the easiest way to accomplish certain multi-booting tasks, thanks to Microsoft's dragging its heels over GPT support.

Good luck!


Unfortunately, nothing came up when I ran that thing =(.  I downloaded the program and am currently running it.  It actually works!  It's recovering ALL my files though, even AIM icons -.-

But it works, and its recovering the files i need in the meantime, so I really can't complain.

Big thanks for the program suggestion!  It's really helpful.  Hopefully I wont run into this program when I try the triple-booting thing again.  It seems its easier following those tutorials than trying to make this gpt thing work out.

---

