---
title: "Creating bootable USB to install Ubuntu 5.04"
date: 2021-12-19
forum: Installation &amp; Upgrades
---

### Post by ^*#gop* on 2021-12-19
Hello,

I have a Dell Inspiron 545, purchased in 2010, with BIOS not UEFI. I downloaded Ubuntu-5.04-install-i386.iso and used Startup Disk Creator to burn the ISO to USB 2.0. USB appears via F2 and F12 during boot but refuses to boot from USB.

gpg ubuntu-5.04-install-i386.iso
gpg: [don't know]: invalid packet (ctb=00)

md5sum ubuntu-5.04-install-i386.iso
ubuntu-5.04-install-i386.iso

Top level of ISO:

```

-r--r--r--  1 colingates  staff     224  7 Apr  2005 README.diskdefines
dr-xr-xr-x  3 colingates  staff    2048  7 Apr  2005 dists
dr-xr-xr-x  3 colingates  staff    2048  7 Apr  2005 doc
dr-xr-xr-x  3 colingates  staff    2048  7 Apr  2005 install
dr-xr-xr-x  2 colingates  staff    4096  7 Apr  2005 isolinux
-r--r--r--  1 colingates  staff  132998  7 Apr  2005 md5sum.txt
dr-xr-xr-x  2 colingates  staff    2048  7 Apr  2005 pics
dr-xr-xr-x  4 colingates  staff    2048  7 Apr  2005 pool
dr-xr-xr-x  2 colingates  staff    2048  7 Apr  2005 preseed
dr-xr-xr-x  2 colingates  staff    2048  7 Apr  2005 tools
lr-xr-xr-x  1 colingates  staff       1  7 Apr  2005 ubuntu 
```

Selecting F12 during boot and selecting USB-HDD0 displays "No boot device available".

Please can someone advise how to resolve problem. Selecting F2 and forcing USB-HDD0 as first boot is ignored.

Thank you.

---

### Post by guiverc on 2021-12-20
Personally I wouldn't spend any time with Ubuntu 5.04 (the 2005-April release of Ubuntu).  It would **not **safe to use online; but even if you're intended to not use it online; I'd opt for a *supported* release of Ubuntu.

If you're going to use it off-line & it's just for *nostalgia *reasons then go for it :P

I don't know your box, but I'm using a dell desktop system (*optiplex 960*) from 2009 and running the Lubuntu *development* (or *jammy*) and used boxes as old as from 2003 in QA-testing releases up to 19.04 (*flavors anyway for x86 or 32-bit boxes*) and up to current *development* or *jammy* for *amd64* (x86_64 or 64-bit).

  If it's 32-bit only I'd opt for a Ubuntu 18.04 LTS *flavor* (*which whilst technically flavors are EOL; there is still support for the Ubuntu base & packages that are in common with main Ubuntu systems that are still in standard support - ie. a good deal of the product is still supported!*)  But it's a desktop from 2010 it's almost certainly a *amd64* or 64-bit box as desktops had been 64-bit for ~5 years at that point.

FYI:  intel 64-bit cpus are still *AMD64* as it was AMD that created a backwards compatible 64-bit CPU; intel's incompatible IA64 did not sell in the marketplace; so even intel sold & still sell *amd64* processors  (*intel understandably don't advertize the AMD name much*).

---

### Post by ^*#gop* on 2021-12-20
guiverc, thank you for your reply. I failed to mention reason for installing Ubuntu 5.04. Currently, I use Ubuntu 16.04 LTS on the fore-mentioned workstation. The reason for wishing to install Ubuntu 5.04 is that I have a Titan Linux Development Board, purchased in 2010. I am attempting to blink LED via GPIO and Inter Integrated Circuit but to build the code, Ubuntu 5.04 is required. As alluded above, I have [COLOR=#000000]Dell Inspiron 545.[/COLOR]

---

### Post by QIII on 2021-12-20
We usually do not like folks to ask for assistance with such old releases, but given your very specific need for a very specific application, we'll see where this goes.

Just be aware that you probably have a difficult row to hoe and there may not be a lot of folks who have not forgotten details about such an old release.  Further, if this is an ARM board or similar, there may not be a port that will work properly.

---

### Post by sudodus on 2021-12-20
Ubuntu-5.04-install-i386.iso is *not* a hybrid iso file, and therefore cloning does not make a bootable USB drive. The current version of Ubuntu Startup Disk Creator is a cloning tool. Disks can also work as a cloning tool.

- I think it would be easiest to make a boot CD or DVD disk with some burning program for example k3b or Brasero.

- An alternative is to get some extracting tool, for example Unetbootin, which might still be able to make a bootable USB drive of Ubuntu 5.04. You can also try some old version of Rufus (and run it in Windows) that might also work with your old iso file.

---

### Post by ^*#gop* on 2021-12-21
Thank you for all your replies. Apologies for my original post but as alluded by QIII, I have a specific requirement. Enlightening reply from sudodus! I do not run Windows following decision in 2013 to focus on Linux. I was hoping to avoid purchase of CD/DVD and burn 5.04 to USB. I will research use of Unetbootin. Thank you, again.

---

### Post by MAFoElffen on 2021-12-21
I am impartial.

It might help if you explain the  "specific requirement" you have....

I am human and have an understanding and life experience for having a 'specific requirement'.

---

### Post by ^*#gop* on 2021-12-21
See my post above which states "[COLOR=#000000]The reason for wishing to install Ubuntu 5.04 is that I have a Titan Linux Development Board, purchased in 2010. I am attempting to blink LED via GPIO and Inter Integrated Circuit but to build the code, Ubuntu 5.04 is required.".[/COLOR]

---

### Post by MAFoElffen on 2021-12-22
Sorry. I reread the thread and found where you had said that... 

I have had problems in the past trying to burn old CD MBR booted ISO's to USB. It may not work with Rufus, or The Ubuntu Startup Creator... But should still work with UNetBootin. It worked with those old ISO's. way back when...

---

### Post by ^*#gop* on 2021-12-22
Thank you. Another post above stated [COLOR=#000000]UNetBootin so, I will attempt.[/COLOR]

---

### Post by yancek on 2021-12-22
With Unetbootin, you can do a 'frugal' install which is basically putting the extracted iso of your Linux (Ubuntu 5.04) system on a partition of the drive and using it to install the Ubuntu to another partition you create.  You would use the grub.cfg file of your already installed 16.04.  The links below give some explanation of the process with the first link being the official site.

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

The link below uses Mint but the process is the same.

[https://forums.linuxmint.com/viewtopic.php?t=122187](https://forums.linuxmint.com/viewtopic.php?t=122187)

---

### Post by paulromano-8 on 2021-12-28
It might be worth trying Ventoy [https://ventoy.net](https://ventoy.net) to create a bootable USB.
Using my Ventoy USB, I downloaded the Ubuntu 5.04 install iso and successfully booted it in legacy BIOS mode.
Note that you can just copy multiple isos to (and delete them from) the Ventoy USB. as opposed to "burning" images one-by-one.

---

### Post by ^*#gop* on 2022-01-01
After experiencing issues with UnetBootin not seeing USB drive, I eventually realised that I need to re-format which solved the problem. Ran UnetBootin successfully but upon boot, I witnessed the attachments. When I boot and select USB via F12, the screen appears as alluded in first attachment. I pressed <TAB> and the screen appears as alluded in second attachment. Any ideas, please? Thank you.

---

### Post by yancek on 2022-01-02
Did you try the frugal method described in the links from my earlier post?  With unetbootin, you should have the usb or partition on your hard drive formatted as FAT32.  I don't know that this will work trying to boot the usb directly from the BIOS.  The frugal install method usually adds a boot menu entry to the already existing bootloader (grub2 of Ubuntu 16.04 in your case).  It's been a long time since I have done any of this and all I can suggest is to review the links posted.  I don not think you will be able to boot directly from the usb but need an entry in your existing grub.cfg file.  Good luck.

---

### Post by ^*#gop* on 2022-01-02
Sorry yancek, the post above was before I realised two pages of posts! The latest situation before reading the second page is that I reformatted the USB as FAT32, re-installed UnetBootin before using to create bootable USB. But upon boot, screen appears as alluded in attachment. So, I will action the posts which I missed unintentionally. Thank you.

---

### Post by yancek on 2022-01-03
The frugal install method for unetbootin should create/add a menuentry to grub.cfg on your installed system (16.04) if you create a FAT32 formatted partition on your hard drive.  I don't know that it will work trying to boot a USB from a selection in the BIOS as you are doing.  Do you not see an entry for the frugal Ubuntu with your standard grub.cfg menu?

A method that almost always works and worked with Grub Legacy as well as Grub2 is to extract or loop mount the iso file (Ubuntu 5.04 in your case), copy the extracted files to a separate partition and put a proper entry in your 16.04 grub.cfg file.  You would probably need to go into the isolinux directory to find a boot file and modify it to suit Grub2 which could be really problematic if you are not familiar with thist type operation.    The link below gives a general overview of it.  The boot menuentry in this example as well as your 5.04 is likely under the isolinux directory, maybe even in an isolinux.cfg file.  Good luck.

[https://www.tecmint.com/extract-files-from-iso-files-linux/](https://www.tecmint.com/extract-files-from-iso-files-linux/)

---

### Post by ^*#gop* on 2022-01-03
I will read the most recent post in more detail. The situation between my previous post and latest post is the attached image which, following an attempt of installing from USB which initially displayed the welcome screen for the install. Now, I will action the last post.

---

### Post by yancek on 2022-01-03
Well, I see the image in your last post mentions 'ventoy' so I guess you are still trying to boot 5.04 from a usb, correct?

---

### Post by ^*#gop* on 2022-01-03
Yes, because I thought this would be the simplest solution but alas not! Thus, I will attempt to understand your posts and implement as I considered them to be more complicated.

---

### Post by ^*#gop* on 2022-01-03
I created loop device as indicated via first attachment. But error message indicated in second attachment when I attempt to format as FAT32.

---

### Post by yancek on 2022-01-04
Maybe the link below will be more helpful.  Loop mount the iso after creating a mount point for it.  If you want to boot from the iso, you should create a partition at least the size of the iso file or larger and then copy the data from the loop mount location to the partition you created.  A loop mount will be gone on reboot which is why you need to copy it to another location.  You will need to examine the isolinux directory and its file to find a menuentry you can use in your 16.04 grub.cfg file to boot.   

[https://linuxize.com/post/how-to-mount-iso-file-on-linux/](https://linuxize.com/post/how-to-mount-iso-file-on-linux/)

---

### Post by ^*#gop* on 2022-01-04
Thank you. Loop mount complete. Using Disks to create partition of 650MB but receive error as alluded in attachment.

---

### Post by yancek on 2022-01-04
I'm not sure what you are using to get the image in your last post.  The image shows unallocated space which is what you would use to create a new partitiion of 650+mb size. Simpler to create a Linux filesystem on it such as ext4 but not necessary.  You would then copy everything from the mount point where you did the loop mount to the new partition.  You would of course need to create a mount point for the new partition, something like newiso:  sudo mkdir /mnt/newiso (use any name you want), then copy the data from the iso to /mnt/newiso..

---

### Post by ^*#gop* on 2022-01-04
Sorry yancek. I am using Disks - gnome-disk-utility 3.18.3.1. Have created partition as ext4 via gparted with mount point /mnt/newiso. loop mounted iso to /mnt/iso. Copied /mnt/iso to /mnt/newiso. So, now for the challenging part to "[COLOR=#000000]examine the isolinux directory and its file to find a menuentry you can use in your 16.04 grub.cfg file to boot.".[/COLOR]

---

### Post by yancek on 2022-01-05
One thing I have learned is that options appended in isolinux on the initrd line go on the linux (kernel) line in Grub.  Good luck.

---

### Post by ^*#gop* on 2022-01-05
Thank you, yancek. This is a dangerous approach! You originally mentioned using unetbootin; is this still an option?

---

### Post by yancek on 2022-01-06
You need to look at the isolinux directory where you have mounted the iso.  There are a number of files there which are similar to the grub.cfg file such as isolinux.cfg, txt.cfg.  I don't know what you would have with Ubuntu 5.04.   The entries for isolinux usually are Menu Label rather than the menuentry you see with grub.cfg.  If you can find the file in isolinux with these entries, you would simply copy it to the grub.cfg on Ubuntu 16.04 you have installed.  THen reboot and select that entry, it either will boot or not, if it doesn't just delete it and try again.

I'm not sure unetbootin will work.  I thought you tried it already.  THe frugal method discussed at the link I posted earlier will basically be the install iso of 5.04 on your hard drive rather than on a usb.  I don't know if it will work. I can't explain using unetbootin for a frugal install better than the unetbootin site.    I don't think unetbootin existed when 5.04 was released and I don't think 5.04 can be booted from a usb but am not sure.  Good luck.

---

### Post by sudodus on 2022-01-06
> **puremathematics said:**
> ... I was hoping to avoid purchase of CD/DVD and burn 5.04 to USB. I will research use of Unetbootin. Thank you, again.

I think it is getting time to purchase a CD/DVD drive and a small package of CD and/or DVD disks.

Edit: Or maybe you can find an old CD writing drive (in an old computer), that can be connected via a USB to IDE & SATA cable (adapter). The Ubuntu 5.04 iso file is small enough for the image to fit in a standard CD disk.

---

### Post by tea for one on 2022-01-06
Is Ubuntu 5.04 an essential ingredient for your Development Board project?

Would another 32-bit Debian-based distro be suitable?

---

### Post by ^*#gop* on 2022-01-06
yancek - attempted your suggestion regarding cfg but the grub displayed as before during boot.
sudodus - I watched a YouTube video stating that 5.04 can be booted from USB hence reason for buying USB; so, assume the person is lying!
tea for one - there are other Linux variants compatible with the board but wished to use Ubuntu as I have used since 2010 - 14.04 and 16.04 but always installed via CD. I was hoping to immerse myself into the 21st Century of installing via USB but obviously, need to revert to an archaic approach.

Thank you for everyone's assistance.

---

### Post by Tadaen_Sylvermane on 2022-01-06
Can this not be run in VirtualBox then point the USB port to it? Else compile whatever software against current libs and such?

---

### Post by MAFoElffen on 2022-01-06
> **Tadaen_Sylvermane said:**
> Can this not be run in VirtualBox then point the USB port to it? Else compile whatever software against current libs and such?
That was what I was thinking... Or using KVM... That is exactly what I do if I need something off of an old Distro or ISO.

OR: Just mount and extract the ISO. The OP did not expand off what exactly he needs off that ISO...

I looked into that project development board... and the development kit that was distributed for it. That development kit, did not contain Debian Branch, but rather a specific old version of CentOS, so I am a bit confused of what he needs off of Ubuntu 5.04(???)

---

### Post by yancek on 2022-01-06
> yancek - attempted your suggestion regarding cfg but the grub displayed as before during boot. 

iF THE other suggestions above don't work for you, post the menuentries you see in isolinux.cfg ot txt.cfg.  Not sure which file is used.  Maybe someone can figure out how to modify it to work with Grub2.

---

### Post by ^*#gop* on 2022-01-06
Purchased workstation in 2010 for the sole purpose of embedded development via Linux. Technical Manual states Ubuntu 5.04 and other Linux variants; so, my current version 16.04 is not compatible.

---

### Post by ^*#gop* on 2022-01-06
My earlier post states reason for installing old version of Linux; no intention to part install but install entire iSO.

---

### Post by ^*#gop* on 2022-01-06
The suggestion to post the menuentries is inducing complication so, I will either purchase CDs or use another Linux variant which I really do not wish for; but I do not wish to use VMs or CDs so, carpe diem and use another Linux variant.

---

### Post by sudodus on 2022-01-06
I tried with Unetbootin but failed. The computer booted from the USB boot drive, but after the first steps it wanted a CD. I could not make the installation continue.

Then I burned the iso file with k3b to a CD disk, and installing from the CD succeeded. Ubuntu 5.04 is running now in my old IBM Thinkpad T42. See the attached screenshot.

Edit: It may be difficult to run this version of Ubuntu in hardware developed after the release (April 2005), because the drivers provided might not work, and it is difficult to make newer drivers work with the old kernel. So I would recommend that you use an old computer for this task. a computer made before or around 2005.

---

### Post by ^*#gop* on 2022-01-07
Thank you, sudodus. Your statement regarding Unetbootin was exactly what I experienced. As mentioned my workstation for Linux was purchased in 2010. My first workstation was purchased in 2000 but sold since; otherwise, would have been perfect. So, I do not have another workstation acquired before 2010. I will just have to see what happens booting from CD or use another Linux variant. Need to locate CDs somewhere in one of thirty boxes or purchase new.

---

### Post by Paulgirardin on 2022-01-07
> **puremathematics said:**
> Thank you, sudodus. Your statement regarding Unetbootin was exactly what I experienced. As mentioned my workstation for Linux was purchased in 2010. My first workstation was purchased in 2000 but sold since; otherwise, would have been perfect. So, I do not have another workstation acquired before 2010. I will just have to see what happens booting from CD or use another Linux variant. Need to locate CDs somewhere in one of thirty boxes or purchase new.

I don't know if this suggestion will be of any use what so ever
Have you tried PLOP Boot manager?
[URL="https://www.plop.at/en/bootmanager/full.html"]https://www.plop.at/en/bootmanager/full.html


[/URL]I had to clone the OS (XP) on a 2004 PC recently to replace the 17 year old HDD. The BIOS did not have the facility to boot from a USB and PLOP corrected that.
I used it off a CD ,but I believe you can install it on the MBR.

---

### Post by ^*#gop* on 2022-01-08
Thank you, I will attempt. The attached is a list of distributions supporting the host environment. I burnt Fedora Core 3 to USB via Unetbootin and upon boot, insisted on CD. I suspect none of the distributions accommodate boot from USB.

---

### Post by yancek on 2022-01-09
I doubt any of the distributions you have listed are capable of being booted from a usb.  I've never used PLOP boot manager suggested above, but that might be worth looking into.  The first release of Unetbootin wasn't until April, 2007 so that may be another problem booting and OS released earlier than that.

The "frugal" install method of using unetbootin to boot an extracted iso from a hard drive partition described in an earlier link should work although unetbootin isn't actually necessary.  Booting extracted iso's with Grub Legacy was done in this manner on CD's at that time.  This can also obviously be done using Grub2.  I've done this in the past but don't know if I still have instructions.  Trying an online search for booting an extracted linux iso isn't helpful as most sites explain how to directly boot an iso file of linux from Grub2 which won't work with the Ubuntu release you are using.

---

### Post by ^*#gop* on 2022-01-09
I viewed the link relating to the PLOP boot manager but, in my opinion, this is complicated and fear that i will cause damage to my workstation due to my inexperience.

---

### Post by MAFoElffen on 2022-01-10
I think that is because in the early versions of the ISO, way back when, that it was hard coded and assumed that the user had at least a CD optical drive. I think I have run into this problem with trying to install native early versions of Ubuntu (onto metal)...

But from installing those early versions in KVM, as a virtual, they install fine, because the CD is virtualized and just used the ISO file of the CD Image, so it thinks it is using the (virtualized) CD drive...

So that begs you (again) to answer... You have an Ubuntu Host and you are trying to boot and install a 32bit image... Why can you not install this as a Virtual Machine on your existing Ubuntu Host? (whether KVM, VirtualBox, or VMware Player?)

^^^ Because, me... As being a Developer, that is how I develop and test my efforts cross-platform. That is where the advantages of being more powerful, flexible in it's resources, being isolated from the actual hardware... excels. Especially when your are trying to develop and test code for an old embedded board, that is Arm32, right?

If it were me... My plan would be to install 5.04 as a VM, in a VM that it could live and develop from... And replicate a VM of your embedded board to test from. But that is just me.

But I am also thinking, that if you are trying to use the 32bit code libraries, that 32bit in Ubuntu went up to Lubuntu 18.04 before it dead-ended. That you should be able to develop and compile your 32bit code on that (in a VM) also, with something that is still supported for a bit longer...

Just thinking out loud, in what I would do, if it were me...

---

### Post by ^*#gop* on 2022-01-10
Thank you. I will look into installing a VM onto my Linux workstation before installing 5.04. To understand your statement about CD, are you saying that the ISO will install on the VM without a CD? I am a C/C++ Software Engineer by profession and used CD via VMs many times. But, this requirement is a personal project to improve my chances of continuing employment in Embedded C/C++ following loss of job during first lockdown in May 2020.

---

### Post by MAFoElffen on 2022-01-10
Yes and no. Yes, without a physical CD. No, in that the VM will have a virtualized CD device that you point to the ISO file...When it boots and runs... the ISO file will mount to the VM as if it is the CD in that virtualized CD device drive. Even though it is hard-code to go directly to CD, it (in essence) "is".

With KVM, usiing virt-manager, create your new amd64 arch VM (it's default)... Select option install from ISO, which will then ask you where your ISO file is located, That will create a CD drive pointing to that ISO file... Give it a memory parameter, how many vCPU's, drive size... install... Once installed,you can tweak the memory and CPU parameters (while powered down)... You can do things and crash that VM while not crashing the physical machine itself...

You can then install support to KVM, for arm32 and arm64 VM's. That way you could create a VM to replicate what you are developing "for"... That way you can run code on it, and have a preview of what it is doing.

I started doing things like that with QEMU, way back when, cooking ROM's  for Win Mobile Phone and Win Mobile CE, then Android Devices...And while cooking/creating/testing Linux ROMs for those. Easier and safer to do something on a VM. to ensure you are not going to brick an embedded device, before you do something 'live' with a ROM image... Right? Easier to change something on a VM, rather than have to solder into UART connections on Physical board to recover from a bricking.

I'm into make things simple and easy. The development and coding for such should be the hard part that you need to concentrate on. If you look at the attachment, these are the architectures I run and develop for with my installation of KVM. That is a bit more than the default installation, and you do not need all those... but it shows you what is possible, right?

---

### Post by ^*#gop* on 2022-01-10
Thank you. I installed virt-manager which required additional work according to:

 [https://askubuntu.com/questions/932200/kvm-virt-manager-error-no-active-connection-to-installed-on](https://askubuntu.com/questions/932200/kvm-virt-manager-error-no-active-connection-to-installed-on) 

Creating a VM using ubuntu-5.04-install-i386.iso but the partition disks section is confusing as per attachment. Unsure which option to choose. Thank you.

---

### Post by MAFoElffen on 2022-01-10
Arrow down to the last option "Finish partitioning and write partitions to disk" and press enter...

---

### Post by MAFoElffen on 2022-01-10
Since you mentioned you are doing C/C++ Embedded you might also be interested in checking out Eclipse IDE for your Host... I use that a lot. There is a version for C/C++ Embedded Development.

---

### Post by ^*#gop* on 2022-01-10
Selected last option but the same screen appears as alluded in previous attachment; does not move on. Regarding Eclipse IDE, I have used this at work via Redhat 5.6/5.9 but never at home. I will investigate version as you alluded.

---

### Post by MAFoElffen on 2022-01-10
Hmmm... Will install 5.04 on my KVM as a guest and see what is up... BRB

---

### Post by ^*#gop* on 2022-01-10
Since my last posting, I re-viewed [https://www.youtube.com/watch?v=ghe6erH-jyY](https://www.youtube.com/watch?v=ghe6erH-jyY) which solved my problem. See attachment for screenshot of my VM session logged into Ubuntu 5.04. Time to play! :) 

Thank you all for your assistance. I guess this thread can be closed. Do I action or admin?

---

### Post by MAFoElffen on 2022-01-11
I used the 32bit Ubuntu Desktop 5.04 image.

The partitioner screen that came up for me, had only two options, which the first option was "Erase entire disk and proceed with installation". I selected that and it is installing right now...

Rebooting... It's using the CD as a local repo to install packages... Installing packages...

Yes... Watching it install packages, now I remember that the embedded board you are developing for only officially supported a Linux Kernel of up to 2.6.x... Seeing packages and versions of packages that I haven't seen in ages. Making me feel old.

Paused at Resolution settings... Confirmed. Continuing to set things up...

Done... See attachment... What are you install questions?

EDIT:
Since I posted... (Took the install time...) I see you got through it. Good Luck... And ensure your visit the thread tools link on this thread to mark this as solved, so other Users can see your solution.

I believe your next step will be to create another ARM VM guest to replicate your embedded device, so you can test on. If you need help with that, or have any other questions about KVM,  please start another thread for that in the "Virtualization Section".

---

### Post by ^*#gop* on 2022-01-11
I was confused by your post and attachments as I already solved the problem. But your edit stated that you saw my post. I did not mark the post as solved as alluded above but will now. Last night, I could not see any evidence on how to close thread but will look again.

---

