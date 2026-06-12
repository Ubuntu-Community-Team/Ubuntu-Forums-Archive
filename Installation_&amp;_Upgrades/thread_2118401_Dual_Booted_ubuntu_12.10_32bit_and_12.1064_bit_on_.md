---
title: "Dual Booted ubuntu 12.10 32bit and 12.1064 bit on External HDD but Can't See options"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by wangolo on 2013-02-21
Hi there recently i followed a tutorial on how to install ubuntu on external drive which used 11.4, but it worked for me on 12.10, It was working pretty fine, but I tried to Dual Boot it on my sumsang external drive with ubuntu 12.10 x64 the installation was fine and smooth. But The choice of choosing the OS to use only appears on the Computer which I installed but if I move to other computers, the Choose option does not appear. I really have no idea why it works fine on the computer i Dual booted from, but not the computer i didn't.

 The main problem is I can't see the Option of Choosing which Ubuntu to use yet I installed both ubuntu 12.10 32 and ubuntu 12.10 x64 on my External Drive. Only the 32 one appears

 Why does the Option appear only on the Computer which I Dual Booted them on my External Drive

---

### Post by oldfred on 2013-02-22
Welcome to the forums.

Did you install grub to the MBR of the external drive and are you booting from it with BIOS or one time boot key (f12 on my system)?

If not you can install grub to external.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    
If you have two installs on external, you have to decide which is in charge. One one can be in MBR. And you may have to boot into both installs and run 
sudo update-grub

You may want to simplify boot updates as each time there is a kernel or grub update you have to boot & update both installs.

         How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Entries like this boot a partition not the specific kernel. Ubuntu puts links to the most current kernel in / and you boot the link in the partition (sda5 in example).

> [B]menuentry "Precise Pangolin 12.04" { 
    set root=(hd0,5) 
        linux /vmlinuz root=/dev/sda5 ro quiet splash         
initrd /initrd.img 
}[/B]

---

