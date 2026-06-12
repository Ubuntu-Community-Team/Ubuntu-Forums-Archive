---
title: "Dual booting on two drives without GRUB"
date: 2017-08-08
forum: Installation &amp; Upgrades
---

### Post by 81chevette on 2017-08-08
My computer has two OS drives plus a data drive. One drive houses Windows 10. The other drive is partitioned for my current Ubuntu version--currently Wily--plus another flavor for me to play with. I've determined, after much pain and heartache, that problems I have properly updating Windows 10 are related to GRUB2's redirect of the Windows bootloader. So I came up with a simple solution. I'd leave GRUB2 alone on my Linux drive, and then when Windows was struggling with an update I'd change my boot order in BIOS. (Actually BIOS; my mobo is too old to UEFI)
Well, much to my horror, I discovered GRUB does something that I don't entirely understand. My Windows drive has a redirect to GRUB2. One that even a "refresh" (where Windows allegedly reinstalls itself without installation media) didn't remove. So if I change my boot order I still end up booting with GRUB2, and if I unplug my Linux drive, I can't boot. 
So I have two questions. One, how do I fix this? I want the ability, when I feel like it, to boot to Windows without GRUB2 touching it. Two, how do I KEEP it fixed? How do I keep a future update-grub from replacing the redirect? I do want to use GRUB2 most of the time, I just want to have a workaround available for when Windows Update gets stupid on me.

---

### Post by ubfan1 on 2017-08-08
On you legacy system, you want the Windows bootloader on the Windows disk, and grub2 on the Ubuntu disk.  What you have now is grub2 on the Windows disk (This should be fixable with a Windows boot media and the fixmbr command).  On the Ubuntu disk, I cannot tell from your description what's on it.  If it can boot grub2 without the windows disk present, then grub2 is installed there, and the only thing to fix is the Windows disk, which is not an Ubuntu issue at all.  Install grub2 to the Ubuntu disk (assuming it is sdb in the following example) by
sudo grub-install /dev/sdb   Ensure you can boot that disk without the Windows disk present, and then fix the Windows bootloader -- maybe check the superuser.com site for Windows help.  What you want is pretty standard, but once the Windows bootloader is replaced with grub, you need to use Windows to replace its bootloader.

---

### Post by oldfred on 2017-08-08
In addition to ubfan1's suggestions, you may need to check on where grub reinstalls on a major update. It saves that data and uses drive info to reinstall. Or it  may reinstall to the Windows drive. You want it only reinstalling to Ubuntu drive, and keep the Windows boot loader always on the Windows drive.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 

   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

