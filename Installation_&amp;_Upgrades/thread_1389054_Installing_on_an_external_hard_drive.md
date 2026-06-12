---
title: "Installing on an external hard drive?"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Phantomhive on 2010-01-23
Is it possible to install Ubuntu - or any Linux for that matter - on an external hard drive? And also while still keeping the current OS (Windows 7)?

I have actually tried it before... without even knowing it I accidentally installed side-by-side to my external HD (LOL) but when I took it out then the computer wouldn't do anything, not even Windows. Is there a workaround?

If so, what external HD is best recommended for it? I have a FreeAgent HD right now. I probably will end up buying a cheap one (I could use more space anyway) mainly for Ubuntu and to always have plugged in.

---

### Post by rogue_0111 on 2010-01-23
Try [virtualbox]("http://www.virtualbox.org/").

Here's a how to video:

[http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows](http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows)


**If you still want to install on an external. **
1. Boot to the bios shut off your internal drive. 
2. Change boot order to CD or USB (wherever your Ubuntu ISO resides). 
3. Save and exit.
4. Boot to Ubuntu ISO and install to the external drive.

--

---

### Post by Phantomhive on 2010-01-24
> **rogue_0111 said:**
> Try [virtualbox]("http://www.virtualbox.org/").

Here's a how to video:

[http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows](http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows)


**If you still want to install on an external. **
1. Boot to the bios shut off your internal drive. 
2. Change boot order to CD or USB (wherever your Ubuntu ISO resides). 
3. Save and exit.
4. Boot to Ubuntu ISO and install to the external drive.

--

Yes, but doesn't it not particularly run well on 64 bit operating systems? (I have one)

---

### Post by I Forgot My Username on 2010-01-24
What doesn't run well on 64 bit, Ubuntu?  I don't know about Win7 64, but when I switched from Vista 32 I saw a noticeable positive change in speed.  I have a 64 bit AMD.

And yes, you can keep your other OS, the graphical installer makes partitioning easy even for me :).  As for installing on an external hard drive, all you have to do is find out what key to press a boot time to allow you to select the boot device(mine's F10).  You can find that key listed on the image that is first to come on to your screen when your computer boots(usually has the manufacturer name).  If it turns out to be too fast(mine was set to show that image for 5 seconds), just hit all the F buttons(F1-F12 one per boot, reboot to try the next key).  You'll probably get a few different results, look for "Choose Boot Device" or something to that effect(I suggest you hit esc for any other results unless you know what you're doing).

---

### Post by d3v1150m471c on 2010-01-24
Yes, you'd need to have the external connected to the computer and boot from the live cd. Select the external hard drive to install to and you're good to go. Boot from usb.

---

### Post by Phantomhive on 2010-01-24
> **I Forgot My Username said:**
> What doesn't run well on 64 bit, Ubuntu?  I don't know about Win7 64, but when I switched from Vista 32 I saw a noticeable positive change in speed.  I have a 64 bit AMD.

And yes, you can keep your other OS, the graphical installer makes partitioning easy even for me :).  As for installing on an external hard drive, all you have to do is find out what key to press a boot time to allow you to select the boot device(mine's F10).  You can find that key listed on the image that is first to come on to your screen when your computer boots(usually has the manufacturer name).  If it turns out to be too fast(mine was set to show that image for 5 seconds), just hit all the F buttons(F1-F12 one per boot, reboot to try the next key).  You'll probably get a few different results, look for "Choose Boot Device" or something to that effect(I suggest you hit esc for any other results unless you know what you're doing).

I meant VirtualBox doesn't run well. I was receiving an error when I tried to and it related to my computer being 64bit.

---

### Post by efflandt on 2010-01-24
The key to properly installing Ubuntu on an external drive is to make sure you select partition(s) on the external drive.  And at the final summary screen just before actual installation proceeds, [COLOR=Red]pay attention to the[/COLOR] **Advanced** button.  That is where you tell it to install grub2 to the mbr of the external drive (instead of default mbr on main hard drive).

Since it uses UUID to identify drives, it seems to boot fine whether sdb on my laptop or sdf on my desktop (due to internal USB multi-memory reader).

If you have any problem booting with different monitors, disable "splash" as a boot parameter.  Splash may halt boot (crash) if resolution in /etc/usplash.conf does not match "native" resolution of DVI/HDMI monitor/TV.

PS: I have done regular installations (with grub2) to USB flash and a couple of WD Passport hard drives.  On one of the latter (160 GB) 64-bit Ubuntu 9.10 is after a FAT32 partition, and on the other (500 GB) same is after NTFS partition.

---

### Post by darkod on 2010-01-24
> **efflandt said:**
> The key to properly installing Ubuntu on an external drive is to make sure you select partition(s) on the external drive.  And at the final summary screen just before actual installation proceeds, [COLOR=Red]pay attention to the[/COLOR] **Advanced** button.  That is where you tell it to install grub2 to the mbr of the external drive (instead of default mbr on main hard drive).


+1. This is the most important step when installing on external hdd. You have to make sure grub2 goes to the external drive, the MBR, not a partition number. For example, to /dev/sdb but not to /dev/sdb1.

Otherwise grub2 will probably go to your internal hdd MBR and since the config files for grub2 will still be on the external where you installed ubuntu, without the external connected you can't boot anything because grub2 is missing its config files.

---

