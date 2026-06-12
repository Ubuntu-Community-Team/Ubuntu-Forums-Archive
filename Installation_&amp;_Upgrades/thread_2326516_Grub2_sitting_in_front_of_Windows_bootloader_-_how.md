---
title: "Grub2 sitting in front of Windows bootloader - how do I change this?"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by jub2 on 2016-06-01
A while back, I had set up a dual boot of Windows 7 and Linux Mint off the same physical disk. The Windows partition was Truecrypt encrypted and is the first partition on the disk. Next is a small boot partition I had intended for Grub2 so that it could load Mint. Next were / and /home partitions for Mint.

I never got this setup working quite right and could only get into Windows, which was fine at the time since I wasn't using the Mint install anyway. I'm making some changes to the system and wish to clean up this dual boot setup. I decrypted the Windows partition, and after rebooting was surprised to discover that the Grub menu comes before the Windows bootloader (while it was Truecrypt encrypted, the TC loader came first, and if I entered the correct password, the Windows loader came next). Now that the first partition is decrypted, I see Grub first, then Windows loader (if I choose Windows from the Grub menu).

How can I get rid of the Grub menu so that only the Windows loader sits in the MBR? I'd like to do this while preserving the Windows installation. I don't mind if the solution nukes the Mint installation, since I'm going to replace it with Xubuntu.

---

### Post by yancek on 2016-06-01
If this is a standard windows 7 MBR install, the first step would be to reinstall windows code to the MBR.  The link to windows 7 forums below explains the process.  You will need the windows installation DVD or Repair disk.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Mark Phelps on 2016-06-02
If you don't have a Win7 installation DVD, you can purchase the ISO file of a Win7 Repair CD from this link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Good Luck

---

### Post by jub2 on 2016-06-02
Thanks, I used a Win 7 disc  to repair the MBR, so no more Grub loader.  :)

---

