---
title: "How to create snapshot (iso) of current running system to be installed in others"
date: 2020-12-03
forum: Installation &amp; Upgrades
---

### Post by williepabon on 2020-12-03
Hi:
I want to know if there is a utility that allows to create an iso (image) file of your currently running system, so that  you can then, make a start up disk and further install it on other machines. Thanks.

Mi system is:

williepabon@williepabon-Macmini:~$ uname -a
Linux williepabon-Macmini 5.4.0-56-generic #62-Ubuntu SMP Mon Nov 23 19:20:19 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
williepabon@williepabon-Macmini:~$ lsb_release -crid
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

---

### Post by CelticWarrior on 2020-12-03
> [COLOR=#000000]I want to know if there is a utility that allows to create an iso (image) file of your currently running system, so that you can then, make a start up disk and further install it on other machines.[/COLOR]

No, there isn't.

There are tools to "remix" a standard installation ISO and add software and/or different/personalized settings. That's how pretty much all derivatives from a given distro are make.
In any case this isn't done from an already installed system.
An already installed system can, for specific purposes, be "cloned" to an image file (ISO) or directly to another drive. Generally not useful if the cloned drive is intended to be booted in different hardware. It is a valid method to retrieve the OS as is when replacing a system drive but other than that running in the same hardware.

---

### Post by ActionParsnip on 2020-12-03
You can boot to the live USB / CD desktop and make an ISO of the unmounted file system to another file system which is mounted read/write

---

### Post by grahammechanical on 2020-12-03
You might want to research Clonezilla

[https://clonezilla.org/](https://clonezilla.org/)

I have not used it myself. I can give no advice on what mistakes not to make. I am not sure if using Clonezilla to clone a drive with Ubuntu on it will produce a startup disc or just give you an image file of the original disc that you will then need to restore onto the other machines. I know that an image file can be restored onto a USB memory stick but that will not make it a startup disc. 

Regards


[https://clonezilla.org/](https://clonezilla.org/)

---

### Post by SeijiSensei on 2020-12-03
I've cloned the drives of both my laptops using ddrescue ("sudo apt install gddrescue"). I connected a blank SSD drive of equivalent size to the machine with a [USB/SATA converter]("https://www.newegg.com/startech-usb2sataide-usb-to-ide-sata/p/N82E16812200155"), then ran ddrescue.  Replacing the original drive with the clone worked flawlessly, booting up in the machine itself. I suspect the clone wouldn't work in another machine with different hardware, but I've never tried.

---

### Post by hk42 on 2020-12-03
I may be wrong but the use of blockID and also various "MAC" addresses prevents 
what you and I would like to do :-)
Now that most installation media is rw it would already be nice if they were updated.
automatically.
Even to reinstall on the same machine I have yet to see an OS that reminds you
that after each "security" update all your backups are obsolete.
A good reason to limit the size of the root partition.
A tip is to store frequently updated programs and data on a NAS
It works fine in Windows and with the appimage format for Linux.
My NAS is samba only so I'm limited on the Linux side.

---

### Post by williepabon on 2020-12-03
[SIZE=4]**hk42:**[/SIZE]

My thoughts on this project is that  I should be able to create a Live usb stick of my running system, so that if go to a different machine I could be able run it from the stick, or install it on the new machine if I so choose. I'm no developer, but assume that this should be possible.

---

### Post by C.S.Cameron on 2020-12-03
I use Gnome-Disks on a Live USB to make an IMG file of a drive.
I can then flash it to another drive using Rufus, Etcher, Win32DiskImager, Disks, dd or mkusb.
The IMG file can be reduced in size using "truncate" and 7Zip xz compression.

You can create a Full install USB using the IMG file and then put a copy of the IMG file on a NTFS data partition on the drive ready to install on the first available computer.

---

### Post by williepabon on 2020-12-04
[SIZE=4]**C.S. Cameron:**[/SIZE]

Thank you very much for your of ideas on how to do this project. It looks somewhat complicated to me due to my limited technical knowledge. First, I would need to be educated on how to create an *.iso file with gnome-disks. Is it possible to use the app to create an *,iso file of a partition instead of the whole drive (my ubuntu system resides in a partition on a Mac hard drive)? As I said previously, my idea (if this is possible) is to have an *.iso (that is essentially a snapshot) of my current system, use this file with the start up disk creator tool from ubuntu to create a Live (bootable) usb stick that I could use to, either run it or install in another machine. I don't know if this could be done with Ubuntu, but I'm assuming that it may be possible. Thanks again for your insights.

---

### Post by Dennis N on 2020-12-04
Have a look at **isomaster**:

> ISO Master is an open-source, easy to use, graphical CD image editor for Linux and BSD. Basically you can use this program to extract files from an ISO, add files to an ISO, and create bootable ISOs - all in a graphical user interface. It can open both ISO and NRG files but can only save as ISO.

I've only used it to add files to an iso. It may or may not be what you are looking for. It's in the Ubuntu repositories.

---

### Post by sudodus on 2020-12-04
I have some installed systems in external drives (USB and eSATA), and they are portable between computers. So it should work to do what you want. You can even move your current drive to the new computer (connect it internally or via an external box) and test how it works before you start cloning.

This means that a *cloned* drive will probably work for you too, if you use the built-in linux drivers (and if necessary install a suitable proprietary driver for graphics and/or wifi if necessary in the target computer). And the cloning can be done via an image file ([FONT=Courier New]**filename.img**[/FONT]), or a compressed image file, or a Clonezilla image (which is a directory with several compressed files).

There are more details in the following links,

[Installed Ubuntu systems are portable](https://askubuntu.com/questions/1032294/clonezilla-disk-to-disk-clone-from-hdd-with-ubuntu-to-hdd-with-windows-on-new/1032401#1032401)

[I would use Clonezilla](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248#958248)

---

### Post by C.S.Cameron on 2020-12-04
> **williepabon said:**
> [SIZE=4]**C.S. Cameron:**[/SIZE]

First, I would need to be educated on how to create an *.iso file with gnome-disks. Is it possible to use the app to create an *,iso file of a partition instead of the whole drive (my ubuntu system resides in a partition on a Mac hard drive)? 

I am talking about using a .img file like Disks, (or dd), creates, not an .iso file. most Live USB creators can work with either. The .img file is a clone image of the OS's disk complete with boot partitions.

Creating an .img of just the OS partition does not make a bootable drive. you would need install GRUB separately after cloning Ubuntu from the Mac to a USB drive of close to your preferred size.

One method that has worked for me is to create a Persistent USB using **mkusb**, then delete the ISO9660 OS partition and writable partition and use GParted to copy/paste a clone of your OS partition into their place. You can then copy the OS's grub.cfg file to the USB's usbboot /boot/grub/ partition and editing as required.

It might be helpful to read: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

The answer "Install Ubuntu from a Pre-built Image File" and the answer by sudodus on that page use an .img file similar to what I suggest: [https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz)

---

### Post by williepabon on 2020-12-10
[SIZE=4]**CS Cameron:**[/SIZE]

Thanks again for your suggestions and ideas on how to do this project. From the information that I've gathered on these threads, I have to say that creating a live usb stick of a running Ubuntu session goes above my expertise. It seems that there is not an easy way (in layman's terms) to do this with Ubuntu. Maybe this project has been tried in other distros. I will keep looking. So, I will consider this thread to be closed. Thanks.

---

### Post by yancek on 2020-12-10
The first piece of software I am aware that did what you want is remastersys.  It was a one man project and got to be too much so the developer stopped.  You would simply install remastersys on your running Ubuntu (or some derivatives) and then run it to create a bootable iso file.  There were several optons and I believe it would include the ubiquity installer.

Other similar software which was and may still be available:  Pinguy Builder and Systemback

Looks like Systemback is still available, see the link below to determine if that is what you want.

[https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10](https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10)

---

### Post by williepabon on 2020-12-13
**[SIZE=4]yancek[/SIZE]**:

Thanks for your suggestions. I investigated both (remastersys, systemback) and looks like they are not actively maintained. I don't think like I will pursue any of them. Anyway, I appreciate your help on this project.
wp

---

