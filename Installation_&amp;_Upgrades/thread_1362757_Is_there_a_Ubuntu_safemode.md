---
title: "Is there a Ubuntu safemode?"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-12-23
My Ubuntu 9.1 installation crashes either during bootup or after about 10-20 seconds after bootup.  Is there a way to run Ubuntu with the minimal settings -- similar to Windows XP safemode?  It handles the recovery console fine and never crashes in Windows XP.  I ran memcheck and it's not the hardware.  Using Intel 945 graphics chipset.  Or is there any information that I can provide to help diagnose this problem?  Ubuntu 9.1 runs fine on one of my other systems.

---

### Post by mjjna on 2009-12-23
in the login screen, just before i have to enter my password, at the bottom i can choose between several session types, including gnome, kde and gnome safe mode.

---

### Post by phillw on 2009-12-23
> **SNYP40A1 said:**
> My Ubuntu 9.1 installation crashes either during bootup or after about 10-20 seconds after bootup.  Is there a way to run Ubuntu with the minimal settings -- similar to Windows XP safemode?  It handles the recovery console fine and never crashes in Windows XP.  I ran memcheck and it's not the hardware.  Using Intel 945 graphics chipset.  Or is there any information that I can provide to help diagnose this problem?  Ubuntu 9.1 runs fine on one of my other systems.

Hi,

I'd suggest booting and running from the LiveCD and see if that is stable as a starting point.

Phill.

---

### Post by scragar on 2009-12-23
You can launch ubuntu in command line mode if that's any help, at the grub screen press **e** to edit the line for ubuntu, then edit the line with the kernel information(it litterally starts **kernel**), and put at the end:
```
nosplash 3
```
This will turn off the splash screen and boot into command line more(init level 3 instead of 5 for full graphics).
Press enter, then **b** to boot this modified line, you should now be able to see the problem.

---

### Post by SNYP40A1 on 2009-12-23
> **scragar said:**
> You can launch ubuntu in command line mode if that's any help, at the grub screen press **e** to edit the line for ubuntu, then edit the line with the kernel information(it litterally starts **kernel**), and put at the end:
```
nosplash 3
```
This will turn off the splash screen and boot into command line more(init level 3 instead of 5 for full graphics).
Press enter, then **b** to boot this modified line, you should now be able to see the problem.

Can you tell me where to insert the **nosplash 3** command?  I have this:

[PHP]
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 945658e3-4807-4e75-aa06-bbdd4d52b\
0d5
linux /boot/vmlinuz-2.6.31-16-generic root=UUID=945658e4-...
...0d5 ro  quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
[/PHP]

I changed the splash to nosplash 3 as well as put nosplash 3 after the splash commend.  However, I still see the ubuntu startup screen and it looks like it's loading full graphics.  How should I modify the above to use minimal driver set.

---

### Post by SNYP40A1 on 2009-12-24
Not completely sure yet, but the problem might be related to the BIOS.  I have a MSI G945 and Core2Duo.  Others have had problems with that combo.  Appears to be a BIOS update available...I'll try it.

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by SNYP40A1 on 2009-12-25
Took a bios update, but didn't seem to fix :-(

---

