---
title: "How do I get stuff I input in boot options to stay wean I install permenently?"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by $4real$ on 2008-02-21
I have a HP dv6000 laptop and I have been struggling to get it to work, I have been following this guide at this link [https://wiki.ubuntu.com/HP_dv6000_Series]("https://wiki.ubuntu.com/HP_dv6000_Series") 
now it has been very useful and I like Ubuntu very much, but in order for the live cd to work I have to hit f6 then enter noapic nolapic for it to work, also i belive i have to put in irqfixup as well because the usb wont work. Now my question is now that I want to install permanently, am I going to have to add these things every time I start my computer?:confused: 
or is there a way to add it for good so i don't have to? 
I really wanna get this installed and working proper, any help would be very useful 
Thank you all

---

### Post by Partyboi2 on 2008-02-21
after you have installed ubuntu you may need to add them to your menu.lst so that it boots with those options automatically each time.
After you have installed and are rebooting press Esc when you see stage1_5 ...loading, which will take you to the grub menu,  then highlight the kernel and press "e" to edit then highlight the line starting with kernel and press "e" again then add your boot options then press enter then "b" to boot. Once you have booted to the desktop open a terminal (Applications>Accessoiries>Terminal) and type
```
gksudo gedit /boot/grub/menu.lst
``` Thats a small L
then look for 
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro quiet splash[/COLOR] then add your boot options to the end of the line starting with [COLOR=Red]#kopt[/COLOR].
after you have added save and then back in the terminal update grub
```
sudo update-grub
```

---

### Post by $4real$ on 2008-02-21
Thank you very much, that should solve my problem perfectly :KS im gunna go install now, thank you for all the help

---

