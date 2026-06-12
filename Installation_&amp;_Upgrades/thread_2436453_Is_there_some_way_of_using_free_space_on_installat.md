---
title: "Is there some way of using free space on installation thumb drives for other files?"
date: 2020-02-06
forum: Installation &amp; Upgrades
---

### Post by raphaell2 on 2020-02-06
Is there some way of using the free space on Ubuntu installation thumb drives to store other files without making a mess of the whole thing in the process? I think I remember vaguely that long ago, there was a software package that allowed you to customize your installation media, but apparently it was abandoned or at least no longer properly maintained and became a collection of bugs and compatibility issues. 

I'm not thinking of all that *many* files - mainly a few text files where I keep notes about what I usually do immediately after a fresh install, and perhaps a few images that can serve as desktop backgrounds. Any ideas?

---

### Post by hk42 on 2020-02-06
One way I like is to customize my installation with apt on the command line and store a copy of my history file.
A copy of firefox short cuts and passwords would be nice too.

---

### Post by dragonfly41 on 2020-02-06
Would it not be easier to mount a second USB flash drive for such notes, if you have a USB hub or spare USB port?
But if you do want it in one flash drive, search "persistent LiveUSB Ubuntu". Here is one writeup.
[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

Another idea is to keep notes in Google drive and keep a note of the url to paste into your LiveUSB browser (usually Firefox).

---

### Post by raphaell2 on 2020-02-06
> **dragonfly41 said:**
> Would it not be easier to mount a second USB flash drive for such notes, if you have a USB hub or spare USB port?


Sure, I just somehow don't like the idea of wasting space.

> 
But if you do want it in one flash drive, search "persistent LiveUSB Ubuntu". Here is one writeup.
[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

Another idea is to keep notes in Google drive and keep a note of the url to paste into your LiveUSB browser (usually Firefox).


Thank you!

---

### Post by CelticWarrior on 2020-02-06
Here's another idea:

[Multisystem]("https://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/") is a French tool for making a multi-distro live/installer USB stick but it can be used to create a single live/installer as well ;).
The advantage of using it is that it extracts and saves each ISO in its own folder without touching the stick's file system (FAT32 is mandatory in this case). This leaves all the remaining space available for use like any regular USB mass storage. Just create one or more folders and save files there as usual.

I use it frequently not only to have several installer in a single 32GB stick and also include some video files (for testing codecs, etc.), text files with some PPAs, useful commands, etc.

---

### Post by raphaell2 on 2020-02-06
@**dragonfly41**, thank you again! I've now tried the method from the article you linked, and after a brief moment of getting used to it, it works really well!

@**CelticWarrior**, thank you, too! I will try your method next.

---

### Post by raphaell2 on 2020-02-07
@**CelticWarrior**, sorry - I've now tried Multisystem, and once it had installed Grub to the thumb drive on which I tried it, it simply wouldn't mount anymore, so I couldn't put any other files on it. I had to reformat it to be able to use it again.

---

### Post by CelticWarrior on 2020-02-07
> **raphaell2 said:**
> @**CelticWarrior**, sorry - I've now tried Multisystem, and once it had installed Grub to the thumb drive on which I tried it, it simply wouldn't mount anymore, so I couldn't put any other files on it. I had to reformat it to be able to use it again.

Something wrong happened. I have 2 sticks working exactly as I described and both with RW permissions in Ubuntu or Windows.

---

### Post by C.S.Cameron on 2020-02-08
A thumb drive made using **UNetbootin** is FAT32 and can be read or written to with Linux, Windows or that Apple OS.
It can be read but not written to while booted.
A drive made with **mkusb** can have a NTFS data partition and be read and written to with Linux or Windows and written to while booted.

Drives made with Startup Disk Creator and Etcher are ISO9660 and are read only.

---

### Post by sudodus on 2020-02-08
**mkusb version 12, mkusb-dus**

Standard [mkusb](https://help.ubuntu.com/community/mkusb), version 12 alias mkusb-dus can make persistent USB boot drives from iso files of all current versions of Ubuntu and the Ubuntu family flavours as well as from Debian live versions 8, 9 and 10. This method gives you two alternatives to store data:

- In the persistent live system (stored in the 'casper-rw' partition you can not only store personal data files, but you can also install program packages (that persist after shutdown and reboot).

- In the 'usbdata' partition with the NTFS file system you can store data, that can be written and read by both Ubuntu and Windows.

Edit: This 'usbdata' partition is the first one, so it can be read also by old Windows systems.

**mkusb-plug**

A new version, [mkusb-plug](https://help.ubuntu.com/community/mkusb/plug), can create persistent live drives of Ubuntu 19.10 and Debian 10 (and newer versions). But what can be relevant here, it is also possible to create a 'regular cloned' live only boot drive with a partition for storage 'behind' the cloned image and that way use the whole drive. You can select between the file systems NTFS, exFAT and FAT32 for this **usbdata** partition.

This way it is **possible to get the storage, that you want, also when making USB boot drives from iso files of other linux distros**, as long as it is created from a hybrid iso file, and most current linux distros provide hybrid iso files.

Edit: This 'usbdata' partition is not the first one, so it cannot be read by old Windows systems, but current Windows 10 can read and write there.

---

### Post by raphaell2 on 2020-02-08
Thank you!

---

