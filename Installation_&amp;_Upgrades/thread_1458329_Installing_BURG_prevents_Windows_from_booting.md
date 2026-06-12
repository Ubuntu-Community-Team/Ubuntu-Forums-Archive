---
title: "Installing BURG prevents Windows from booting"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by INH on 2010-04-19
I'm posting this here because I couldn't figure out where else to post it.  Sorry if it's out of place!

Ubuntu Lucid 10.04 Beta 2 64-bit
Dual-boot with Windows 7 Professional 64-bit
Compaq CQ50-215NR laptop with 3GB system memory, 1.9GHz Athlon X2 QL-60 dual-core processor, nVIDIA GeForce 8200M G, 160GB HDD

Today I decided to install the BURG bootmenu on my computer so that I could enjoy nice, pretty graphical bootmenus instead of boring old text-based ones.  I installed and configured BURG using [this](http://nourlinux.wordpress.com/2010/04/06/get-animated-themed-icon-only-grub-menu-using-burg/) tutorial (after some few snafus wherein I tried to use older tutorials and went through many needless complicated steps that didn't end up working anyway).  Restarted, and it worked great - except for one thing.  Windows would no longer boot.  It would get to the "Starting Windows" screen, then about halfway through there it would flash and restart.  It wouldn't start in "Startup Repair Mode" either (the same thing happened).  So, I did some frantic googling, and discovered [this](http://ubuntuforums.org/archive/index.php/t-1393848.html) thread.  I followed a set of instructions posted therein to install Lilo, reconfigure my MBR to Windows' liking, and reinstall Grub2.  Windows booted after that.  Well, I thought that the problem must have been caused by one of the numerous false starts I made while trying to get BURG installed, so I installed BURG again, set it up again, and bang - Windows wouldn't boot any more.  So, I re-did the MBR with Lilo again, only this time I forgot to reinstall Grub2 (oops!) and had to boot from my LiveCD and install it thataway.  

At any rate, I'm fairly certain that installing BURG is what's keeping Windows from booting.  Does anybody know why this would be happening and/or have a workaround for it?

---

### Post by INH on 2010-04-20
(bump)

Anybody?

---

### Post by Mark Phelps on 2010-04-21
I think you would do better going to the BURG unixmen website and asking the question on their forum.

---

### Post by INH on 2010-04-22
OK, thanks.

---

### Post by bean123 on 2010-04-24
Yeah, I have seen similar reports before. I believe the reason for is that GRUB2/BURG writes multiple sectors to MBR, which conflicts with system data on some machine. Fortunately, BURG has an alternative install mode with only install one sector, this should be able to solve this problem.

To use it, add --alt option in burg-install, for example:

```

burg-install --alt /dev/sda

```

If it still doesn't work, you can post it to the BURG forum at:

[http://www.burgloader.com/bbs/](http://www.burgloader.com/bbs/)

---

### Post by inoh on 2010-05-14
I had the same problem with grub/grub2 and Compaq cq60-215dx.  Turns out  HP uses proprietary software which prevents any changes to the MBR.   This corrupts the MBR to protect the system from unauthorized changes.   After a month of frustration I found out the solution was to delete all  HP software which isn't a big deal for me since I only use Vista for  itunes to update my iphone.  Final solution for me was to wipe  everything clean, install Vista and update everything, install Ubuntu,  boot Vista to ensure everything is updated and remove all HP software.   Worked great since.

Hope this helps.

---

