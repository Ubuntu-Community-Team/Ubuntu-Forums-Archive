---
title: "Trouble dualbooting brand new PC"
date: 2017-09-15
forum: Installation &amp; Upgrades
---

### Post by kloek2 on 2017-09-15
[SIZE=2]Hi, I just bought a brand new PC that I'm planning to use both for gaming, and software development (machine learning) so i wanted to dual boot windows 10 and ubuntu 16.04! since i have owned a dual boot before i thought this would be easy, but last time i owned a dual boot pc was right before uefi went mainstream!

So here is my state, Installing windows 10 went fine! and then moving on to ubuntu, I knew I had read something about dual booting on uefi, so i started following this: [ post ]("https://help.ubuntu.com/community/UEFI") ( the general principals list), I disabled QuickBoot/FastBoot, but then i had trouble finding anything about Intel Smart Response Technology so i thought i could just skip it!!! later realised i had installed a intel RST GUI with the drives for widows, so i uninstalled it! But I'm not sure this actually disables it!

Then i created a usb according to [ 1.1 in this post]("https://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/")

But when i try to boot from the usb i get the following:
[Picture of my situation]("https://photos.app.goo.gl/7JShPLnoeDjDi1742") <- same as attachment incase this link dies

most of the times, these errors has poped up right away when i select the ubuntu usb stick, but a couple of times i have reached the (grub?) screen for selecting "run from stick"/install/install as oem/ ... and so on, but no mather what i chose there i reach the same error as previous picture!!! 

Would really appreciate any help, the only answers that i've been able to find is inapplicable since they are either based on older systems/software, or they are with a working ubuntu install so that they still have access to terminal!


**Update:**
1. ive tried creating the bootable USB in multiple ways (and different sticks)  and get identical errors every time! so i dont think the usb is the problem!

2. This is a "no name pc build" with specs (I didn't assemble it, a pro company did)
[/SIZE][SIZE=2]- Intel Core i7-7820X Processor [/SIZE][SIZE=2]Socket-2066, 8-Core, 16-Thread, 3.6/4.5GHz, 140W, 28 PCIe-lanes[/SIZE]
[SIZE=2]- MSI X299 SLI Plus, Socket-2066 [/SIZE][SIZE=2]Motherboard, ATX, X299, 8xDDR4, 4xPCIe-x16, SLI/CFX, Mystic Light, 2xM.2[/SIZE]
[SIZE=2]- HyperX Fury DDR4 2666MHz 32GB [/SIZE][SIZE=2]4x8GB CL16 Black[/SIZE]
[SIZE=2]- ASUS GeForce GTX 1080Ti ROG Strix Gaming [/SIZE][SIZE=2]PCI-Express 3.0, 11GB GDDR5X, 1493/1607MHz, Aura Sync RGB, Pascal[/SIZE]
[SIZE=2]- Samsung PM961 SSD 512GB M.2 NVMe [/SIZE][SIZE=2]V3 TLC, Polaris, up to 2800/1600MB/s read/write, PCIe 3.0 x4[/SIZE]
[SIZE=2]Then i added an old 2T sata hdd that i already had at home!

3.[/SIZE] 
[FONT=arial]q: Is drive set for AHCI not RAID nor IDE. And Intel SRT may be seen as RAID by Linux.[/FONT]
[FONT=arial]a: SATA mode is set to AHCI Mode in bios, but i use a m.2 pcie drive as main (Samsung PM961 SSD 512GB M.2 NVMe)not sure if that matters?[/FONT]

[SIZE=2]4.
it's 16.04 LTS that i want to install, but i have also tried 17.04, resulting in same error screen!

**[SOLVED]**[/SIZE]
So i ran into some more closely related trouble after the initial, and i'm not a hundred % sure what solved what! so I'm just gonna go thru all: 

1. installed latest BIOS
2. Updated NVMe drivers
3. added "nouveau.modeset=0" to setparams (reached by pressing "e" in grub) [LINK 1]("https://askubuntu.com/questions/715390/ubuntu-installation-issues-acpi-pcc-probe-failed[SIZE=2")[SIZE=2]
(clarification to point 3, most of the times i didn't even get to grub before the error popped up, but by smashing "e" while selecting boot device i started reaching it most times! After adding this to setparams, the error still popped up, but the ubuntu still booted from the usb!!)

Then on to a new problem!
When installing from usb boot, the install froze ( multiple tries, sam result every time!)
The solution i found to this was yet another setparam namely "acpi=off" [/SIZE][ LINK 2 ]("https://askubuntu.com/questions/861743/installation-of-ubuntu-16-04-from-a-usb-drive-freezes")

[SIZE=2]After that it is of course important to remember that booting the installed ubuntu will have the same issues, and there by need the same setparams!!! 
the setparams can be permanetly added like the answers in this link: [/SIZE][ LINK 3 ]("https://askubuntu.com/questions/345254/there-is-no-menu-lst-under-boot-grub-and-12-04-server-cant-boot")
[SIZE=2]or maybe the problem can be removed with correct nvidia drivers, like LINK 2 says, haven't tried that yet though!!!!!
[/SIZE]
[SIZE=2]
Best Regards,
Anton[/SIZE]

---

### Post by ubfan1 on 2017-09-15
The standard ISOs will boot UEFI and legacy, so if you want UEFI, set your machine to boot UEFI.  Use a standard tool like (DVD burn image or unetbootin?) to create your bootable install media, and try booting that.  When the ISOs switched formats, and started including a link, all the old  FAT32 copy files then modifying them stopped working, so these days,  use the ISO directory (dd or DVD burn equivalent), or use mkusb.

---

### Post by oldfred on 2017-09-15
What brand/model system?
Is drive set for AHCI not RAID nor IDE. And Intel SRT may be seen as RAID by Linux.
You may have to add AHCI drivers to Windows before changing if not already there.

What video card/chip?

 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

Also for UEFI many more links in link in my signature.

---

### Post by kloek2 on 2017-09-16
[SIZE=2][FONT=arial]hi @ubfan2 , i have tried creating the usb media a couple of ways, and i tried unebootin now... but i get the exact same error screen every time!

@oldfred
[/FONT][/SIZE][SIZE=2][FONT=arial]q: What brand/model system?[/FONT][/SIZE]
[SIZE=2][FONT=arial]a: Its a "no name" pc build, "configure yourself" from a Swedish company, where they have built it, but i bought it without any OS.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]q: Is drive set for AHCI not RAID nor IDE. And Intel SRT may be seen as RAID by Linux.[/FONT][/SIZE]
[SIZE=2][FONT=arial]a: SATA mode is set to AHCI Mode in bios, but i use a m.2 pcie drive as main (Samsung PM961 SSD 512GB M.2 NVMe)not sure if that matters?[/FONT][/SIZE]
[SIZE=2][FONT=arial]
[/FONT][/SIZE]
[SIZE=2][FONT=arial]q: You may have to add AHCI drivers to Windows before changing if not already there.[/FONT][/SIZE]
[SIZE=2][FONT=arial]a: Gonna look into that! ( when i search for intel ahci drives i end up at INTEL RST stuff) but since AHCI mode was already set in bios i assume this is not the problem?
[/FONT][/SIZE]
[SIZE=2][FONT=arial]q: What video card/chip?[/FONT][/SIZE]
[SIZE=2][FONT=arial]a: Asus GTX 1080 Ti / Intel Core I7-7820X[/FONT][/SIZE]
[SIZE=2][FONT=arial]On a MSI x299 SLI plus mother board with latest BIOS installed (upgraded yesterday since i thought it could be the problem)
(im gonna add full specs in original post if that helps)[/FONT][/SIZE]

---

### Post by oldfred on 2017-09-16
In addition to updating UEFI as you have done, you may also need to update the firmware in the NVMe drive.

I think the Samsung firmware for Linux use to update was under the professional section. But if you have Windows it may be easier to use the Windows version.

I know on my Asus Z97, I must have had 8 or 10 UEFI settings to change, some required & others were optional but improved system. I keep a record of what I change as with old BIOS everything was reset with a BIOS update. Now with UEFI some settings may be saved as UEFI has NVRAM.

These are older MSI threads, but UEFI for newer versions is usually just some updates for newest features as Intel basically is same structure.
       MSI Z170M Intel i7 6700 GTX 980TI 16.10 does not work, 16.04 does
[URL="https://ubuntuforums.org/showthread.php?t=2357641"]https://ubuntuforums.org/showthread.php?t=2357641
[/URL]
 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

Some have turned off nVidia in UEFI and installed using Intel video. Then add nVidia drivers and re-enable nVidia card. 
With nVidia card, it should work, but you need nomodeset until you install the nVidia driver. You probably will need to add ppa to get newest driver. Do not download directly from nVidia.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
   If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms

---

### Post by yoshii on 2017-09-16
I'm not sure if this helps, but it's good to have both Rufus Portable (rufusp) and UnetBootIn because there are times when UnetBootIn fails but Rufus prevails.  
It can be a bit fussy.  They are both similar in use.

---

### Post by kloek2 on 2017-09-16
@oldfred Thank you for the support! Awesome to get such extensive answers so quickly!!!!
The dual boot now works more or less exactly like i want! Ran in to more trouble after the first one, but solved all eventually with the help of your links and some google-ing! Gonna update the main post to include solutions for others to see!

Best Regards,
Anton

---

### Post by oldfred on 2017-09-16
Glad you got it working. :)

Since you are adding details of what works, I will add this thread to my notes of possible solutions for those with MSI motherboards.

---

