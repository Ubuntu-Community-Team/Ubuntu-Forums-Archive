---
title: "Grub intallation problem"
date: 2004-11-20
forum: Installation &amp; Upgrades
---

### Post by jozmak on 2004-11-20
Hi,

I have a dual boot XP, fedora 2  which runs great on hda. To day, i have decided to install Ubuntu on my second hard drive because i have heard good things about this distro. 
The installation went fine till Grub install came up, then i got a fatal error message; Grub cannot be installed in MBR; to start Ubuntu type root=/dev/hdb1. So I installed Ubuntu without boot loader. Now, how can i start ubuntu this is my question.
Any help would be appreciated. If you answer keep in mind that i am not a complete beginner but not an advanced Linux user either. 

Thanks a lot
jozmak

---

### Post by wazoo42 on 2004-11-21
When you do the install have it install grub on the /boot partition.  If you have the fedora/windoze hd boot first, is it using grub also?  If so, change it so that there is a section for ubuntu

title ubuntu
root (hd1,0)/grub   ***this is your /boot partition***
chainloader +1

---

### Post by jozmak on 2004-11-21
When i started the installer i chose the automatic partition option on hdb1, which was already formated ext3. Then the installer deleted that partition and repartitioned it automatically into / and swap and then I just went ahead with the installation. Then when it came to installing grub it asked me where i wanted to install it. I said MBR then i got the fatal error message, then i went ahead to install the rest without grub. This was the procedure in a nutshell. 
So, it is not clear how to install grub in a boot partition
On other forums, it was suggested to past the following command into Fedora's grub.conf file.
I did.

title           Ubuntu
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.8.1-2-386 root=/dev/hdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.8.1-2-386
savedefault
boot

Then i rebooted. Now, the ubuntu option shows on the list but when i click on it I get an Error 15 message. Then when i hit enter the screen goes back to the original start list.

jozmak

---

### Post by wazoo42 on 2004-11-21
Hmmmmmmmmmmm...So let me see if I understand.  XP and fedora are on hda, and they use grub.  Ubuntu setup could not load grub, and it made hdb1 / and hdb2 swap.  

If this is the case then my way surely would not work because it requires grub to be on the /boot partition (or any partition).  I should think that the answer you got elsewhere should work, though I have never seen the savedefault and boot options before (namely I have never used them).  You might try without those.  One thing that doesn't look quite right is the initrd.img-2.6.8.1-2-386, look in /boot to make sure this is correct, I am guessing it is initrd-2.6.8.1-2-386.img.  Just one more thought, do a ls -l in /boot.  Usually there are two soft links where vmlinuz points to the latest kernel and initrd.img points to the associated initrd file, this just makes life easier so you don't have to worry about the -2.6.etc .  Thus, you would be able to just use:

kernel /boot/vmlinuz root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img

Another option is to reinstall ubuntu and put grub on the / partition in the /boot directory.  Then my first way would probably work.

---

### Post by jozmak on 2004-11-21
Hi wazoo42

Thanks a lot for the grub installation advice. I reinstalled Ubuntu, as you said and installed grub in the same partition and the installation worked like magic. Now, i can boot into Ubuntu from Fedora's grub boot loader. The distro looks great and i still exploring gnome 2.8 which looks clean. But now, i have another problem. During the installation i wasn't asked to enter root password, now i am without it and i don’t have root privileges. I cannot modify fstab and the system doesn't let me  mount windows and other Linux partitions.  
My modem also doesn’t work. I have a robotics external modem which works fine with Fedora. I guess i have to make a modem link in  /dev but because i don’t have root password the system doesn’t let me do it. 
Any help in solving my root password problem would be appreciated. 

Thanks
jozmak

---

### Post by wazoo42 on 2004-11-21
Jozmak, ubuntu uses sudo instead of having a root user.  Thus, you can type:

sudo vi /etc/fstab

and it will ask for your password, and then you should be good.  Alternatively if you need to do a lot of stuff as root you can go to the top bar and somewhere in the right hand tree there is a root console (under utilities?).  You have to type in your password again and it should work.

---

