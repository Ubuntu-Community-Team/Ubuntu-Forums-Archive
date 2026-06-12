---
title: "Questin about partitioning using Grub...."
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by lilskaterpunk on 2007-07-21
I had Windows XP installed first then I partitioned my hard drive so I could install ubuntu 6.10. I used the Gparted live cd and installed Grub and everything worked fine. Now my problem is my boot option screen looked like this (Screen shot 1 *before*) but the other day when I started my computer some reason it has 2.6.17-12-generic added to the list.... (Screen shot 2 *after*) Im not sure if I added it somehow? or is there a way to fix it so its like my first screen shot? or whats the difference with -10-generic and -12-gereric? Srry if this is a dumb question as its my first time installing Ubuntu and playing around with the partition setup...

Thanks:)

(Before)
[img]http://img440.imageshack.us/img440/5310/xpubuntu09previewzb5.jpg[/img]
(After)
[img]http://img227.imageshack.us/img227/3171/afterubuntuvg1.jpg[/img]

---

### Post by n00blet88 on 2007-07-21
thats what mine looks like aswell. my dad had a heart attack when he couldnt get on windows. id say tht is kind of handy if u wanton windows all u do is press arrow keys down t windows :D but i dont know what ur prob is soz im having problems aswell only installed ubuntu last night and having problems with wine

---

### Post by Pumalite on 2007-07-21
Don't worry about it. You are fine. They are just slightly different versions of a kernel. You have a working system, no?

---

### Post by lilskaterpunk on 2007-07-21
> **n00blet88 said:**
> thats what mine looks like aswell. my dad had a heart attack when he couldnt get on windows. id say tht is kind of handy if u wanton windows all u do is press arrow keys down t windows :D but i dont know what ur prob is soz im having problems aswell only installed ubuntu last night and having problems with wine
[img]http://bestsmileys.com/lol/12.gif[/img]Luckily this is my own computer:p Anywayz I didn't really have a problem...I was just curious why I had 2.6.17-10-generic and now 2.6.17-12-generic was added to the list.
> **Pumalite said:**
> Don't worry about it. You are fine. They are just slightly different versions of a kernel. You have a working system, no?
I sure do have a working system:) Both XP and Ubuntu work great but I'm wondering when I boot my computer and get the option to choose what OP system I want to use (between the Ubuntu) what one would be best... the 2.6.17-10-generic or 2.6.17-12-generic? is one newer or more stable?

Thanks for the fast replys guys;)

---

### Post by kirios on 2007-07-21
2.6.17-12 is an updated version of the kernel. Ubuntu keeps the older version (2.6.17-10 in this case) in the boot menu too  in case you have problems with the new kernel and want to revert back to the previous version. 

You can change the menu options by doing **Alt-F2** and typing 

```
gksudo gedit /boot/grub/menu.lst 
```
Add #  in front of the lines referring to the 2.6.17-10 kernel if you don't want this option on your grub menu.

---

### Post by Pumalite on 2007-07-21
> **lilskaterpunk said:**
> [img]http://bestsmileys.com/lol/12.gif[/img]Luckily this is my own computer:p Anywayz I didn't really have a problem...I was just curious why I had 2.6.17-10-generic and now 2.6.17-12-generic was added to the list.

I sure do have a working system:) Both XP and Ubuntu work great but I'm wondering when I boot my computer and get the option to choose what OP system I want to use (between the Ubuntu) what one would be best... the 2.6.17-10-generic or 2.6.17-12-generic? is one newer or more stable?

Thanks for the fast replys guys;)

Try both and see what you like best. I'd keep the old version in case of an update gone south. Is a good idea to make backup copies of your /boot/grub/menu.lst, and /etc/fstab. They may come in handy one day.

---

### Post by lilskaterpunk on 2007-07-21
> **Pumalite said:**
> Try both and see what you like best. I'd keep the old version in case of an update gone south. Is a good idea to make backup copies of your /boot/grub/menu.lst, and /etc/fstab. They may come in handy one day.
Sounds good\\:D/ Both kernels seem to run the same to me, so its all good:lolflag:

Big Thanks to all you guys that helped me out and very fast replys too!!:)

Thanks!

---

