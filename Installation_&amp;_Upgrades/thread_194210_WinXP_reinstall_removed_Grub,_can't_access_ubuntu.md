---
title: "WinXP reinstall removed Grub, can't access ubuntu"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Sharkee on 2006-06-11
Thanks for supporting all of us newbies.

I have a laptop w/ a single hard drive, and had winXP home installed on it.  I put Ubuntu on and loved it.  Then I decided to re-install windows to make more room for ubuntu, but when I re-installed windows, it over-wrote my GRUB.

Now Windows has control of the MBR.  I've tried 
[LIST]
[*]using the menu from Parition Magic (Boot Magic) and pointed it to my Linux extended partition- refused to boot ubuntu
[*]using BOOTPART.exe to make UBUNTU.BIN for use in my windows's BOOT.INI (MBR)
[*]using boot CD's to boot from ubuntu's partition
[*]running "grub-install" off Ubuntu 6.06 Desktop's boot cd - it could not mount any of my hard drive's partitions.
[/LIST]

None of those things worked.  I'm assuming because no scraps of GRUB were left on the actual ubuntu partition?

Things I have at my disposal:
[LIST]
[*]Ubuntu 6.06 Desktop live/install cd
[*]1 GB Flash drive
[*]"Multiboot UtilsCD v3" including Hiren's
[*]Windows XP Home is running fine (including having Partition/Boot Magic 8)
[*]an Acronis backup of my windows partition (the way I like it) on a DVD
[*]YTMND's of MacGuyver fixing things with fewer items
[/LIST]

Any help would be greatly appreciated.  I got my Ubuntu (and Kubuntu) installed with all the stuff I wanted on it and it was fantastic, please help me get it back and away from stupid friggin Microsoft Windows.

Here is what Partition Magic 8 reports for my single hard drive:
WinXP(C:)        FAT32          ACTIVE      PRIMARY
SHARED           FAT32          HIDDEN**    PRIMARY
LOCAL DISK      Linux Ext3     NONE         PRIMARY
(*)                 Extended      NONE          PRIMARY
SWAPSPACE2(*) Linux Swap   NONE        LOGICAL

**= I intend on making this "Shared" partition visible.  I want both OS'es to be able to read/write to it.

---

### Post by linuchsan on 2006-06-11
Start from de cd  in rescue mode
After some questions you can choose for  &#8220;reinstall grub boot loader&#8221;
Follow the instructions.

---

### Post by Sharkee on 2006-06-11
yeah, a guy on Qunu helped me find this page (same solution)

[http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access]("http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access")

In case anyone hadn't heard of it, Qunu is a FREE personal real-time help system.
Qunu.com

---

