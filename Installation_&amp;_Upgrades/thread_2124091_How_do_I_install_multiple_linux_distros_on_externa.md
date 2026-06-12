---
title: "How do I install multiple linux distros on external usb hd"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by redmon on 2013-03-09
I have XP installed on an T42 laptop and xubuntu installed on an external usb hd partition.  Grub for xubuntu is installed on the xubuntu partition.  To boot xp, I start the computer and it boots xp through the regular windows process.  To boot xubuntu, I start the computer, go into the boot device menu, select the external usb hd, and select xubuntu in the grub menu on the usb hd.  I would like to install another (or maybe more) linux distro on the usb hd, but want to keep the boot process the same.  When I tried to do this, I selected the usb hd in the boot device menu, but grub on the usb hd only displayed xubuntu and xp, not the second linux distro.  How can I do this?  Should grub for the second linux distro be installed on the first distro partition?  How do I change the order of distros on the grub list?

---

### Post by ibjsb4 on 2013-03-09
I have six HDDs in one box and multiple ubuntu installs.  How to keep form borking grub can become a challenge.  And I still manage to get it screwed up from time to time, for me its just a pain in the ..  So Im not going to try to tell you how to do it, but will give you some links to study up on.

  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+grub2&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+grub2&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+do+I+install+multiple+linux+distros+on+external+usb+hd+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=How+do+I+install+multiple+linux+distros+on+external+usb+hd+&sa=Search&cof=FORID:9)

I have found for me that the best way to test out different distros is with a virtual machine.  This has limitations, but depending on your computer specs, it can be quite advantageous.  No grub to deal with, easy to repair, easy to install, no CD/DVDs to burn, just makes things easier.  There is a learning curve, but I think its worth it.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

And theres a sub-forum here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=virtualbox&sa=Search&cof=FORID:9)

---

### Post by redmon on 2013-03-13
Thanks for your reply, ibjsb4.

  I read through several links and realize that what I want to do may be beyond my ability, or at least beyond what I want to try at the risk of really screwing up what I already have.  I apologize if I am not using some terms correctly.  To review my current configuration, I have XP on a laptop and xubuntu on an external usb hd.  If I simply turn on the laptop and do nothing else, it goes straight into XP.  If I turn on the laptop and go into the boot device menu, select the usb hd, I get a menu that allows me to select either xubuntu or XP.

  Let's say I have two partitions on the usb hd, sdb1 with xubuntu and sdb2 empty.  When I installed xubuntu, grub (I assume) was installed on sdb1.  Back to my original question, if I installed another linux distro on sdb2 and during installation put grub on sdb1, would the new distro be added to the menu with xubuntu and XP?  Nothing I have read indicates it would be that simple.  But if not, why does XP appear in the xubuntu grub menu?

---

### Post by oldfred on 2013-03-13
You have to use Something Else in Ubuntu or manual install so you get a choice of where to install the grub2 boot loader. If a second install you do not have to install its boot loader but it will want to as it assumes you need a boot loader. Any of the auto install options will install the boot loader to the MBR of sda which probably is the internal drive. Ubuntu does not offer an option to not install grub, but you can install it to the PBR or partition with the install and never use it.
Then in your main install run this and it will find all your other installed systems.
sudo update-grub

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If you have swap already, you do not need another one unless you hibernate. And Ubuntu finds it automatically. For another install you just want to test you only need a 10 to 25GB / (root) partition. But if you start multi-booting you will find you want some of the same data in all systems. When I still dual booted XP I created a NTFS shared data partition and put Firefox & Thunderbird profiles into the shared so all my systems have the same bookmarks & emails.

---

### Post by redmon on 2013-03-13
oldfred, you are making it appear as if it is as simple as I hoped it would be.

So using my hypothetical situation, on an external usb hd I have xubuntu with grub installed on sdb1.  From liveCD, I manual install second distro with grub on sdb2.  When installation is finished, I reboot and f12 into boot device menu, then select the usb hd.  What happens next?  Will I see the xubuntu boot menu or will the second distro boot?  If I get the xubuntu boot menu, then I boot into xubuntu and run sudo update-grub to add the second distro to the xubuntu boot menu?  What do I do if, after selecting usb hd, the second distro boots instead of xubuntu?

---

### Post by oldfred on 2013-03-13
If you use manual install you get the choice of where to install grub2's boot loader on the bottom of the partitioning & formatting screen.

But if the new install boots & has Xubuntu as a choice you can boot into Xubuntu and install its copy of grub to the MBR of the external. 

Assuming external is sdb
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But if Ubuntu based (or maybe Debian based) each copy of grub will remember where to reinstall on updates, so you may have issues if major grub updates cause it to be reinstalled to MBR. This may prevent that on second install.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And you can always use a liveCD or flash and reinstall grub2.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling)

Or use Boot-Repair
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by redmon on 2013-05-20
oldfred,

Thank you for all your help.  I have been busy with another project and, frankly, was concerned about destroying my customized xubuntu installation on the ext usb hd.  During manual installation of the second distro, I designated installing bootloader on sdb (no number after sdb).  It was that simple.  If I select ext usb hd from boot device menu (f12), the grub menu gives me a choice of xp, xubuntu, or crunchbang.  If I boot laptop without selecting boot device menu (f12), it boots directly into xp.  Just what I wanted.

---

### Post by oldfred on 2013-05-20
Glad you got it working the way you want. :)

---

