---
title: "Windows 8 Option not in Grub"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by Ben_C on 2014-09-06
I ran the Boot Repair thing on Ubuntu 14.04 and it finishes with one error and gives me a link

When I boot the computer the option to boot windows 8.1 is gone.
I saw a thread askubuntu.com/questions/401629/windows-has-gone-missing-from-the-grub-menu and I think the solution here is exactly what I need, but I don't know what it means by moving the boot flag back to sda1 or any of that, I need simpler instructions.

I don't have a Windows  repair CD or flash drive, it said you can use gparted so I guess I have to use that

This is what it says when it's done

An error occurred during the repair.


Please write on a paper the following URL:
[http://paste.ubuntu.com/8274183/](http://paste.ubuntu.com/8274183/)


In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 


You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (500GB) disk!


The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by grahammechanical on 2014-09-06
Can you load Ubuntu? If so run this command

```
sudo update-grub
```

The terminal printout should show a list of operating systems that have been detected. Does the printout show a Windows 8 boot loader in the list?

Regards.

---

### Post by Ben_C on 2014-09-06
It doesn't, just linux stuff

---

### Post by Ben_C on 2014-09-06
It says this 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Adding boot menu entry for EFI firmware configuration
done

---

### Post by Ben_C on 2014-09-06
[COLOR=#070F14][FONT=Verdana]Also it has my boot mode in EFI, if I change it to Legacy, which I believe it was originally before I ran BootRepair and if I change it to legacy it says no operating system found[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-09-06
You have windows 8 and it was surely installed in EFI mode. Was Ubuntu installed in EFI mode?

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Ben_C on 2014-09-06
I think it was set to Legacy when I installed Ubuntu and I think BootRepair changed it to EFI, if I change it to Legacy it says no Operating System found
Windows 8.1 came preinstalled if that helps

---

### Post by Ben_C on 2014-09-06
I don't know if this means anything but if I go to disks on Ubuntu I had DIAGS and WINRETOOLS and OS all unmounted, clicking mount doesn't seem to do anything though [http://tinypic.com/r/2a8lsn8/8](http://tinypic.com/r/2a8lsn8/8)

---

### Post by fantab on 2014-09-07
> parted -lm:
                                                                          
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.

This can be fixed by just running the following command from Live ubuntu:
```
sudo gdisk /dev/sda
```
..copy and paste the output here.
and quit 'gdisk' by typing '**q**'.

'gdisk' will refresh the partition tables.

reboot.

---

### Post by oldfred on 2014-09-09
You have what looks like normal UEFI install of Windows and Ubuntu.
But you also have a 32GB second drive SSD often used by Windows for cache for the fast boot. Since it is only the same as RAM usually the entire 32GB is not used. Many users have either installed Ubuntu into the unused space to make Ubuntu very fast or turned off fast boot and Intel SRT in UEFI/BIOS and only installed Ubuntu to SSD. Windows then does not boot so fast, but Ubuntu is then very fast for everything.

You do need to have fast boot off in Windows and usually best to have secure boot off also. You may have to turn Intel SRT off to get grub to fully install correctly but then should be able to turn it back on after it is working. 

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 

With 14.04 it has usually worked ok.

 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

