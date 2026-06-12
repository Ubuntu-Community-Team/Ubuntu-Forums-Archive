---
title: "My computer refuses to boot Ubuntu off of a USB stick"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by NovaFlame on 2011-08-13
So here's the problem. I just bought a brand new 4gb stick today in hopes of getting Ubuntu to boot and install on my computer (I do not have a CD burner). I downloaded the latest ISO and used the Universal USB installer to unpack everything on to the stick, then I rebooted my computer and accessed the boot menu. These are the choices I got. 

1) USB-CDROM
2) USB-HDD
3) USB-FDD
4) USB-ZIP 

I tried all of them and all I got was a "Boot Error". So I went into the BIOS and configured the boot order to try every single combination of the USB boot (listed above). Still no luck. So I was like alright, I'll delete the unpacked contents on the stick and try unpacking using Unetbootin. Still didn't work. So I'm a little miffed here. I was kind of hoping I would be able to boot Ubuntu fairly easily. Any advice? Am I missing something obvious here? Am I just stupid? I'm a beginner to linux by the way.

EDIT: I also tried plugging the stick into every available port.

---

### Post by Hakunka-Matata on 2011-08-14
Welcome to the Forum:
does sound weird.  You're writing here on the forum so you are up and running some OS, Windows?  
Anyway can you plug your USB stick in and read the directory of it?
Is it formatted FAT32?
Look like the attached .png?

---

### Post by NovaFlame on 2011-08-14
I am on Windows XP, and yes to all three of those questions.

---

### Post by Hakunka-Matata on 2011-08-14
what brand - make usb stick is it?  I read about a certain make that uses some sort of pre-installed software called "U3" that causes problems, maybe?????????????  Since it's new and this is presumably the first time you're trying it?

---

### Post by NovaFlame on 2011-08-14
The brand is Kingston I believe. It does have some software on the stick, though I doubt it'll interfere.

---

### Post by garvinrick4 on 2011-08-14
Reinstall on flashdrive and try again. You have an .iso file you have an app that makes a bootable USB flash drive. That is all there is to it. You really do nothing but point the app towards the .iso file and install on this USB flash drive.  If it says error there is an error.

---

### Post by Hakunka-Matata on 2011-08-14
> **NovaFlame said:**
> The brand is Kingston I believe. It does have [COLOR=Red]**some software**[/COLOR] on the stick, though I doubt it'll interfere.

Some software???  you mean the directory actually shows additional files?  Or ???

---

### Post by Hakunka-Matata on 2011-08-14
If it is a new Kingston drive, the one that is described in the attached HyperLink, I'll be willing to bet that is the problem

[http://www.kingston.com/flash/dt101g2.asp](http://www.kingston.com/flash/dt101g2.asp)

---

### Post by NovaFlame on 2011-08-14
Yes that is the one :(. But I can uninstall the software. That will help? And to the other user who replied, there were no errors during unpacking.

---

### Post by Hakunka-Matata on 2011-08-14
if you want to back up whatever the software packages are, ok.  But I do believe to make a bootable USB you'll have to get rid of it.  Best way would be to just create a new partition table on the device, but you'll have to do that with something that runs on Windows, I don't know off hand what program that would be.  Creating a new partition table, an msdos partition table, will destroy/wipe clean the usb, then you'd have to format it to FAT32, then go back and run unetbootin to burn the .iso package to it again.  I read a thread where people were complaining about the Sandisk (and others) that now have the U3 software preinstalled, they said Ubuntu 11.04 choked on it, but 10.04 actually didn't mind it.  So it's a new thing, don't know all the ramifications yet.  Good Luck, time for some sleep for me.

---

### Post by varunendra on 2011-08-14
> **NovaFlame said:**
> I rebooted my computer and accessed the boot menu. These are the choices I got. 

1) USB-CDROM
2) USB-HDD
3) USB-FDD
4) USB-ZIP 

I tried all of them and all I got was a "Boot Error"....
I have some HP Pavillion dx2480 desktops in our office and they have exactly the same boot options available. This desktop model is relatively new (almost 2yrs old I think) **but the bummer is - it can't boot from a USB key!** On the other hand, we have other outdated desktops (IBM Think Center, HCL with DDR-1 RAM, etc.) which boot from all kind of USBs I've tried. There's no newer BIOS available for the HP desktop I mentioned.

Having said this, I've seen some perfectly working kingston USB keys not being able to boot a computer. So try using a different brand. As for the software on it, it is simply copied on it along with an 'autorun.inf' file that works with windows systems. You can simply move these two (the program file/folder + the autorun.inf file) to another place instead of 'deleting' them. If you need them later (some of these have a good file/folder 'sync' option), just copy them back to the root of the USB key.

Also, one of my HCL desktops shows my transcend USB key under the list of hard disk instead of USB hard disk or any other USB device. I also remember to have once found a USB key under 'floppy' instead of USB devices in a laptop's BIOS.

The point is- where the USB key may show up depends upon "the type of emulation its manufacturers use for booting + the way the BIOS understands it". It is not necessary that it'll be listed under USB devices only. So try all kind of boot devices you have as options.

Hope your BIOS does not have a dead-end like my dx2480's.

---

