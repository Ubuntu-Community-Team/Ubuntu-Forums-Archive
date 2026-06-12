---
title: "grub configuration"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by jim caster on 2007-05-17
I am not a newbie to linux but new to ubuntu. I have a laptop with 100gb hd. The factory config is 3 partitions.
The first is a "restore partition" the second is the main operating system and the third is just storage.

I chose to try to install 7.0.4 to a 30 gb usb drive. The install went fine and all is working. My mistake is that I thought that if I installed to the external drive, I would be able to plug it in and boot or worst case have to adjust the bios when I wanted to run linux as it will only boot from the "first" of multiple "hard drives"

In fact it appears that grub has installed only a reference or possibly a "chain loading" instruction on the boot sector of the primary internal drive so that the system will not boot at all unless the "external, usb drive" is plugged in.

Upon boot the system is being redirected to the external drive in order to load the grub menu.

Preferably, I would like to be able to use my first scenario. I would like to restore my machine to boot directly to XP Home (bootconfig.exe is not available), unless the external drive is plugged in.

If I can not do this, then I need to get grub installed directly to the mbr of my internal drive with instructions to boot to the external usb drive.

Any insight as to how to do this without wiping out my XP installation would be much appreciated.

Thanks

---

### Post by jim caster on 2007-05-17
I am not a newbie to linux but new to ubuntu. I have a laptop with 100gb hd. The factory config is 3 partitions.
The first is a "restore partition" the second is the main operating system and the third is just storage.

I chose to try to install 7.0.4 to a 30 gb usb drive. The install went fine and all is working. My mistake is that I thought that if I installed to the external drive, I would be able to plug it in and boot or worst case have to adjust the bios when I wanted to run linux as it will only boot from the "first" of multiple "hard drives"

In fact it appears that grub has installed only a reference or possibly a "chain loading" instruction on the boot sector of the primary internal drive so that the system will not boot at all unless the "external, usb drive" is plugged in.

Upon boot the system is being redirected to the external drive in order to load the grub menu.

Preferably, I would like to be able to use my first scenario. I would like to restore my machine to boot directly to XP Home (bootconfig.exe is not available), unless the external drive is plugged in.

If I can not do this, then I need to get grub installed directly to the mbr of my internal drive with instructions to boot to the external usb drive to run ubuntu and the 2nd partition of my internal drive to run XP.

Does grub modify the mbr with it's own intructions or does it just modify the boot.ini file?
My boot.ini currently reads;

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NOExecure=OptOut

Would removing the "/NOExecute-OptOut" restore the defualt boot to XP?

Any insight as to how to do this without wiping out my XP installation would be much appreciated.

Thanks,
Jim

*PS something in this BBS is putting the spaces in WINDOW S and Micro soft. I overtyped each 2x in preview to try to correct

---

### Post by heimo on 2007-05-17
Are you aware that you can edit your posts? No need for separate threads.
[http://ubuntuforums.org/showthread.php?t=446728](http://ubuntuforums.org/showthread.php?t=446728)

---

### Post by naren.bharatwaj on 2007-05-17
hi.

if u want to do the first thing, get an xp installation cd. insert it and boot from it. enter the recovery mode when it asks u to either install a fresh copy or recover a previous installation. U will be directed to a command line sort of interface. At that command prompt type "fixmbr".
Note that do not plug ur USB drive during this time. Answer YES to any questions that are asked after u type the command. Now ur MBR has been fixed and u can boot into Windows XP without any problems.
For the second question, i may not be able to hep u. i suggest u to search the net. it maynot a big issue. maybe i think u need to disconnect ur internal hard disk " i.e the one with xp on it before u can restore grub on ur usb drive.

all the best

---

### Post by bulldog on 2007-05-17
> **jim caster said:**
> I am not a newbie to linux but new to ubuntu. I have a laptop with 100gb hd. The factory config is 3 partitions.
The first is a "restore partition" the second is the main operating system and the third is just storage.

I chose to try to install 7.0.4 to a 30 gb usb drive. The install went fine and all is working. My mistake is that I thought that if I installed to the external drive, I would be able to plug it in and boot or worst case have to adjust the bios when I wanted to run linux as it will only boot from the "first" of multiple "hard drives"

In fact it appears that grub has installed only a reference or possibly a "chain loading" instruction on the boot sector of the primary internal drive so that the system will not boot at all unless the "external, usb drive" is plugged in.

Upon boot the system is being redirected to the external drive in order to load the grub menu.

Preferably, I would like to be able to use my first scenario. I would like to restore my machine to boot directly to XP Home (bootconfig.exe is not available), unless the external drive is plugged in.

If I can not do this, then I need to get grub installed directly to the mbr of my internal drive with instructions to boot to the external usb drive.

Any insight as to how to do this without wiping out my XP installation would be much appreciated.

Thanks

Well you can repair the windows boot with the windows install disk and use the recovery console.
Type fixmbr and fixboot and grub is replaced with the windows boot loader.

For the second problem,you have to boot from the ubuntu live cd,open a terminal and perform the next commands.
Keep in mind that the location given by the find command,example (hd1,0),you must use setup (hd1) instead of (hd0).
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0) or (hd1) depending on the find location!!
```
Exit the grub shell
```
quit
```

---

### Post by bapoumba on 2007-05-17
@ jim caster: threads merged.

---

### Post by jim caster on 2007-05-17
I want to thank you guys for fast clear answers!

---

