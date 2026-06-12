---
title: "Slow connection: Can I copy new packages to another computer?"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by justin75 on 2006-12-19
Greetings,

I have a slow connection problem... this is me:  ](*,) 

I have two ubuntu computers with hoary installed. I've downloaded the latest upgrades on one computer, is there a way to copy the package files (via cdrom or usb drive) to the 2nd computer for it's upgrade? ie so i don't have to download all the packages again.

I've tried apt-cache and apt-proxy-import, but they all have to do with a local network which i don't have, i only have two standalone computers...

tia
:)

---

### Post by scrooge_74 on 2006-12-19
there are ways to configure one of your pcs as a repository system. I saw a howto a few weeks back but did not bookmarked the page and I can't remember how to do it since I don't have a need for it

---

### Post by justin75 on 2006-12-21
anyone else remember how it's done?

:-k 

it seens like it ought to be a simple thing to copy the .deb files, then have the computer scan the folder and update the database... I'm lost as to why this is so difficult.

---

### Post by aysiu on 2006-12-21
All the .deb files live in /var/cache/apt/archives

Copy those to CD or USB drive and then put them on the desktop of the other computer and type these in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by justin75 on 2006-12-21
> sudo dpkg -i *.deb

i could do that if there were a few specific packages i wanted to upgrade, but there are so many misc lib and dev packages that are required... it's not that easy.

And the 2nd computer is an older model and cannot handle all of the packages installed on the 1st computer, so i definitely do not want to install all debs.

What I really want to do is copy the debs, then choose what to upgrade via synaptic or other gui prog.

is that possible?

Silly me thought i could just copy /var/cache/apt/archives along with 
pkgcache.bin ... but that didn't work, synaptic still tried to download all packages even though they were already in /var/cache/apt/archives. #-o

---

### Post by aysiu on 2006-12-21
Maybe [this](http://www.ubuntuforums.org/showthread.php?t=188158) might help?

---

