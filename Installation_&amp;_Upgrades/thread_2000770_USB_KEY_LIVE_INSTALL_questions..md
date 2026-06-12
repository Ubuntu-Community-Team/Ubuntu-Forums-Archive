---
title: "USB KEY LIVE INSTALL questions."
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by faze1337 on 2012-06-10
I plan on installing ubuntu 12.04 on a usb key for the sake of having an operating system at my finger tips but I was wondering if I could install programs on the live usb key of ubuntu like Skype and a torrent program and various Google programs if supported if so is there anything I need to do or any advice for a better path to take? It'll be on a 32gig usb key so space isn't a huge issue. If I don't respond here please private message me so I get an email to check back here thanks.

---

### Post by codemaniac on 2012-06-10
Hello faze1337 ,

Welcome to the UbuntuForums !!

You can go for two options .

1. Make a live Ubuntu usb with persistence .That would remember all your data , configurations and installed packages on next boot .

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

2.Go for a normal dedicated installation as you have a good amount of space on your flash drive .

---

### Post by faze1337 on 2012-06-10
What would be the more stable/long term option? Depending on difficulty I haven't touched ubuntu in years I just have alot of free time now

---

### Post by codemaniac on 2012-06-10
I would go for option 2 .

---

### Post by wilee-nilee on 2012-06-10
With 32 gigs I would do a full install.

The ISO load with a persistent is really designed for short use, it has its own set of problems not associated with a full install.

Updates are one, you don't want any kernel updates, the ISO is still being used as a read only.

The persistent file can fill up, and can't be cleaned really.

A full install will run like a install on a internal drive, although a little slower. Although I had one this way for awhile it was as fast as the internal on  a netbook basically. I suspect it depends on the quality of the usb stick.

---

### Post by faze1337 on 2012-06-10
How would I go about that plug the key in and reboot choosing the key as the partition? (its been years since I've done this stuff sorry)

---

### Post by wilee-nilee on 2012-06-10
> **faze1337 said:**
> How would I go about that plug the key in and reboot choosing the key as the partition? (its been years since I've done this stuff sorry)

Boot a live cd plug the stick in, and use a custom install, format it there to a ext 4 set the mount as / and install. Make sure in the custom that grub is pointed at the mbr of the stick.

---

### Post by codemaniac on 2012-06-10
It would be a normal ubuntu installation , but make sure that you choose the correct device (your 32 gb flash) and not messing up your internal hdd .

From the live cd environment you can launch gparted and create the necessary partitions as suggested by wilee-nilee above , before going ahead with the installation .

The rest of the journey would be a normal Ubuntu install .

[https://help.ubuntu.com/11.04/installation-guide/i386/index.html](https://help.ubuntu.com/11.04/installation-guide/i386/index.html)

---

### Post by sudodus on 2012-06-10
If you want a long term solution, a full install is the best, as explained by previous posts.

1. If you want full portability, you should avoid proprietary drivers (for example the drivers for graphics and wifi).

2. A draw-back is that updating is much slower than on an internal hard drive. I think it is because a large number of small files are written, and this is very inefficient on USB pendrives compared to internal drives. So I have an internal drive, that I use at home, and that I can easily clone to and from the pendrive. And I do big updating jobs on the internal drive (it is much faster also taking into account the cloning). This also works as a backup system.

3. In order to avoid corrupting the file system, you should have a USB pen-drive with a light emitting diode. Then you can see when it is working and you can avoid pulling it out or switching off the computer too early.

I have such a system (Lubuntu with xubuntu-desktop added) and it works fine. Often the read/write speed is slower than the limits of USB 2.0, so choose a pendrive with high speed. I use a USB 3 pendrive booted from a USB 2.0 port.

---

### Post by faze1337 on 2012-06-10
It's a "key shaped" usb 2.0 key from Hong Kong ebay lol but transfer speed is 20-30mbps

---

### Post by sudodus on 2012-06-10
I wanted to add: if you install to a pendrive, you should disconnect all other drives except the live one (source) and the one to be install onto (target). If you have internal hard drives connected, the installer 'wants to' include them into the boot environment, which is bad, if you want to use the pendrive on other computers.

---

### Post by sudodus on 2012-06-10
> **faze1337 said:**
> It's a "key shaped" usb 2.0 key from Hong Kong ebay lol but transfer speed is 20-30mbps
If it is 20-30 MB/s both read and write I think it is good enough :-) But still, you might find it slow writing many small files.

---

### Post by faze1337 on 2012-06-10
Not sure but I can easily let it work overnight but I doesn't have a light on it and ill be installing from a windows based laptop if that makes a difference?

---

### Post by sudodus on 2012-06-10
> **faze1337 said:**
> Not sure but I can easily let it work overnight but I doesn't have a light on it and ill be installing from a windows based laptop if that makes a difference?
If you boot a live Ubuntu system from a CD or USB drive, it does not matter what system it is on the computer hard drive.

It is more complicated to disconnect the internal drive from a laptop than from a desktop/tower computer, but it is not too difficult.

But if you don't want to disconnect it, you can be very careful, when selecting the system partition and where to put grub. Select the manual selection of partitions, choose 'Something else'. Grub should be put onto the head of the target USB pendrive (not to a partition). If the target drive is /dev/sdc, grub should be written to /dev/sdc (not /dev/sdc1, /dev/sdc2 ...).

And after installation, you might want to change the grub settings (because it will probably identify windows on the internal drive, and make a boot option for it), unless of course, you want to have the windows option there.

---

### Post by wilee-nilee on 2012-06-10
If you don't want windows in the grub menu on the boot from the usb, just remove the os-prober, once you are installed run in the install.
```
sudo apt-get remove os-prober
```
Then run to update grub.
```
sudo update-grub
```

---

### Post by faze1337 on 2012-06-10
Ok now I'm getting a little confused. When installing it'll know the drive letters correct I just have it install to the root of the usb key correct?

---

### Post by wilee-nilee on 2012-06-10
> **faze1337 said:**
> Ok now I'm getting a little confused. When installing it'll know the drive letters correct I just have it install to the root of the usb key correct?

When you boot the live cd and have the stick plugged in run this command to identify the stick.

```
sudo fdisk -l
```You will see the internal drive and the stick listed. You are looking for the first three letters of the stick, it will probably be sdb.

When you get to the something other option in the install and open that gui you will have a drop down giving you choices of where grub goes. If the stick is sdb choose the sdb option. No partition numbers here.

Before any of this really make sure you have a recovery or install disc of windows. If this is W7 you can make one in the windows backup and recovery there is a option there.

This is a tool you must have anyway, it allows you to make repairs and run a terminal for windows, for reloading the internal HD's mbr if ever needed amongst other repairs if ever needed.

If you decide to use gparted as suggested on the live cd to make the ext4 partition on the stick that will tell you the sticks letters.

You will have to use the  custom install no matter what here.

---

### Post by faze1337 on 2012-06-10
Alright the usb key isn't here yet but I think I got the idea ill attempt it when it arrives for now thanks.

---

