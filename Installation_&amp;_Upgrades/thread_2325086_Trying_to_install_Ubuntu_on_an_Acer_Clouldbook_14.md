---
title: "Trying to install Ubuntu on an Acer Clouldbook 14"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by leonl on 2016-05-19
Hello all,

Rather than typing out my problem, I will link to an ask Ubuntu question. I am having the exact same issue as this person, except on the 14 inch model. Any help would be greatly appreciated.

Edit: didn't realize links werent allowed

Essentially, I am trying to install ubunutu on an acer cloudbook. I have tried 15.10, 16.04, and even linux mint(not ubuntu, I know). But no matter what I do then install hangs/freezes up after the menu. I select install, and it goes to a black screen. As best I can tell, I seem to have the same problem as this person


However, the granularity of the instructions is quite variable and is making the process difficult to follow. At this point, I've created Kubuntu USB install drives with both Kubuntu 14 and 16, and they both do the same thing. The machine boots from either (BIOS adjustments for boot order and touchpad alrady successfully done), but I try the option to boot or to install (for OEM's), and they both just lock up on a black screen, either version. Backlight still on, machine still on, but nothing on screen. Any ideas? HOw long should this bootup take, approximately? I waited about an hour on one occasion, and still nothin'.




Again, any help would be appreciated as it has been a frustrating few hours.

---

### Post by QIII on 2016-05-19
Hello!

We would really prefer that rather than just adding a link to someone else's question off-site, that you did type out your own question, for two reasons:

1.  Your problem may seem to be the same as someone else's, but actually be entirely different.

2.  By adding a link, you have asked people to make the effort to go look somewhere else in order to answer your question.  Some who would otherwise help you will simply not bother and move on, while others might express that you have been rude.

Please be courteous enough to avoid making others go of looking for your question.

Cheers!

---

### Post by vasa1 on 2016-05-19
Before trying to install Ubuntu, did you try a Live USB?

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

or

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

---

### Post by leonl on 2016-05-19
> **vasa1 said:**
> Before trying to install Ubuntu, did you try a Live USB?

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

or

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

Yes, downloaded 16.04, made a bootable usb and tried both the regular install and running it as a live usb, neither worked. When I made the usb, i used the option in rufus that checks the usb drive for bad sectors, and the program said it was good. I hit enter on a menu option, the usb drive flashes like it is being accesed and then nothing. I have even tried adding nomodeset by hitting e and nothing happens. The same thing happens with 15.04, and linux mint.

---

### Post by oldfred on 2016-05-19
A review says it is not the Intel Bay Trail issue and is the version after that.

But some of the limited systems use a 32 bit UEFI, is this one of those?
Linux did not used to have a 32 bit UEFI, so the vendors were designing Windows only systems, like iPads are Apple only.
But now there is a 32bit UEFI for Linux, but not part of standard distribution. 

Specs often in review sites do not get to that level of detail.

---

### Post by leonl on 2016-05-19
To my knowledge, its a 64bit UEFI. Several other people have had success with this, and according to this guy [http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

It should be a simple process, but I am following his instructions and I am getting nothing.

---

### Post by oldfred on 2016-05-19
Are you getting grub menu from UEFI boot?
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

If no Grub menu:
With the installers we find various issues with either the installer, or the flash drive, or the port used, or what the user did.
So confirming that ISO is correct with md5sum.
That ISO is written to flash drive drive correctly, not copied.
That different ports or different flash drives or different installers have been tried.

Some UEFI also have had issue with either MBR or gpt partitioning on flash drive. Either should work, but some need one or the other. 

       [URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL]
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
      
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[URL="http://rufus.akeo.ie/"]http://rufus.akeo.ie/
[/URL] 
If you get grub menu you can try Intel boot options. Usually nomodeset does not work with Intel.
       # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by leonl on 2016-05-19
I get a grub menu, then select the install method and it goes to a blank screen. I am going to pick up a new usb drive today and see if that helps. I have both UEFI and Legacy Bios. It does not work in either legacy bios or uefi

---

### Post by oldfred on 2016-05-19
Blank screen after grub menu is usually a video issue.
But can also be one of the other boot parameters.

Did you try any of the Intel video boot parameters?

---

### Post by leonl on 2016-05-19
I tried the intel boot options and nothing worked.

I tried to install in legacy mode and this happened [http://i.imgur.com/h2oTMCz.jpg](http://i.imgur.com/h2oTMCz.jpg)

I used the noapic option in uefi mode and this happened [http://i.imgur.com/tXzQFuQ.jpg](http://i.imgur.com/tXzQFuQ.jpg)

---

### Post by oldfred on 2016-05-19
It looks like UEFI got you a lot further into boot process.
Did you then try the other boot parameters?

---

### Post by leonl on 2016-05-19
yes, i tried all of them

Progress and a new problem. I got lubuntu 16.04 to boot all the way to the live cd option using noapic, but now it cant detect the hd

---

### Post by oldfred on 2016-05-20
Does UEFI/BIOS show drive correctly?

---

### Post by leonl on 2016-05-20
Yes, the UEFI/BIOS shows the hard drive. I tried using the fdisk-l command in terminal but it just shows a the flash drive and a bunch of weird entries like dev/ram/10 or something like that(I'm at work right now, can't give exact listing). The drive is a 32gb built in flash drive, eMMC I belive

Also tried using Gparted, but it just shows the USB drive.

---

### Post by oldfred on 2016-05-20
With gpt which is the standard partitioning system with UEFI, fdisk does not work. There is a new fdisk version in 16.04 that does work to show gpt partitions.
Use parted or gdisk to see gpt partitions.

       sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

---

### Post by leonl on 2016-05-20
> **oldfred said:**
> With gpt which is the standard partitioning system with UEFI, fdisk does not work. There is a new fdisk version in 16.04 that does work to show gpt partitions.
Use parted or gdisk to see gpt partitions.

       sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

Thank You, will try when I get home.

Should I disable secure boot when I do this. Also, assuming it me the HD, how do I get the installation to recognize it. When I click on install lubuntu, it does not show any drives in the options of where to install.

---

### Post by oldfred on 2016-05-20
It will not show drives if MBR & all 4 primary partitions are used.
Also some partition type errors like left over RAID metadata, both MBR & gpt backup partition data and a few others can prevent partitions from being seen. 
See what parted and gdisk show.

---

### Post by cristianomaria-cumer on 2016-05-23
Try noapic edd=off modprobe.blacklist=pinctrl_cherryview,sdhci_acpi it will boot but I will not be able to use the internal eMMC. Which bios revision do you have? Which mfg date? Did you use W10 on this PC before?

---

### Post by leonl on 2016-05-27
> **cristianomaria-cumer said:**
> Try noapic edd=off modprobe.blacklist=pinctrl_cherryview,sdhci_acpi it will boot but I will not be able to use the internal eMMC. Which bios revision do you have? Which mfg date? Did you use W10 on this PC before?

First off sorry for triple posting, but it doesn't seem like I can delete my posts. I have been able to get it to boot with noapic. Is there  a way to get it to boot that will show the eMMC. can I enable the eMMC once it has booted.  I have tried all of the intel graphic things listed earlier in this thread and they don't work

---

### Post by oldfred on 2016-05-27
So it does fully boot with noapci?

What is issue on eMMC. 
If a removeable device generally better not to try to auto mount with fstab when booting. If you remove it and reboot, you get errors and may then have trouble booting.

If permanent, you can add to fstab.

---

### Post by leonl on 2016-05-27
> **oldfred said:**
> So it does fully boot with noapci?

What is issue on eMMC. 
If a removeable device generally better not to try to auto mount with fstab when booting. If you remove it and reboot, you get errors and may then have trouble booting.

If permanent, you can add to fstab.

Yes, it full boots noapic into the live cd environment.  It has a 32gb internal eMMC drive. How do I mount with fstab? if I can't see the eMMC drive

---

### Post by oldfred on 2016-05-27
Post these:
sudo parted -l
sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

---

