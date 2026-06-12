---
title: "latest upgrade ruins my Fedora bootloader and Ubuntu does not start"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by valugi2 on 2013-10-28
I did some Ubuntu updates on my laptop that had also Fedora and now Ubuntu starts directly bypassing the bootloader. Fedora was my primary system and the bootloader was from them.
So Ubuntu tries to start automatically, but the screen turns black and it halts. I have a Lenovo ideapad with UEFI, but UEFI is disabled.

Please give me some recommendations to recover my OSs.

---

### Post by ajgreeny on 2013-10-28
If you originally installed fedora by the default method you may have it using LVM, which I do not understand other than knowing that without a fair bit of fiddling and adding lvm packages, Ubuntu will not be able to detect it nor put it in the grub menu.  You may do better at the fedora forum getting info on restoring grub from that OS, then you may be able to boot to that at the very least.

Without more info it is impossible to know why your Ubuntu boots to a black screen.

What hardware do you have and what version of ubuntu is it?

---

### Post by oldfred on 2013-10-28
Grub2 saves the default drive install info. So on major updates it may reinstall to the MBR. So even if later you put another boot loader in the MBR, then grub from first install my get reinstalled. (As you found out). 
One advantage of UEFI is all boot loaders exist side by side in efi partition and you control default boot from UEFI menu. Some may still change which is default but then it is easy to change back,

If a black screen often a video issue. What video card/chip? Often nomodeset is a solution, but some need different settings.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

In Ubuntu you need to add the lvm2 driver and mount the Fedora partition. Then grub2's os-prober will find your Fedora install. Often those mulitple booting install Fedora in a standard ext4 partition rather than the default LVM. LVM;s advantage is more when it controls an entire hard drive.

 sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub 

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
If you unchoose everything then it should not reinstall to any drive or partition. Recheck with above debconf-show command.

---

