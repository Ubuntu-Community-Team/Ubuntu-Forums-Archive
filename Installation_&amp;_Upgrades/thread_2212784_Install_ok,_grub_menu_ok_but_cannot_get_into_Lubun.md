---
title: "Install ok, grub menu ok but cannot get into Lubuntu"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by zzzmuzz on 2014-03-23
I successfully installed Lubuntu on my old Asus M2400N laptop. The Grub menu seemed to install ok so i have he menu selections of Lubuntu and Lubuntu recovery, as well as Windows XP.

Can't recall Lubuntu version but Grub menu shows Linux 3.2.0-23-generic

When I select Lubuntu, there are some flickerings on the screen kind of like a black and white wall paper, but after that nothing.  I assume this is a display issue, but being new to this I don't have the expertise with Ubuntu to work out the solution, not even using the various forums!

Help please.

---

### Post by ajgreeny on 2014-03-23
When you see the grub menu use the "e" key to "edit" the entry for just the one boot.  Go to the line that will look something like 
```
linux    /boot/vmlinuz-3.5.0-46-generic root=UUID=1fd42bfe-b5d4-4389-9607-1207af1c3e8b ro   **quiet splash** $vt_handoff
```
Yours may look a bit different but there will be a line with **quiet splash** in there at the end.  With the cursor keys go to that line and delete those two words and replace with **nomodeset** then hit Ctrl+X to try to boot.

With luck you will get a GUI and you can then fully update the OS and look for a driver for the graphic card using the Additional Drivers utility, which you can get to if you cant find it in the menu by using the command **/usr/bin/jockey-gtk** in terminal.

There are many other boot options available but that is the most likely to get you going.  Once the new graphic driver is installed you may not need any further actions for future boots.

---

### Post by zzzmuzz on 2014-03-23
Thanks very much for your input.
Mine was very different, and with no quiet splash at the end. 

Mine:
Set params 'Ubuntu, with Linux 3.2.0-23-generic

recordfail
gfxmode $linux_gfx-mode
insmod gzio
insmod part-msdos
insmod ext2
root='(hd0,msdos)'
GNu Gru(?) v 1.99-21ubuntu 3.14

The setup is dual boot with XP.  So in Grub I have
Ubuntu
Ubuntu (recovery)
XP
(as well as mem tests etc)

I am trying a reinstall with these disabled. (I have tried this before though and it didnt help.  I do seem to recall attempting to install Ubuntu on this laptop years ago and was recommended these settings.)

[LIST]
[*]acpi=off
[*]noapic
[*]nolapic
[/LIST]

The install itself went fine, so I suspect I am not far away and the issue is a display one. 

btw, the display on this is Intel(R) 82852/82855 GM/GME Graphics
Digital Flat Panel (1024x68) [Monitor] (s/n 3)

---

### Post by zzzmuzz on 2014-03-23
I reinstalled, got rid of Xp and Lubuntu booted straight up after using the settings above. 

Thanks..it looks like I am on track now.

---

