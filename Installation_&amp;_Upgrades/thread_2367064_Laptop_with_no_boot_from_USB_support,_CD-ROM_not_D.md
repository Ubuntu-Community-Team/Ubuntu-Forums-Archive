---
title: "Laptop with no boot from USB support, CD-ROM not DVD"
date: 2017-07-25
forum: Installation &amp; Upgrades
---

### Post by johnmheinzel on 2017-07-25
My laptop HDD has no OS installed (Compaq Presario CQ35). I'd like to install ubuntu desktop 16.04.02. 
The Bios does not allow boot from USB (I had a USB connected and it was not in the boot options).
It has a CD-ROM, not a DVD-ROM, so I cannot burn any current ubuntu distro to a single CD as they are over 700mb. 
What are my simplest options to install the latest ubuntu desktop? 
Can you burn a usable ISO over multiple CDs?
Is there something you need to do to a USB stick to make it bootable? 
I have a separate working laptop with a DVD drive that I can plop the HDD into, but would ubuntu work after moving it back considering the vastly different hardware in my other laptop (Dell LATITUDE E6540)?

---

### Post by Geoffrey_Arndt on 2017-07-25
Because the USB Flash-Stick was not shown in the boot options, does not necessarly mean your laptop is incapable of booting from USB Flash-Stick.    Often, people are not aware that the BIOS/Firmware needs to be modified to enable alternate boot sequence, as well as selecting the proper device options (usb-hdd or usb-flash or similar).   Plus, a "reliable" proven tool should be used to enable the iso image to be properly written to the flash-stick to make it "bootable".     

I really like this Electron/AppImage program . . . Etcher.    Pls see 

[https://etcher.io/](https://etcher.io/)

---

### Post by johnmheinzel on 2017-07-25
Thanks, I am now trying unetbootin [COLOR=#006621][FONT=Roboto]https://sourceforge.net/projects/unetbootin [/FONT][/COLOR]to create a bootable USB drive with the ubuntu iso. My mistake was likely in just copying files from a bootable DVD to the USB thinking it would just work. We'll see.

---

### Post by BenginM on 2017-07-25
Salutations! and welcome to the forums.

I suppose you can use the mini netboot iso and burn it to a CD .. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://www.youtube.com/watch?v=U42Ln3k7VK0&t=633s](https://www.youtube.com/watch?v=U42Ln3k7VK0&t=633s)

[https://www.youtube.com/watch?v=fIfQ8SehcNU](https://www.youtube.com/watch?v=fIfQ8SehcNU)

it's fairly simple, just make sure you're connected to wired ethernet , and when you get to the software selection , select the desktop environments you want by pressing the space key , for Ubuntu Unity desktop , you need to choose the package ubuntu-dekstop , for lubuntu ( lubuntu-desktop , Xubuntu ( Xubuntu-desktop ..

---

### Post by oldfred on 2017-07-25
That machine looks like it is new enough to boot USB.
But USB flash drive has to be correctly configured, and sometime one flash drive or another works better.
Systems may not show USB boot, but then have another hard drive shown which is the USB flash drive.

Since somewhat older, you may prefer Lubuntu or Xubuntu.
But my 10 year old Toshiba booted from USB, ran older versions of Ubuntu. But when 12.04 with Unity was installed it just was too slow. I then added flashback/fallback/gnome-panel which was also a lighter weight gui. 
I recently installed 16.04 just to see if it still worked. And Unity even was usable, just not very fast.
So some improvements in Unity over the years.

---

### Post by Autodave on 2017-07-25
To answer your question about swapping the HD: I have done that many times and have never had an issue. Just make sure that you do not install and drivers until the HD is back in the correct machine.

Side note: I repair computers as a hobby. I have two HDs sitting on my workbench: one 2.5" and one regular size for desktops. I have swapped both of those into various machines many times and they have always functioned.

---

### Post by johnmheinzel on 2017-07-26
So the problem was really multiple problems that had to do with formatting. First, the USB stick was formatted as exFAT. I made it bootable using unetbootin, but the PC didn't give me an option to boot from USB. It seems the solution was to format the USB stick as FAT32, then use unetbootin to make it bootable with the Ubuntu distro. When that was done, the BIOS boot options showed the USB after all. 
However, during installation Ubuntu would not see the HDD - this was at the *Installation type* window where **Device for boot loader installation:** is shown, after Erase disk and install Ubuntu (with Encrypt and Use LVM options). I don't know if all this was necessary, but I connected the HDD to my Windows laptop and deleted the partitions and volumes, until the disk was all unallocated space. Reconnected to the Compaq ubuntu install still didn't see it. Back on the Dell I then created a partition for the full disk and formatted it as NTFS. Back on Ubuntu, the installation was now able to proceed, and it finally finished.

---

### Post by johnmheinzel on 2017-07-26
Thanks, I'm sure that would work, but I did get the USB stick to show in BIOS after formatting it FAT32 and using [COLOR=#000000]unetbootin to make it bootable with the ubuntu distro.[/COLOR]

---

### Post by johnmheinzel on 2017-07-26
Good to know. My one experience was with a fully configured HDD for a Windows laptop and the device drivers definitely did not like the change of scenery.

---

