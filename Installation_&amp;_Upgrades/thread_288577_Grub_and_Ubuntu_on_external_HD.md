---
title: "Grub and Ubuntu on external HD"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by dschmider on 2006-10-30
Hi,
Like many, I'm a noob to anything linux, but need dual boot with my xp because of supported software, blah blah.
As I did not have enough room in my internal HD I connected an external 2.5 drive via USB. 
I split the partition to install ubuntu, but also have a fat32 drive that both OS's could see, so I can move between OS easily.
The problem I've got now, is that to start uo my original XP, I need to always connect my USB drive because Grub is running from there.
Is there a way for me to automatically boot xp from my internal HD if the external drive is not connected?
Heres hoping.
Regards
David

---

### Post by dogon on 2006-10-30
If this is possible depends on your BIOS. Most modern computers are capable of booting from USB drives. If your BIOS can do this then you could install grub on the external drive, put the drive in BIOS as your primary startup drive and put the internal drive as a secundary or tertiary, depending on where you want to put CDROM.

When the USB drive is plugged in you should start from the USB drive, when you unplug it it starts from the internal drive.

In the mean time during installation procedures I would recommend physically unplugging the internal harddrives since you dont need them and dont want to change them anyway. This should not be necesary, but better safe than sorry. That way after unplugging usb and reattaching the drives your system will be 100% as it was before.

---

### Post by dschmider on 2006-10-30
Thanks for your reply dogon,

Ah, wish, I'd unplugged the internal drive now... tsk!](*,) 

Do you know how I re-install Grub on my USB drive, and revert the windows drive back to normal?:-k 
Seems the only sensible way now.

Thanks
David

---

### Post by dschmider on 2006-10-30
BTW, THe error  when the USB drive is not connected is Error 21

---

### Post by dogon on 2006-10-30
Hmm there is another way, the problem is that grub is installed on the MBR, but the menu.lst is on the disabled USB drive. It wont find it and thats probably your error 25. When the drive is turned on, the menu.lst can be found and boot succeeds.

You only have windows on your internal disks so you cannot store menu.lst on an internal drive. Which only leaves the option of a different boot loader to take care of things. Check if XP can boot into an USB linux partition. Chances are it only boots into windows. I never experimented with the windows bootloader. I don't know. If it can boot into an USB linux partition then you're done with just one bootloader.

However if this is not the case then you need to setup grub on the USB drive and use the bios trick I described earlier.

Setting up grub you would do by booting into the USB drive. From there go to a root terminal and use "grub-install (usb drive device name (/dev/sda?))" (You can find the device name with "fdisk -l")

That should overwrite the USB drives bootsector. 

Windows XP has a bootsect.exe program that you can use to restore the bootsector. Its probably best to switch off your usb drive once you've booted into windows. There may be a graphical tool that does this, I have no experience since my task was usually to get rid of the windows boot sector, not put it back :)

---

