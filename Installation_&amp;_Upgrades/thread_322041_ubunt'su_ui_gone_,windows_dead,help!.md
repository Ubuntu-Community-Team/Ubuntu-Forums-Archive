---
title: "ubunt'su ui gone ,windows dead,help!"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by matka on 2006-12-19
i installed linux 6.06 yesterday for the first time on my pc which also has xp installed..  today when i tried to install the nvidia drivers the ui crashed ..i get this error mssg on a blue screen...
"failed to start x server (your graphical interface). it is likely that it is not set up correctly. would you like to view the x server output to diagnose the problem?"
 
i click ok and get x"window system server version 7.0.0.... bla bla .. and in the end...
"(ww)Nvidia: no matching device section for instance (bus id pci:1:1:0:0)"
"(ee) no devices detected 
Fatal sever error 
no screens found...


also when i tried loggin in to windows it gives me "hal.dll is corrupted or missing".. tried copying new file from xp cd .. but i still get the above mssg...


so now i m again on ubuntu live cd .. plzzz help ...... how do i fix linux ui (or windows)??

---

### Post by meng on 2006-12-19
I suggest trying this:
sudo dpkg-reconfigure xserver-xorg

and among the first questions you will be asked is what video driver to use
choose "nv" (not "nvidia")

and then for the other choices you can generally take the default (just hit enter)
then:
startx

---

### Post by matka on 2006-12-19
thx for replyin so fast..
w8 i will try what u said

---

### Post by nish_lal on 2006-12-19
thaxxxx a lot ... got back into ubuntu ui ... ur directions worked like a charm:D :D :D 
 

any idea abt what to do wid windows??? (format it eh?:-k :-k )

---

### Post by meng on 2006-12-19
No, I would advise you keep Windows until you're sure you never want to put it back on. Even if you have another computer with Windows on it, it's more of a hassle if you decide you need a dual-boot, to reinstall Windows after Ubuntu rather than what you have now, Ubuntu installed after Windows. By the way at the moment you're running open-source non-proprietary video drivers, so there's no decent 3d acceleration. If you need the 3d-accel, you'll have to install the nvidia drivers, but without screwing up the system this time :)

---

### Post by nish_lal on 2006-12-19
k thx ... going over to windows forums to fix it ..  then i will try nvidia drivers again for ubuntu...

---

### Post by meng on 2006-12-19
Sorry, didn't read your post properly and didn't realize that Windows is screwed too. You can reinstall Windows over the non-working Windows, but there's a small bit of jiggery-pokery you need to do after that to get back to a dual-boot situation (Windows is selfish and doesn't install with a dual-boot option).

---

### Post by nish_lal on 2006-12-19
can u tell what sort of "jiggery-pokery" are uy reffering to .. or can u gimme a link where i can read about it?

---

### Post by thelinuxguy on 2006-12-19
> **nish_lal said:**
> can u tell what sort of "jiggery-pokery" are uy reffering to .. or can u gimme a link where i can read about it?

You will need to restore grub so that you can boot into Ubuntu. Immediately after installing XP you won't have the grub menu. 

You can do either of the following:

1) Use the Ubuntu Live CD. 
Then issue the following commands as root:

grub
root (hd0,?)  (? is a number which indicates where your Ubuntu partition is)
setup (hd0)

2) Use the Super Grub Disk
[http://supergrub.forjamari.linex.org/index.php](http://supergrub.forjamari.linex.org/index.php)

The link to SuperGrub was from [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation")

---

