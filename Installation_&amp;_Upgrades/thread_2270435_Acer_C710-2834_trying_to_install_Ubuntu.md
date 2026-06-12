---
title: "Acer C710-2834 trying to install Ubuntu"
date: 2015-03-23
forum: Installation &amp; Upgrades
---

### Post by draky87120 on 2015-03-23
Hello, I'm new to Ubuntu and have used it a few times only. I recently purchased a Acer 710-2834, upgraded the HD and RAM on it and want to load Ubuntu. I have the "developer bios" loaded, says I can hit ctrl+U on the OS verification screen to boot off of a usb drive but I can't get it to read my usb drive. The drive is formatted with FAT32 and I followed the steps I found at [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Does anyone have an ideas for me I can try? The Chrubuntu doesn't work for me (script runs successfully but boots back into chrome OS) and Crouton just seems a little off to me for some reason. 

Thanks in advance, I tried to search for this but I couldn't find anything on it with what I was trying to search for.

---

### Post by Bucky Ball on 2015-03-23
*Thread moved to **Installation & Upgrades**.*

If your USB is formatted FAT32, what are you installing Ubuntu with? You need to download the ISO, burn a disk image to the USB with [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") or another tool to create a bootable USB stick, then try again.

It might not be finding the USB as it is a non-bootable device formatted in FAT32.

---

### Post by draky87120 on 2015-03-23
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

If your USB is formatted FAT32, what are you installing Ubuntu with? You need to download the ISO, burn a disk image to the USB with [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") or another tool to create a bootable USB stick, then try again.

It might not be finding the USB as it is a non-bootable device formatted in FAT32.
Sorry I posted in the wrong forum.

As far as what I'm installing, I've tried that tool you posted (was the same as the one I put in my original post). I installed it per the instructions [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) but it's still not able to install. I've now tried 2 different thumb drives and all 3 usb ports on the Chromebook. I also am able to browse the thumb drive in Chrome OS so I know the usb drives are good and so is the thumb drive. 

Now, looking at this it looks like a windows installer with .exe file. Is there something specific I should have or a specific .iso for 12.04  I should download? I chose the "Ubuntu 12.04.5 Desktop (64-bit)" found under BitTorrent in Ubuntu downloads page.

Edited: I just got back into it and for booting it says:
"Booting any self-signed kernel from SSD/USB/SDCard slot is enabled. Insert bootable media into USB/SDCard slot and press Ctrl-U in developer screen to boot your own image."
That was from SeaBIOS... I found this about SeaBIOS:
"SeaBIOS has been tested with GRUB, LILO, and Syslinux. Linux booting works well."

---

### Post by Bucky Ball on 2015-03-23
Wrong. The .exe file is Wubi, which installs inside Windows like a regular program, and, although it is still an option on some releases, is no longer supported.

Download the ISO from the official Ubuntu site. There is a torrent there under Alternative Downloads. Look a bit down [this]("http://www.ubuntu.com/download/alternative-downloads") page for Bittorrent.

Don't install Wubi or any .exe file. You should have a downloaded ISO file.

---

### Post by draky87120 on 2015-03-23
> **Bucky Ball said:**
> Wrong. The .exe file is Wubi, which installs inside Windows like a regular program, and, although it is still an option on some releases, is no longer supported.

Download the ISO from the official Ubuntu site. There is a torrent there under Alternative Downloads. Look a bit down [this]("http://www.ubuntu.com/download/alternative-downloads") page for Bittorrent.

Don't install Wubi or any .exe file. You should have a downloaded ISO file.
Thanks for the reply, the .exe file was in the usb drive after I ran the file from the .iso file. I just can't get this chromebook to see my USB stick as bootable even with the SeaBIOS. I am hoping someone on here has a solution to this, what is the SeaBIOS looking for specifically so it can boot off of the Ubuntu iso so I can install it?

---

### Post by draky87120 on 2015-03-23
Edit: I got Chrubuntu to install finally! YAY! I'm at a command prompt however and I would like to download the Ubuntu UI... Anyone have the command for that one please?

---

### Post by hans12345 on 2015-12-31
> **draky87120 said:**
> Edit: I got Chrubuntu to install finally! YAY! ... 

I am about to start the same process.

How did you solve your problem?

---

### Post by Bucky Ball on 2015-12-31
```
sudo apt-get install ubuntu-desktop
```

That's it. When finished, reboot, choose the Ubuntu session from the 'Sessions' menu at the login screen, login. Don't know of the specs of that machine, but if you don't have much RAM, Ubuntu will probably be too heavy. Good luck.

PS: I also have no idea about Chrubuntu, which isn't supported here, or what conflicts may arise by installing Ubuntu Desktop on top of it. You may end up with a bunch of duplicate apps, redundancy or plain deal-breaking software conflicts. Or it may run fine. One way to find out.

---

### Post by hans12345 on 2016-01-01
Thanks
:p

---

