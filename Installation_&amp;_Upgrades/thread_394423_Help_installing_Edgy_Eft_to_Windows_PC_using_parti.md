---
title: "Help installing Edgy Eft to Windows PC using partitions"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Cherry Cotton on 2007-03-26
Arrr! So, I'm attempting to install Edgy Eft Ubuntu Linux to my PC, right? It's a Windows PC, but using QTParted on Knoppix, I made an "ext3" partition that's about six gigs, for Ubuntu Linux. On my brother's advice, I made a "linux-swap" partition that's about half a gig, which is also how much RAM I have. (I used GNOME Partition Editor on the Ubuntu LiveCD to make the swap partition; QTParted had become crabby about that.)

So, I have four partitions, in the order listed on QTParted and GParted:

hda2, a small FAT32 partition for recovery of Windows data. It came with my computer.
hda1, an NTFS partition of 40-50 gigs. Contains Windows XP and all my Windows data.
hda3, my six-gig "ext3" partition, created for Ubuntu Linux.
hda4, the half-gig "linux-swap" partition.

So, I run the Ubuntu LiveCD. It's very, very slow, but that won't be a problem, I think, because I'm about to install it, and have a partition ready and waiting.

Sometimes, it will crash. It once crashed while trying to set the time during the installation process, so I haven't bothered since (why does assume that your clock is set to GMT, no matter what time zone you specify?). So, I try to get through it as fast as possible. (I thought activating the swap partition would help, but it hasn't seemed to.)

On step five, specifying a partition, it gives me two options. First, nuke my hard disk, which is not appealing. Second, I can edit the partition table. It seems unnecessary to *edit* my partition table, but that certainly sounds less dangerous than giving my accumulated Windows data the heave-ho. (Yes, my important stuff is backed up... still...)

So I tell it to edit the partition table. (By the way, that first option, "nuke the hard disk;" it refers to my *entire* hard disk, that is, "hda," rather than asking me to choose a partition. It describes my hard disk by name, "hda," size, "61.25GB," and model number, which is way long. That "size" figure, by the way, is the size of all four partitions combined.) When I choose to edit the partition table, it will start up GParted... and I wait... and it freezes. This happens *every time*. The system is *completely frozen up*.

This is agonizing. I can run the Install program. I can run GParted. However, if Install tries to activate GParted, the system freezes up. And, I cannot simply tell Ubuntu to use the hda3 partition that *I created for it*. I have no idea what to do. Once, by sheer chance... I think this was after I specified an "ext3" partition, but couldn't get a "linux-swap" partition just yet (QTParted was cranky). Wahoo, I thought, it's working! It began to install, and then... it told me I needed a root filesystem, and that I can fix this in the partition editor. Waaa? So, yes, I think that's when I discovered that I could run GParted, just not at the same time as Install... anyway, yes, I have no idea what a root filesystem is. None. And I so, so, so wish I could simply tell the installer to use a specific partition, rather than give me the unsatisfactory options of erasing my hard disk and editing a partition table that does not *need* editing... or so I thought, anyway.

Okay, so, that's what I need help with. Thank you! My system is a crappy eMachines box, yes, but it works, usually, except that sometimes my wireless card goes dead and I have to restart (ARGH I'm sick of that). Again, I have about half a gig of RAM. I am computer-literate, but I'm new to Linux so PLEASE don't tell me that all I have to do is reflux my fibulating recon drives and I'm home free. It'll just go right over my head. Fear of partitioning my hard disk kept me from installing Linux for years. (And yes, I want to keep Windows... I need something to watch Homestar Runner cartoons on...)

---

### Post by codesplice on 2007-03-26
First off, the important stuff - you can watch Homestar Runner on Linux.  I've been doing it for years :)

Secondly, did you try verifying the LiveCD before running it?  From the boot menu the disk presents you with, choose "Verify" or something to that extent.  Something may not be quite right on the disk, which could cause several problems for sure.

From my experience, there's not really any need to edit the partition table before you boot from the LiveCD - the editor on the install routine seems to do just fine.  

From that editor, be sure to choose a mount point for your ext3 partition - "/" should be sufficient ("/" being the root directory).  Also, the swap partition should be mounted as "/swap".

Hopefully some of this will help you out :)

---

### Post by Cherry Cotton on 2007-03-26
Regarding Homestar Runner: Oh, good! I'm sure I'll use Windows for... something... a paperweight...

Anyway, thanks. I'm not sure how to mount a partition from the partition editor. When GParted starts up, it shows "mountpoint" as one of the columns, but once it finishes scanning my hard drive and displays the data, that column goes away. Shoot, I really thought that would work... (I've exhausted the menu options, as well... the most I can do, it seems, is assign a "boot" tag to one partition or another. By default, and as it is currently, the NTFS partition is "boot.")

I've verified the CD, and it's 100% good. Also, please remember... when I select "edit the partition table" from the Install program, it will attempt to load GParted and then freeze. The only time I've had a choice other than erasing my hard disk or opening the partition editor is when I was able to choose "use the largest continuous free space" (I think because the swap partition was then unallocated), which worked at first but soon caused the installer to complain that I have no root filesystem.

So, as of right now, I can only edit the partition table before the installation process, not during. I hoped that activating the swap partition would help, but it hasn't.

(Oh, there is an "unmount" option for each partition on GParted, but it's disabled for each partition except for the swap partition, where it is listed as "swapoff." So, I suppose they're "mounted," but I don't know where to... or how Ye Olde Linux would view them by default.)

---

### Post by codesplice on 2007-03-26
Hmmm, that is strange.  I'll see if I can come up with any other things to try.

---

### Post by Cherry Cotton on 2007-03-31
Hey, I should let you know: I burned the Feisty Fawn beta, and it installs like a dream! It's got a much improved installer that really helps especially for migrating from Windows. It's great.

But... now I have a new problem! My wireless card doesn't work. It's got that funky "Texas Instruments ACX 111" chipset. Arrr! I started [a thread for that]("http://www.ubuntuforums.org/showthread.php?t=397563") here in the networking forum.

Thanks for your help! I'm glad I've got Ubuntu running, it's a great system even offline.

---

