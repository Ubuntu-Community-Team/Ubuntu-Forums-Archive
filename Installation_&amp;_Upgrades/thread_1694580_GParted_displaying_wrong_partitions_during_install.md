---
title: "GParted displaying wrong partitions during installation"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by digi198816 on 2011-02-24
Hey, 
  I have installed ubuntu many times before and never encountered this problem. The installer shows partition sizes which do not match my current sizes at all. This occurs during LiveCD too, I have taken a screenshot of the problem. GParted seems to be showing incorrect partitions while the one the right is correct. Any help regarding this topic will be appreciated.
Thank you very much

[IMG]http://img153.imageshack.us/img153/8633/screenshotvvv.png[/IMG]

---

### Post by srs5694 on 2011-02-24
I'm far from positive of this, but there's a chance that you're seeing a mixup of old GUID Partition Table (GPT) data shown by GParted and new Master Boot Record (MBR) data shown by Disk Utility. To get more diagnostic data, I recommend you do the following:


[list=1]
[*]Download GPT fdisk (gdisk) from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) You'll need the .deb file for your architecture (probably i386 or amd64). Do not use the version in the Ubuntu repositories unless you're using the 11.04 alpha version; in previous Ubuntu versions, the gdisk version in the repositories is hopelessly out of date.
[*]Double-click the .deb file you download to install the package.
[*]Open a text-mode Terminal window.
[*]In the Terminal, type "sudo gdisk -l /dev/sda"
[*]Look at the four lines following "Partition table scan," as described below.
[*]If gdisk asks whether to use the MBR or the GPT data, select either option, or hit Ctrl+C to exit.
[/list]


The GPT fdisk partition table scan looks for the presence of four different partition table types: MBR, GPT, BSD disklabels, and Apple Partition Map (APM). The report looks something like this:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

This example shows a GPT disk. If the disk uses MBR, the "MBR" line would read "MBR only" and the "GPT" line would read "not present." If your disk is misconfigured as I suspect it might be, the "MBR" line will read "MBR only" and the "GPT" line will read "present". If this is the case, you should do a little more digging with fdisk and gdisk to verify which set of partitions is correct (probably MBR, but I don't want to tell you to wipe out the stray GPT data until that's 100% certain). Once you know which partition table to keep, you can delete or overwrite the unwanted one, which should clear up the problem.

There's also a chance that old BSD or APM data are present on the disk, which could cause similar problems. If so, the partition table scan should alert you to this fact, but the details of the report will be different.

Of course, as stated at the outset, I'm far from positive that my hypothesis is correct. Run the test with gdisk and report back the results. Whatever you do, though, *do not* write any changes to your partitions using any utility until you know what's causing the problem! Poking about with such things at random is likely to make matters worse.

---

### Post by digi198816 on 2011-02-24
> **srs5694 said:**
> I'm far from positive of this, but there's a chance that you're seeing a mixup of old GUID Partition Table (GPT) data shown by GParted and new Master Boot Record (MBR) data shown by Disk Utility. To get more diagnostic data, I recommend you do the following:


[LIST=1]
[*]Download GPT fdisk (gdisk) from [its Sourceforge download page.]("http://sourceforge.net/projects/gptfdisk/files/") You'll need the .deb file for your architecture (probably i386 or amd64). Do not use the version in the Ubuntu repositories unless you're using the 11.04 alpha version; in previous Ubuntu versions, the gdisk version in the repositories is hopelessly out of date.
[*]Double-click the .deb file you download to install the package.
[*]Open a text-mode Terminal window.
[*]In the Terminal, type "sudo gdisk -l /dev/sda"
[*]Look at the four lines following "Partition table scan," as described below.
[*]If gdisk asks whether to use the MBR or the GPT data, select either option, or hit Ctrl+C to exit.
[/LIST]


The GPT fdisk partition table scan looks for the presence of four different partition table types: MBR, GPT, BSD disklabels, and Apple Partition Map (APM). The report looks something like this:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```This example shows a GPT disk. If the disk uses MBR, the "MBR" line would read "MBR only" and the "GPT" line would read "not present." If your disk is misconfigured as I suspect it might be, the "MBR" line will read "MBR only" and the "GPT" line will read "present". If this is the case, you should do a little more digging with fdisk and gdisk to verify which set of partitions is correct (probably MBR, but I don't want to tell you to wipe out the stray GPT data until that's 100% certain). Once you know which partition table to keep, you can delete or overwrite the unwanted one, which should clear up the problem.

There's also a chance that old BSD or APM data are present on the disk, which could cause similar problems. If so, the partition table scan should alert you to this fact, but the details of the report will be different.

Of course, as stated at the outset, I'm far from positive that my hypothesis is correct. Run the test with gdisk and report back the results. Whatever you do, though, *do not* write any changes to your partitions using any utility until you know what's causing the problem! Poking about with such things at random is likely to make matters worse.

Hey,
I proceeded as you advised and you were correct in your assumption as "GPT" line does indeed read present and "MBR" reads MBR only. I am not sure however on how to proceed as I would hate to further damage the drive in anyway. 
In addition, When I print data from MBR, I get accurate results of my current drive and when I use GPT, I get the past partitions, I am guessing I would need to delete GPT in this case? I am pasting the results below:

MBR - Correct Results

```
Command (? for help): p
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4B5887A1-D14F-484B-9F60-BD127D0DE1A8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 4973 sectors (2.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Linux/Windows data
   2          206848       234438655   111.7 GiB   0700  Linux/Windows data
```

GPT - Incorrect!

```
Your answer: 2
Using GPT and creating fresh protective MBR.

Command (? for help): p
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9BB14605-AEC7-4AC7-BD28-6F9A3BF9FF1B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 8-sector boundaries
Total free space is 264733 sectors (129.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640        59011447   27.9 GiB    AF00  MacOSX
   3        59275264       234440703   83.5 GiB    0700  WINDOWS
```

All help is appreciated.
Thanks a lot!

---

### Post by Skaperen on 2011-02-24
In a command shell under the installer or live CD, do the following:

**[FONT=Courier New]cat /proc/partitions[/FONT]**

Do these sizes match the MBR or GPT?  This is what the kernel sees.

All  software should use the MBR over the GPT, since the GPT is technically  not valid without a protective MBR (even if the secondary table at the  end of the drive matches perfectly).  But some things don't do it right.

This  is fixable, but the command to do it is dangerous and with the  slightest typo can ruin the MBR, although you have already posted enough  info that I could restore a ruined MBR.  But that dangerous command  could also wipe the data, too, and I could not restore that.  If it were  my computer, I wouldn't hesitate the slightest in fixing this, but I  have had people mistype commands I give, before.

---

### Post by digi198816 on 2011-02-24
Hello,
 Thanks a lot for your help. I went ahead and got rid of the GPT and now everything is fine :) I really appreciate the help, 

Thank you.

---

### Post by AySz88 on 2011-04-15
I have this exact problem - the MBR is "MBR only" and correct, but the GPT is utterly wrong.  What is the command one needs to use to delete or fix the GPT?  I tried the gdisk's 'r,f' command ("Load MBR and build fresh GPT from it.") but that didn't seem to do anything.

[edit] Ah, I forgot to write the new table to disk using the 'w' command - so it'd be 'r,f,w'.  And to delete the GPT instead, it looks like it should be "r,x,z,w"?

[edit 2] So, I figured that I didn't actually want a GPT, so I did gdisk's 'r,g,w' to get rid of it and go back to MBR-only...and then my Windows partition failed to boot.  Had to re-add the boot flag to my Windows partition in gparted, and then it worked again.  Whew.

---

### Post by srs5694 on 2011-04-16
AySz88, are you now able to install Linux? Is your problem fixed? If not, please start a new thread and describe precisely what you're seeing.

Also, for future reference, what you did with gdisk was not the best thing to do. It's lucky you got away from that with as little trouble as you did. Remember: Messing with partitions is dangerous, particularly when you don't fully understand the problems or the tools. I've written extensive documentation for GPT fdisk, both [on the Web](http://www.rodsbooks.com/gdisk/) and in the form of its man pages. *Please* consult the documentation for these (and all other) programs if you don't fully understand what they do!

---

### Post by dino99 on 2011-04-16
the installer is a nightmare, i never use it for partitioning, better to use partedmagic

[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

then use the "alternate" iso to make a manual install

---

### Post by AySz88 on 2011-04-17
> **srs5694 said:**
> AySz88, are you now able to install Linux? Is your problem fixed? If not, please start a new thread and describe precisely what you're seeing.

Also, for future reference, what you did with gdisk was not the best thing to do. It's lucky you got away from that with as little trouble as you did. Remember: Messing with partitions is dangerous, particularly when you don't fully understand the problems or the tools. I've written extensive documentation for GPT fdisk, both [on the Web](http://www.rodsbooks.com/gdisk/) and in the form of its man pages. *Please* consult the documentation for these (and all other) programs if you don't fully understand what they do!

Well, I'm actually not installing Ubuntu at the moment (I have a Kubuntu partition, though); I just happened to see the same problem in GParted and gdisk in a GParted Live CD.  GParted still is complaining about not being able to satisfy constraints on resizing, but I'll start a different thread elsewhere about that.

And to be frank, I thought that *was* what I was supposed to do after reading the gdisk man page.  What should it have been instead?

---

### Post by srs5694 on 2011-04-17
From what I can tell, your disk wasn't a GPT disk at all, so you shouldn't have used gdisk to convert it to GPT form (which is what you did). You should have used the "z" option on the experts' menu to wipe the stray GPT data; or used [FixParts](http://www.rodsbooks.com/fixparts/) to wipe the stray GPT data. The "f" option on gdisk's recovery & transformation menu is intended for creating a *GPT* disk using MBR data:

[quote=gdisk man page]f - Load MBR and build fresh GPT from it. Use this option if your GPT is corrupt or conflicts with the MBR and you want to use the MBR as the basis for a new set of GPT partitions. 
[/quote]

I suspect you don't understand the difference between MBR and GPT. See [this page](http://www.rodsbooks.com/gdisk/whatsgpt.html) for a summary.

As to the "constraints on resizing" issue, that can probably be overcome by selecting a different partition alignment option; these have changed recently, and GParted still has what I'm guessing are rounding bugs that cause problems when you try to resize a partition when a nearby partition uses a different partition alignment policy than the current settings.

---

