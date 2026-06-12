---
title: "Dual boot fails, cannot start ubuntu, only windows 7"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by Wimboo on 2012-07-27
Hello,

After installing ubuntu 12.04 (32bit) via live-cd and wubi, on a asus laptop (A55VD-SX030V, efi, windows 7 pre-installed, added linux and extended boot entry using windows easyBcd) i have the following result.

* Windows boot loader is started and immediately after boot and the loader menu shows windows 7, linux (the live one and wubi one) and the extended boot
  * Windows 7 works fine
  * All other menu result in a *.mbr file that is missing or corrupt error
    * Disabling efi in the bios does not change a thing

* When booting the with the super grub 2 disk 
  * i can find and start the grub2 config in sda6 (installed with the live-cd)
    * i can start&run ubuntu
    * when trying to run windows from here i get error

Boot repair does not fix the system.  

Boot summary info (bootRepair):
[http://paste.ubuntu.com/1113534/](http://paste.ubuntu.com/1113534/)

How do i create a dual boot from here whithout having to use a superGrub2 disk. Either using grub2 or the windows loader.

Many thanks for your help, 
Wim.

---

### Post by darkod on 2012-07-27
I don't use UEFI, but from what has been said here, it's very important how you boot the ubuntu cd. On UEFI boards you would have two different cd-rom devices, like the standard one and UEFI.
You need to boot the UEFI cd-rom, in other words to boot the cd in UEFI mode. This is needed because ubuntu will install in the mode you boot it into, so you need the UEFI mode for UEFI install.

Also, i am not sure if fdisk is confused, but in the bootinfo results it says you have two EFI system partitions. You should only have one, and it needs to be the first partition on the disk. Not sure what the other one is.

I would suggest deleting all ubuntu partitions and try another install making sure you boot in UEFI (the board boot menu might be the best way to make an exact selection).

As for wubi, I have no idea how that would work on UEFI. I personally don't use it and can't go into it. But since it's not meant to be a long term install, just a quick try, I suggest you forget about wubi (at least temporarily) and see if you can get the dual boot to work. If it does work, why would you need wubi anyway. Simply remove it like any other software from Programs in win7.

Before you start the new ubuntu install you might wanna google around how to install on UEFI, most importantly where the bootloader goes. I am not sure about that, whether it would be the MBR, the ubuntu partition, etc. I don't even know if it's used at all since UEFI boots differently with its own boot manager I believe.

---

### Post by Wimboo on 2012-07-27
Thanks for the feedback! 

After some more reading i did the following:
*Removed ubuntu wubi (removed in windows) 
*Enabled uefi boot in bios (to enable the boot of the live usb in uefi mode)
*Downloaded and created live cd (actually usb, ubuntu Secure Remix 64bit (sourceforge, note: 32 did not work)
*Install ubuntu with live cd (usb)(replace previous ubuntu install).

I now have a system that:
*Boots into grub2
*Runs ubuntu
*Gives the following error when starting windows 7 (loader on /dev/sda3):
 error: invalid EFI file path

Hope that that is an improvement. Any hints?

Thanks again for the help, Wim.

---

### Post by darkod on 2012-07-27
Uh, not really.

Can you open the EFI system partition (/dev/sda1) and check whether there are win7 boot files there? If they are missing that could explain the file path error.

i think earlier there was a bug where the ubuntu install was overwriting the win7 efi boot files but that should have been fixed I think.

---

### Post by oldfred on 2012-07-27
Just last week, Yanni updated Boot-Repair to put in a correct chain load entry to Windows. Grub was putting in a standard BIOS/MBR type entry and it has to be different.

I know he was testing which Windows efi file should be used and put all 3 in. At least two posters said 2 of the 3 Windows chain entries worked.
[http://ubuntuforums.org/showthread.php?t=2027888](http://ubuntuforums.org/showthread.php?t=2027888)

Please add to this bug if your problem is the same. It only has 4 so far and they prioritize based on the number of users who have issues. You do have to create a login in launchpad.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
may be related?
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

---

### Post by Wimboo on 2012-07-27
In one of the threads i found a remark about running boot-repair. 

After doing that two entries were generated and added in 40_custom. These entries start the windows bootloader from where i can start windows 7.

The generated windows entries from the are not correct. But i can live with the current situation. 

Thanks!

---

