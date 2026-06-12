---
title: "Dual Boot Vista Ubuntu"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by xRes on 2008-01-15
**[COLOR="Red"][ SORTED][/COLOR]**

Hi
I had Vista installed on my laptop when I bought it. Its an Acer so it had the C: the D: (Data) and the hidden drive (Think that has a copy of the upgrade/restore disk on which I already own). I removed the data drive and the hidden drive and have installed Ubuntu in its place. Grub brings up Ubuntu and a Vista option but vista will not boot *(Link on GRUB - Windows Vista/Longhorn (loader))*. I can see from accessing the windows C: drive in Ubuntu that all the OS files and my documents etc are still there!

How can I edit Grub to show the Vista OS option correctly?

It's mount point appears to be /media/sda2

Thanks

---

### Post by logos34 on 2008-01-15
if vista is sda2, your /boot/grub/menu.lst windows entry should have 'root (hd0,1)'.  Is that what it says?

---

### Post by RockHaxor on 2008-01-15
If you did a clean install on your hard drive and installed Ubuntu before you installed Windows, then Ubuntu will not have anything in the grub configuration for Windows. This is where you’ll have to do a bit of manual editing to the grub boot menu file.

Open a terminal **applications/accessories/terminal**

Open the file /boot/grub/menu.lst with the following command in the terminal:

```
sudo gedit /boot/grub/menu.lst
```

Copy this code and insert it at the bottom of this open document (In the windows portion you can call windows whatever you like:) )
```
title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1
```

Look at the top of this document where it annotates that the grub loader is hidden by default. If you want the selection to be visible instead of having to hit (esc) when booting place a (#) sign in front of this line.

Save this document and reboot your system

Note: You should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)

---

### Post by RockHaxor on 2008-01-15
If you still can't boot Vista, the MBR might be damaged. You can repair it using one of these great tools.

I found this tool to be a great asset, it has everything you could possibly want and more.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

download this iso image , burn it to a cd and use a tool on the disc called Super Grub Disc.

I believe it will repair the MBR for you.

If you don't want the entire Ultimate Boot CD then you can download Super Grub at this link:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Good Luck
___________

---

### Post by xRes on 2008-01-16
**[COLOR="Red"]Sorted now, thanks all![/COLOR]**

---

