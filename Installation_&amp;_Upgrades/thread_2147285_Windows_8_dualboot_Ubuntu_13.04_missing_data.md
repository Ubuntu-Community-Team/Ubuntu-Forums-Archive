---
title: "Windows 8 dualboot Ubuntu 13.04 missing data"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by dankojoffrey on 2013-05-21
Hi, I installed ubuntu 13.04 alongside preinstalled Windows 8. I disabled fastboot and secure boot in bios and fastboot in windows. I set /etc/fstab to automount my D:\ drive. After I start ubuntu and use ntfs partition and then I reboot to Windows some files are missing, but disk space is being used. Other time I cannot write anything to D:\ drive. Only solution is that I have to run chkdsk, which repairs drive and files reappear.

Any ideas what could be causing it?

Thanks...

---

### Post by oldfred on 2013-05-21
It sounds like Windows is still in hibernation and then the Linux NTFS driver will not mount a NTFS partition with either a hibernation flag or chkdsk needed flag set.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by dankojoffrey on 2013-05-21
actually I have disabled fast boot and hybernation right after I installed ubuntu... still interesting thing is few days ago, almost 150 GB of data (mostly movies) disappeared, but the space on HDD was still occupied and after I ran chkdsk all the files suddenly appeared...

update: Files that I copy to NTFS in Ubuntu after chkdsc appears to be 0 B size.

---

