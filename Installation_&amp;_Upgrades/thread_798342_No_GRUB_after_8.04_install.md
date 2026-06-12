---
title: "No GRUB after 8.04 install"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Jungle-Cat on 2008-05-18
Hey guys,
I just did a fresh install of XP on its own partition, and am trying to dual boot it with Hardy Heron.

I've got a 4gb partition (ntfs) for XP, and a 35gb ext3 for Ubuntu. I run the installer via live cd and everything seams to work; but GRUB does not appear to have installed. Windows XP boots, as if Ubuntu doesn't exist.

I had no problems with 7.10...

Thanks

---

### Post by tommcd on 2008-05-18
Just to be clear, did you install XP first to a primary partition, and the install Ubuntu? If XP was installed last it will overwrite grub  on the MBR. Assuming Ubuntu installed ok, then you just need to reinstall grub. To reinstall grub, boot up the live CD, open a terminal, and follow this:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Jungle-Cat on 2008-05-18
I installed Ubuntu AFTER Windows to prevent it overwriting the MBR.

I'll try the above now.

---

### Post by Jungle-Cat on 2008-05-19
Thanks, I did the above and now GRUB is installed.

The menu items are all named correct, and I can boot Winxp. However, If I try and run one of the Ubuntu items I get "Partition not found". That's rubbish; Ubuntu is installed on (hd1,1) where xp is on (hd1,0). So my setup is something like this:
hd1,0 - NTFS - Winxp - 40gb
hd1,1 - ext3 - Ubuntu 8.04 - 35gb
linux-swap - 2gb
free space - 1gb

The menu.lst points to (hd1,1) for Ubuntu, but I get "Partition not found"... is there a tool I can run from the live-cd to 'suss it out' ?

---

### Post by iaculallad on 2008-05-19
Boot from the Ubuntu LiveCD. From your desktop, open the terminal and issue the command:

sudo update-grub

to re-create your /boot/grub/menu.lst

---

### Post by Jungle-Cat on 2008-05-19
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

>D:

---

### Post by iaculallad on 2008-05-19
Follow this [link]("http://ubuntuforums.org/showthread.php?t=224351") to re-create your GRUB.

---

### Post by Jungle-Cat on 2008-05-19
Ok; now I'm really screwed.

I have no idea where GRUB is installed, I can't find stage1... how do I completely remove grub and install it to my Ubuntu partition?

//edit
I think it is trying to setup and update GRUB on "/" (live cd root) instead of "/media/disk-1/boot/grub"... I think I'm going to have to reinstall Ubuntu. Possible Windows as well and start from scratch... very disappointing; Ubuntu 7.10 worked a charm, Ubuntu 8.04 is a complete crock up for both me and my Dad.

//edit
Ok; here is what I did:
sudo gparted
unmount disk-1
linuxswap off
delete partition disk-1
delete linuxswap

Windows recovery console:
fixmbr

voila!

I'll try again next week :P

---

