---
title: "Trouble dual booting Windows 8 and Ubuntu 13.04"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by qazp7 on 2013-07-04
I just installed Ubuntu 13.04 (64bit) from a live DVD on an Acer Aspire with Windows 8 following the directions from this page: [http://help.ubuntu.com/community/UEFI](http://help.ubuntu.com/community/UEFI) . There were no options in bios for quickboot/fastboot, Intel Smart Response Technology or FastStartup, and the live DVD booted fine so I didn't try to disable SecureBoot. I used gparted to shrink the windows partition and was able to install ubuntu like normal.

When I rebooted after the install finished, windows 8 loaded straight away (no grub). I used the live DVD to run Boot-Repair and it said "Please disable secureBoot in the bios. Then try again. Do you want to continue?"". So I went into bios, and under the Boot menu theres a "Boot Mode" option that can be changed from UEFI to Legacy Bios, and underneath that is a heading that says "Secure Boot:", which switches to "disabled" when the Boot Mode is changed to Legacy Bios, but it cant be changed on its own. So this means I can only either have UEFI and SecureBoot or Legacy Bios and no SecureBoot. 

When I ran Boot-Repair again, this time with SecureBoot off (and Legacy Bios on) it said "The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode", and it completed successfully (paste.ubuntu.com/5842519). When I rebooted again (it rebooted with legacy bios), it stopped at a black screen saying:

"PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcoam PXE ROM
No bootable device - insert boot disk and press any key"

When I change Boot Mode back to UEFI, it comes up with a message saying "HDD: has been blocked by current security policy". I tried running Boot-Repair with EUFI mode on (and secureboot on) but the same thing happens. Legacy bios and no secureBoot comes up with the black screen and PXE errors, EUFI and secureBoot with the "blocked" errors. Any ideas?
[COLOR=#222222][FONT=Times][FONT=Ubuntubeta]
[/FONT][/FONT][/COLOR]

---

### Post by kc1di on 2013-07-04
Hello and welcome to Ubuntu,

Here's the problem if ubuntu was installed when the machine is in legacy mode, it will install grub-pc instead of grub-efi.  Which is needed to boot window 8.  

Here's how to fix that using boot-repair.  

load the live cd  and download and install boot repair as instructed under i believe section two on the boot-repair page [here.]("https://help.ubuntu.com/community/Boot-Repair")

once boot-repair is up and running go to the advanced option select the grub location tab.  make sure the box is checked that says ```
seperate/boot/efi partition
```  or something like that and continue with the boot repair.  it will give you a couple of scripts you will have to run inorder to remove grub-pc and install grub-efi  run those and reboot you may have to go back into the boot menu /what I use to call bios and enable UEFI again.  you should then see a boot menu that will allow you to boot either Ubuntu or Window 8.  good luck

you may also want to [read this blog]("http://www.rodsbooks.com/efi-bootloaders/bootrepair.html") it's a bit long but has some good points in it.

---

### Post by qazp7 on 2013-07-04
I followed your directions, but on the last command that Boot-Repair told me to run in the terminal (sudo chroot "/mnt/boot-sav/sda6" apt-get install -y --force-yes grub-efi linux), I got an error:

Creating config file /etc/default/grub with new version
source_dir doesn't exist. Please specify --target or --directory
dpkg: error processing grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)

But i clicked continue and it said it was successful (like last time). When I rebooted I enabled UEFI again but its still saying "HDD: has been blocked by the current security policy".

Also, I don't think I installed in legacy mode, the bios setting was UEFI when I installed it, but I ran Boot-Repair for the first time in Legacy Bios mode. This is the paste page from when I just ran boot-repair and it gave the error, [http://paste.ubuntu.com/5843278](http://paste.ubuntu.com/5843278) , dont know if that helps. Thanks.

---

### Post by qazp7 on 2013-07-04
Okay, so I tried looking to reinstall "grub-efi-amd64" because of what it said in the error message I posted above, and after following the directions on this site: [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi) and running boot-repair again (with UEFI and SecureBoot on) I now get the grub menu and can boot Ubuntu fine, but neither of the two windows options in grub work.

There is "Windows UEFI bkpbootmgfw.efi" and "Windows Boot UEFI loader", but when you select either of them it says:

/EndEntire
file path: (very long file path, same for both options)
Error: cannot load image
Press any key to continue

This was the paste page from the last time I ran boot-repair (that got grub an ubuntu working): [http://paste.ubuntu.com/5843599](http://paste.ubuntu.com/5843599)

---

### Post by kc1di on 2013-07-05
> **qazp7 said:**
> 

But i clicked continue and it said it was successful (like last time). When I rebooted I enabled UEFI again but its still saying "HDD: has been blocked by the current security policy".



I get that message when secure boot is turned on.  in my laptop there are two setting one for secure boot and one for uefi.  you want the uefi enabled but the secure boot disabled.  

other that that hope someone else chimes in.  good luck

---

### Post by fantab on 2013-07-05
Are you sure you disabled 'fast startup'? [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html) Windows needs to shutdown properly before you install any other OS.

---

### Post by qazp7 on 2013-07-05
> **kc1di said:**
> I get that message when secure boot is turned on.   in my laptop there are two setting one for secure boot and one for  uefi.  you want the uefi enabled but the secure boot disabled.  

other that that hope someone else chimes in.  good luck

    
I can't, for some reason in Bios theres only a setting to switch from UEFI to Legacy Bios. Changing to legacy disables secureboot, keeping EUFI enables secureboot. Theres no option to change secureboot on/off by itself.


> **fantab said:**
> Are you sure you disabled 'fast startup'? [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html) Windows needs to shutdown properly before you install any other OS.

Uh-oh. When I was following the directions to install with UEFI, when I got to this step: "In your BIOS, disable QuickBoot/FastBoot and Intel Smart Response Technology (SRT). If you have Windows8, also disable FastStartup.", I assumed it meant the option to disable FastStartup was in the bios, so I skipped it because I couldn't find it. Now I feel like an idiot :(  . I don't suppose theres a way to fix this seeing as I cant access Fast Startup settings, seeing as I cant load windows at all?

The funny thing is I actually remember reading something about making sure to restart windows before installing Ubuntu instead of shutting down, because this would stop problems with the way windows 8 saves data for faststartup. I did restart before I installed, but when Windows booted up straight away instead of grub, Im pretty sure I pressed shutdown, not restart. I guess this might be the problem then. Any ideas as to how to fix it?

---

### Post by fantab on 2013-07-06
Check your BIOS/UEFI there may be an optiton Under Boot to boot Windows directly. If that doesn't help then Remove Ubuntu and try to boot Windows8. If that fails too then Windows Recovery/Repair should do it for you.

---

### Post by the86death on 2013-07-20
Aren't you supposed to reboot windows so the boot manager can detect the partition changes in the drive?

---

