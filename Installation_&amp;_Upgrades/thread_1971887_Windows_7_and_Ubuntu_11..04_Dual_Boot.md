---
title: "Windows 7 and Ubuntu 11..04 Dual Boot"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by brianpb245 on 2012-05-03
for those that havent used windows 8 its the same thing so if you have instructions for windows 7, i can use it thanks!

I currently have Ubuntu dual booted with my windows 8, and was currently upgrading to 12.04 and my laptop went on standby and now it is corrupted, I thought when I dual booted it it was two separate partitions so when i went to the partitions manager, its only my main harddrive C: and thats it..... so im guessing my ubuntu is installed inside it along with my windows?

Question is how do I get rid of this corrupted ubuntu so i can reinstall it since it isn't its own partition.

---

### Post by jualin on 2012-05-03
If you have access to a Live CD/Usb you can boot into it and start "gparted" to see all of the partitions since from a standard Windows installation you cannot see the Linux partitions (ext3/ext4). 
Using the gparted you can then reinstall Ubuntu. 
Hope this helps!

---

### Post by darkod on 2012-05-03
Boot with a 12.04 cd in live mode first, see if it works correctly.

Then in terminal you can take a look at partitions with:
sudo fdisk -l (small L)

Post the result here if you need help. The ubuntu partition(s) might have been made unreadable depending how the upgrade failed, so it still doesn't mean you had wubi inside windows (by the way you should know these things :) ).

If the ntfs partition takes the whole disk then you probably have wubi inside windows. If it's not, there is the chance you have (had) ubuntu partitions and proper dual boot.

---

### Post by brianpb245 on 2012-05-03
i looked at both gparted and the terminal command but I still cannot find the partition for the ubuntu to delete 
this is what i get 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625139711   312466432    7  HPFS/NTFS/exFAT

On boot menu , I see my windows and the Ubuntu but when I click on it it doesnt work

---

### Post by darkod on 2012-05-03
> **brianpb245 said:**
> i looked at both gparted and the terminal command but I still cannot find the partition for the ubuntu to delete 
this is what i get 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625139711   312466432    7  HPFS/NTFS/exFAT

On boot menu , I see my windows and the Ubuntu but when I click on it it doesnt work

You should have posted the full results so we can see the total number of sectors. That way you know if /dev/sda2 takes the whole hdd to the end or there are other partitions after it that might be temporarily missing.

But so far, it looks like wubi inside windows. And in lots of cases an upgrade would break wubi, that's one of the main reasons not to use it.

Wubi is not a long term install to use, update, upgrade, etc. It was designed only as a quick try.

You want a long term system, install a proper dual boot.

---

### Post by jualin on 2012-05-03
> **brianpb245 said:**
> i looked at both gparted and the terminal command but I still cannot find the partition for the ubuntu to delete 
this is what i get 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625139711   312466432    7  HPFS/NTFS/exFAT

On boot menu , I see my windows and the Ubuntu but when I click on it it doesnt work

You should post the entire results but I agree, it sounds like you used the Wubi installer You can check if you are using the Windows boot manager which should like this: [IMG]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=boot-screen.jpg[/IMG]

If that's how it looks then you used [[COLOR="Red"]Wubi[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1"), you should be able to uninstall it by going to your Windows Control Panel (where you usually uninstall programs).

---

