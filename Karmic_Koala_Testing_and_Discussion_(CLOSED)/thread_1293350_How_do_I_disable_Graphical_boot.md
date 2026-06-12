---
title: "How do I disable Graphical boot?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tijuana on 2009-10-16
Hi!

I'd like to disable all of the GUI boot, so thinking as it was in previous versions of (kx)ubuntu I installed rcconf to disablegdm... but to my surprise both gdm and kdm are disabled! How do I get a GUI-less boot in this new version of ubuntu?

Thanks!

---

### Post by renkinjutsu on 2009-10-16
sudo nano /etc/defaults/grub

where it says ```
quiet splash
```
change it to just ```
quiet
```

---

### Post by tijuana on 2009-10-17
did that, nothing happened.

BTW what I want is for ubuntu to show info on everything it's loading at boot time and then drop me into a tty (no GUI) so I can login and manually start X server as I see fit

Thanks!

---

### Post by tijuana on 2009-10-17
bump

---

### Post by cariboo on 2009-10-17
With older versions, all you had to do was disable gdm and usplash eg:

```
sudo update-rc.d -f gdm remove
```

With the changes that have been made to the boot process of a full installation, I'm not sure if it will work any more, but give it a try.

---

### Post by cdahmedeh on 2009-10-17
> **renkinjutsu said:**
> sudo nano /etc/defaults/grub

where it says ```
quiet splash
```
change it to just ```
quiet
```

Don't forget to run "sudo update-grub" after you have made those changes ?

---

### Post by emarkay on 2009-10-17
It ** still** doesn't actually give the same text-boot as Jaunty, but I understand that is by design and can't be changed.  

However,  you will find if you boot from  Recovery Menu, that it really does show everything.  Only the "X" loading text is obscured.  The "Cylon Warrior Throbber Thing" is there regardless, even if ypu remove "quiet splash".

---

### Post by cdahmedeh on 2009-10-17
You can remove the 'cyclone warrior' by removing the package called 'xsplash'. You will still be booting into X at the same time, you will just see a waiting cursor instead.

---

### Post by wnelson on 2009-10-17
You can fix this problem by editing /etc/event.d/rc-default file
First backup file,

sudo cp /etc/event.d/rc-default /etc/event.d/rc-default.bakup

Open /etc/event.d/rc-default

Find all lines read as - telinit 2 and replace with telinit 3

---

### Post by tijuana on 2009-10-17
wow! a lot of info for a weekend day, I'll try it out monday morning

Thanks a lot for your feedback!

Regards

---

### Post by tijuana on 2009-10-18
ok...

so I couldn't wait until monday...

after update-grub the splash screen is finally out of the picture, but ubuntu still boots X.

@wnelson I can't modify the file you mention 'cause it doesn't exist on my pc. In fact, /etc/event.d/ doesn't exist on my pc... any Ideas?

Thanks!

---

### Post by SheVa77 on 2009-10-18
Try to move the file /etc/init/gdm.conf elsewhere and reboot. Don't remove it since you may need it back in the future. I didn't try this but theoretically I think this should work

---

### Post by SheVa77 on 2009-10-18
Tried it - works. Removing 'quiet splash' from the /etc/default/grub and moving the gdm.conf out of the /etc/init brings the pure command line. startx will bring gnome up.
I'm not sure that everything will work in the gnome since maybe there are other services that are dependent on the 'gdm' and not started.

---

### Post by tijuana on 2009-10-18
thanks! I'll try it out and see if something comes up during the week

Regards!

---

### Post by fluxbuntu on 2009-10-18
If your looking for an all verbose boot as debian has, I did it by editing /boot/grub/menu.lst Just remove quiet and splash from the first kernel listed, or all of them if you wish.

 from...
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic

to...
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c ro 
initrd        /boot/initrd.img-2.6.28-15-generic

---

### Post by tekstr1der on 2009-10-18
> **fluxbuntu said:**
> If your looking for an all verbose boot as debian has, I did it by editing /boot/grub/menu.lst Just remove quiet and splash from the first kernel listed, or all of them if you wish.

 from...
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic

to...
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3c58d45d-ae5a-4a4f-9b44-9bfbd1ccca4c ro 
initrd        /boot/initrd.img-2.6.28-15-generic

We are in the karmic forum. This is no longer the way to achive a verbose text-only boot. Did you read any previous posts in this thread?

---

### Post by SheVa77 on 2009-10-18
Forgot to mention, however it was said before by others, that after editing the /etc/default/grub you have to run:
sudo update-grub2

---

### Post by tijuana on 2009-10-18
yep! moved that gdm config file and now I get a textmode boot

Thanks! =D

---

### Post by tijuana on 2009-10-18
ok so after following the last tip it worked but some functions stopped working properly (like any app that requires elevated privileges must be explicitly started from a terminal instead of prompting for the password on start). So I took a look inside the config file.

the last 2 line announce gdm is starting and then start it (or that's what I inferred) so I commented them out, renamed the file back so it would load on startup and viola! I now have terminal boot with the gdm script in place. maybe not starting gdm itself won't make the problems mentioned go away, but at least the rest of the file is loading, and that's (I guess) better than no file at all.

Regards!

---

### Post by tijuana on 2009-10-19
I uncommented the second to last line and am still booting into a terminal. now whenever I want to start X, I use "sudo gdm-binary" and boot into gnome with my account and everything just as if I were booting using gdm in the first place.

Regards!

---

