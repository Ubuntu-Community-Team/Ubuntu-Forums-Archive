---
title: "Removing Ubuntu - Help Please :-)"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by Jerry786 on 2011-01-28
Hey guys, i need to remove ubuntu and restore my system to the way it was previously. I need to do this as i need to sent my laptop off for repair
 
I have no CD/DVD drive nor am i able to boot into Win7 recovery to reinstall Win 7 [Dont even ask :(]
 
Instructions please? 
Many Thanks

---

### Post by ebasa on 2011-01-28
Maybe just wipe the drive? What type of repair?

---

### Post by Jerry786 on 2011-01-28
> **ebasa said:**
> Maybe just wipe the drive? What type of repair?

Hardware repair. How do i wipe the drive, i have no CD/DVD Drive nor can i boot into Win 7 recovery

Ive tried deleting the ubuntu partition but it says grub menu error or something on boot up, Had to reinstall Ububtu to get it working again

---

### Post by Jerry786 on 2011-01-28
**Deleted the ubuntu partition, rebooted...**
 
**I get this message**
**GRUB- error: no such partitieon grub rescue**
 
**Please help me with this nightmare**

---

### Post by mharrison on 2011-01-28
Try reading over this to restore the windows MBR

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by Jerry786 on 2011-01-28
> **mharrison said:**
> Try reading over this to restore the windows MBR

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

:( no luck

How do i repair MBR

---

### Post by mharrison on 2011-01-28
> **Jerry786 said:**
> :( no luck

How do i repair MBR

Sorry, I should have taken a minute to explain...was in a hurry.

Boot from a Live CD of Ubuntu.

Open a terminal and type in:
```
sudo fdisk -l
```

This will give you a listing of your current partition table.

You are looking for a line that has NTFS as the System type.
You want to make a note of the /dev/hd portion.  For example, if the NTFS line is on /dev/hda1 you want to write that down.

Then run
```
sudo apt-get install ms-sys 
```

followed by
```
ms-sys --mbr /dev/hdX
```
replacing the /dev/hdX with what you wrote down above.

After you do this try to reboot and see if your Windows boots up first.

---

### Post by Jerry786 on 2011-01-28
It says **E: Unable to locate package ms-sys** when entering second command

Any ideas? I need to get this sorted as soon as
Thanks

---

### Post by mharrison on 2011-01-28
I'm sorry, it appears I should read more too.  The ms-sys is apparently no longer in the repos.

Try this instead


```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```And replace sda if you want to install the MBR to a different drive. Or another method:


```
sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda
```

For either method, remember that the /dev/sda would be what you wrote down before for the Windows Partition's Drive.

---

### Post by presence1960 on 2011-01-28
Boot your Ubuntu Live CD/USb, choose try ubuntu. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings and proceed. This will install lilo to Live session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```This will put a generic windows boot loader on the MBR.

Reboot without your Live CD/USB and you should boot right to windows. Use Windows disk management to claim the space from Ubuntu back to C:

---

### Post by Jerry786 on 2011-01-28
> **presence1960 said:**
> Boot your Ubuntu Live CD/USb, choose try ubuntu. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings and proceed. This will install lilo to Live session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```This will put a generic windows boot loader on the MBR.

Reboot without your Live CD/USB and you should boot right to windows. Use Windows disk management to claim the space from Ubuntu back to C:

Thank you both for the replies. I tried your way Presence1960,  but when i reboot..It says BOOTMGR Missing?

... How do i resolve this?
Thanks

---

### Post by Jerry786 on 2011-01-28
Just to add, i cannot boot into windows 7 recovery mode as i previously stated :(

---

### Post by steveneddy on 2011-01-28
why can't the OP simply install Windows from the CD and then take it to the shop for repairs?

I know - silly question, but I had to ask.

---

### Post by Khakilang on 2011-01-28
The OP say he doesn't have a CD/DVD drive so I guess he has to make a bootable USB and work from there.

---

### Post by steveneddy on 2011-01-29
> **Khakilang said:**
> The OP say he doesn't have a CD/DVD drive so I guess he has to make a bootable USB and work from there.

Ah - stoopid me...

---

### Post by Jerry786 on 2011-01-29
Yup, i have no CD/DVD Drive, I messed up the recovery partition and thats the reason i cant boot into the built in windows 7 recovery mode by pressing F8

How do i make a bootable USB? I dont have back up repair disc so i assume id have to download ISO from somewhere?

I need this sorting as soon as [By that i mean Sunday], i cant send it in for repair in this state
Regret even installing Ubuntu now! :(

---

### Post by Jerry786 on 2011-01-29
Anyone?

---

### Post by slixz85 on 2011-01-29
open synaptic package manager and install unetbootin

the program is real simple and when you use it your usb stick will prolly be sdc just click the "just click the box for show all drives and click it back off actually" it will find the usb most likely.

---

### Post by nighttrap on 2011-01-29
If you have another computer, prepare win 7 usb, which you can find the instructions on the net

After that boot with usb

Select "repair" option after language selection and select Windows 7

than choose command

wrote

bootrec.exe /fixboot
bootrec.exe /fixmbr
bootrec.exe /rebuildbcd

Then reboot

If no any other problem, you should boot into windows

---

### Post by Jerry786 on 2011-01-29
YES! Ive been trying for days to make a bootable USB and ive finally done it, Booted computer up in USB, Windows recovery did the rest. Thanks everyone

---

### Post by steveneddy on 2011-02-02
> **Jerry786 said:**
> YES! Ive been trying for days to make a bootable USB and ive finally done it, Booted computer up in USB, Windows recovery did the rest. Thanks everyone

Sweet! Where else can you get this level of help for free for your Windows issues and concerns?

I believe that the UF fixes more Windows PC's than the Windows forums do - lol.

---

### Post by slixz85 on 2011-02-02
> **steveneddy said:**
> Sweet! Where else can you get this level of help for free for your Windows issues and concerns?

I believe that the UF fixes more Windows PC's than the Windows forums do - lol.

probably lol surprising they dont charge for answers on there forums

---

