---
title: "Booting Ubuntu 16.10 from USB 3.0 doesn't work"
date: 2016-10-27
forum: Installation &amp; Upgrades
---

### Post by laetificat on 2016-10-27
Hello dear ubuntu users,

I'm fairly new to Ubuntu or Linux distributions in general.
I have a Laptop running Windows 10 with boot environment EFI and want to have an USB 3.0 drive with Ubuntu persistently installed on it so i can plug in my usb drive whenever i want and use ubuntu as if i installed it on my Laptop (without doing so).
I followed the instructions in this guide: [https://usbubuntu.wordpress.com/make-usb/](https://usbubuntu.wordpress.com/make-usb/)
I used an ubuntu-16.10-desktop-amd64.iso image and following the instructions in the guide i created 2 usb drives. One with 64GB and USB 3.0 where i want to make ubuntu persistent on (following the guide) and one with 8GB and USB 2.0 to try out ubuntu on and do steps 3-5 of the guide (where i needed gparted -> i used the gparted that comes with the live-usb/tryout thing).
After completing step 5 i shut down my computer and plugged out the USB 2.0 drive and let the USB 3.0 drive plugged in. On startup i went to my boot menu/efi and changed boot order to start with the usb 3.0 drive with 64GB (where i made the ubuntu persistent on, following the guide).
On my first try i got an error during booting "operation system not found" (or sth like that).
After that i repeated the whole guide and chose MBR Partition for BIOS or UEFI instead of GPT (in Rufus) for my USB 3.0 drive, like i did with my USB 2.0 drive from the beginning.
Also i disabled fast startup in Windows 10 (also looked for "fast boot" option in EFI to disable it, but couldn't find one), although this wasn't a problem before, but who knows (i don't).
After that i tried again and this time i didn't get an error during booting but i think it doesn't boot at all now. I only get a black screen with a blinking underscore, that moves 3 lines down and stays there blinking forever. I read this means that my computer/laptop isn't able to boot from the device.

I really don't know what to do anymore. Also i don't have much knowledge about the subject matter and i would be really thankful if someone here can help me since i'm trying this stuff for around the 3rd time and still don't get it :(
Please excuse my English if it isn't good enough.

Best wishes,
laetificat

---

### Post by C.S.Cameron on 2016-10-27
I have not had luck making persistent partitions with 64bit 16.04 using that method.
Better to install **mkusb** to the 32bit drive and use it to make the 64bit USB3 drive.
Works for me.

Mkusb can create a persistent partition and a ntfs partition accessible to both Linux and Windows.

Since 14.04 syslinux type live systems don't seem to be working with persistent partitions, this includes SDC and UNetbootin.
The grub2 type systems I have tried, do work with persistent casper-rw, home-rw partitions, this includes mkusb and MultiBootUSB.
I recall persistent partitions were working with 14.04 32bit and I think 16.04 32bit.

---

### Post by laetificat on 2016-11-01
First of all, thank you for your reply.
I tried to create a persistent live distribution with mkusb but when the programm is trying to do it's job, i get the error message "mkusb 11.0.5 - '/dev/sdc3' could not be mounted    Poweroff and cold boot for mkusb to make persistent live drives again!".
Also when i try to use gparted to look for which partition it is that causes the problems i get a Libparted Error "Invalid argument during seek for read on /dev/sdc" (sdc is my 64GB 3.0 USB drive).
I doubleclick on cancel and then i can see what partition the sdc3 is - it has the file system fat32, the label ubu1604132 and a size of 122.00 MiB.

So what is causing the problem during the mkusb process?

btw i used a 32Bit Ubuntu 16.04 iso image this time

---

### Post by oldfred on 2016-11-01
Black screen is usually a video issue. But some systems also need other boot parameters and/or settings in UEFI.
Only 64 bit is UEFI capable. 
What video card/chip?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If a 64GB USB3 flash drive, you have space for a full install of Ubuntu. It is larger, but then you can update drivers and system. On both my 32GB & 64GB flash drives I do a full install & have data partition(s).

---

### Post by laetificat on 2016-11-01
It's an Intel HD Graphics card (running dxdiag i can't find more information than that since the video card is part of the laptop itself).
Since i tried at first with an 64 bit image i thought it should work sind my OS is 64bit  and my laptop is running EFI.
Do 32bit images not work then (on 64bit computers)? Since C.S.Cameron suggested to use a 32bit image.
You were talking about grub menu. I don't run a linux operating system. Only thing i have is my small USB drive with a live distribution on it, so i don't think i can change that stuff?
Also, would be nice if you could explain why i should make the changes you suggested (if it's possible), so i can understand what i do.

How did you do your full install of Ubuntu on your USB drives? That's what i'm trying to do but i don't seem to figure it out.

---

### Post by oldfred on 2016-11-02
The 32 bit image will only install in BIOS boot mode. But then you cannot dual boot from grub menu. But should be able to boot from UEFI menu, but may have to turn on/off UEFI or BIOS settings.

If Windows is 64 bit you sould resolve issues with your 64 bit installer.

This HP would only install from USB2 port not from USB3 port. Still should be able to use a USB3 flash drive.
[https://ubuntuforums.org/showthread.php?t=2341851](https://ubuntuforums.org/showthread.php?t=2341851)

What brand/model system?

---

### Post by laetificat on 2016-11-02
I'm sorry if this wasn't clear but i don't want to dualboot if that means i have two OS's on my laptop.
I want my laptop with Win10 on it and the USB 3.0 drive with Ubuntu persistent on it (so i can save all my data and changes on the drive, too and keep them). So no Ubuntu data on my laptop.

Windows 10 is 64 bit version as i said and systemtype is also x64-based computer.
brand/model is ASUSTeK COMPUTER INC. X201EP
bios modus is UEFI
the USB 3.0 drive is the following: [COLOR=#111111][FONT=Arial]Transcend JetFlash 790K 64GB USB-Stick USB 3.0 black[/FONT][/COLOR]

So you say i should keep with the 64bit installer. Okay, i will do that.
I tried the whole process again. I used the guide i posted in my first post again.
This time i downloaded "ubuntu-16.04.1-desktop-amd64.iso" image and used Rufus again to setup the 3.0 drive.
In the guide it is suggested to use "MBR partition scheme for BIOS or UEFI computers".

On my first try this time i used "GPT paritions scheme for UEFI" and in the end i ended up with the message "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key" when trying to boot from the 3.0 drive (this time plugged into a 2.0 port!).

On my second try i used "MBR partition scheme for UEFI" and again i ended up with the blinking underscore during boot (again, i plugged the 3.0 drive into a 2.0 port).
So to sum it up i got the same results as described in my first post (although using a different ubuntu version this time and plugging the 3.0 drive into a 2.0 port).

I didn't use the "MBR partition scheme for BIOS or UEFI computers" suggested in the guide since i have UEFI, i think this shouldn't be the problem, right?

Also, Rufus is telling me my image is a hybrid image and i can choose between iso and dd, where iso is suggested (and i took it), could this cause problems?

And last but not least i want to mention that as soon as i select my amd64 image in Rufus the partition scheme automatically changes to GPT, i guess this is the default for my image then? Although it doesn't work (mentioned above)

Thank you all for your effort to help, appreciate that. I'm really helpless with this issue :(
Hope we can get this solved, would be really nice!

---

### Post by oldfred on 2016-11-03
For the flash drive, it should not matter if MBR(msdos) or gpt(GUID).
But a few computers seem to have issues with one or the other. 

MBR is required for BIOS boot on hard drive with Windows. 
And gpt is required on hard drive for UEFI boot with Windows.
But installers do not have to be one or the other partitioning schemes, normally.

While most systems have to have UEFI/BIOS settings to only UEFI to boot in UEFI mode, so seem to need CSM/BIOS/Legacy on, but still choose UEFI boot.
 Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/) 

Often issues are more common by brand, and other model's issues may be the same as yours. Many Asus seem to need pci=nomsi boot parameter.
      
 Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update

 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570) 
[URL="http://ubuntuforums.org/showthread.php?t=2307273"]http://ubuntuforums.org/showthread.php?t=2307273
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) [URL="http://ubuntuforums.org/showthread.php?t=2307273"]
[/URL]

---

