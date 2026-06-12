---
title: "Trying to run a .bin"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by MrPickle on 2008-05-05
I am trying to install diablo but the file's in .bin format, I've read about and read I need to do:

chmod -x diablo2cd1.bin
diablo2cd1.bin

But when I run the later it says: 
bash: diablo2cd1.bin: command not found

I read around and read to run ls -la, this is the output:
total 1756284
drwxr-xr-x 2 james james      4096 2008-05-04 23:53 [COLOR="Blue"].[/COLOR]
drwxr-xr-x 3 james james      4096 2008-05-05 21:00 [COLOR="Blue"]..[/COLOR]
-rwxr-xr-x 1 james james 585831456 2008-05-05 13:13 [COLOR="Lime"]diablo2cd1.bin[/COLOR]
-rw-r--r-- 1 james james        95 2008-05-05 00:01 diablo2cd1.cue
-rw-r--r-- 1 james james 701147664 2008-05-05 13:13 diablo2cd2.bin
-rw-r--r-- 1 james james        95 2008-05-05 00:18 diablo2cd2.cue
-rw-r--r-- 1 james james 509654880 2008-05-05 13:13 diablo2cd3.bin
-rw-r--r-- 1 james james        95 2008-05-05 11:56 diablo2cd3.cue

---

### Post by RATM_Owns on 2008-05-05
I think it is chmod +x but meh.
In front of the file, add a ./
Like to run moo.x when you're in its directory, you'd type
./moo.x

---

### Post by MrPickle on 2008-05-05
Thank you that has worked but now it's saying:
bash: ./diablo2cd1.bin: cannot execute binary file

---

