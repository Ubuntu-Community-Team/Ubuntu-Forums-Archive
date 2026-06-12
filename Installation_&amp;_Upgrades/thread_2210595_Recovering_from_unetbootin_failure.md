---
title: "Recovering from unetbootin failure"
date: 2014-03-11
forum: Installation &amp; Upgrades
---

### Post by truefdk on 2014-03-11
Computer: Dell Latitude d400 (yes I know it's ancient)

Hard drive is useless from being dropped, so I've been running a Bento Ubuntu Remix (from LinuxVillage) off a 32gb Sandisk Cruzer Glide for a while now, but not without hassle. The d400 doesnt accept any OS that requires pae, so I had a hard time getting Bento to work...after many tries I finally was able to run it after using grub rescue commands
```
set root=(hd1,msdos2) 
set prefix=(hd1,msdos2)/boot/grub 
insmod normal 
normal
```
However, I then did a very stupid thing. Wanting to play some windows-only games, I tried to use unetbootin to install windows xp on the Cruzer alongside Bento. Now when I boot, the only option is default (which is nothing), causing an infinite auto-boot 10 second countdown loop. If I hit Esc and tell it to boot vmlinuz, it refuses, saying pae is required.
I've got files I need in the Bento partition, and I can't get them out because I dont have access to a computer that can read linux filesystems. So, how can I get in from the boot: prompt and/or remove unetbootin?

---

