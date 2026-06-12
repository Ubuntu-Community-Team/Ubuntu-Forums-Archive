---
title: "noapic after installation?"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by GnomeFoot on 2008-01-16
When Im running the livecd I have to start with the noapic command. If I install Ubuntu onto my harddrive, do I have to use the noapic command everytime I boot?

---

### Post by Partyboi2 on 2008-01-17
you will need to add it to the grub menu.lst once ubuntu is installed
To do that open up grub.menu.lst
Alt+F2 and type
```
gksudo gedit /boot/grub/menu.lst
```look for something like this
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro [/COLOR][COLOR=Red] 
[COLOR=Black]and add noapic to the end of the line I hightlighted so it will look like
[/COLOR][/COLOR]```
# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro noapic
```then save
and open a terminal (Applications>Accessories>Terminal)
and update grub
```
sudo update-grub
```

---

