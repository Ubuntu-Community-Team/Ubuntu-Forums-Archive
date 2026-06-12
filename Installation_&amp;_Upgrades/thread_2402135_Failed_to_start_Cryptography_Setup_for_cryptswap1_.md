---
title: "Failed to start Cryptography Setup for cryptswap1 after trying to upgrade system."
date: 2018-09-26
forum: Installation &amp; Upgrades
---

### Post by chuoithat on 2018-09-26
Hello. 
I'm sorry if this has been answered before however after countless hours of trying all the solutions I could find none worked.

I tried to upgrade my 17.10 Ubuntu to the 18.04 version however in the middle of it error messages started to display that some of the libraries are already configured and it quit and shutdown halfway through after saying the installation was not succesfull. Now if I try to boot Ubuntu no matter which kernel I try to load the same error messages happen, namely that Crystography setup for cryptswap1 failed and Failed to activate swap /swapfile. It actually freezes later on however on a line that says it starts something (changes depending on which kernel I choose) and details.es.pp link was shutdown. The GRUB menu seems to be working. I have a Windows installed in a separate partition and it loads fine. 

Not sure what else to include as I am new to this and really inexperienced. If there is any information at all that could be helpful to know please let me know and I'll try and find it. 

I have tried editing the etc/fstab file as well as a couple others and each time it didn't work I made sure to return it to the way it was when I found it. I also tried to use a live version of ubuntu from USB however it fails to initialize. I can either choose Windows or Ubuntu from the hard drive, there is no option to launch Ubuntu from the USB.  It is an Intel touchscreen toshiba laptop. I have not had any problems at all before with Ubuntu.

Thank you in advance to anyone who will try to help me.

---

### Post by TheFu on 2018-09-26
I don't have any ideas for fixing what you have today.  A few key things for the future.
a) if you use any sort of encryption, you need perfect, know-you-can-restore backups.  PERIOD. 
b) when using encryption, be aware that less than 5% of the users choose that mode, to it isn't well-tested.
c) before attempting to upgrade an OS, always have a backup. ALWAYS.  It should include anything you can't loose AND if you want it to work later, it needs to include user, group, permissions, ACLs and extended attributes.  The files alone are NOT sufficient.

With where you are today, I'd wipe the install and start over.  I don't know how to install encrypted Ubuntu with Windows on the same disk.  It likes to wipe the entire disk during the install if you choose to encrypt.  That would wipe Windows, which might be exactly what you want. IDK.

After the install, I'd restore my HOME and any other users' HOMEs followed by the list of packages from the prior install.  Normally, this will get a system back to do most things in about 30-45 minutes.  Then if I have large media files, those would be restored ... which could be 10min or 3 days.  Just depends on the system.

If you don't have a backup already and using LUKS dm-crypt is the sort of encryption used, it should be possible to get the data off by using the flash drive.  I've accessed external LUKS-encrypted storage using ubuntu-mate before.  Not hard, if you know to install lvm and cryptsetup tools, then activate the LVM PVs, VGs, and LVs after opening the LUKS container.

If you don't plan on total OS migrations every 6 months, stick with LTS releases and ignore the others.

---

### Post by chuoithat on 2018-09-26
Thanks for responding so quickly. 

Until this happened I did not even know that the Ubuntu install was encrypted somehow and don't know how I've done that. I will ensure I am not using that mode in the future. 

There are only a couple of smaller files on there that I would much rather prefer to recover however it looks like they are probably not worth the hassle especially since I have no clue how I managed to encrypt in the first place. 

This might sound like a silly question but how would I wipe the install? I have access in the Ubuntu part only to the root shell prompt in a recovery kernel and I do not have access to a Windows installation USB thing.My laptop also does not have a CD reader as part of its hardware.

Thanks again for trying to help me out.

---

### Post by chuoithat on 2018-09-26
I have done some more poking around and trying to find out what went wrong. It appears that the encrypted swap partition does not exist as far as i can tell. Also /dev/mapper/cryptswap does not exist either according to the terminal. When I tried to stop it from running on boot by commenting out the two bottom lines of fstab (/swapfile and /dev/mapper/cryptswap lines) and the only line that was in /etc/crypttab then the error does not appear anymore. 

However if I try to load the default kernel the black screen with just one line is displayed saying: /dev/sda7: clean, 849163/3858432 files, 11211518/15415040 blocks. 

Trying to boot the recovery kernel results in it getting stuck on Removed slice User Slice of gdm after starting and stopping user manager for uid 121. uid 121 seems to correspond to the gnome desktop.

---

### Post by TheFu on 2018-09-26
I think are are misinterpreting some things.  Gnome runs under the userid logged in.  A uid number isn't the same across all systems. They get setup in order of package installation, so if they happen to be similar on 2 different systems, that is luck.

If you post your **fstab** and the output from **sudo fdisk -l**, someone might be able to help.  Attempted interpretations are suspect. ** df -hT** would be helpful too.  But really if you can post the URL generated by a **boot-info** script, that would provide all the data someone would need to help.   But really, I would have wiped the system and been back to normal in 45m.  Some things just aren't worth figuring out.

---

