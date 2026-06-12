---
title: "Installed Ubuntu just fine, but messed up my Suse installation"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by ssalman on 2005-11-22
I’m having a strange problem, it could be my own doing, but still it is strange! :)
    
I had a dual boot with XP and Suse 10.0 for a while, and then wanted to try on Ubuntu and setup a triple boot: XP on hda2, Suse on hda6 and Ubuntu on hda7. So I got the CDs and intalled 5.10, all went well, until I rebooted to find out that my Grub have been replaced by Ubuntu’s version and that it is not showing Suse anymore, only Ubuntu and XP. “Well that’s a configuration file issue”, or at least I thought so! :rolleyes:. I tried to lookup my menu.lst, vmlinuz and initd files on the Suse’s partition \boot folder but it was empty, nothing, nada!!
    
So I thought I might have done something wrong in the installation process to erase the boot folder of the Suse partition, I can’t see how, but I’m a Linux newbie after all!
    
   So I did some Googling and Suse/Ubuntu forum searches, and found the following Grub commands:
    
   ```

   >find /vmlinuz
    
   (hd0,6)
    
   >find /sbin/init
    
   (hd0,5)
   (hd0,6)
   
```     
That told me that I’m missing my kernel files in the Suse \boot folder, so I booted into Ubuntu, and did a search over the entire hda6 drive for “vmlinuz*” and “menu.lst”, and found none!
    
   Okay, I know I have done something serious now :???:, I put in the Suse 10.0 DVD and did a repair session. It found that I’m messing my kernel files, the Grub package and some postfix package, so I reinstalled all three, tried the above steps one more time, got the same results again, so I go back into the DVD one more time, did the same repair actions, and to find that the grub package is still not installed, and when I try to install it, I get errors. Somehow I got the boot part of my Suse installation messed-up, although the rest of the folders are just fine, or seem to be that way (I have no way of checking)!!
    
 How would I fix this mess, and better yet, how would I prevent this from happening again, what could I have done during the installation process to mess up another’s partition boot folder??
    
   I would appreciate any help in getting back my Suse setup. Thanks.

---

### Post by aysiu on 2005-11-22
I've done triple-boots and quadruple boots with many Linux distros (I'm currently quadruple-booting Windows XP, Mepis, Ubuntu, and SuSE), and I've never encountered one distro messing with another distro's /boot folder.

This is strange.

It's normal to:

1. Accidentally wipe out the entire partition by picking the wrong partition to install the new distro to.
2. Replace the other distro's Lilo or Grub on the MBR

But it's not normal to have the other distro more or less intact except for the /boot folder.

Am I wrong in assuming that you're able to successfully mount the /dev/hda6 partition and see that the rest of the SuSE installation is intact *except* for the /boot folder (which is otherwise empty)?

---

### Post by ssalman on 2005-11-22
[quote=aysiu]
Am I wrong in assuming that you're able to successfully mount the /dev/hda6 partition and see that the rest of the SuSE installation is intact *except* for the /boot folder (which is otherwise empty)?[/quote] No you are right, Ubuntu automatically mounted hda6 and I could see all my files on the Suse partition, I have also checked hda6 using the Suse setup DVD repair utility &#8211; partition checkup utility, and there was nothing wrong with it!!

Could it be that the \boot folder was mounted to a different partition (I don&#8217;t remember the default settings for the Suse installer), and I have screwed it by repartitioning for Ubuntu (as I had assumed that Suse uses only hda6)?
    
Is there a way I can check if Suse uses a multiple partitions and if the \boot was actually mounted to a different partition or not??

---

### Post by wrtrdood on 2005-11-22
[QUOTE=ssalman]
Could it be that the \boot folder was mounted to a different partition (I don&#8217;t remember the default settings for the Suse installer), and I have screwed it by repartitioning for Ubuntu (as I had assumed that Suse uses only hda6)?
    
Is there a way I can check if Suse uses a multiple partitions and if the \boot was actually mounted to a different partition or not??[/QUOTE]

This would be my guess.  Check your existing partitions on the drive with **fdisk -l /dev/hda** and see if you can find a smaller partition that may include the boot files.  If you have not deleted it during the partitioning, it should still be there.

It could be as simple as adding the specific device for that partition to grub.  I've tried doing that before and had marginal success (gets really confusing).  If you do find a boot partition, you could copy the contents to a /boot directory on the Suse system drive and things will be a lot easier.  You'll have to tell grub where it is, though.

---

### Post by wrtrdood on 2005-11-22
[dup]

---

### Post by taurus on 2005-11-22
Just a quick note.  /boot is NOT the same as \boot!!!

---

### Post by ssalman on 2005-11-23
[quote=wrtrdood]This would be my guess.  Check your existing partitions on the drive with **fdisk -l /dev/hda** and see if you can find a smaller partition that may include the boot files. If you have not deleted it during the partitioning, it should still be there.

It could be as simple as adding the specific device for that partition to grub. I've tried doing that before and had marginal success (gets really confusing). If you do find a boot partition, you could copy the contents to a /boot directory on the Suse system drive and things will be a lot easier. You'll have to tell grub where it is, though.[/quote] 
  Okay I found the problem:D, it looks like when I created the new partition for Ubuntu using Yast, I somehow mounted the new partition to /boot, and when I installed Ubuntu, it replaced all the boot files and configurations. Stupid mistake on my side:oops:.
    
I found out this fact after I used the Suse DVD to repair my boot, and it didn’t work, I logged into Ubuntu to do other stuff, and found that all the Suse vmlinuz, initrd, and Grub files laying around on my Ubuntu partition root.
    
   I’m also now able to boot into Suse using the following commands in Grub command line:
    
   ```

   > root (hd0,5)
   > kernel (hd0,6)\vmlinuz
   > initrd (hd0,6)\initrd
   > boot
   
```     
     I hope this will be of some help to someone!!
 
   Thanks **wrtrdood,**** aysiu, and ****taurus** for helping out.

---

