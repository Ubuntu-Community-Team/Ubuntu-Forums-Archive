---
title: "[SOLVED] Nvidia drivers needed (i think) :("
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by cus1984 on 2008-02-16
lo all, 
the only way i can boot into Ubuntu 7.10 is by using the Live cd, and using the option similar to 'start/install with safe graphics'. Any other way, results in the desktop freezing immediately upon reaching it... i cannot right click, select anything and am not able to use the keyboard. Consequently i can only use ubuntu live, and am having difficulty finding a way of installing the drivers.

I dont have a hardware problem XP, and Mandriva run fine.

I'm looking for help, in that i need to get the drivers installed (thats what i'm presuming anyway).

there is an option on the 7.10 live distribution boot menu to 'install with driver update CD'

1) is this the way to go?
2) if so which drivers do i choose?
3) where do i get them? (7800 gt)
4) how will i get them to run, through this menu option?
5) any1 have any other ideas?

SPECS

athlon 3200+
7800 gt 256mb
256 or ram

by the way i have no experience of using any linux system even though i successfully installed mandriva.

---

### Post by Pumalite on 2008-02-16
You cannot boot a Live CD with 256 MB of RAM. Try this:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
(Alternate)

---

### Post by overdrank on 2008-02-16
> **cus1984 said:**
> lo all, 
the only way i can boot into Ubuntu 7.10 is by using the Live cd, and using the option similar to 'start/install with safe graphics'. Any other way, results in the desktop freezing immediately upon reaching it... i cannot right click, select anything and am not able to use the keyboard. Consequently i can only use ubuntu live, and am having difficulty finding a way of installing the drivers.

I dont have a hardware problem XP, and Mandriva run fine.

I'm looking for help, in that i need to get the drivers installed (thats what i'm presuming anyway).

there is an option on the 7.10 live distribution boot menu to 'install with driver update CD'

1) is this the way to go?
2) if so which drivers do i choose?
3) where do i get them? (7800 gt)
4) how will i get them to run, through this menu option?
5) any1 have any other ideas?

SPECS

athlon 3200+
7800 gt 256mb
256 or ram

by the way i have no experience of using any linux system even though i successfully installed mandriva.

Ok you have Ubuntu installed correct? If you do and you boot into recovery mode can you reconfigure your xorg. If you installed Mandriva after Ubuntu it has been my experience that Mandriva will not add Ubuntu to the boot.

---

### Post by cus1984 on 2008-02-16
mistake: its 512 of ram

my bad sorry

---

### Post by cus1984 on 2008-02-16
i've experienced the same problems, without mandriva installed, and anyways it is added to the boot.

Yes btw 7.10 is installed

I saw this on another post...... Do you mean to proceed with this???


Boot in Recovery Mode (select it from the GRUB menu)

type:
Code:

sudo dpkg-reconfigure xserver-xorg

select the "nv" driver and press ENTER whenever you don't know the answer to a question.

then type:
Code:

reboot

and boot as usual

On next reboot the Xserver should work fine

---

### Post by overdrank on 2008-02-16
> **cus1984 said:**
> i've experienced the same problems, without mandriva installed, and anyways it is added to the boot.

Yes btw 7.10 is installed

I saw this on another post...... Do you mean to proceed with this???


Boot in Recovery Mode (select it from the GRUB menu)

type:
Code:

sudo dpkg-reconfigure xserver-xorg

select the "nv" driver and press ENTER whenever you don't know the answer to a question.

then type:
Code:

reboot

and boot as usual

On next reboot the Xserver should work fine

Hi and yes or use the driver vesa. Then you can use the restricted drivers or Envy. :)

---

### Post by cus1984 on 2008-02-16
Thanks very much for the posts, The 'nv' drivers worked for me even though its only booted  into low graphics mode.... but at least Ubuntu is finally running after two days and about 10 different installs. Now i can try to install the proper drivers and have a pay around with Linux lol :)

---

