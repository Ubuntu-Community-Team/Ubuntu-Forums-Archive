---
title: "Ubuntu 19.10 installation issues on HP Pavilion laptop"
date: 2020-04-19
forum: Installation &amp; Upgrades
---

### Post by simplisagar on 2020-04-19
Laptop: HP pavilion (L8V46AV - not sure if this matters :-|).

As per the norm, created a bootable USB drive with ubuntu 19.10 desktop image. There is a pre-installed windows 10 on the laptop. Booted into ubuntu using the 'try ubuntu wihout installing' option and proceeded to install install from there. The installation wizard took a long time to open up and throughout the installation process, it was very slow (took 7 hours to the end). Chose to install the full feature set with apps and drivers (also configured secure boot). I had spared a space of 230GB in my 1TB hard disk. Created partitions manually in this configuration.

root - logical - 140 GB (largest as apps get installed here)
swap space - logical - 4 GB (The laptop is equipped with 8 GB RAM)
home - logical - 86.7 (leftover space)

It took almost 5 hours to reach this stage. Configured the time zone and proceeded to the page where one specifies the username, password and laptop name. This is where things went out of control. After clicking the install button, the installation stayed on the same screen for atleast 2 hours and showed no sighs of completion. Terminated the installation with long press of the power button.

Apart from doing the mistake of plugging the USB drive in a non-USB 2.0 port :)  I seem to have followed the standard process. After all this, I was not able to boot again into 'try ubuntu wihout installing' mode as it seemed to be struck in the loading screen forever. Logged back into windows and removed the partitions.

Can the knowledgeable tell me, what went wrong or what could have been done better? I've heard that there are issues with installation of ubuntu on a HP laptop.

I am planning to perform a second round of installation but this time choose basic installation (barebones installation with just the browser and essentials) but still am skeptical about it.

---

### Post by yancek on 2020-04-19
The first thing I would suggest is that you go to the Ubuntu site at the link below and use the md5sums link to get the correct md5sum for the version you downloaded.  Then run the md5checksum to verify the download process did not corrupt the iso file.  It should not take much more than 30 minutes to do an install.

 [http://releases.ubuntu.com/19.10/](http://releases.ubuntu.com/19.10/)

If you want a dual boot with windows, Ubuntu documentation on the subject is available at their site at the link below detailing the entire process.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mörgæs on 2020-04-19
Have you tried installing other Buntus than Ubuntu?

---

### Post by oldfred on 2020-04-19
Something not correct as install does not take that long.
OK, I tried installing 20.04 on my 2006 Laptop with 1.5 GB of RAM. After two days gave up. But installed server in about an hour and updated to lightweight gui in another hour.

My install to SSD is under 10 minutes. And even to fast hard drive is just over 10 Min. Not counting starting ISO nor partitioning as already done in advance.

have you updated UEFI?
Is drive set for AHCI, not RAID nor Intel RST? And installed AHCI drivers into Windows or it will not work with AHCI.
What video card/chip? If you have nVidia, you need nomodeset to boot installer. And if you do not include install of proprietary driver during install, you need nomodeset on first boot of install.

Booted in UEFI mode, not 35 year old BIOS mode?

See also link below in my signature.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Even if not same model, issues are often common by vendor. Bigger difference if AMD or Intel based.
HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)

---

### Post by Impavidus on 2020-04-19
There are a few things that struck me as not normal.
> There is a **pre-installed windows 10** on the laptop.
root - **logical** - 140 GB (largest as apps get installed here)
A pre-installed Windows 10 system uses UEFI on a GPT partitioned hard drive. Microsoft requires that, although Windows 10 can be installed in legacy mode on MBR drives. There are no logical partitions on GPT drives.
> took 7 hours to the end
It should take about 20 minutes, depending on the speed of your drives.
> root - logical - **140 GB (largest as apps get installed here)**Applications aren't large. Media files are large, but you store those on your /home partition, a dedicated partition for media files or a data partition to share them with Windows. If you have a separate /home partition, about 25GB is enough for the root file system. Unless you want to do something special.
> Apart from doing the mistake of plugging the USB drive in a non-USB 2.0 portI'm not familiar with a rule that you should only boot a live usb in a usb2 port. Some computers don't boot from every usb port, but yours obviously booted, so that was OK.

BTW, Ubuntu 20.04 will be released in a few days and will be an LTS release. You may prefer the longer support.

---

### Post by simplisagar on 2020-04-23
Thank you all for the suggestions. I will try them and go with the new LTS release.

---

### Post by simplisagar on 2020-04-25
I was able to install 20.04. The trouble previously can mostly be attributed to a faulty pen drive. The read/write operations were abnormally slow for reasons unknown. Used a different pen drive the second time and saw better results. Now that ubuntu is installed, there are a host of other problems but they are for another thread. Thank you for all the suggestions.

---

