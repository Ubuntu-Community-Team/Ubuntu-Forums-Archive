---
title: "Won't Install!"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Qinjuehang on 2007-10-04
The first part of the error is:
Int 14: CR2 f8000000 error 00000000
Didn't have time to take all down, was pretty long. Anyway, I had tried updating BIOS, and adding acpi=off noapic and still doesn't work. Compaq SR1150AP. Anyway I heard there are a lot of problems with running Ubunru on Compaq Presario, but I really want to get it to work, because my windows is pretty screwed, Firefox taking over a whole minute to start up (my registries are not in a good condition). So anyone who has any idea what went wrong, please respond...:)

---

### Post by Qinjuehang on 2007-10-04
Ok...SUCCESS!!! used "linux acip=off irqpoll" together. Without quotes, of course :lolflag: I'm defragmenting my drive now in Windows (I came to Windows cuz I forgot my wireless key stored in a encrypted zip)

---

### Post by Nebutron on 2008-02-09
> **Qinjuehang said:**
> Ok...SUCCESS!!! used "linux acip=off irqpoll" together. Without quotes, of course :lolflag: I'm defragmenting my drive now in Windows (I came to Windows cuz I forgot my wireless key stored in a encrypted zip)

Hi, having the same problem, but don't understand how to do the apci=off irqpoll thing.  Can you explain to a relative newb how to do that?

---

### Post by Partyboi2 on 2008-02-09
If you are trying to install from the live cd at the main menu press F6 then at the end of the line add ```
apci=off irqpoll
```then press enter to boot.
If you are trying to add it to ubuntu that is already installed, you will need to access the grub menu at boot when you see something like  "stage1_5..." by pressing Esc if you are not dual booting. If you are dual booting then you should see grub menu when you boot. When you are at grub men highlight the kernel you are going to boot into and press "e" then highlight the line starting with "kernel" and press "e" then at the end of the line add ```
apci=off irqpoll
``` press "enter" then "b' to boot
If the boot options work for you, you will need to add them to the grub menu.lst so that its permanent.

Edit: _[COLOR=Blue]How to add to grub menu.lst[/COLOR]_
open a terminal (Applications>Accessories>Terminal)
type:
```
gksudo gedit /boot/grub/menu.lst
``` (That is a small L for menu.lst) When it opens look for this part:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro splash[/COLOR]Add apci=off irqpoll to end of the line starting with kopt=root
so it will look something like this
[COLOR=Red][COLOR=Black]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro splash[/COLOR] acpi=off irqpoll
[COLOR=Black]Then save and type in the terminal[/COLOR]
[/COLOR]```
sudo update-grub
```

---

