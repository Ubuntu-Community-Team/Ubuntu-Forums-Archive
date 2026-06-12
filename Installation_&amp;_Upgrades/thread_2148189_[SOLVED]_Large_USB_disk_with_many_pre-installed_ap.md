---
title: "[SOLVED] Large USB disk with many pre-installed apps"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by yogyakor on 2013-05-24
Our school needs to install LInux as a dual boot with Win7 on some 60 desktops in a computer lab.
We need some specific software on it: LaTex, AMC, Inkscape, etc.

I would like to create a large installer image with all these programs.

How to go about doing that? Can I just use StartUp disk Creator to create a LiveUSB and install all these programs during live session?
When I install to computer the newly added programs are also installed as well?

Thanks, sorry if this has been discussed before.

---

### Post by grahammechanical on 2013-05-24
You can use Startup Disk Creator to install Ubuntu on to a USB memory stick. You must allocate space on the disk for what is called a persistence file. Then when Ubuntu is run from the USB live session you can install applications to the USB memory. This memory stick can then be used to install Ubuntu. The normal installation process will ask if it is connected to the internet but you should still be able to install Ubuntu. It will not install those applications that are not part of the default set of applications. This link might help you:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

work your way down the page until you get to the section: Installing Packages Without an Internet Connection.

That section seems to give advice on what you want to do.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Note the image of usb-creator and see the label Stored in Reserved Extra Space. Make sure that it has a check mark and then use the slider to allocate the amount of extra space. The larger the size of the USB memory stick the better.

Regards.

---

### Post by Tjkhan on 2013-05-24
I tried that months ago but i couldnt. I dont think this work. I would tell u to install individually but 60 desktops.... thats a pain.

---

### Post by C.S.Cameron on 2013-05-24
installing from an image, (.img) is probably the fastest, checkout [https://launchpad.net/win32-image-writer](https://launchpad.net/win32-image-writer) for windows or [http://packages.ubuntu.com/lucid/usb-imagewriter](http://packages.ubuntu.com/lucid/usb-imagewriter) for Ubuntu.

---

### Post by yogyakor on 2013-05-25
Thank you all for your replies. I have found a program called Ubuntu Builder which promises to do exactly what we need, that is create a customized install image. I will give that a go first and see how it turns out.

[https://launchpad.net/ubuntu-builder](https://launchpad.net/ubuntu-builder)

---

### Post by sudodus on 2013-05-25
> **C.S.Cameron said:**
> installing from an image, (.img) is probably the fastest, checkout [https://launchpad.net/win32-image-writer](https://launchpad.net/win32-image-writer) for windows or [http://packages.ubuntu.com/lucid/usb-imagewriter](http://packages.ubuntu.com/lucid/usb-imagewriter) for Ubuntu.

+1

I suggest you make one system as you want it, a prototype. Make an image of it and install from the image.

---

### Post by yogyakor on 2013-05-25
Thank you for your suggestion. I have already started with Ubuntu builder before I saw your post. I will report the results when it is finished.

Meanwhile, a question about using image writer for future projects. Which program should I use to make bootable usb from this custom image?

---

### Post by sudodus on 2013-05-25
You can make the image as well as clone it to a USB drive with ***dd***. But it is nicknamed 'disk destroyer' because it does what you tell it to do without questions. So if you tell it to overwrite your internal hdd ... the margin between miracle and disaster is very narrow. This is one reason why the ***image-writer*** software is offered. It will only suggest writing to USB devices, thus protecting internal drives, and it has a GUI, which is attractive for many people.

So when you have a working installation, you make an image of it, and then clone that image. If you want to save space, you can make a compressed image, but then the cloning process might be slower (if limited by the decompression).

Another alternative is to make a custom image with ***remastersys***. I don't know the details about [ubuntu-builder]("https://launchpad.net/ubuntu-builder"), that you selected, maybe it is doing something similar as remastersys.

---

### Post by yogyakor on 2013-05-25
Thank you for patience in explaining this.

One teacher already has a desired system prototype running on 30GB partition in his laptop. Could we use image-writer to transfer that image to an external HD partition? I suppose another option would be to resize the prototype system partition down to 7GB so it can fit on a USB.

One thing that I don't understand is, how to transfer this image of a prototype system to a computer with running Win7 installation and make it bootable. Does the image-writer software automatically take care of that? What I mean is, once I have an image of a prototype system on external HD or USB, how do I install it? What is confusing for me, it is an image of an already installed system. 

Sorry if my questions seem too obvious, the Ubuntu Builder is not working out for me so I want to make sure I know exactly what I am doing beforehand this time.

---

### Post by sudodus on 2013-05-26
You have to  find out if the image-writer software assumes the  image is an image of a whole drive, or if it works also for a single partition. I am not sure about that.

1. Clone the whole drive

Cloning the whole drive means that you need to clone Windows 7 too, which is possible and legal if you have the right kind of license. (I think that is how many big organisations install Windows. You need to edit the internet address of each computer afterwards, so that the internal network can see a difference between the computers).

This can be done with ***dd*** and ***image-writer***, but it is done more efficiently with ***Clonezilla***, which makes an image of only the parts of the drive, that contain data (and skips free space).

2. Clone a partition

But dd is very flexible, and can be used also to clone a partition. Clonezilla can do it too, but it is more difficult, if the partition is not located in the same place.

- If the Windows 7 systems have developed into individuals, that need to be preserved, or if the licenses are limited to each individual computer, you can keep Windows.

- Make an image of the partition with the desired system prototype, that your colleague has created.

- Create a partition on every computer for the image. Make it exactly the same size (30GB) as the partition of the desired system prototype.

- Clone the image to that partition on every computer.

- Finally you need to install the linux bootloader and make it point to the linux partition, boot into linux and update grub to include also Windows into to the boot options.

-o-

Editing partitions is risky, and you need good backup of all user data.

7GB is no magical size for a USB pendrive unless you already have a lot of 'almost 8GB pendrives'. The prices for 16 GB and 32 GB pendrives are not that much higher than for 8GB pendrives. But USB will make the system much slower than the internal HDD unless you have USB 3.

I reboot the computer from a boot CD/DVD/USB drive, when I edit partitions and clone the internal drive. Unless there is unallocated space available for the new partition, you need to shrink the windows partition, and then you have to shut off windows and have that partition unmounted.

---

### Post by yogyakor on 2013-05-26
Thank you for the detailed explanation. We'll give this a go next week in school and see if we get a usable system. I need to do some research on installing and pointing grub bootloader, but that is surely already well documented elsewhere.

 As I have already mentioned Ubuntu Builder not working for me, I should also say that I got it working meanwhile. It is quite straightforward and easy to use if one wants to make a custom installation image from scratch. I would recommend it for newbies  because of streamlined and simple GUI except for a small bug in the final build process. Here is the relevant bug in the Build file located at

```
/usr/share/ubuntu-builder/extras.
```

[https://bugs.launchpad.net/ubuntu-builder/+bug/1169492](https://bugs.launchpad.net/ubuntu-builder/+bug/1169492).

The solutions and a patch proposed on that thread actually did not work for me, but they pointed to the relevant lines in the file (lines 235-239). Instead of using wildcard * to identify the linux kernel I edited the text file and specified the kernel version I wanted to use. I deleted the other kernels using Synaptic that comes bundled with Ubuntu Builder. After that I got a bootable image.

```
cp -f $FSPATH/boot/initrd.img-3.8.0-22-generic $ISOPATH/casper/initrd.lz 
cp -f $FSPATH/boot/vmlinuz-3.8.0-22-generic $ISOPATH/casper/vmlinuz
cp -f $FSPATH/boot/vmlinuz-3.8.0-22-generic $ISOPATH/casper/vmlinuz.efi
```

 Interestingly, the resultant .iso still wouldn't run in QEMU that comes bundled with Ubuntu Builder, but it ran in Virtual Box. VirtualBox did complain about some parameter not being set properly, but it still ran properly. I will try physical installation on a couple computers tomorrow and see how that turns out. I believe this software has a lot of potential, I hope they iron out the kinks soon.

---

### Post by yogyakor on 2013-05-29
Okay, so Ubuntu-Builder definitely didn't work out for me. I went 'remastersys' route, and it was surprisingly simple.

1. Make LIVE USB flashdisk
2. Install remastersys-gtk + all the programs we need on LIVE USB
3. Run remastersys-gtk from terminal in LIVE USB, set the working folder path to my hard drive, run the Backup option
4. Wait a while, finish, reboot
4. New image runs well in VirtualBox, all settings and programs preserved, still have to try installing on physical comp

---

### Post by sudodus on 2013-05-30
I think it is time for 

Congratulations :KS

---

### Post by yogyakor on 2013-05-31
Thanks, whoever made remastersys is briliant, the app works really fast to create a usable .iso. I've heard about it before, but initially didn't want to try because it has recently been discontinued and official repos for it seem to be broken links.

However, it is really a good project, I hope someone picks up the development.

---

### Post by C.S.Cameron on 2013-05-31
Remastersys has been officially forked:

[http://system-imaging.blogspot.ca/](http://system-imaging.blogspot.ca/)

---

### Post by gordintoronto on 2013-05-31
Another approach would be to prepare an OEM Install. (thanks to cheesemill)

When you boot the installation media, hit SHIFT to get to the installation menu, then hit F4 and select 'OEM Install'. When Ubuntu has finished booting, install the system as usual, you will be prompted for a temporary username and password.

When installation has finished, boot the system and log on with the temporary username and password you created earlier, you can now make any other alterations to the system that you want, for example getting updates and installing extra software. (Corporate wallpaper!) When you're all done, just double-click on the 'Prepare for shipping to end user' icon on the desktop and then shut down the machine. You can take an image of the drive, and install that on as many computers as you want.

---

