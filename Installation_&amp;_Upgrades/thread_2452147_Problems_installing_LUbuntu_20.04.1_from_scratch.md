---
title: "Problems installing LUbuntu 20.04.1 from scratch"
date: 2020-10-17
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2020-10-17
Wanted to install on GPT disk.  Was told to create a FAT32 partition /boot/efi with boot and ESP flags set.  The installer gave me no way to set the ESP flag.

KDE partition manager would not do that either.  I had to install GParted to set that ESP flag.

---

### Post by GhX6GZMB on 2020-10-17
A few tips (the Lubuntu installer is quite easy, actually).

Do a correct language and keyboard layout selection already when doing the live boot. This makes things easier. You'll need to select language, keyboard and locale again during the real installation.

The Lubuntu live boot selection is not called "Try Ubuntu", but "Start Lubuntu".

Think about your disk partitioning. It's MUCH easier to define this during installation than later. And select "Format" for all partitions if it's a completely new install.

Otherwise it's easy. With an HDD it'll take about an hour, with an SSD 30 min. (DVD media, faster with USB).

Cheers.

---

### Post by grahammechanical on 2020-10-17
This issue has been noted before. This post dating from early on in the year might help

[https://ubuntuforums.org/showthread.php?t=2442269](https://ubuntuforums.org/showthread.php?t=2442269)

The Lubuntu installation guide does indeed say 

> f you are booting your computer in UEFI mode a more modern firmware  compared to BIOS you will need to create an EFI system partition (see [efi system partition Wikipedia]("https://en.wikipedia.org/wiki/EFI_System_partition")  for more detail). To create this partition you will need a FAT32  file-system with the ESP flag to be mounted at /boot/efi/ under the  mount point. You will also need a root (/) file-system, several  file-systems included for Lubuntu are Ext4, XFS, and Btrfs.

But it seems that when it comes to flags the list in the partitioner does not include ESP. I cannot prove that for sure

Regards

---

### Post by dragonfly41 on 2020-10-17
You can set ESP partition boot flags through Gparted which I use from LiveUSB.

---

### Post by GhX6GZMB on 2020-10-17
There's really no need for all this when installing Lubuntu 20.04 from scratch. The installer will do it all for you. Just live boot and start the installer.

After selecting language, location and keyboard, the installer will take you to disk partitioning.

Select "Manual partitioning".

After that, select "New partition table". There you can select MBR or GPT.

The rest is self-explanatory. And if you've planned your partitions beforehand really simple. Add your partitions, select the mount points and tick the Format box for each of them.

There's absolutely no need to muck around with gparted or other such stuff or creating GPT partitions first. The installer will fix it.

It's easy. Really easy.

---

### Post by David_Partridge on 2020-10-17
No actually that's the whole point of my post -there was NO WAY TO SET THE FLAG

---

### Post by GhX6GZMB on 2020-10-17
> **David_Partridge said:**
> No actually that's the whole point of my post -there was NO WAY TO SET THE FLAG

You'll find that the installer does that kind of thing for you. It seems to me you're mixing a cocktail of Lubuntu installer, CLI commands and what do I know for no reason at all.
Just do the install. Period.

I cannot reproduce your problem. And just WHO told you to "[COLOR=#000000]create a FAT32 partition /boot/efi with boot and ESP flags set[/COLOR]?" Selecting /boot as mount point should be enough for that partition. Calamares (the installer) doesn't care about the rest. And at no time during the installation does this issue pop up.

Perhaps you should just install "as is" instead of adding dubious advice into the equation? It really IS very simple.

---

### Post by David_Partridge on 2020-10-17
The installer told me to do that when i just created a btrfs partition - it told me I needed to create a FAT32 to be mounted at /boot/efi and that the ESP flag needed to be set.   When I just created a FAT32 and told it to mount at /boot/efi as instructed, the installer COMPLAINED the ESP flag wasn't set.

---

### Post by guiverc on 2020-10-18
I'll provide a link to an answer I've given on askubuntu

[https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may/1276789#1276789](https://askubuntu.com/questions/1273421/lubuntu-installer-giving-error-after-partition-creation-your-system-may-or-may/1276789#1276789)

It just follows an QA-test install I wanted to do (*groovy*) and what I normally do (*with manual partitioning*).  The question was about a *focal* or 20.04 install, but it's identical.

Also FYI:  I've got that message today (*twice I think; more groovy installs*), but install worked regardless of warning, as some boxes (*firmware*) have different levels of what is required (*the warning applies generally to more modern boxes, it can be ignored on some older boxes*). Following what I describe in the ask ubuntu question resolves it (*answered that way as I find it easy to remember; adjust for your circumstance*s)

---

### Post by GhX6GZMB on 2020-10-19
First, my apologies to @David_Partridge for implying that he's doing something wrong and mixing things up. Sorry.

It seems that the Lubuntu 20.04.1 .ISO has problems compared to the original Lubuntu 20.04 .ISO which I'm using. The original 20.04 installs without problems any time.

The 20.04.1 is called a "convenience update" which includes updates after 20.04, but apparently someone's been mucking around with other things, including the installer.

My recommendation: use the 20.04 .ISO, not the 20.04.1 .ISO and do the upgrades afterwards. Works every time.

---

### Post by David_Partridge on 2020-10-19
Apology accepted!  Good of you to put things straight.  Thank you

David

---

### Post by GhX6GZMB on 2020-10-19
Thanks.
The original (working) 20.04 .ISO is here:
[https://cdimage.ubuntu.com/lubuntu/releases/20.04/release/](https://cdimage.ubuntu.com/lubuntu/releases/20.04/release/)

Cheers.

---

