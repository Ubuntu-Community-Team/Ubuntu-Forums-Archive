---
title: "[SOLVED] 7.10 amd64 install hangs after initial screen"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by Macbeth417 on 2008-02-10
Using ubuntu-7.10-desktop-amd64.iso

I get a blank screen after making a selection from the cd initial splash screen. The cd spins initially for about 45 seconds then spins down, then nothing. The screen and keyboard receive no signal.

Tried:
re-burning the cd
booting from another CD/DVD-rom drive
checked the md5 checksum on the cd

I don't no were to go from here. If i could see and error or **anything ** happened I'd be scouring Google... but nothing happens... Just spins for a while, then nothing... machine stays on but nothing happens. 

System information:
AMD 64 3700+
Asus A8N-E motherboard
ATI radeon x800
Onboard Sound
1Gig  Ram
Seagate ST340824A 40.0GB (HDD master)
WESTERN DIGITAL WD1600JB 160GB (HDD slave)
Toshiba DVD-Rom SD-M1912 (DVD master)
Pioneer DVD-RW DVR-112D (DVD slave)
Keyboard and mouse sp/2 
Samsung SyncMaster 931bf LCD


I am downloading the alternate Amd64 iso and will try that,even if that does work, I would still like to understand the issue.

Any help would be greatly appreciated.

---

### Post by Partyboi2 on 2008-02-10
when you boot the live cd at the main menu press F6 and change the word splash to nosplash then press enter to boot. That might show you where its hanging.

---

### Post by Macbeth417 on 2008-02-10
Partyboi2:

I did just that, and followed the terminal output with a pen handy ready to write the output from the last line before hang... and I'll be damned it just booted into the live cd and Im writing this from Ubuntu... 

That's odd and I don't see what is different, but it is working and I'll go ahead and install and be happy with it.

:)

---

### Post by mrsteveman1 on 2008-02-10
I have an amd64 box that does something similar, edd=off in the kernel line fixes it every time.

Random crashes can be anything though.

---

### Post by Macbeth417 on 2008-02-10
I was able to install. Now, when I choose the standard ubuntu boot selection from the boot loader I experience the exact same thing I did with the cd.

I see
-------------------------------------
Kernel alive
Kernel Direct mapping tables up to 100000000 @ 800-d000
-----------------------------------
Then the screen goes black and soon after it hangs.

This is becoming somewhat frustrating.   I can boot into command line (second grub option)

---

### Post by Partyboi2 on 2008-02-10
Try removing splash again
At the grub menu, highlight the first option then press "e" to edit then select the line starting with "kernel" and press "e" again and change splash to nosplash, then press "enter" then "b" to boot. If this works you will need to add it to grub menu.lst so that its permanent. To do that open a terminal (Applications>Accessories>Terminal) Then type
```
gksudo gedit /boot/grub/menu.lst
``` menu.lst is with a small L
when it has opened look for this part:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro splash[/COLOR] change splash to nosplash. So it will look something like
# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro [COLOR=Red]nosplash[/COLOR]
save then type
```
sudo update-grub
```

---

### Post by Macbeth417 on 2008-02-10
Did the trick. Is this a common issue?

---

