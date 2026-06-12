---
title: "Ubuntu 12.10 dual-boot on ASUS Q500A Windows 8"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by ryanchang on 2013-04-23
Hi all,

Before you ask: Yes, I have read various threads, some marked 'SOLVED' and others not, about this topic. I'm merely posting here to ask for a general, guiding rubric on the safest way to install Ubuntu 12.10 alongside a pre-installed Windows 8 on my ASUS Q500A Series machine.

Though I'm pretty tech-savvy, this is my first encounter with both 64-bit technology *and* UEFI boot systems. I'm a student so I can't really take any major risks.

The initial steps, from my research, seem to both include 1) disabling Secure Boot and 2) making sure that Ubuntu is installed in EFI mode. After this, partitioning the drive appropriately is confusing (Should I have a separate /boot at the beginning of the drive? Does this go underneath the Windows partition, or am I misunderstanding that?). 

Hopefully you guys can help shed some light on this. You guys rule.

Best
Ryan

---

### Post by screening on 2013-04-23
I buy an Asus, n56vj and did the same questions you talk. 
First step I try installing in dual boot, you don't need a separate partition /boot. Only one to /, and, if you consider other to /home. The first partition (efi) is the manager of boot process. Windows and Linux can use them (I think) 
Now I formated the entire hdd and leave only Ubuntu because I Don't like windows. 
Take care, after installing you need to adjust in setup to boot Ubuntu in first order, if you don't select in setup and reboot, windows still load before grub. 
Sorry for my bad English.

---

### Post by oldfred on 2013-04-23
You should not need a separate /boot. You need at the minimum for Ubuntu / (root) and swap. For newer users we often suggest making / smaller like 25GB and have a separate /home. It makes new clean installs easier.
But if dual booting with Windows it also is suggested to have a separate NTFS formatted data partition for any data you want to share with Windows. 

Is this model an UltraBook with Optimus video and small SSD using Intel SRT? A lot more configuration is then required.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Some other Asus.

 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Blank screen resolved by turning secure boot off
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

Do not know about touchscreens, supposed some work, others?
Some very new computers may work better if you wait until Thursday and use 13.04.

---

### Post by ryanchang on 2013-04-24
Hi oldfred,

Thanks for getting back to me. No, this is not the ultrabook model (no touch, SSD or SRT). I have a few follow-up questions, and for clarity I'll directly quote.

"> You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode"

So the 64bit .iso files are marked amd64, regardless of my intel chipset? 
"from the UEFI menu..." -- This means after I have booted from the cd. What is the flash drive, if it is a CD?

> Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI

Do you mean that I haven't changed the BIOS settings to boot into Legacy? 


I also poked around in my BIOS to see if I could change the boot order on my devices, but it looked liked I needed to provide a manual path (of which I don't know how to do). Is this even necessary if the boot CD should recognize my computer?

Thanks so much for your help and patience!!!

---

### Post by oldfred on 2013-04-24
There is a lot of interesting history of licensing, legal issues,  and competition between AMD & Intel on why the install is AMD for both AMD and Intel 64 bit computers. 

Another thread just found a typo in the naming of the signed efi secure boot files in 12.04.2. That may be why I have had to tell everyone to just install with secure boot off but efi on. A few system will not install that way and can only install in BIOS/Legacy/CSM mode and then you have to use Boot-Repair to convert to UEFI by uninstalling grub-pc and installing grub-efi. Some only boot with secure boot on, and then you have to have the signed versions of grub & kernel.

Most find flash drive works better than DVDs, CDs are now not large enough, but some have issues with certain flash drives.
       Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

Someone posted this from their system, but each UEFI varies. Staples was the label of his flash drive.

---

### Post by ryanchang on 2013-04-24
I see, so you recommend using a LiveUSB over DVD/CD. OK, think I will get one then.

Will repost with an image of my BIOS in the next day or two in case I come into a problem with the boot device not showing up, or something. Thank you again, oldfred.

---

### Post by FenrirXIII on 2013-04-24
here some quick guide:

get a LIVE, bootable, USB stick with a signed UEFI ubuntu (12.04.2, 12.10 or later)

SHRINK VOLUME

on windows 8,
go to My computer (then right click) >> to Manage >> Disk Management (then right click) >> Shrink Volume: Enter desire amount of Free Space.
after that plug the LIVE USB then do the following:

Now that you have space, locate the SHUT DOWN button in windows 8

HOLD SHIFT and click power button,
KEEP HOLDING SHIFT and select RESTART
KEEP HOLDING SHIFT

just before the computer actually shuts down you will have a choice,
Select either enter BIOS or something similar under UEFI category

on BIOS

disable SECURE BOOT or something similar
SAVE changes.

press the corresponding key for BOOT OPTION or similar, select the USB STICK

Install via selecting custom partition (the last option)

now select the FREE PARTITION (sda7... maybe) and click CHANGE
make the FREE PARTITION EXT4 and select the "/" (no quote) mounting point.

install as you normally would

now once you restart the computer you will automatically go to ubuntu instead of GRUB

but not to worry...

once you are logged in and connected to the internet go to TERMINAL and write the following

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair

select the recommended repair.

you have now successfully dual booted. ENJOY

---

### Post by ryanchang on 2013-04-24
hey Fenrir,

Thanks for the step-by-step. Next logical question would be if you have a recommendation on how to create a liveUSB in Windows 8. If this is a stupid question (i.e., all I would need to do is right click on the image or liveUSB) please let me know. Thanks!

---

### Post by oldfred on 2013-04-24
Do not know if different for Windows 8, but this shows how for both Windows & Linux.
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Also

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Maybe best after shrinking Windows to reboot back into Windows  a couple of times. It wants to run chkdsk or make repairs to its new size and best to do that before the install of Ubuntu. Then it is a good time to backup your entire Windows install and the efi partition. A few have clicked on the wrong icon that in [COLOR=#ff0000]RED[/COLOR] says it will erase drive but do it anyway and wonder where Windows went. Of course I have never clicked on the wrong thing and damaged system. :)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Also Windows 8 is always hibernated so it pretends to boot faster. Best if dual booting to turn that off.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ryanchang on 2013-04-24
Great--thanks a million, oldfred. I think this is enough information to get me going. If I have any more questions I will be sure to re-post here.

---

### Post by ryanchang on 2013-04-25
oldfred: I see 13.04 is released--would you recommend it for a windows8 dual boot?

---

### Post by ryanchang on 2013-04-26
Success! Albeit with a tiny snag: in GNOME 2 the topbar on windows immediately goes underneath the top bar on the desktop, so I can't move application windows around. Maybe I have to install latest drivers for video card?

---

