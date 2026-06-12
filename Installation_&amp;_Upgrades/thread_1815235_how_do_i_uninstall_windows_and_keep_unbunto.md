---
title: "how do i uninstall windows and keep unbunto"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by bradycc on 2011-07-30
i am kinda new to ubunto how do i un-install windows after i have installed ubunto.

it asks me witch OS i want to run when i turn on the computer. if you could, can you give me a step by step process on how to un-install windows. or point me somewhere where i can find a step by step process to tell me how to do it.

thanks for the help.

---

### Post by Roter1337 on 2011-07-30
If you were installing ubuntu it gave you an option to wipe disc and install it, Thats the option you want if you want to get rid of windows. But since you didnt, Install Gparted live, burn it to a cd, boot into it, go to partition editor, delete windows, expand ubuntu partition to span to drive. Good luck!

---

### Post by bradycc on 2011-07-30
how do i find Gparted Live?   

i can onlyfine Gparted.

---

### Post by Duncan Williams on 2011-07-30
You can use gparted.
boot it in ubuntu and if you are comfortable with it you can delete your windows partition. (and reformat, resize, etc.)
Gparted is a partition manager.
more info:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)

[http://download.cnet.com/GParted-LiveCD/3000-2094_4-10698802.html](http://download.cnet.com/GParted-LiveCD/3000-2094_4-10698802.html)

tutorial:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Hakunka-Matata on 2011-07-31
Gparted (Gnome Partition Editor) is not installed by default on a new installation.  So you have to install the program first.  You can install it by using the 

[LIST]
[*]Ubuntu Software Center under Applications, or by using
[*]synaptic Package manager under System, Admiinistration or
[*]lastly by using the Terminal. Open a Terminal under Applications, Accesories,   In the terminal window type this code:
[/LIST]
 ```
sudo apt-get install gparted
```type in your password at the prompt, you will not see anything while typing your password, just type it in and hit Enter.

---

### Post by halj32 on 2011-07-31
don't forget to update grub after you've removed your windows partition


edit
just in case you don't know how
sudo grub-update

---

