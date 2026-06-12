---
title: "stuck in grub rescue"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by dc200 on 2011-01-21
so i foolishly decided to remove my linux partition from windows and am now regretting it.

as soon as i boot up, "grub rescue" shows up with an error message telling me that a partition was not found. none of the commands work, and to top it all off, my cd/dvd drive is broken and trying to boot from a usb stick gives me the error "missing operating system".

i really don't know what to do now. i'm guessing my only option at this point is to do something in "grub rescue", but none of the damn commands work.

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums :)

If this was a proper dual-boot (not Wubi) then you are seeing vestiges of GRUB in the MBR.

You need to restore the Windows bootloader to fix this:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by dc200 on 2011-01-21
my cd/dvd drive isn't working. however i did manage to get the vista recovery disc into a usb key and boot it, but the "bootrec.exe /fixboot" and "bootrec.exe /fixmbr" commands did absolutely nothing.

all i want is to get my vista partition back. i have no idea why the bootrec.exe utility in the recovery disc can't overwrite grub.

**update**

i managed to get rescatux (super grub) onto the usb key and boot off it. YAY! now i need to figure out how to get rid of grub from in there. any help would be greatly appreciated.

---

### Post by dc200 on 2011-01-21
bump...

tried booting a ubuntu live cd from the usb (using unetbootin) with the intention of installing ubuntu and restoring grub to its original state. i couldn't install ubuntu because gparted can't resize the main partition.

this whole thing began when i deleted the linux partition and resized the vista partition.

---

### Post by IWantFroyo on 2011-01-21
Just restore the entire thing from your windows recovery disk. Repair or restore. If repair doesn't work, restore will (if you have a backup).

---

### Post by dc200 on 2011-01-21
i've already tried reparing from a recovery disc, and that didn't work. the "fixboot" and "fixmbr" options did absolutely nothing. also, i can't do restore because i haven't got a backup of my vista partition.

---

### Post by bcbc on 2011-01-21
No sure why bootrec.exe /fixmbr didn't work. You can also install lilo. But why don't you post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results.

---

### Post by drs305 on 2011-01-21
From the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Disregard any other commands lilo wants you to run.
This assumes your Windows drive is sda. If it isn't sda, change it in the command.

If your Windows boot files are intact and it's only the MBR that needs replacing, this should allow you to boot Windows.

Added: Just saw *bcbc's* post. If the above doesn't work, post the results as he has requested.

---

### Post by dc200 on 2011-01-21
> **drs305 said:**
> From the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Disregard any other commands lilo wants you to run.
This assumes your Windows drive is sda. If it isn't sda, change it in the command.

If your Windows boot files are intact and it's only the MBR that needs replacing, this should allow you to boot Windows.

Added: Just saw *bcbc's* post. If the above doesn't work, post the results as he has requested.

i love you so much (it worked). i spent the last six hours trying to figure this out.

---

### Post by drs305 on 2011-01-21
> i love you so much (it worked). i spent the last six hours trying to figure this out.

Lucky guess.  ;-)

You can mark the thread solved via the 'Thread Tools' link near the top right of the first post if you don't have any other issues related to this topic.

---

### Post by dc200 on 2011-01-21
done. thankfully this was the only issue. thanks again for the help! :D

bcbc: i was running the vista recovery disc off a usb drive because my optical drive was broken. i'm not sure whether that may have had something to do with it.

i also let the recovery disc autodetect and fix any startup issues. it did pick up problems, but couldn't fix them for some odd reason.

---

