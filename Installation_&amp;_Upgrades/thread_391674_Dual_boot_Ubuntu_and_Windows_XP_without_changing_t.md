---
title: "Dual boot Ubuntu and Windows XP without changing the Windows MBR"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by rajen on 2007-03-23
I'm trying to install grub to /dev/sda3 (linux partition), so that I don't overwrite the window MBR 

I have used the alternate cd and specified /dev/sda3 during the installation.  However, it still installs grub to the MBR.

Thinkpad R60e with Windows XP / Ubuntu 6.10

---

### Post by ffxr on 2007-03-23
i dont know if you can disable the grub installation durin a ubuntu install.. m sure there is a way; i just dont know it.. 

but.. if your happy to issue the fixmbr command, and recover your boot record that way... maybe you can do that....

this guide may be of interest to you on how to get linux booting from a windows bootloader.. tthis is written for puppylinux but  m sure its easily manipulated to get ubuntu loading,...

i have used it and it works well.. (for puppy linux, granted..)

[http://www.icpug.org.uk/national/linnwin/step1-intro.htm](http://www.icpug.org.uk/national/linnwin/step1-intro.htm)

---

### Post by NJC on 2007-03-23
rajen;

The first time I did an install, Grub was loaded into the MBR. After fixing it, I disconnected the other Win drives and installed Ubuntu onto the only connected drive.

After you hook up the Win drive(s), you need to properly point Grub to where the Ubuntu boot section is in menu.lst. Do a search for dual boot and you'll find lots of info. BTW, in order to get Win to dual boot you have fool it into thinking it's the Master drive. I added the following to the menu.lst: 

```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

Note this was for Win 98. In the Bios I have my Win 98 drive as Master, and Ubuntu as slave. I also added "timeout 10" to the menu.lst so I have time to get into Grub boot menu and start Win if I need to.

EDIT: Above code was from a post discussing Win XP dual boot
[http://www.ubuntuforums.org/showthread.php?t=124989](http://www.ubuntuforums.org/showthread.php?t=124989)

---

