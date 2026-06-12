---
title: "Installing grub to a different drive?"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by t3ddyg on 2011-07-29
Hello,
I'm in a jam with this Dell 400SC because it has some chipset limitation where it will auto-default to try and boot from a SATA drive, if one is present.  There is no bios setting to select the primary master as the boot drive if SATA is also present.  My current setup is: 

Primary Master IDE - Ubuntu 11.04 install
SATA1 - Windows 7 and misc files
SATA2 - Files storage

Whenever I turn on the computer, it automatically tries to load the windows install on SATA1.  I found this forum post explaining how someone worked around this by installing "graphical boot manager".
[http://en.community.dell.com/support-forums/servers/f/956/t/17718849.aspx](http://en.community.dell.com/support-forums/servers/f/956/t/17718849.aspx)

Is that the best way to go?  I thought grub is pretty cutting edge.  I don't want to install some weird outdated app on top of it.  Do i have to change the location where grub installs itself? I'm not sure what to do.  Thanks for any help/suggestions.  

P.S. I'm not particularly concerned about the windows install.  I plan to move files from SATA1 to SATA2 after everything is booting properly, and format SATA1 to ext4 (currently ntfs).  I need to get the files moved before utilizing Ubuntu as the sole operating system on this computer.

---

### Post by drs305 on 2011-07-29
If you can boot into your Ubuntu OS, just run the following, with X being the your Ubuntu drive:
```

sudo grub-install /dev/sd[COLOR="DarkRed"]**X**[/COLOR]
```
Do not include the partition number.

Once you have run the command, reboot. If the computer is looking at the Ubuntu drive first, its MBR will point to the Ubuntu boot files. 

Note: If there is another OS's information on the MBR of sdX, it will be overwritten.

If you can't boot Ubuntu, boot the LiveCD and run the following:
```
sudo mount /dev/sdXY /mnt # (example: sda1 )
sudo grub-install --root-directory=/mnt /dev/sdX
```

---

### Post by inertself on 2011-07-29
Run the live cd, mount all of your drives, and do 
 
```
sudo fdisk -l
```
 
Pick which drive you want to install grub to (your sda drive probably, check the size).  
 
Also, to restore windows, create a recovery cd from your backup menu in the control panel, use this to fix the mbr (startup repair).  Do this before installing grub, or it will remove grub.

---

### Post by t3ddyg on 2011-07-31
Hey guys, thanks for the pointers.  I got it working by doing a fresh install and choosing manual partitioning option.  It had a drop down for "install loader to X drive" or something like that, and I selected the SATA drive.  All is well now.:guitar:

---

