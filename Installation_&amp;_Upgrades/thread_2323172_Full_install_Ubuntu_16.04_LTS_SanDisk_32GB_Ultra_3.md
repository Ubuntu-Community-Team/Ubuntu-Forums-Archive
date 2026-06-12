---
title: "Full install Ubuntu 16.04 LTS SanDisk 32GB Ultra 3.0"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by Doktertje on 2016-05-03
Hello all! I'm new to this forum and to Ubuntu. I've been messing around with a live USB for a couple of days, but what I ultimately want(ed) is a full install of Ubuntu 16.04 LTS on my USB stick (32 GB 3.0 SanDisk Ultra). I've been reading multiple pages on how you can install Ubuntu on an HDD or USB flash station and I am aware that a full install will shorten the life span of the USB stick quite a lot, but that is okay. It is just for fun and for the sake of portability. However, I still encounter a problem with the USB stick not being able to boot.  Here is what I have done so far:  1) Install Ubuntu 16.04 LTS.iso to a second USB stick (8GB Verbatim Store 'n Go) with either Universal USB Installer/UNetBootin and Rufus. UNetBootin did not work that nicely for me, so I tried Rufus, which I now like best;  2) Shutdown laptop and plug in live USB;  3) Turn on laptop and boot into the live USB (works like a charm, already gave the USB stations the highest priority in the UEFI/BIOS menu);  4) From the live USB > install Ubuntu 16.04 LTS with the following options:      a) English;          b) Something Else;     c) Select SanDisk USB and make the following partitions:          i) 30 GB for ext.4 for / (root);          ii) rest for FAT32 with boot flag (gparted);       iii) select device for bootloader installation: /dev/sdb (or /dev/sdc, depending on the order in which I plugged in the USB drives; I always selected my SanDisk stick); 5) Follow installation procedure;  6) Installation finished;  7) Shut down laptop and reboot.  After step 7 I have encountered a couple of scenarios:    1) The computer booted into GRUB and let me choose Ubuntu or Windows when the SanDisk stick was plugged in;  2) The computer booted into some kind of GRUB when the SanDisk was not plugged in (GNU GRUB ~ version a.x.y (I do not remember the entire build number) and only gave a command      line interface, like:            grub> (from here I could run some commands; I always used the command "exit" and then chose the Windows partition to boot from);  3) No menu at all and straight boot into Windows.    I have also created an EFI partition during some occassion on the SanDisk with gparted, but this was to no avail. I tried fixing this with boot-repair and this did recognise the /EFI partition on the SanDisk (when I had it) and I could specify GRUB to be installed on the SanDisk from the boot-repair menu, but the USB stick was never booted from after this procedure. I still have the USB sticks as the first priority in the UEFI/BIOS menu.    For boot scenario 1 and 2 I also observed that there was an entry "ubuntu" in the UEFI/BIOS menu of my laptop, indicating that some part of GRUB was installed to my original UEFI/BIOS instead of to the SanDisk USB.    So, the problem is as follows:  "How do I install Ubuntu 16.04 LTS in such a way on my USB stick that I can still enjoy the "plug and play" kind of fun, but with a full install?" Moreover, how do I make sure that GRUB is installed correctly, as it has obviously failed a couple of times, even when specifying that /dev/sdb or /dev/sdc should be the location for bootloader installation?    To be more specific: I do NOT want a live USB with persistence, because I really want to mess around with a full installation. I am aware of the shortened life span of the USB, but that is alright for me. Furthermore, I do not want to dual-boot Ubuntu with Windows or overwrite Windows entirely, because this is the laptop I use for my studies. I have a back-up of all relevant data.    I am running Windows 10 (recently re-installed with a live USB stick after messing around with Ubuntu -- I wanted to start over) on an ACER V7-482PG laptop. Specs:   - Windows 10 Home 64 bits (10.0, build 10586);  - BIOS V2.25;  - Intel(R) Core(TM) i5-4200U CPU @ 1.60 GHz (4 CPUs), ~2.3 GHz;  - 8192MB RAM; - Swap: 2188MB in use, 7803 available;  - DirectX: 12    I would like to apologise for any inconveniences and mistakes in advance, because this is my first time trying Linux/Ubuntu, so I am still a rookie.  Thanks for all your effort!

---

### Post by Doktertje on 2016-05-03
Apparently something went wrong with the lay-out of my post. Therefore, I now upload the same post as a .pdf file. Thanks again!

---

### Post by grahammechanical on 2016-05-03
It is difficult reading. It needs what in the old days when people had typewriters were called carriage returns. Pressing the enter key to create a new line & paragraph.

Something that you should know. When we have 2 disks and one is internal and one external removable and we install Ubuntu onto the external disk the boot loader will be installed on to the internal disk by default. We need to direct the installer to put the boot loader (Grub) onto the external disk.

Linux calls the first disk in the system sda. The second disk is called sdb. And so on. The Ubuntu installer always default to installing Grub to sda. There should be a panel informing us of the location that the boot loader is going to be installed to. It has a drop down menu that we can use to direct the installer to install Grub to the second disk (sdb) or the third (sdc). As the case may be.

When Grub loads it looks to a folder on the Ubuntu partition for its configuration files. If it cannot find them Grub will go into Grub rescue mode. Now consider your situation.

Grub is installed on to the internal disk but its configuration files are on an external removable disk. What is going to happen if we remove the external disk and then restart? I can think of no other explanation of what is happening with your machine.

Oh, you will also need to re-install the Windows boot loader to the internal disk to load windows.

Regards

---

### Post by sudodus on 2016-05-03
Welcome to the Ubuntu Forums :-)

I have been thinking a lot about the things that you want to do, and I think I have a solution. I install bootloaders for both UEFI and BIOS mode, and for an ***external*** drive. You can do it yourself 'from scratch' according to the description or take a short-cut and use the compressed image files. It is described and explained at the following links,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) with details at [.../stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

---

### Post by oldfred on 2016-05-03
I install to sdb hard drive or sdc flash drive regularly.
But with UEFI, grub only installs to sda even when you say install to sdb. And installer even says installing to sdb during install.

You have to partition in advance.  I normally use gpt and include both the ESP & bios_grub, so it can be configured for UEFI or BIOS. Sudodus has procedures to get it to be both. But I just have several flash drives.

With UEFI and grub installed to sda, you then have to manually copy /EFI/ubuntu to sdb (or whatever flash drive is). But external devices with UEFI only boot from /EFI/Boot/bootx64.efi. So we copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi. You need the /EFI/ubuntu because the version of grub we are copying is hard coded to look for /EFI/ubuntu/grub.cfg which is just a configfile to find the real grub.cfg in your install.

---

### Post by Doktertje on 2016-05-04
Hi all,

Thanks for the replies! I will first read the information and then try it myself. I will let you know how it has worked out! Thanks again :)

---

### Post by Doktertje on 2016-05-25
Hi all,

Sorry for the late update, but I didn't have much time on hand during the past couple of weeks. I've read Sudodus' suggestions, but they seemed a bit more complicated than what I had time for, especially with taking out the hard drive, which is not very easy for my Acer V7-482PG laptop.

So, instead, I tried oldfred's suggestion of copying the ubuntu folder from my windows EFI partition, where grub was installed ('mis-installed rather, because I indicated for it to be placed on /dev/sdb), and rename the file shimx64.efi into bootx64.efi. I placed that folder in the /boot/efi folder on my thumb drive and I created a new /EFI/Boot/ folder on the EFI partition of my usb drive (this had not been created before).

Now, I need to check/try if the bootloader is correctly installed. Currently some part of grub is still installed on my windows EFI partition. I know that I can remove this with efibootmgr, but if grub is not correctly placed on my usb drive, then I cannot access it anymore (except for wiping and re-installing). Is there another way to check this? Or is this just trial and error?

Thanks in advance!

---

### Post by oldfred on 2016-05-25
Do not know if your Acer needs the UEFI password & trust for external devices. 
I do not think so, as many with Acer seem to be able to install, but then have to set "trust" on the ubuntu efi boot files to get it to work on internal drive. But many systems have to turn on or allow USB boot. My desktop which seems to have more settings than most laptops, also has settings for USB/flash for UEFI only, UEFI & BIOS or BIOS only. I could only get it to boot in UEFI mode with UEFI only, even with standard installer which is configured for both.

The external drives with UEFI always boot from /EFI/Boot/bootx64.efi. Both Windows & Ubuntu installers use that file. Windows version is just another copy of its efi boot file. When copying the version of grub/shim we install to an internal drive, it is hard coded to find /EFI/ubuntu/grub which is just a 3 line configfile to find the full grub.cfg in the install.

You should see entry in UEFI for UEFI:name where name may be the brand of flash drive, label on flash drive partition or something like my desktop's entry: 
UEFI:  PMAP, Partition 1    

Try booting that that entry, before housecleaning ESP internal partition and UEFI NVRAM entries.

I do not know Acer models, but some threads post that they had to down grade UEFI a version to get system to work. But then some newer threads said they installed the very newest from Acer and that works so down grade not required.
Do you have latest version of UEFI from Acer for your model?

---

### Post by Doktertje on 2016-05-30
Hi oldfred,

I've re-installed my USB drive and upgraded to 16.04 LTS from within the installed 15.04/15.10 (either one of them) ubuntu. I had to do this, because an upgrade of my Acer BIOS from version x.25 to x.30 prevented me from booting into the USB drive.

After installation, but before upgrading, I set a supervisor password for my Acer drives, which allowed me to disable SecureBoot. I disabled SecureBoot and ran Boot-Repair. I did this twice, but with different settings (specifying GRUB to be installed either to sdb or to /dev/sda2 on the /boot/efi partition). I've saved the output from Boot-Repair in the two pastebins (see attached).

To be clear: I want to have a USB drive that has Ubuntu installed and that I can boot whenever it is plugged in. If it is not plugged in, then I want Windows10 to boot automatically, without GRUB rescue to pop up. If that is not do-able, then I would like a system that shows a complete GRUB from the internal driving, allowing me to boot into Windows or into Ubuntu when the USB drive is plugged in.

Is this possible?

What commands can I run to provide you with more information?

Kind Regards

---

### Post by oldfred on 2016-05-30
With UEFI grub only installs to the ESP - efi system partition on sda. Does not matter what you tell it.
With BIOS it will install where you tell it and you install BIOS boot loader to sdb, but that should not be used.
You also installed a BIOS Windows boot loader to the MBR of sda, that cannot be used. Windows only boots from gpt drives with UEFI.
Do not turn on BIOS/CSM/Legacy boot in your UEFI configuration. Leave only UEFI boot.

Did you set "trust" on grub & shim files in UEFI after setting password?

If only booting external from internal you just need to change boot order.
But normally UEFI forgets UEFI settings when a drive is disconnected, so not sure if Ubuntu entries will be saved.

 BootOrder: 0001,0000,0002,2001,2002,2003
Boot0000* HDD0:     HD(2,GPT,879da88e-bef2-4327-9482-6ac9c8852698,0xc8800,0x96000)/File(EFIubuntugrubx64.efi)RC
Boot0001* ubuntu    HD(2,GPT,879da88e-bef2-4327-9482-6ac9c8852698,0xc8800,0x96000)/File(EFIubuntushimx64.efi)
Boot0002* Windows Boot Manager    HD(2,GPT,879da88e-bef2-4327-9482-6ac9c8852698,0xc8800,0x96000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x. 

You need 0001 first and 0002 as second.
Run these:
sudo efibootmgr -v
sudo efibootmgr -o 1,2
To confirm settings have changed.
sudo efibootmgr -v 

 Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 


External drives only boot from /EFI/Boot/bootx64.efi. So if UEFI forgets you entries when you unplug drive, you need to make sure you have a way to boot external from UEFI.
Copy /EFI/ubuntu from ESP on sda to ESP on sdb.
Copy it again from /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi
Then you can boot external from one time boot key and it will show external as UEFI bootable.

Because the ESP is on the internal drive, it may not forget the entires as that ESP is not removed. Let us know if it does or not.

---

### Post by sudodus on 2016-05-31
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I have been thinking a lot about the things that you want to do, and I think I have a solution. I install bootloaders for both UEFI and BIOS mode, and for an ***external*** drive. You can do it yourself 'from scratch' according to the description or ***take a short-cut and use the compressed image files***. It is described and explained at the following links,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) with details at [.../stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

> **Doktertje said:**
> Hi all,

I've read Sudodus' suggestions, but they seemed a bit more complicated than what I had time for, especially with taking out the hard drive, which is not very easy for my Acer V7-482PG laptop.

...

Thanks in advance!

Good luck trying along the advice of *oldfred* :-)

But if still no luck, you can 'take a short-cut and use the compressed image files' according to my first post. You need not remove your internal drive to use that method.

---

### Post by Doktertje on 2016-06-04
Hi oldfred,

I did the following things after your latest piece of advice:

1) run sudo efibootmgr to find which entry is booted first. This was the ubuntu entry, because I had already previously set that ubuntu must be booted first in my BIOS. I ran your commands anyway, just to be sure;

2) I mounted /dev/sda2 on /mnt/efipart (my windows ESP partition) and copied the ubuntu folder from there to my home folder (easier to copy it to here first, then move it to its designated spot);

3) unmount /dev/sda2 from /mnt/efipart and mount /dev/sdb1 (USB ESP partition) on /mnt/efipart. I made the folder /EFI and copied the ubuntu folder into this folder. I made the Boot folder within /EFI and also copied the ubuntu folder into this Boot folder (/EFI/Boot). In the Boot folder, I renamed shimx64.efi to bootx64.efi;

4) I rebooted my laptop and booted into BIOS. I found an option to set "trust" on files (didn't know this option existed in my BIOS) and set trust on shimx64.efi, bootx64.efi, and grub.cfg (maybe the name of the grub file is wrong, but it was at least the grub file within the ubuntu folder). This added these files to "allowed databases";

5) I shutdown my laptop and booted again, with the USB drive with Ubuntu inserted. My laptop booted straight into Windows, even without showing GRUB.

My BIOS boots in UEFI mode, not Legacy mode.

Did I miss something here?
What commands can I run next to give you more information?

Kind Regards,

Sjoerd

---

### Post by oldfred on 2016-06-04
In the sdb drive it has to be /EFI/Boot/bootx64.efi.
Your description seems to say it is /EFI/Boot/ubuntu/bootx64.efi

And it has to be /EFI/ubuntu for the standard grub/ubuntu files. 
The versions of shim & grub installed to sda normally are hard coded to look for /EFI/ubuntu.

The trust settings would normally be on the files in the internal drive. 
The external drive should always boot from /EFI/Boot/bootx64.efi.

---

