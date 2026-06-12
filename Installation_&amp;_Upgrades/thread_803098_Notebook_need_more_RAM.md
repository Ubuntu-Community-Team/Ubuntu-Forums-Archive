---
title: "Notebook: need more RAM"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-22
I have a Toshiba Portege CT3440 with the "full RAM" of 192 MB !!!

I cannot add more RAM.

Would more swap help? Like a USB MICRO___DRIVE___ ?

Or is there anything I still can do?

bye

R.

---

### Post by EXCiD3 on 2008-05-22
Increasing swap will help because swap is used when your ram is fully used up. One thing to help improve performance is to use XFCE instead of Gnome or another light window manager and to cut back on as many eye candy things as possible.

---

### Post by ELMIT on 2008-05-24
Before I go out to buy a Microdrive I tested an external harddisk.

I added the swap partition, and in free or top I can see more swap space, however, it is not used! Do I miss something?

---

### Post by Herman on 2008-05-24
A Live CD will scan your hard disks and automatically find and mount any swap area it finds on boot-up.

A hard disk installed operating system doesn't do that though, you need to open your /etc/fstab file and tell your hard drive installed Ubuntu the UUID number for the file system you want it to use as a swap area.

You can find the UUID numbers for your file systems with either the sudo blkid command or the [COLOR=#000000][FONT=Bitstream Vera Sans Mono]sudo ls /dev/disk/by-uuid/ -alh command.

When you have that you can open your /etc/fstab file and copy and paste the right UUID number into your /etc/fstab file so your operating system will mount it. 
You can have more than one swap area if you make another entry in your /etc/fstab file, you can have as many swap areas as you like.

Your new swap area will be mounted after you enter the mount -a command, or reboot.
[/FONT][/COLOR]```
sudo ls /dev/disk/by-uuid/ -alh
```
```
gksudo gedit /etc/fstab
```
```
sudo mount -a
```
[COLOR=#000000][FONT=Bitstream Vera Sans Mono] 

[/FONT][/COLOR]

---

### Post by ELMIT on 2008-05-25
Thank you for your suggestion.

However, (if you read my posting) it is not a problem to mount / add the swap partition, ... it is just not used.

I have only 192MB RAM, and a swap partition of 256 and from the external hard disk additional 512 MB. I think it is obvious, that Ubuntu would need more than 192 MB RAM pretty soon. However, mem shows that it uses 240 MB of swap only, whatever I do on that computer. Something blocks the system to use this additional swap partition on the USB hard disk.

bye

R.

---

### Post by EXCiD3 on 2008-05-25
Is it just possible that you dont need the extra swap? Have you tried running a virtual machine and seeing if the swap usage goes up then?

---

