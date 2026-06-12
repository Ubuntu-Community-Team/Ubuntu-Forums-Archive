---
title: "Installing OS on USB question"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by jones0610 on 2012-10-31
I apologize for asking such a silly question.  I fully expected to see the answer in the install doc(s) or the FAQ.  But if it's there I couldn't find it. 

Installed 12.10 on a USB and the trial experience went fine as I expected that it would.  It is my desire to run the "real" Ubuntu OS (not just the trial iso) via a USB so that I can carry it around rather than installing it on a desktop.  Sort of like Tails which is what I've been using.

There doesn't seem to be a way to do that though.  

To be honest, I didn't actually try hitting the install button since I am on someone else's computer and didn't want to wipe out their OS.  So.....  does Ubuntu running from the USB trial .iso even know that there is a USB stick there and if so, does it offer up the USB drive option for installing there?  If not, I'm sure there is a way to do this...  perhaps someone could pass along how?

Many thanks in advance.

---

### Post by 8grod on 2012-10-31
It isn't a "trial" version. The OS on your drive is a base install with the most common and necessary packages and hardware support. It's a fully-fledged OS.
If your flash drive is big enough, you can install extra packages. I've been doing that with a minimal Ubuntu install on a 2 gb stick.

Granted, I'm running piratebox on it, so you may get different mileage than I do.

The problem I see is if you're going to be using it on a wide range of machines that you may run into hardware issues. For example, I've learned that different broadcom drivers don't like to play together.

Have you perhaps considered something like QEMU? I've done that before and it's an overall consistent experience.

---

### Post by jones0610 on 2012-10-31
Perhaps I'm confused.  Downloaded the Ubuntu iso and installed it on the USB stick per the installation instructions.

Rebooted and Ubuntu did come up and seems to operate as though it's the real, full meal deal OS.  But...  any changes I made (setting up Thunderbird, wireless, etc) were not saved.

I can't recall exactly but it seems like I was presented with two choices:  run the "trial" version or install Ubuntu.  I did not want to install Ubuntu on a laptop that isn't mine....  I just want to be able to run it on any computer that will boot my USB stick.

Your HW compatibility comments are duly noted.  I've been running Tails from a USB stick in my pocket for years and mostly without problems.  I like Ubuntu and would like to have a more fully implemented *NIX distro available.  Tails is mostly aimed at stealth users.

I have a 16 GB stick so space is not an issue.  But installing per the web site instructions does NOT create a persistent OS install. It's operates as a read only distro.

---

### Post by 2F4U on 2012-10-31
> Rebooted and Ubuntu did come up and seems to operate as though it's the  real, full meal deal OS.  But...  any changes I made (setting up  Thunderbird, wireless, etc) were not saved.

You are running a liveUSB at the moment. This is nice for testing things before attempting to install, but Ubuntu is not installed on your machine.

I don't know which instructions you followed, but on both the instructions for Windows and those for Ubuntu the screenshots show the persistence options.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

Of course, it doesn't automatically create a USB with persistence.

---

### Post by jones0610 on 2012-10-31
Followed:
[http://www.ubuntu.com/download/help/...ick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
[]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")
This is exactly the problem I am asking about:
Of course, it doesn't automatically create a USB with persistence.

LiveUSB is running perfectly.

But when I reboot, all of the changes I made while running Ubuntu are lost.

I do not want to install Ubuntu onto a HDD.  I want to install it on a USB so that I can carry it around and run it on various computers.

I know that this should be possible since I am running Tails from a USB this way (also a *NIX "distro")

My question is: How do I install Ubuntu on a USB and not on a HDD?

---

### Post by darkod on 2012-10-31
And the answer is simple: The same way as you would install on a hdd only you specify the usb stick as destination. It will be listed together with all disks as a possible destination.

It's best to use the manual install method, that way you have full control where it gets installed, and most important, where does the bootloader go. You need the bootloader on the usb stick so that you can boot it on another computer.

So, for example, if you have only one hdd and it's /dev/sda, and the usb stick is /dev/sdb, you will install ubuntu on /dev/sdb creating the partitions you want on it, and tell it to install the bootloader on /dev/sdb too.

---

### Post by nothingspecial on 2012-10-31
> **darkod said:**
>  You need the bootloader on the usb stick so that you can boot it on another computer.



Also, if you don't install the bootloader on the stick and install it on your computer's internal drive, the computer will not boot without the stick plugged in, so it is very important you get that bit right.

---

### Post by jones0610 on 2012-10-31
Much obliged Darkod and caution noted.

I was certain that the process was simple.. thanks for illuminating me.

I don't happen to have any available machines that can boot off of a CD so I booted the iso off of USB.

Wasn't sure if I could do the full install Ubuntu on the same USB that LiveUSB is running from.  It has plenty of room and the Live USB stuff is running from RAM anyway.  Don't know, but I guess I'll find out if the new bootloader will overwrite the current USB bootloader.  Guess I don't see why it wouldn't since it will apparently happily stomp on the Win7 host's boot loader :)

My ideal would be to boot off of a DVD and then install Ubuntu on a USB but unfortunately I don't have any configuration available to support that.

---

### Post by oldfred on 2012-10-31
Just to add a bit of info.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

With my 16GB flash drive I installed full Ubuntu to a 8GB / partition and left the rest as data. No swap (but I have 4GB of RAM). You also want to change some settings to reduce writes similar to the settings for SSDs.

Full install of 12.04 to USB device C.S.Cameron post #5 Includes a FAT partition so some data can be copied from a Windows machine. Windows formatted data partition must be first.
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

It does not have to be encrypted BIOS based system as that does add a level of complication:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. Process is similar but without LVM, screens will look a bit different.
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

You have to use Something Else or manual install to get the combo box on where to install grub2's boot loader. Combo box at bottom of partitioning screen and choose external drive/flash drive'MBR,  not any partitions.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

