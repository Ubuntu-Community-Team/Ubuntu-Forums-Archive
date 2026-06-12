---
title: "boot multiple OS's"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Sasquatch2000 on 2006-06-26
I have an XP installation on a SATA drive which works fine. 

I also installed on a regular IDE ATA drive the 606 Ubuntu which also works OK.

Is there any way I can have both drives running at the same time, and be able to choose which to boot off of when starting up? 

Second, is there a way I can share files between the two? 

Thanks.

---

### Post by kb3hkg on 2006-06-26
to choose which to boot off of you can use a boot manager libe grub or lilo, or a hardware option where you push a button and it selects the drive to boot from for you. I recommend the bootloader though.

To share files between the 2 I recommend making a fat32 partition on one of them.

As for both OS's running at sametime, it is rumored that the next line of intel chips will be able to do this but that is all I have heard.

---

### Post by bohboh on 2006-06-26
You mean have a menu that you see when you boot the machine which allows you to pick from either ubuntu or xp? If so then you need grub

---

### Post by Sasquatch2000 on 2006-06-26
I don't mean both OS's running at same time, but both drives (to share data).

Yes, I want something which lets me choose which OS at startup. This should be software, not hardware related. I saw someone with Mandrake (I think) who had this. Also, I rember a commercial application which did this years and years ago (1997?). I see "grub" when Xubuntu starts up now. How do I add another OS?

---

### Post by kb3hkg on 2006-06-26
depends on the OS, if it is windows it must be installed first because Microsoft's bootloader kindly overwrites grub

---

### Post by bohboh on 2006-06-26
This refers to restoring grub, but it may help in setting it up also:

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing)

---

### Post by confused57 on 2006-06-26
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I'm assuming you installed Ubuntu to the IDE drive possibly with the SATA drive disconnected and grub is installed on the Ubuntu drive.  You may be able to set your bios to boot the IDE drive 1st, then go into your menu.lst in Ubuntu and add the Windows boot entry(with the mapping commands) to enable selecting which OS you want to boot at startup.

---

### Post by Sasquatch2000 on 2006-07-07
> **confused57 said:**
> See this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I'm assuming you installed Ubuntu to the IDE drive possibly with the SATA drive disconnected and grub is installed on the Ubuntu drive.  You may be able to set your bios to boot the IDE drive 1st, then go into your menu.lst in Ubuntu and add the Windows boot entry(with the mapping commands) to enable selecting which OS you want to boot at startup.

Yes, I installed each one independently of the other and now want to join them.

I get the initial concept up to the menu.lst part. Where do I find that, and how do I tell it to also show Windows XP on the SATA drive?

---

### Post by Sasquatch2000 on 2006-08-15
Just passing this along:

[Boot Ubuntu using NTLDR](http://www.ubuntuforums.org/showthread.php?t=236846)

---

