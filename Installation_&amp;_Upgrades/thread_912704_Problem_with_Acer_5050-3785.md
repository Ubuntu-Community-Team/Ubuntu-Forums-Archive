---
title: "Problem with Acer 5050-3785"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2008-09-07
hello all
i want install 8.04 but i have a problem with acpi....how i can fix this issue...???
on this moment i use 7.10

---

### Post by Partyboi2 on 2008-09-07
try using a boot option at boot. At the main menu press F6 and add the boot option to the end of the line and see if you have success. Here are a few you can try.
noapic
nolapic
acpi=off

---

### Post by chanfle on 2008-09-07
> **Partyboi2 said:**
> try using a boot option at boot. At the main menu press F6 and add the boot option to the end of the line and see if you have success. Here are a few you can try.
noapic
nolapic
acpi=off

ok...but after install ubuntu...how i can boot the OS....and the fan it work 100%....

---

### Post by Partyboi2 on 2008-09-07
When you find the boot option that works for you and you have installed ubuntu you will need to boot again with that option then add it to your menu.lst 
To use the boot option after you have installed press "Esc" when you see "grub loading..". this will take you to the grub menu where you highlight the kernel you are going to boot into (normally the 1st one) then press "e" then highlight the line starting with "Kernel" and press "e" again then at the end of the line add the boot option, then press "b" to boot.
To make this change permanent, once you are at the Desktop open a terminal (Applications>Accessories>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
``` then look for the section looking something like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro[/COLOR] and add the boot option to the end of the highlighted line, then save and back in the terminal type
```
sudo update-grub
```

---

### Post by chanfle on 2008-09-07
> **Partyboi2 said:**
> When you find the boot option that works for you and you have installed ubuntu you will need to boot again with that option then add it to your menu.lst 
To use the boot option after you have installed press "Esc" when you see "grub loading..". this will take you to the grub menu where you highlight the kernel you are going to boot into (normally the 1st one) then press "e" then highlight the line starting with "Kernel" and press "e" again then at the end of the line add the boot option, then press "b" to boot.
To make this change permanent, once you are at the Desktop open a terminal (Applications>Accessories>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
``` then look for the section looking something like this:
 and add the boot option to the end of the highlighted line, then save and back in the terminal type
```
sudo update-grub
```

ok...but what line i need to add on the file...???

---

### Post by Partyboi2 on 2008-09-07
Add on what ever boot option worked for you.
So if noapic worked for you, you would add that to the end so it would look something like this:
                                                > ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=805b623e-614e-4560-ae10-e1cf0b44876a ro splash [COLOR=DarkOrchid]noapic[/COLOR][/COLOR]
But its no point adding to your boot menu.lst if they don't work for you, so you need to try out different boot options to see if one works for you.

---

