---
title: "Grub not detecting prior OS's"
date: 2009-06-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-06-21
I just installed alpha 2 yesterday and now on boot I can only memtest and boot alpha 2.  I have Jaunty and vista installed as well.  I would like these to all be boot options.  How do I do so?

Grub 2 is configured different.  Reading forums even now but I can't seem to find it.

---

### Post by autocrosser on 2009-06-21
The "quick'n'dirty" way is to edit your grub.cfg--look for my Grub theming thread: [http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)

Be very careful editing the grub.cfg---you can b0rk things very easily.......

---

### Post by cecilpierce on 2009-06-23
os-prober 
[mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory]
What does this mean ? How do I get grub2 to find other os's and hard drives ?

---

### Post by budluva04 on 2009-06-23
hey, since the beginning of ALPHA 2 i have been trying to compile a decent GRUB 2 wiki page, along with the Grub2Testing page....

[http://wiki.ubuntu.com/Grub2]("http://wiki.ubuntu.com/Grub2")

the answer to your guy's problem of not detecting multiple OS's is here....
[https://wiki.ubuntu.com/Grub2#Dual-booting]("https://wiki.ubuntu.com/Grub2#Dual-booting")

---

### Post by cecilpierce on 2009-06-23
Thanks budluva04, just got rid of my headache!

---

