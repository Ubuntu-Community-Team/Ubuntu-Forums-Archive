---
title: "[SOLVED] BUG: soft lockup - CPU#0 stuck for 11s! [modprobe:1292]"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by raley on 2008-09-15
Ok, im getting this error, and found to remove the "quiet splash --" and it will load from the disk.  but i can't get it to do this from the HD.

Now, how do i set this to ALWAYS remove these things?

Im running an Acer Aspire 5050 (64bit, 1gb ram, 120g hd) with Ubuntu that i received on disk from Canonical.  It is Ubuntu 8.04 LTS Desktop Edition (64-bit).

someone please help.

---

### Post by Partyboi2 on 2008-09-15
when you boot and see "grub loading ..." press "Esc" then highlight the kernel you are booting with and press "e" to edit then highlight the line starting with "kernel" and press "e' again then at the end add your boot options then press "b" to boot. Once you are at the Desktop open a terminal (Applications>Accessories>Terminal) and open your /boot/grub/menu.lst with
```
gksudo gedit /boot/grub/menu.lst
```then look for a section looking like this
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro quiet splashand edit this line
```
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro quiet 
```to what you want, then save and back in the terminal
update grub
```
sudo update-grub
```

---

### Post by raley on 2008-09-15
Thank you for the quick response.

Is there a way to turn off the ACPI, when i installed i had to turn that off also.

---

### Post by Partyboi2 on 2008-09-15
just add it to your menu.lst like I have posted above adding acpi=off to [FONT=monospace]
[/FONT]```
# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro acpi=off
```
then update grub after the changes
```
sudo update-grub
```

---

### Post by raley on 2008-09-15
OK.  I can get it to run when doing "try Ubuntu without any changes to your computer"

IF in the boot options i delete splash and quite --

AND in other options check apci=off

My start is:

> root  (hd0 ,0)
kernel  /boot/vmlinuz-2.6.24-16-generic root=UUID=660de69f-a93e-45f5-9e15-cc76a8238cc8 ro apci=off [COLOR="Red"]*** REMOVED QUIET AND SPLASH ***[/COLOR]
initrd  /boot/initrd.imp-2.6.24-16-generic
[COLOR="Red"]*** REMOVED QUIET ***[/COLOR]

AND IT WORKS!!!!!!!


thank you so much. how do i give you thank points!

---

### Post by Lord C on 2008-11-16
This also helped me. Bought a new GIGABYTE WI07HT card and it was stopping Ubuntu EEE from booting, unless I disabled WiFi in BIOS.

Turned off acpi, and now Ubuntu EEE boots fine.

Of course I have no battery monitor now :/ But I'm hoping that will be fixed in 8.10. Whatever the problem was :/

---

