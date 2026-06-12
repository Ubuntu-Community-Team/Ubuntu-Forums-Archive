---
title: "Installation Problems"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by Stannly on 2006-11-02
hi there im new to ubuntu, but im having installation problems, i have a amd64 opteron and geforce 6800gs and a asus mobo, i boot from the cd and the boot menu comes up wether i choose install or boot into safe mode the loading screen pops up looking a bit grey and outof place, after its loaded i get a screen that looks corrupt, all white and green rectangles with lines thru,and thats it 


i have tryed both a 86 version for amd opteron and a normal version, i know for a fact the normal version works because i installed it on my brothers machine. 

any help would be appreciated thx

---

### Post by taurus on 2006-11-02
Have you tried using the alternate CD version!  It will let you install Edgy using text base so no need to boot into Live first...  You can download the alternate CD at the same place that you've downloaded the desktop CD/LiveCD.

---

### Post by Stannly on 2006-11-02
thx ill give that a go when i get back rom uni in 2 hours
hope it works :P if not ill try the i386 version. bloody opteron

---

### Post by taurus on 2006-11-02
Well, you can give me your opteron and you can have my x86!!!  ;)

---

### Post by Stannly on 2006-11-02
heh opteron 165 tis nice if u get the right amd drivers

---

### Post by Stannly on 2006-11-02
ok i used the alternate instalation and the text install worked up until i rebooted after instal

but this time the recover console worked so i ran 

sudo dpkg-reconfigure xserver-xorg and choose vesa as the gfx driver ( i dont know if this is the right one for my geforce 6800) i rebooted and i could then see the login page, but when i tried to login(with correct details) it the screen went blank and just returned me to the login page. if i entered my details wrong it said details wrong. 

could anyone tell me what driver to use and how to get round that login problem

---

### Post by taurus on 2006-11-02
Since you have nVidia graphic card, why not pick "nv" instead of "vesa" as a driver.  And if you boot into a recovery mode, no need to use "sudo" since you are already log in as root!  So, you can either run that command again, without the sudo in front, or you can edit your /etc/X11/xorg.conf and replace "vesa" with "nv".

```
nano -w /etc/X11/xorg.conf
```
Save the change and see if you can bring up X with

```
startx
```

---

