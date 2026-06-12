---
title: "problem after upgrade to gusty,bushbox error"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by nikef on 2007-10-19
Hi all

i hope some1 can help,

i downloaded and installed gutsy last night 

when i switch pc on i get this error 

it gets to the splash screen and hangs for a while,then i get this error 

busybox v1.13/debian 1.1.13-5ubuntu7 built in shell (ash)

please can some1 help me to get the system back ,i can choose to boot into old ubuntu 

thanks

---

### Post by nikef on 2007-10-19
i pressed escape at grub and choose ubuntu o/s

i have  a few of gusty icons on there,is there anything i can do ?

---

### Post by nikef on 2007-10-19
does this mean i need to re-install  ](*,)

---

### Post by nikef on 2007-10-19
OK,
while looking  @ ubuntu  7.0.4 i have the green running man and lots of other gutsy stuff

i check my version of ubuntu in 

system ,about ubuntu it says

thank you for your interest in gutsy gibbon 7.10 

what is going on  :confused:

---

### Post by nikef on 2007-10-19
i also can change the desktop to kubuntu desktop

it tells me that i can upgrade to gutsy gibbon 7.10

is this my problem,do i have to update in kubuntu desktop ?

---

### Post by nikef on 2007-10-22
Hmmmmmmmm
Any1 got any answers yet :(

---

### Post by monkeymoo on 2007-10-22
Same as this? 
[http://ubuntuforums.org/showthread.php?t=586606](http://ubuntuforums.org/showthread.php?t=586606)

---

### Post by nikef on 2007-10-22
thanks,i doubt we are going to get this fixed :(

---

### Post by monkeymoo on 2007-10-22
Have you tried using Ubuntu 7.10, kernel 2.6.20-16-generic until maybe a fix is found? It works ok for me. And if you change your /boot/grub/menu.lst to default to that for the time being then your computer will start without a hitch.

---

### Post by nikef on 2007-10-22
thank you
how do i go about making it the default?

---

### Post by monkeymoo on 2007-10-22
Do "sudo gedit /boot/grub/menu.lst" in the terminal to open the file. 

You need to change the number next to "default" to correspond to the kernel you want to default to. The list of kernels is near the bottom of the file (the bit that isn't commented out). The one that works for me is Ubuntu 7.10, kernel 2.6.20-16-generic". 

Note that zero relates to the 1st one on the list. My guess is that the kernel that works would be the 3rd one, so that would mean setting default to 2. Just make sure you set it to the correct one! 

Good luck!

---

### Post by nikef on 2007-10-22
thanks,but i am an noob and not sure what to change,i have the list here
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7ed39ed6-6894-42d7-8ad1-46bde4e76cf7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by monkeymoo on 2007-10-22
The default line will be near the top of the file. Maybe line 14? Look around there. It'll say "default" and then a number. 

From what you've posted I think you should try changing that number to 4 and then reboot. 

Hope this works.

---

### Post by nikef on 2007-10-23
Thanks,will have a go at changing it

---

