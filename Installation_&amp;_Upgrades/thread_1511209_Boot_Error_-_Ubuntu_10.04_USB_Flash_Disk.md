---
title: "Boot Error - Ubuntu 10.04 USB Flash Disk"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by mpanichi on 2010-06-16
Checked many threads and couldn´t find a solution to this one yet:

Just bought a new PC with **no OS** (MoBo Intel Atom D945GCLF2D) and I´m trying to install Ubuntu 10.04 (desktop i386 32B) from a USB Flash Disk (the PC has no CD-Rom or floppy). 

On booting the machine the message is: **Boot Error **

I tried **in a Dell Lap Top** the same Flash disk and **[COLOR=Black]it worked just fine[/COLOR]**. I tried the same flash disk in my old PC and the same msg appeared - Boot Error.

Steps I followed with no success in my new PC:
1) Bootable Disk with Universal-USB-Installer and Ubuntu 10.04 Iso in a Windows XP
2) Enable USB as first boot option at Bios
3) Tried to boot another OS from USB (also Linux) and it worked fine
4) Followed an advice to enter bios (F2) during boot and press ESC after that (no results);

I thank any tip on what to do. Rgds

---

### Post by im.saravanan on 2010-06-17
Same problem her too. Used universal usb installer and installed unbuntu 10.04 on 8 gb kingston pendrive DT101 and when booting i get boot error In My PC. But it works fine in my acer D250 netbook.

My PC config:

Intel 945GNCL mobo
intel core2duo 2.2 ghz processor
2 gb ram

Any idea why this is happening only in Desktops?????

---

### Post by NoBugs! on 2010-06-17
Have you checked bios boot settings? Your desktop might not have the option to boot from usb.

---

### Post by im.saravanan on 2010-06-17
Solution found.( My Desktop is usb bootable. ):guitar:

Solution: The problem is not in Ubuntu or Live USB creator softwares...the problem is in  bios settings...

1. go to Bios Boot Menu...
2. After setting first bootable device as USB 
3. Search for ' USB Mass Storage Emulation type'
4. Default:<Auto>
5. Change it to:<All Fixed Disc>
    or something similar

Above solution was posted by [registerkar]("http://ubuntuforums.org/member.php?u=927550") at [http://ubuntuforums.org/showthread.php?t=1042487](http://ubuntuforums.org/showthread.php?t=1042487).

---

### Post by ericeclifford on 2010-06-17
> **im.saravanan said:**
> Solution found.( My Desktop is usb bootable. ):guitar:

Solution: The problem is not in Ubuntu or Live USB creator softwares...the problem is in  bios settings...

1. go to Bios Boot Menu...
2. After setting first bootable device as USB 
3. Search for ' USB Mass Storage Emulation type'
4. Default:<Auto>
5. Change it to:<All Fixed Disc>
    or something similar

Above solution was posted by [registerkar]("http://ubuntuforums.org/member.php?u=927550") at [http://ubuntuforums.org/showthread.php?t=1042487](http://ubuntuforums.org/showthread.php?t=1042487).

I have the same problem, i get boot error with the USB or Live CD, I can not find the USB Mass storage emulation type in the BIOS

Is it in advanced boot configurations?

I might need to upgrade my BIOS, or something, I see USB mass storage boot device settings, that gives me options for auto/fdd/hdd but I do not see USB mass storage emulation anywhere in the bios.

---

### Post by gadolinio on 2010-06-17
> **ericeclifford said:**
> I have the same problem, i get boot error with the USB or Live CD, I can not find the USB Mass storage emulation type in the BIOS

Is it in advanced boot configurations?

I might need to upgrade my BIOS, or something, I see USB mass storage boot device settings, that gives me options for auto/fdd/hdd but I do not see USB mass storage emulation anywhere in the bios.

Have you tried downloading the iso file again? sometimes it has errors, so that file doesn't work.

---

### Post by vickystylton on 2010-06-17
> **ericeclifford said:**
> 

Is it in advanced boot configurations?



Yes, it is in the advanced boot configurations. Usually, under the boot tab, the view will be normal with an option to change it to advanced.

---

### Post by C.S.Cameron on 2010-06-17
Some BIOS has Hard Disk Drives, you need to select the flash drive as your first hard disk.

---

### Post by mpanichi on 2010-06-18
I solved without touching the BIOS configs (they seemed to be fine).

I used Linux Live USB to make the bootable Pen Drive (in Windows) and it worked just fine to boot Ubuntu from USB in my new PC:

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

