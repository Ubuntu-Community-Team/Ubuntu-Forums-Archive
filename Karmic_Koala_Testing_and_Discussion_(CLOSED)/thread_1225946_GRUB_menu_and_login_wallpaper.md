---
title: "GRUB menu and login wallpaper"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-07-29
Well I finally got Alpha 3 to recognize my wireless card, whew! I was wondering if anyone knows how to hide the GRUB menu (like in legacy), and I want to change my wallpaper at the new login screen. Thanks in advance.

---

### Post by pmlxuser on 2009-07-29
sudo nano /boot/grub/menu.lst

change timeout from 3 to 0

you don't see the grub menu.

---

### Post by Gourgi on 2009-07-29
> **pmlxuser said:**
> sudo nano /boot/grub/menu.lst

change timeout from 3 to 0

you don't see the grub menu.
Karmic (after alpha2) uses grub2 and the above wont work.
uses this thread if you are using grub2 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by theozzlives on 2009-07-29
> **Gourgi said:**
> Karmic (after alpha2) uses grub2 and the above wont work.
uses this thread if you are using grub2 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thanks for providing that info, it still didn't show me how to hide the menu. I tried Startup Manager with no luck, I guess I'll have to be patient for Startup Manager 2.

I found a quick and dirty way to change the login wallpaper. I just renamed and copied my wallpaper to the backgrounds folder. I know this will change back with the next Alpha, but it works for now.

---

### Post by taavikko on 2009-07-29
> **theozzlives said:**
> 
I found a quick and dirty way to change the login wallpaper. I just renamed and copied my wallpaper to the backgrounds folder. I know this will change back with the next Alpha, but it works for now.

Actually it changes when the related package is upgraded

---

### Post by Hairy_Palms on 2009-07-29
do you mean the GDM background? if so look at 
[http://ubuntuforums.org/showpost.php?p=7583352&postcount=391](http://ubuntuforums.org/showpost.php?p=7583352&postcount=391)

---

### Post by dinxter on 2009-07-29
hidden menu is no longer a grub command but can be created using a [new script]("http://grub.enbug.org/Hiddenmenu") in /etc/grub.d/
ie, create a file, "/etc/grub.d/04_hidden_menu"
with,
> 
#!/bin/sh
 cat << EOF
echo -n "Press ESC for the menu..."
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then
 set timeout=0
else
 set timeout=-1
fi
EOF
an then run update-grub. a smarter version is on someones todo list as i remember

[EDIT] [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916)

added the file as attachment as web forms dont seem to like the formatting that bash craves :)

---

### Post by dinxter on 2009-07-29
now i think about it, if you've set a grub background image you might want to rename 04_hidden_menu to 41_hidden_menu or suchlike, moves it down the pecking order so the background is set before the countdown

---

### Post by theozzlives on 2009-07-29
> **dinxter said:**
> now i think about it, if you've set a grub background image you might want to rename 04_hidden_menu to 41_hidden_menu or suchlike, moves it down the pecking order so the background is set before the countdown


hairy_palms
It says it won't work with 64 bit

dinxter
Not the GRUB image, the GDM wallpaper

---

### Post by wayne_cat on 2009-07-29
> **theozzlives said:**
> hairy_palms
It says it won't work with 64 bit

dinxter
Not the GRUB image, the GDM wallpaper

from:

[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /data/pictures/Grassy.jpg
```

---

### Post by theozzlives on 2009-07-29
Thanks ya'll you've been a big help. Now to begin testing hehe.

---

### Post by zika on 2009-07-29
> **wayne_cat said:**
> from:

[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /data/pictures/Grassy.jpg
```Works. Thank You. Manual page is wrong i.e. lacks using user gdm ...

---

