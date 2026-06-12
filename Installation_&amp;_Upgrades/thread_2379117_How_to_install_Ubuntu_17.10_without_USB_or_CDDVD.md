---
title: "How to install Ubuntu 17.10 without USB or CD/DVD?"
date: 2017-12-01
forum: Installation &amp; Upgrades
---

### Post by lemmer on 2017-12-01
Hello, I need to install Ubuntu 17.10 on an external SSD, which will connect to my laptop via the only USB 3.0 port. I have no CD/DVD reader/writer either and the rest are USB-C ports and I don't have any adapter.

How do I do that? 
Is there a way to use Ubuntu live in VirtualBox on Win10, connect the SSD and perform the installation there?
I also have an 8 GB SD card and my laptop has a SD card reader.

---

### Post by leunam12 on 2017-12-01
The way I see it you have several options.

1-I don't know about the virtual box trick, it may work.
2-Booting from the SD card may work depending on the computer, some computers don't
boot from an SD card so easy, others have no problem at all. I had Androidx86 installed on SD card
a few years ago and sometimes it booted and sometimes it didn't. Worth a try.
3-A USB hub may work, again, depending on the computer.
4-I think EasyBCD will let you boot from an ISO file, or load it to RAM from the USB. but I am not 100% sure, worth finding out.
5-Install to a partition on the internal hard drive and then clone it to the removable.
6-Maybe borrow a friend's computer.

Ok, I ran out of ideas.

---

### Post by littlefoot505 on 2017-12-01
I wouldn't suggest using a USB hub, as that can slow the data transfer and if it's not an AC-powered one, the devices my not get enough power to work well. You can TRY using the SD card. Using VirtualBox would probably be a craps shoot. I'd recommend using another computer, getting a USB-C to USB-A dongle (I think Amazon has them pretty cheap), or installing it to a partition on your internal HD and cloning it to the SSD. I think you only need a few gigabytes to do a full Linux install, so it wouldn't have to be a big partition.

---

### Post by VMC on 2017-12-01
Here's one idea to try:
[https://www.raymond.cc/blog/how-to-run-livecd-iso-image-file-directly-in-windows/](https://www.raymond.cc/blog/how-to-run-livecd-iso-image-file-directly-in-windows/)

---

### Post by sudodus on 2017-12-01
> **leunam12 said:**
> The way I see it you have several options.

... load it to RAM from the USB. but I am not 100% sure, worth finding out.



It works to boot a live session from a USB pendrive with the boot option **toram**. Then you can unmount all partitions on the USB pendrive and unplug it, which gives you a chance to plug in your USB-SSD. The live system will be in RAM.

This link shows how to add a boot option, [Boot options](https://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by leunam12 on 2017-12-01
> **sudodus said:**
> It works to boot a live session from a USB pendrive with the boot option **toram**. Then you can unmount all partitions on the USB pendrive and unplug it, which gives you a chance to plug in your USB-SSD. The live system will be in RAM.

This link shows how to add a boot option, [Boot options]("https://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808")
This is great, I was wondering if you could do that, just like Parted Magic. Have you tried it? I know Parted Magic freezes sometimes if you don't have enough RAM.

---

### Post by C.S.Cameron on 2017-12-01
You can install using a cell phone:

[https://askubuntu.com/questions/925400/installing-ubuntu-using-cell-phone-only](https://askubuntu.com/questions/925400/installing-ubuntu-using-cell-phone-only)

You can use VirtualBox:

[https://askubuntu.com/questions/857102/install-ubuntu-to-usb-without-cd/857145#857145](https://askubuntu.com/questions/857102/install-ubuntu-to-usb-without-cd/857145#857145)

Sudodus has made some Lubuntu .img files that can be written to disk from Windows using Win32 Disk Imager, (Image Writer).

You can install Ubuntu Live to SD card using UNetbooten or Rufus and use that to install to external SSD.

---

### Post by sudodus on 2017-12-02
> **leunam12 said:**
> This is great, I was wondering if you could do that, just like Parted Magic. Have you tried it? I know Parted Magic freezes sometimes if you don't have enough RAM.

Yes I have tried it, and it works for me. But you need more RAM than if you do not use the **toram** boot option.

---

### Post by C.S.Cameron on 2017-12-02
More detail - Can Ubuntu be installed to the pendrive it was booted from?

[https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

---

