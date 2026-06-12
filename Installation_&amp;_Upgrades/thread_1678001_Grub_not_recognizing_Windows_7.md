---
title: "Grub not recognizing Windows 7"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by dlucci on 2011-01-29
Background:  I dual boot  Ubuntu 10.10 and Windows 7.  I use an HP laptop. 

So here's the deal.  My Windows 7 partition got a virus a few weeks  back.  So, I removed the partition and replaced that partition with a  squeaky clean version of Windows 7.  Then, since Windows had installed, I  could not get grub to work.  So I booted up my disk and installed a  third partition, which was a second Ubuntu partition, which I plan on  deleting.  I did this so I could get grub back.  Now I have grub back  but no Windows.  I can mount Windows from both partitions.  Then, I  modified the /boot/grub/grub.cfg file to add windows.  It showed up in  grub but when I booted into it, it says "bootmgr not found."  I also did an update on grub and that didn't work.  I want to  be able to boot into that windows partition.
  Let me know if you need any more information.
  Cheers

---

### Post by oldfred on 2011-01-29
You should have just needed to reinstall grub to boot the existing install. If you remove the new install the grub in the MBR will still be looking for that partition to boot from. If you can boot into the install you want to keep, then reinstall grub2 to the MBR with this:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If the sudo update-grub still has not found windows:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

