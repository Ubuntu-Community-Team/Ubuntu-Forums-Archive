---
title: "can't access fedora after installing ubuntu"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by daudiam on 2010-02-27
I installed Ubuntu after installing Fedora. Now there is no boot menu from which to select a OS. Ubuntu directly loads on startup. Now I think that I have to make changes in the menu.lst file (i have ubuntu 9.10) and add the contents of the fedora's grub.conf file there (or the menu.lst fil, I'm not sure). But, I am not able to open these two files. It says that u don't have permission to see thier contents. If I can't access them, how can I boot my Fedora through Ubuntu.

SOmeone said that I should login as the root. But, when I mount the directory conataining Fedora, it does ask for my password and I am able to enter into it. But the directory inside the home directory as well  as the above 2 files have a cross marked onto them. What should I do ?

Note : Ubuntu is in a logical partition while Fdora is a primary partition

---

### Post by ajgreeny on 2010-02-27
Ubuntu 9.10 will not have a menu.lst file any more but all the configuration of grub will be from /boot/grub/grub.cfg, which is written when you run ```
sudo update-grub
``` in terminal from other configuration files contained in **/etc/default/grub** and **/etc/grub.d**

It is possible that Ubuntu may be able to find fedora if you use the **update-grub** command just shown, but I suspect the problem is that by default fedora puts everything on LVM partitions and they are not directly readable by ubuntu without a few extra packages.  Search "lvm" in synaptic and you may find several that are needed and will allow you to access fedora.

---

### Post by oldfred on 2010-02-27
I have several links to others with Fedora:

Fix for Fedora:
sudo apt-get install --reinstall libdebian-installer4

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}
 
[http://ubuntuforums.org/showthread.php?t=1367305](http://ubuntuforums.org/showthread.php?t=1367305)
If the linux has no bootloader, the os-prober will look for the kernel file name that starts with vmlinu[zx] and the initrd file name that starts with initrd.
In my case, I have installed fedora without bootloader and the initrd file name starts with initramfs. I have made a simple change to the os-prober by make it looking for the file starts with initr instead of initrd.

---

### Post by daudiam on 2010-03-08
Thanks a lot to everyone who helped

I finally got it to work

I copied the code from fedora's menu.lst file 
I gave the following command (after mounting Fedora)

/media/Fedora/boot/grub

then, sudo vi menu.lst

I found something of this type there : 

title Fedora (2.6.31.5-127.fc12.x86_64)
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=8451bdcb-531c-44e6-97a4-88ed2af20ad2  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
        initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img

I compared it to Ubuntu's grub2's /boot/grub/grub.cfg 's way of doing the same thing. I found that the following reformatting will make it similar to ubuntu's :

menuentry "Fedora (2.6.31.5-127.fc12.x86_64)"
{
    
        set root=(hd0,0)
    search --no-floppy --fs-uuid --set 8451bdcb-531c-44e6-97a4-88ed2af20ad2 
        linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=UUID=8451bdcb-531c-44e6-97a4-88ed2af20ad2  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
        initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

This I DID NOT ADD IN grub.cfg but in /etc/grub.d/40_custom

I saved the file and exited. Then, I typed

update-grub

On restarting, I kept the shift key down, I had the Fedora option there.

---

### Post by workdowg on 2010-09-19
My solution is a little messier...but worked for me.

Boot Ubuntu.

Install lvm2:
$ sudo apt-get install lvm2

Load the necessary module(s):
$ sudo modprobe dm-mod

Scan your system for LVM volumes and identify in the output the volume  group name that has your Fedora volume (mine proved to be vgacer-fedora):
$ sudo vgscan

Activate the volume:
$ sudo vgchange -ay vgacer-fedora (replace with what you got from vgscan)

Update grub:
$ sudo update-grub

You should now have a menu option(s) for your Fedora installation...

---

