---
title: "Bootable USB with Ubuntu 12.04"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by Brad wilkinson on 2015-02-20
I have followed the instructions [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) and created a bootable USB stick on a 4Gig partition on a 8Gig Kingston DataTraveller 100G3. Also there is a swap partition on the usb as well.

When I go to boot the PC, I interupt the boot, go to the BIOS and select the boot device to be the USB stick. It goes ok, comes up with the first splash screen (little keyboard and person at the bottom), then goes to the Ubuntu with little dots usnder it screen. All seems to be going well.

Then it drops to a text screen with the following:

```
Busybox v1.18.5 (blah blah) built in shell
Enter "Help" for list of commands

(initramfs) unable to find a medium containing a live file system
```

The PC is a Gigabyte 990FXA-UD3 with a Phenom II 1055, 8Gig ram, and runs Ubuntu 14.04 ok except it doesn't recognise the USB 3 ports on the machine. I'm plugging the USB drive into a USB 2 port.

Can anyone tell me how to get this to run so I can dual-boot into 12.04 to see if the USB 3 works or not?

---

### Post by grahammechanical on 2015-02-20
I cannot offer suggestions about the USB live session problem. Logically speaking if Ubuntu 14.04 is not recognising USB 3 ports then 12.04 should not recognise them either.

Hardware modules are part of the Linux kernel. Every release of Ubuntu gets later Linux kernels with later Linux firmware or hardware enablement stack. Ubuntu Long Term Support releases are kept up to date with kernel progress by having "point" releases during the first two years of its support period.

The latest Ubuntu 12.04 is 12.04.5 and that should have the same Linux kernel and firmware as 14.04 when it was first released. So, if regular updating of 14.04 has not fixed this problem, I do not see how installing 12.04.5 will fix it.

Ubuntu 14.04 is right now receiving its second "point" release. Moving on to 14.04.2. I suggest downloading the latest 14.04.2 ISO image and seeing if that live session detects USB 3 hardware. If it does then you will have to make a decision.

The new 14.04.2 ISO image has the newer Linux kernel and firmware. Installed versions of 14.04 will move on to 14.04.2 during an normal update but will not get the newer kernel and hardware enablement stack unless the user accepts the offer to upgrade. There is a reason  for this.

The Linux kernels in 14.04 and 14.04.1 are supported with security fixes until April 2019 but the kernels in 14.04.2 and 14.04.3 and 14.04.4 will only be supported until the August after the release of Ubuntu 16.04.

There will be a 14.04.5 release and the kernel in that will be supported until April 2019. 

So, the choice is - Stick with the 14.04.1 kernel and hardware enablement stack for the life of 14.04 or upgrade to each point release enablement stack until we can upgrade to 16.04 or continue with 14.04 moving on the 14.04.5.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by Brad wilkinson on 2015-02-20
hello Graham,

The reason I am trying to load 12.04 to see if it will support USB3 is because on my last PC (who's motherboard failed, hence why I've put together the new one) recognised and used correctly the PCIe add in board USB3 ports correctly while running 12.04

If you look in my last thread on these forums, you will see I have posted a bunch of details on my efforts to get USB3 running on my current machine, but with a disturbing lack of replies from the community.

I understand that the reason that I cannot run USB3 on this machine is almost certainly something simple I have overlooked or done wrong, but since no one is offering suggestions as to what I need to do to fix it, I'm pretty much stuffed.

Which is sad as I had just go into making videos for youtube, and I really don't want to have to transfer ~3Gig files from my camera to PC over USB2.

---

### Post by C.S.Cameron on 2015-02-20
I understand that Ubuntu 12.04 requires 5GB of disk space.
I have had the same error message due to a bad download.
Check your iso with MD5SUM.

---

### Post by Brad wilkinson on 2015-02-23
So I reformatted the drive with W95 FAT32 (LBA) (Bootable) at 6.7 Gig, and left a 1Gig swap partition.

I checked the MD5SUM of my .iso download, and it matches the MD5SUM on the Ubuntu website.

I used the startup disk creator that comes with 14.04.

I then rebooted and got exactly the same outcome as I listed in my original post.

Anyone have any other suggestions?

---

### Post by efflandt on 2015-02-24
Since you seem to be having USB issues, do you have a DVD writer, to try booting the live/install iso from DVD?

---

### Post by C.S.Cameron on 2015-02-27
Have you tried the Flash drive on another computer?

---

### Post by sudodus on 2015-02-27
> **Brad wilkinson said:**
> ... a bootable USB stick on a 4Gig partition on a 8Gig Kingston DataTraveller 100G3. Also there is a swap partition on the usb as well.

I have such a pendrive, and it works for me. It should need no swap.
> 
When I go to boot the PC, I interupt the boot, go to the BIOS and select the boot device to be the USB stick. It goes ok, comes up with the first splash screen (little keyboard and person at the bottom), then goes to the Ubuntu with little dots usnder it screen. All seems to be going well.

Then it drops to a text screen with the following:

```
Busybox v1.18.5 (blah blah) built in shell
Enter "Help" for list of commands

(initramfs) unable to find a medium containing a live file system
```

The PC is a Gigabyte 990FXA-UD3 with a Phenom II 1055, 8Gig ram, and runs Ubuntu 14.04 ok except it doesn't recognise the USB 3 ports on the machine. I'm plugging the USB drive into a USB 2 port.

Can anyone tell me how to get this to run so I can dual-boot into 12.04 to see if the USB 3 works or not?

> **Brad wilkinson said:**
> hello Graham,

The reason I am trying to load 12.04 to see if it will support USB3 is because on my last PC (who's motherboard failed, hence why I've put together the new one) recognised and used correctly the PCIe add in board USB3 ports correctly while running 12.04

If you look in my last thread on these forums, you will see I have posted a bunch of details on my efforts to get USB3 running on my current machine, but with a disturbing lack of replies from the community.

I understand that the reason that I cannot run USB3 on this machine is almost certainly something simple I have overlooked or done wrong, but since no one is offering suggestions as to what I need to do to fix it, I'm pretty much stuffed.

Which is sad as I had just go into making videos for youtube, and I really don't want to have to transfer ~3Gig files from my camera to PC over USB2.

It is often difficult to make a computer work with USB 3, maybe not standardized enough yet.

> **Brad wilkinson said:**
> So I reformatted the drive with W95 FAT32 (LBA) (Bootable) at 6.7 Gig, and left a 1Gig swap partition.

I checked the MD5SUM of my .iso download, and it matches the MD5SUM on the Ubuntu website.
Good :-)> 
I used the startup disk creator that comes with 14.04.

I then rebooted and got exactly the same outcome as I listed in my original post.

Anyone have any other suggestions?

You can try another tool to make the USB bootable: [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb")  in Windows.

But there might also be some other problem. What graphics chip/card is it?

Did you try the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset**?
You can also try the boot option **text** (which boots to a text screen) and avoids some of the problems due to problems with the driver for your graphics chip.

---

