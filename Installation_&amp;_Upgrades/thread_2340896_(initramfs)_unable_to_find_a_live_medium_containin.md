---
title: "(initramfs) unable to find a live medium containing a live file system"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by DoABarrelRoll on 2016-10-23
Hi everyone. I'm new to Ubuntu. I'm trying to use a bootable USB pen drive(32gb) to install Ubuntu to another pen drive (128gb) so that I can just boot to the 128gb and keep the install separate from Windows 10. I got as far as booting to the 32gb and going through the installer to the point it asked me where I want to install Ubuntu. However, I forgot to plug the 128gb in before booting so it wasn't on the list of locations. I rebooted back to Windows, plugged in the 128gb drive and then used the advanced boot options to boot back to the 32gb drive. When I do that, GRUB comes up like the first time and I use the arrows and enter key to select Install Ubuntu just like I did the first time. However now it just shows the Ubuntu logo with the loading dots underneath it and it takes a lot longer before it comes up with the error message in the title. I did not change and BIOS settings or anything like that (seems to be a common problem when googling this issue). I made 0 changes. The installer worked and then I booted back to Windows and now it gives me the error, seemingly out of the blue. Any ideas on how this happened or how to fix it without changing any BIOS settings as it was working with the same settings earlier.

My laptop info is as follows;

Inspiron 13-7353
Windows 10 Home Edition v1607 build 14393.321
Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz 2.40GHz
8.00 GB RAM (7.86 usable)
64-bit operating system x64-based processor
I am trying to use the latest Ubuntu LTS ISO.
I used the Rufus bootable USB drive guide on Ubuntu.com to make the 32gb media install drive.

Any help would be appreciated.

---

### Post by Bucky Ball on 2016-10-23
If you want a persistent install to USB you might try doing it directly to the USB from the ISO. [Try this]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") and slide the persistence slider to whatever you want to use for storage.

What is on the 128Gb USB already? Sounds suspiciously like when you plug one in it is changing id and when you then try to install it is swapped around the order and the 128Gb is trying to install to the 32Gb.

A VERY important point to make is that before you create the USB, regardless of what app you use, your target USB _*MUST be completely blank and formatted as FAT32*_. Completely erase it and format it as FAT32. If there are any residual files or anything else on that USB you are looking for problems.

PS: If you do a dual-boot install with Win on one partition and Ubuntu on the other the two OSs will have *nothing* to do with each other. Impossible for that to be the case. You can no longer install Ubuntu inside Windows (WUBI) if that's your concern. Not advised, not supported.

---

### Post by DoABarrelRoll on 2016-10-23
Thanks for the reply. Yes I had already formatted the 128gb as FAT32, it was blank. I ended up solving the issue (for now) by making the bootable drive using a SDcard in the SD slot. Booted right into the installer and the 128gb SanDisk was now an option to install Ubuntu on. It is currently installing on the 128gb drive as we speak. My only concern at this point is that since I was getting the error while trying to boot the installer off of USB, it might not boot into the Ubuntu OS either. Only time will tell, I guess. 

Also as stated in the OP, I want to keep the installs separate. Maybe that's poorly worded. My end goal is to have no trace of Ubuntu anywhere on the laptop when the pen drive isn't plugged in. I don't want any partitions that came with the PC altered by the install.

---

### Post by Bucky Ball on 2016-10-23
Got ya. One thing to think about is that how are you going to boot it? This will mean dropping to the BIOS of the machine and booting from the USB. Lot of machine have a boot device list if you hit F12 at boot also. Did you check the ISO? The MD5SUM? If you are suspecting a dodgy ISO that would be the thing to do. If it is faulty safest is to torrent the image. The torrent file is available on the Ubuntu download page.

Sounds like you fixed your original issue so please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post. This will not close the thread to further discussion but if you come across a different issue best for your chances to post a new thread with a descriptive title. ;)

(It may have just been something dodgy with the 32Gb USB. Have you tried it on another machine and does it behave the same?)

---

### Post by DoABarrelRoll on 2016-10-23
I did confirm the hash is the same as on the website. The ISO is not corrupted. 

As far as how I'll boot to it.. Probably just from inside windows. If I hit the Windows key and bring up the start menu and type "boot" the suggest to change how the PC boots comes up. I click the restart to advanced options and boot from USB. Not the most efficient way, I'm sure, but I'm really only planning to use it every once and a while to compile a custom kernel for my android device. Just starting out, so it'll just be syncing stock kernel sources and building it with no changes for the time being.

The install is now just about finished. I will mark the thread solved given I can actually boot into it. If not, I am still having the same issue. The fact that I am getting this no medium containing a live file system error while trying to boot from USB that started happing out of nowhere.

Just finished, restarting now I'll see how it goes.

---

### Post by Bucky Ball on 2016-10-23
Got ya again ...

If same issue suggest instaling to the 32Gb to confirm if problem with 128Gb USB.

Just thought of something: you are installing the grub to the same device as you are installing Ubuntu and *not* the hard drive, sda? You do this during the partitioning section of the install so if you are doing an automatic install you may be installing the boot files to the hard drive, *not* the USB. When installing, are you using the 'Something Else' option or partitioning automatically?

---

### Post by DoABarrelRoll on 2016-10-23
Ok! I'm in business!

When I attempt to boot to USB, GRUB comes back up. Asks if I want to boot to Ubuntu or Windows boot manager. Confirmed all my Windows partitions are untouched and booting from USB works fine!

Only I ran into a new issues. For some reason upon login it's telling me my password is incorrect. Worst comes to worst I'll install Ubuntu on the drive again and do the install over. For now though, OG issue is solved!

---

### Post by DoABarrelRoll on 2016-10-23
I asked on another forum and was told not to use "Something Else". 

I used erase disk and install Ubuntu. When I click continue there is a drop down menu which had 2 options. 128gb SATA Samsung SSD(/dev/sda my internal SSD with Windows) & 128GB SanDisk pen drive. I just selected the pen drive and installed it

---

### Post by Bucky Ball on 2016-10-23
> **DoABarrelRoll said:**
> I asked on another forum and was told not to use "Something Else".

Whatever. The difference is you are given what Ubuntu gives you as far as partitioning goes and that doesn't suit a lot of users.

Switch the computer off, take the Ubuntu USB out, boot the machine. Can you still boot to Windows? 

Thanks for marking as solved.

---

### Post by DoABarrelRoll on 2016-10-23
Yes I can still boot to Windows with the USB plugged in or not.

However I do think something is messed up (user error, I'm sure.) 

When I boot with it plugged in it pops up with grub first thing. I can select Ubuntu, advanced options for Ubuntu, windows boot manager and 1 or 2 more items. Windows boot manager boots into Windows just fine. When I unplug the USB drive and boot it still comes up to a grub screen, but different. There's no real options to do anything. If I type "exit" from that screen, it boots directly to Windows

---

### Post by DoABarrelRoll on 2016-10-23
Another question.. Going into the UEFI settings under "Boot Sequence" and Ubuntu is first, followed by Windows Boot Manager and then a 3rd, UEFI generic-sd/mmc/ms pro 1.00 partition 1. The 3rd option wasn't there last time I looked in the boot options. Is that the SD card that I have the Ubuntu installer on? It's still in the PC, haven't removed it. I'm assuming bumping up windows to top of the list would boot windows normally and I'd have to manually boot to USB for.grub, right? That would be ideal setup

Edit- Ok so removing the SD card does in fact remove the 3rd option to boot in bios settings. Setting Windows Boot Manager above Ubuntu worked! Now when I power off the device and do not have the USB drive plugged in it boots straight to windows. I don't have to type exit at the black screen anymore. Just straight to windows. Awesome. Plug it back in and I can boot to Ubuntu after grub comes up. Thanks for all your replies! I think I'm all good to go now.

---

### Post by oldfred on 2016-10-23
Whoever said not to use Something Else was wrong. It always is a better choice if you understand partitions, some new users do not.
But with any second drive or external device Something Else install option is required.

You have UEFI system, and grub only installs boot loader into the ESP - efi system partition on the drive seen as sda. So you always are booting grub from UEFI, and in UEFI Windows is second option when grub fails (or you exit error).

Another complication with external devices is with UEFI, then only boot from /EFI/Boot/bootmgr file in ESP on external device which must be FAT32.
So to do a full install to an external, you must partition in advance with ESP as first partition, use something Else to install. Choosing to install grub to sdb (or sdf) will not work, it just installs to sda. But then you copy /EFI/ubuntu from ESP on sda to ESP on external device. Then copy again to /EFI/Boot and then rename shimx64.efi to bootx64.efi so UEFI can boot external. You need both copies as full install version of grub is internally hard coded to find more boot files in /EFI/ubuntu folder in ESP. You also need to change efi entry in fstab to UUID for ESP on flash drive not on internal drive.

This user documented process a bit more.
       Full install to USB flash drive, UEFI Boot
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836)
And Ubuntu's UEFI grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP on external drive.

---

### Post by DoABarrelRoll on 2016-10-23
Thanks for that link! Bookmarked. 

As for now, this is just a kind of whatever laptop. I bought it just to have something to browse on while at home. I was browsing from bed one night and put it on the floor when I was passing out. Woke up in the morning and stepped on it just enough to crack the screen. So now I just have it mirrored to my TV via HDMI. So for now since I can boot to both OS with no issues (especially since bumping up WBM to the top of the list) it works for me now. When I eventually build a PC with a friend's help (he knows how to do all that, IT, knows how to code, build custom rigs, all that fancy stuff) I will definitely follow that link to a T. It would be awesome to take my Ubuntu install with me anywhere I go so long as the PC in question has UEFI. 

Just one last question and I think we're good here. I noticed in system updates it says there is an update available. Is that safe to do with the way I installed Ubuntu? Would it know to update the OS on pen drive or would it mess with Windows settings you think?

---

### Post by oldfred on 2016-10-23
I know many users have posted that Windows updates have reset Windows to first in UEFI boot order.
Have not seen that issue with Ubuntu/grub updates, unless you do a full reinstall of grub which then may re-add it to UEFI menu as first in boot order.

Most updates are just for security issues and should be run.

---

