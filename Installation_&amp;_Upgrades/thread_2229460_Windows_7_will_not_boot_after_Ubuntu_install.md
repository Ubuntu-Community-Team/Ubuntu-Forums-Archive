---
title: "Windows 7 will not boot after Ubuntu install"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by cheid001 on 2014-06-13
My laptop came with a small SSD just for booting windows, I think... I say this because I have just finished a Ubuntu install on the machine and now I can not boot back into windows.  Grub tells me that I can boot into windows recovery by booting from partition /dev/sda1, which works.  However, it wants me to boot windows 7 itself from /dev/sda2, which produces nothing but a black screen.  The partition sda2 is a small 105MB partition, I don't know what is on there.  The small SSD drive, which I think has all the windows stuff on it is located at /dev/sdb2 and is a 16GB partition.

Does anyone have any experience with this and willing to help me?

Its not that I can not work in a Linux environment, its just, I had a lot of nice productivity software in windows that made it easier to work in the Linux environments I routinely SSH into (Notepad++ and WinSCP especially).

---

### Post by Mark Phelps on 2014-06-13
It's likely that the SSD is just being used as a cache -- it's really too small for anything else. The 105MB partition was used to hold the Windows boot loader files.  IF you've messed those up with partitioning and installs, Windows won't boot anymore.

I would ordinarily recommend that you download the ISO image for the Win7 Repair CD, burn a CD from it, boot from it and run Startup Repair -- but if yours really is one of these "hybrid SSD/HDD systems", I don't think that will work.

If you're interested anyway, check out the link:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by yancek on 2014-06-13
Windows 7 OEM installations usually had a small boot partition which is probably what your sda2 is.  You say your recovery is on sda1, do you have any other ntfs partitions on the drive with the system files?  I would suggest running:  sudo os-prober and watch the output.  See if another windows is detected.  If so, run;  sudo update-grub.

---

