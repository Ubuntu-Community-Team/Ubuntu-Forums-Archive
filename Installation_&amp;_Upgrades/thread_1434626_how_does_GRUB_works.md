---
title: "how does GRUB works ?"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by 2xd on 2010-03-20
hi all,
 
i've decided not to ask my question (regarding installing windows 7 on Vista & Ubunto 9.10 system) but instead i would like to understand it myself if I could.
 
so, can anyone please explaing to me briefy as he can, how the hall does all the boot issue applys ? i mean, while I install windows, where does it put his boot manager and where does ubunto put it ? 
 
how can i make changes there ? if at all
 
i case windows has replaced the boot manager with his one, how can i put GRUB in there back again ?
 
thanks for any one who have sometime for me. :)

---

### Post by bigpayne69 on 2010-03-20
Ok so here is the down and dirty on GRUB. If you are running true dual-boot, or in your case tri-boot, GRUB acts like an middle man between your bios/post and your boot loader. GRUB doesn't delete the boot loaders for your Windows OS because its on a completely different partition. All that GRUB does is that when your POST is done, it hands the computer over to GRUB, from there, you get a count down and either you can stop the count by pressing ESC and then manually selecting what OS to load or you can let the timer run out and GRUB will automatically load whatever OS you have set as the first one in your GRUB menu. Thats about it

---

### Post by 2xd on 2010-03-20
thanks man
 
so basiicly how can i control GRUB from windows ?
in other words, if i'm due to upgrade to win7, how can i make sure GRUB will know it ? and will be able to direct me in to it ?
 
and btw, what is POST ?

---

### Post by bigpayne69 on 2010-03-20
POST is the self test that your computer does when you first turn it on before it ever trys to load an OS. As far as the windows 7 thing goes, Grub references the the operating system by the partition its in so if you are trying to upgrade from Vista to 7 then 7 will be on the same partition that your vista was on so as far as you grub menu goes you shouldn't have to change anything. Just a heads up though, I loaded XP on my laptop that had been strictly Ubuntu Hardy on it and when I did, the windows boot loader took over and grub wouldn't even pop up; it would just load straight into windows. The only way I was able to finally fix it was to was to use an Ubuntu boot disk, boot off of it, reinstall grub, and then change the grub menu back to the way I wanted it. 

PS: I have never dealt with Vista or 7, I have only used XP and earlier when it comes to Windows so what I did should work for you but you never know when it comes to ol' Microsoft

---

### Post by bigpayne69 on 2010-03-20
sorry, I forgot to mention, grub can be modified temporarily from the grub menu itself but if you want to make permanent changes to the menu, the way that I do is to use sudo gedit to open the menu.lst that is inside the grub folder.

---

### Post by 98cwitr on 2010-03-21
[http://cquirke.wordpress.com/2009/11/20/edit-grub-menu-in-ubuntu-9-10-and-older-2/](http://cquirke.wordpress.com/2009/11/20/edit-grub-menu-in-ubuntu-9-10-and-older-2/)

---

### Post by 2xd on 2010-03-21
well thanks you all,
 
i'll update you after i'll update to w7 so you could know what happaned...
 
 
btw, if anyone can direct me to more harsh explanation regarding the location of the boot loaders (technically), i'll be more then happy to learn.
 
thanks

---

