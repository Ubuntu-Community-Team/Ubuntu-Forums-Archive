---
title: "ubuntu takes long time to boot and the logo will not show up"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by lifeheart on 2008-03-18
Hello everyone 


I installed ubuntu 7.10 on my laptop (dual boot) with vista

the ubuntu works 100% fine

the only thing is when I power up my laptop and select ubuntu it will take 2 -3 minutes just to boot. and during this time I will not see anything but black screen. ( I can't see ubuntu logo and the loading bar beneath it)

is there any way I can change the boot screen to text based where I can see the services and scripts as they load up just like  Red Hat text mode boot screen ?

thanks

---

### Post by Rocket2DMn on 2008-03-18
The reason that you're not seeing the logo is probably because it is at the wrong resolution. I don't have that fix off the top of my head, but you can easily search for it.
To show text only at bootup, you need to edit the grub menu.lst file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Where it says something like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=30fcb748-ad1e-4228-af2f-951e8e7b56df ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```
Remove the "quiet" and "splash"
You can also add "savedefault" to the end (add a new line at the end) so it doesn't revert back to quiet and splash when your menu.lst file is auto-updated as it sometimes is.
So the new entry would look similar to this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=30fcb748-ad1e-4228-af2f-951e8e7b56df ro
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
savedefault
```

Do NOT copy and paste my entires since your kernel may be different and your UUID (and possibly root hd) will certainly be different.

---

### Post by Northsider on 2008-03-30
Yes, I'm getting the same problem and I cannot find anything about changing the resolution in the search.  :-[

---

### Post by The Cake is a Lie on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=579684&page=3](http://ubuntuforums.org/showthread.php?t=579684&page=3)

This thread helped me fix this issue

If you have an ATI card, this even helped me, 

```
sudo gedit /etc/usplash.conf
```

Set your resolution and then type this into console

```
sudo dpkg-reconfigure usplash
```

Good Luck everyone!

---

### Post by Northsider on 2008-03-30
Thanks, I also found this post a little bit ago that seems to have worked:

[http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

---

### Post by lifeheart on 2008-04-03
I would like to thank all of your for your kind support 

I would like to inform you that the solution provided by (The Cake is a Lie) was effective and fixed the problem. 

I can see now the loading bar and everything 

I have changed the screen resolution...  I set it to 1280 x 800 and it fixed it

many Thanks to you guys for your kind help. :)

---

