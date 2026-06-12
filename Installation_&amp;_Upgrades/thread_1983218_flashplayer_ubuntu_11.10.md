---
title: "flashplayer ubuntu 11.10"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by bushmonkey90 on 2012-05-19
im fairly new to linux but im getting the hang of things ,however, i am having trouble geting a flash player installed. Ive tried various ways to get one. on the ubuntu software center it never finishes applying changes. Ive tried searching google for answers but no luck. Can anyone help?

---

### Post by VMC on 2012-05-19
> **bushmonkey90 said:**
> im fairly new to linux but im getting the hang of things ,however, i am having trouble geting a flash player installed. Ive tried various ways to get one. on the ubuntu software center it never finishes applying changes. Ive tried searching google for answers but no luck. Can anyone help?

What Ubuntu release are you using, what browser, and what methods have you tried?

I use chrome, and I have to install it manually:
```
if [ ! -d /usr/lib/mozilla/plugins ]; then sudo mkdir -p /usr/lib/mozilla/plugins; fi; sudo install -m 644 libflashplayer.so /usr/lib/mozilla/plugins/
```
chrome is suppose to have it built in, but it doesn't work for me.

edit: This might be what your looking for, if you use firefox:

```
sudo apt-get install flashplugin-installer
```

---

### Post by darkod on 2012-05-20
My approach is: forget about everything in the repositories/software centre.

Remove all packages you installed trying to make flash work.

Go to the adobe website, download the flash for linux. It's a tar.gz archive. Extract somewhere in your Home folder.

In your Home folder press Ctrl + H to show hidden folders and open .mozilla. Make a folder named plugins in there.

From the flash file you extracted, copy just the libflashplayer.so into the /Home/.mozilla/plugins folder you created.

Restart firefox. Flash is working.

---

### Post by annsurr on 2012-05-22
Thank you so much! I was going insane, and just about to give up and go back to Windows. I have been loving Ubuntu but I could not get flash working.

---

### Post by SaimonC on 2012-05-23
Thanks Darko!! Worked perfectly. Geez... this had been going on for weeks and I'd forgotten how to do this... yeah, I've had to do this once before. Adobe Flash Player is very buggy.

---

