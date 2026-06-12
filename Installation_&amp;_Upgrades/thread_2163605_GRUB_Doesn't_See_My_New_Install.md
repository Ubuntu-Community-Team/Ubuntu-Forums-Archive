---
title: "GRUB Doesn't See My New Install"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2013-07-19
My desktop has three hard drives.  One holds Xubuntu 13.04, which is my normal login on the desktop.  (I have Kubuntu on my laptop, but not here).  My second drive holds an older Ubuntu 10.04 installation, which I never use.  Recdently I decided to replace the older distro with Ubuntru 13.04.  I installed from scratch, reformatted the hard drive, and should have a fresh install.

Unfortunately, I ended up with two copies of GRUB, one on each HD, and the new one seems to be nonfunctional. (I thought that I had put the boot instructions on the existing grub in my first HD, but apparantly I didn't).
Now, when I boot up, my GRUB menu list Ubuntu on top, but it's done that ever since I put Xubuntu on there, and that's what it boots to.  It also still displays the old Ubuntu 10.04 option, but if I choose that, I end up with a message saying the operating system doesn't exist (which it shouldn't).  When I go into the BIOS's boot menu on start up, and change to the other hard drive, it somehow redirects me back to the first GRUB menu, and I'm back where I started.  

Is there anything I can do to GRUB itself to put the correct boot information on it?

eta:  Partly solved.  I figured out how to get to the correct Grub.  Now I need to find out how to make the GRUB on my boot drive see the OS on the other drive at startup.

---

### Post by dino99 on 2013-07-19
**** I ended up with two copies of GRUB, one on each HD, and the new one seems to be nonfunctional *****

that means : the old grub is the master (which upgrade the grub menu), and the new one is the slave. So run update-grub on the master, to get the change made on the other partition been upgraded.
Or set the grub only on the partition you expect to do upgrades (sudo dpkg-reconfigure grub-pc)

---

### Post by oldfred on 2013-07-19
I have multiple drives and keep the version of grub for that drive's install in the MBR of that drive. Or each drive can boot without any other drive, but each also has the grub boot entries for the other drives. But I have to change BIOS to boot from my other drives. My default boot drive is currently sdd.

If you do not have your grub on correct drive.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Sometimes it is difficult to know what is installed where, so I run either Boot-Repair of the bootinfoscript which also is in the first part of BootInfo report from Boot-Repair.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/")
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

