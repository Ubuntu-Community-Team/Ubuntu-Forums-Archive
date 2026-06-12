---
title: "xubuntu installation problem"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by blitz_mohit on 2008-01-12
i am new to linux and downloaded xubuntu 6.06 to be my first linux distro but there is some problem with installation..
i checked the cd errors.it wasnt there so i tried to install after some unpackin and loadin it showed me the following error
4294674.828000 Pci :failed to allocate mem resource#6:100000@fd000000 for 0000:01:00.0

my comp config is:
pentium 3 451mhz
256 ram(2*128 chip)
60 Gb Hdd
52x cd writer
i440BX motherboard
nvidia 8 Mb graphics card
anyone suggestionz pls..

---

### Post by Partyboi2 on 2008-01-12
You could try using a boot option.
At the main menu press F6 and at the end of the line add
```
pci=routeirq
```then enter
if it works you will need to add to grub menu.lst. Post back if it works and someone will tell you how to add it to grub menu
If that does not work then maybe the alternate cd might be a option?
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)
Bug report
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294)

---

### Post by blitz_mohit on 2008-01-12
thanks for the wonderful piece of advice it worked though i would surely like to know wat did it to exactly..and yea u mentioned somethin bout grub menu wat was that..

---

### Post by Partyboi2 on 2008-01-12
to add to grub menu.lst
Open /boot/grub/menu.lst by either opening a terminal (Applications>Accessories>terminal)
and type
```
gksudo gedit /boot/grub/menu.lst
```or
press Alt+F2
and type
```
gksudo gedit /boot/grub/menu.lst
```then press "Run"
When it opens look for a section like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro[/COLOR]Add to the line I have highlighted the boot option 
```
pci=routeirq
```So it will look something like:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro **[COLOR=Blue]pci=routeirq[/COLOR]**[/COLOR]then save
then update grub menu.lst
type in a terminal
```
sudo update-grub
```then you should be away laughing :)

---

