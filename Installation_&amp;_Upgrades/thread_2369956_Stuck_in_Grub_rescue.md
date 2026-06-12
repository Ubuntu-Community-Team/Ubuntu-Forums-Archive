---
title: "Stuck in Grub rescue"
date: 2017-08-29
forum: Installation &amp; Upgrades
---

### Post by bottaetok on 2017-08-29
I  am quite a newbie to Linux. My laptop is Lenovo G560. Lubuntu was installed from live USB by choosing "Erase everything and install...".
A few days ago I used Boot Repair to fix  some problems, but it hasn't finished: after the step of removing Grub  files, I made my laptop hibernate and intended to continue later (I  didn't know that would cause serious damage). 
 
And now, after it woke up from hibernate, despite pressing Ctrl+Alt+Del  many times, only Grub-rescue shows up, I cannot follow popular solutions  from the Internet to locate Grub files because they are completely  removed and not replaced. I also can't even enter BIOS settings and Boot  options to boot from a Live USB (from my little knowledge,I think because of hibernating). 
 
This is what I got: 
 
    ```
error: file 'boot/grub/i386-pc/normal.mod' not found. 
Entering rescue mode...    
grub rescue> ls (hd0,1) 
(hd0,1): Filesystem is ext2. 
grub rescue> setprefix=(hd0,1)/boot/grub 
grub rescue> set root=(hd01,1) 
grub rescue> insmod normal
error: file '/boot/grub/i386-pc/normal.mod' not found. 
```
 
I tried to power off, unpluged power suppliers, then pressed and holded the power button, then  turned it on again but no boot options at all, just the Lenovo splash  screen as you can see in the photo.

I asked this on Askubuntu, but I didn't receive any reponse.

Please give me some advices, thank you all!

---

### Post by oldfred on 2017-08-29
Is this an full drive encrypted LVM install?
That first partition is ext2 may indicate BIOS boot & LVM.

The normal not found is often booting in the wrong boot mode (UEFI/BIOS) or version of grub is different.

But you need to get into UEFI/BIOS to do anything. 
I might try the full power down again, be sure to remove laptop battery.
If that does not work, you may have to remove the coin battery on motherboard to totally reset. A few systems have a tiny hole in bottom for reset, but most are tablet type systems that have that.

---

### Post by bottaetok on 2017-08-29
I don't remmeber clealr about full drive encrypted LVM, but after first boot a message about drive encryption poped up and a phrassphase was given.
I've tried full power down countless times without battery, still no results.
I will remove motherboard's coin battery as you suggested.
Thank you!

---

### Post by oldfred on 2017-08-29
Also if you remove coin battery, you may have to reset any changes you made in UEFI.
With BIOS it always reset everything. UEFI now has NVRAM, so some settings may be saved, but best to always check your settings after a reset.

---

### Post by bottaetok on 2017-09-03
Solved!

I found this: **[https://unix.stackexchange.com/questions/77263/use-grub-rescue-to-boot-from-windows-xp-partition-cd-or-usb](https://unix.stackexchange.com/questions/77263/use-grub-rescue-to-boot-from-windows-xp-partition-cd-or-usb)**
and followed a some what similar solution: install Lubuntu to a USB like with hard drive and set prefix, set root onto it, then boot and reinstall like normal.
Thank you very much, Oldfred, but I am very hesitant to touch inner hardware.

---

