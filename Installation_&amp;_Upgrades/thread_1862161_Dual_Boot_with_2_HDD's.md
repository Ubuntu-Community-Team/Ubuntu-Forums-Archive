---
title: "Dual Boot with 2 HDD's"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by time4e on 2011-10-16
[CENTER]I want to create a dual boot install using two HDDs. My windows Vista install is on a single 2TB hdd and is currently up and running. I would like to add a 1TB HDD for a deducted Ubuntu 11.10 install. I attempted this last night and it was a complete failure more than likely a circumstance of user error.
   I thought I configured the install to use the 1TB HDD and that I wanted the boot loader configured for the 2TB (I first selected the 1TB for the bootloader but this failed and allowed me to use the 2TB drive) Long story short I wiped my win vista drive (2tb) and was not even able to boot into either OS [FONT=Wingdings][FONT=Wingdings]:([/FONT][/FONT]. Luckily I create a windows complete backup before hand and win vista is currently restoring. Perhaps the problem arouse from creating the swap partition (again I thought I set the swap up on the 1tb HDD. 
  After the restore is complete I will boldly attempt the same configuration again. If anyone could provide any insight, advise, and links to walkthroughs I would greatly appreciate it. 

Ps it may also be note worthy to add that the 1TB drive in question was used in another system and formatted for NTFS.  Both hard drive's have passed qtech bench mark tests.
   
  Thanks,
   
  -Tim[/CENTER]

---

### Post by time4e on 2012-02-25
Ha, I guess this question was so lame it was not worth any ones time to reply. So yea I guess I could have done a little more reading online before posting. But incase this ever happens to one of you ubununt nubs out there here is what I did.

-I removed the Windows Vista hard drive and only left the hard drive intended for the Ubuntu install.

-After the install I put my Windows Vista hard drive back, and set my bios to boot to the Ubuntu drive. 

-edited grub using grubconf 

-the system is now bootable.

Thanks,
-Tim

---

### Post by Zimmer on 2012-02-25
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

[https://help.ubuntu.com/community/DualBoot/WindowsFirst](https://help.ubuntu.com/community/DualBoot/WindowsFirst)

[https://help.ubuntu.com/community/TitleIndex](https://help.ubuntu.com/community/TitleIndex)

Sorry your post got missed, but I guess you were keen enough to dual boot you are not too worried about it now.

The one thing I found about the Ubuntu distribution was the wealth of documentation...
The friendly community and user base has grown considerably since I joined in 2005..
The geek-experienced user/novice ratio is probably a lot different to then, so theres more chance of a missed post, I guess...

Regards
Zimmer

---

