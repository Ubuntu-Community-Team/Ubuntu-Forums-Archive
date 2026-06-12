---
title: "no boot splash or boot messages after upgrade"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by jimbren on 2006-10-26
I just upgraded from Kubuntu Dapper to Edgy with very few problems, except for the fact that I don't have a boot splash screen now, and I don't see any boot messages.  

Booting itself seems to take longer than pre-Dapper, and I'd like to take a look at what is going on.  (I just haven't looked at my boot log yet.)

Has anyone else seen this issue?  It's more of a cosmetic thing than anything else--I want the full Edgy Experience, and I'm missing it right now.  :)

Thanks in advance.

jimbo.

---

### Post by rexey on 2006-10-26
Same problem here.
Works fine once it's up but it takes twice as long and you're in the dark.
If I figure it out I'll let you know.

/I am an egg

---

### Post by t0ny on 2006-10-27
Same problem but with the normal Edgy not the kde version.
It takes about twice as long and just a blinking cursor.

---

### Post by frodon on 2006-10-27
Check your /boot/grub/menu.list file and see if you didn't put there a wrong vga resolution.
If you don't even know this file or never edited it run this command :
```
sudo update-alternatives --config usplash-artwork.so
```Then select again the default usplash, then run a : ```
sudo dpkg-reconfigure linux-image-`uname -r`
```It should be good for most usplash problems.

---

