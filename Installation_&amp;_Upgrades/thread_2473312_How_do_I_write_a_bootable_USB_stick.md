---
title: "How do I write a bootable USB stick?"
date: 2022-03-31
forum: Installation &amp; Upgrades
---

### Post by drkirkby on 2022-03-31
I have Ubuntu 20.0.1 (I think) on a Dell 7920 (2x26 core CPUs, 368 GB RA. Iinstall a slightly later 20.04.4 on another on a Sun Ultra 27.. I have downloaded a 20.04.4 iso image, and are trying to write it to a USB stick. I thought this would be a simple case of using dd, but so far this as been running for about 20 hours, and not completed. I don't know whether it just needs to run longer, or it is stuck, and I should give up, and use another method. 

 I've stuck in a USB stick. I run
```
# fdisk -l > a
Then inserted the USB stick
# fdisk -l1 > b
Now, comparing these two files, I see 
# diff a b

```
and see 

```

root@canary:/home/drkirkby/Desktop# diff a b
223,229d222
< 
< 
< Disk /dev/sdd: 64 MiB, 67108864 bytes, 131072 sectors
< Disk model: SK6238A BLoader 
< Units: sectors of 1 * 512 = 512 bytes
< Sector size (logical/physical): 512 bytes / 512 bytes
< I/O size (minimum/optimal): 512 bytes / 512 bytes
```

[B]I thought this indicated the USB stick was /dev/sdd, so I typed.
[/B]

```
 # dd if=ubuntu-20.04.4-desktop-amd64.iso of=/dev/sdd
```
which I thought would write the 20.04.04 image to the 64 MB USB stick. But around 20 hours later, the command has not completed. It's possible it's a USB 2 memory stick, not a faster USB 3.0, but even so, I would have expected it to complete within 20 hours.

Am I doing something fundamentally wrong? Am I being impatient?

---

### Post by ajgreeny on 2022-03-31
There is no version** Ubuntu 20.0.1** so you need to be sure what you already have before we can give you better advice.

In your current version run command **[B]lsb_release -a**[/B] and/or ***inxi -Fzx*** which will tell us what you have at the moment.

To write a boot disk of a live Ubuntu version I now find [mkusb]("http://https://help.ubuntu.com/community/mkusb") the quickest and best way, though ***dd*** should have worked and certainly should not take as long as your attempt did.

There is also a package in the repos called usb-creator-gtk (or usb-creator-kde) which some users say works fine though I've not tried it for many years.

What filesystem is on the usb disk?  It must be fat32 for a successful live usb to work.

---

### Post by drkirkby on 2022-03-31
Thank you. I'm running Ubuntu 20.04.4 LTS, so it is the same as I downloaded, which is rather stupid, as it means I have downloaded the same file twice. 

I've no idea what was on the USB stick, and in any case it would have been destroyed by my use of dd, which is still running. But does the ISO image not overwrite whatever was on the USB stick, making it irrelevant what was there in the first place? I have another USB stick, so if this one is ruined it is not the end of the world. 

I recall using dd to create the install disk for this system. I probably used a Solaris machine for that. It took a long time on that, but I don't think more than a day. So perhaps dd is just a very slow way of doing it, or maybe one needs to add some options (block size etc) to dd to speed it up. 

I was not sure what the device file to use. If it's not /dev/sdd, then that could explain it. I''ll look at the solution you suggested. 

Dave

---

### Post by ubfan1 on 2022-03-31
64MB is way too small, did you think it was a 64GB stick?

---

### Post by ajgreeny on 2022-03-31
> **ubfan1 said:**
> 64MB is way too small, did you think it was a 64GB stick?
I'm so stupid !!!

I read that as 64GB, not 64MB, and ubfan1 is correct, if the USB really is 64MB you will get nowhere with it.  The USB needs to be at least 4GB I think, but all mine are far larger so I have not though about this much when using them for installation.

And never mind that strange way you figured out which disk is which, just use ```
sudo fdisk -l
``` instead and show us the total output you see.

---

### Post by SeijiSensei on 2022-03-31
Ubuntu has two graphical programs to write a bootable USB.

If you're using Kubuntu or another KDE spinoff like Neon, run
```
sudo apt install usb-creator-kde
usb-creator-kde &
```

For other versions of Ubuntu use
```
sudo apt install usb-creator-gtk
usb-creator-gtk &
```

I use the KDE desktop so I've only ever run usb-creator-kde, but it's been very easy to use. I suspect the GTK version will work similarly.

---

### Post by TheFu on 2022-03-31
> **drkirkby said:**
> Am I doing something fundamentally wrong? Am I being impatient?

The imaging time is almost always tied to the USB write performance.   How long does it take to copy 1G?  The server ISO is less than 1G.  Less than 5 minutes is typical. On faster USB3 storage, 1-2 min is common.

> **drkirkby said:**
> 
 # dd if=ubuntu-20.04.4-desktop-amd64.iso of=/dev/sdd

You can use any program that moves bytes from A ---> B without molesting them.  There are lots of those. I switched to using cp a few years ago rather than dd, since dd can be slow if the bs= option isn't set to a reasonable value.  cp seems to always work.

I don't know what an Ultra 27 is. Had multiple Ultra1/140 workstations over the years before the job changed to a different Unix vendor. SPARC and Intel are both little Endian, so you don't need to swap the bytes like on an Irix system.

So, I'd use
```
$ sudo cp [COLOR="#FF0000"]/path/to/[/COLOR]ubuntu-20.04.4-desktop-amd64.iso /dev/sdd
```
assuming that I was 100% positive that sdd was the correct device ***this boot***. At each boot, device names can move around. It is a kernel discovery timing thing. Not guaranteed what any device name will be from boot to boot.

The cp / dd / cat / more / less command used to move the bytes to /dev/sdd will also depend on sdd actually in working order. 

Flash storage, especially cheap flash storage, will wear out after less than 1000 write cycles to the cells. More expensive flash storage will handle wear leveling automatically which can make for a much longer life time.  The entire device is made up of virtual cells and there's no way for the OS or humans to know which cell is assigned as a sector inside the device. Based on the wear leveling controller, cells will be used and presented as the next contiguous sector to the OS and all storage drivers.  SSDs do this too - REALLY well.  More costly SSDs will have more over-provisioning, storage cells with much higher write durability, and faster, smarter, controllers to present these virtual cells to the OS.

If the flash drive can be formatted (not needed for this effort) and files can be copied to it, then I'd think most of the storage on it will have some write cycles remaining. If it doesn't accept a format + cp of a 500MB file, then I'd assume the flash to be bad and put it into my "to be shot" pile for the next outing to a gun range.

---

### Post by him610 on 2022-03-31
If you are using *buntu, maybe you consider using *mkusb* - [https://ubuntuforums.org/showthread.php?t=1958073]("https://ubuntuforums.org/showthread.php?t=1958073")
The developer/maintainer, sudodus, periodically updates the tutorial so don't be put off by the original date. 
It works very well for just about anything one wants to do with a USB thumb drive. It is the only utility I use to manage and write to USB thumb drives.

---

### Post by Impavidus on 2022-03-31
> **drkirkby said:**
> Thank you. I'm running Ubuntu 20.04.4 LTS, so it is the same as I downloaded, which is rather stupid, as it means I have downloaded the same file twice.
Not necessarily. If you installed it as 20.04.1 and kept up to date with your regular upgrades, it must have upgraded to 20.04.4 by now.

I think the smallest usb drive I've ever seen was 128MB, and that must have been close to 20 years ago. How old is that drive? It may be broken (and is definitely way too small). Even on an old usb 1 connection you should be able to fill all of it in less than a minute. It should have given you an error for no space left on device.

---

### Post by ajgreeny on 2022-04-01
> **Impavidus said:**
> Not necessarily. If you installed it as 20.04.1 and kept up to date with your regular upgrades, it must have upgraded to 20.04.4 by now.

I think the smallest usb drive I've ever seen was 128MB, and that must have been close to 20 years ago. How old is that drive? It may be broken (and is definitely way too small). Even on an old usb 1 connection you should be able to fill all of it in less than a minute. It should have given you an error for no space left on device.
Just for the full picture, the only big difference between a 20.04.1 and a newly installed 20.04.4 will be the kernel series used; 20.04.1 came with the 5.4.0-# series, now at 5.4.0-107, but the iso for 20.04.4 started with an HWE kernel series and will now probably be on 5.13.0-39.

It may not matter too much; if your hardware works on the 5.4.0-series there is no reason to move to the HWE kernel series.

---

