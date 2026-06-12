---
title: "installation and partitioning scheme suggestions"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by Denis on 2005-08-07
Hi, I have decided to install Ubuntu on my new computer when it arrives. I've already tried Mandrake and Gentoo before, but it was never my main operating system. I think Ubuntu will be more suited for me. I've looked though a lot of info concerning Ubuntu Linux. I would like to hear your suggestions on the installation.

I've got the following physical harddisks: 
-Maxtor 250GB  16MB 7200rpm
-Maxtor 160GB 8MB 7200rpm

and this is the partitioning table I figured out: 

```

hda1   *      3GB        NTFS
hda2          80GB      fat32
hda3                        extended
  hda5 *     32MB      ext2 /boot
  hda6         2GB       linux swap
  hda7       165GB     ext3

hdb1         160GB     reiserfs

```

The system would be a dualboot with Windows on the NTFS partition and the fat32 partition would be used to share files. I'm not sure whether fat32 can handle such a large partion or not. 

When I decided the structure I want to use, what would be the best way to apply it? 
I think I will make the ntfs and fat32 partition first (with an Ubuntu of Gentoo cd?) and install Windows XP. 
Will I be able to partition the rest of the disk space the way I want it with the Ubuntu installer? And how can I do that?


That will be all for the moment, thanks for your help.

---

### Post by edwina on 2005-08-07
Hello. I'm pretty new to this, but perhaps I can be of some help ...

If you install XP first, you can use the installer to set up your partitions in their unformatted state. The Ubuntu installer can then format them as you want (fat32, reiserfs etc.), set up the root partition and add the appropriate boot flag and boot loader. If either of your HDDs are SATA, then you may have to set them to "enhanced" mode in the BIOS in order to get Ubuntu to recognise them.

I have a feeling that a swap partition is likely to be unnecessary if you have, say 1Gb of RAM. Mind you, there is clearly plenty of space on your disks, so it can't hurt!

Does any of that help? Ask again, if you need a bit more information.

---

### Post by Denis on 2005-08-08
Thanks, that did help me. 

I'm going to use fdisk, from a live cd, to set up all my (unformatted) partitions, since that's more conveniant for me than the windows installer. 

And afterwards I'll use the Ubuntu installer to format these partitions, as you said.

You may be right about the swap partition, I am indeed going to have 1GB RAM. But hey, some application may need 2GB of memory in the future... :)


Can anyone inform me about that 80GB fat32 partition. Can fat32 handle that?

---

### Post by buster on 2005-08-08
Since you have so much space, I wouldn't stint on hda1 for XP. You may start installing stuff in XP that someone in the family needs, and also want to keep your fat32 as strictly data. 10 gig for XP wont hurt you much, and means you can always opt for the default install of software in Windows.

I am NOT encouraging you to use XP by the way, just speaking from experience.

---

