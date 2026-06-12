---
title: "Hybrid ISO"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by gatewayasteroid on 2011-08-08
There's a quick and easy method of installing Ubuntu (or any derivative) from a pendrive: **isohybrid**.
It's a tool which is part of the **syslinux** package.
just install it, then type
```
isohybrid FILENAME.ISO
```
where FILENAME.ISO is your iso file. The md5 checksum will change, of course.
Then, you can just write your modified iso file to a pendrive:
```
sudo su
umount /dev/sdx
```
where sdX is your pendrive device name. Pay attention!
```
dd if=FILENAME.ISO of=/dev/sdX
sync
```

I wonder why the standard ISOs aren't already patched with this. Or maybe they are and I didn't know it? :D

Hope this helps

---

### Post by Basher101 on 2011-08-08
Thanks for this. Although i use the USB creator for windows from pendrivelinux.com. Havent had a problem yet. I never tried it with wine though...i will do so right away and post the outcome

---

### Post by jerrrys on 2011-08-08
is the **syslinux** package only part of the usb build if installing from a linux machine?  if so, then this would not be an option when loading a usb from a windows machine?  or am i wrong?

---

### Post by gatewayasteroid on 2011-08-08
> **Basher101 said:**
> Thanks for this. Although i use the USB creator for windows from pendrivelinux.com. Havent had a problem yet. I never tried it with wine though...i will do so right away and post the outcome

Yes, they all work, unetbootin as well, but this one is quicker (if you already have a linux machine) ;)

---

### Post by gatewayasteroid on 2011-08-08
> **jerrrys said:**
> is the **syslinux** package only part of the usb build if installing from a linux machine?  if so, then this would not be an option when loading a usb from a windows machine?  or am i wrong?

I'm not sure I understood your question, but the syslinux package is part of the standard Ubuntu repository, altough it's not installed by default.

---

### Post by jerrrys on 2011-08-08
i think i got my answer.  when installing an .iso to usb, using a machine running only windows, this is not a option.  thanks

---

### Post by oldfred on 2011-08-08
Ubuntu will be hybrid.

The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.  :grin:
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

But since flash drives are now larger I do not want just one ISO per flash drive. So I use grub2 to loop mount the ISO and can have as many ISO per flash as it will hold.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

Or you can use a script to automate it.
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by gatewayasteroid on 2011-08-09
> **oldfred said:**
> Ubuntu will be hybrid.

The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.  :grin:
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

But since flash drives are now larger I do not want just one ISO per flash drive. So I use grub2 to loop mount the ISO and can have as many ISO per flash as it will hold.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

Or you can use a script to automate it.
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Thanks for this. I missed that post :)

---

### Post by sikander3786 on 2011-08-09
Here is some further info regarding the Hybrid Images. Importantly, you can create additional partitions in the free space after writing the image to the USB drive.

[http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html](http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html)

---

