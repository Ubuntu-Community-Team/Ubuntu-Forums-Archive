---
title: "apt horribly corrupted"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by dorris on 2007-03-16
please can someone help me.

I was in the middle of an apt-get, it had got to the installation stage, when power died on my laptop.

now i get :
```

root@doram-laptop:/var/lib/dpkg# apt-get install samba
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```
when I run dpkg --configure -a, i get 
```

root@doram-laptop:/var/lib/dpkg# dpkg --configure  -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `

```
I have tried renaming status-old, and all sorts of other things, any ideas?

---

### Post by Arby on 2007-03-16
Have you tried removing that file altogether? It looks like it was something that got left behind by your interrupted update. I've just checked and /var/lib/dpkg/updates is an empty directory on my system. So it could be a temporary file that is meant to be removed at the end of the update and wasn't. If it was me I'd try the following but it's a complete guess, you have been warned.

Move the file another location. e.g. ```
sudo mv /var/lib/dpkg/updates/0000 /home/you/dpkg_update_0000
```then you can put the file back if you need to. then run```
 sudo dpkg --configure -a
``` again. If that works then try ```
sudo apt-get update
followed by
sudo apt-get install samba
```

that's my guess, feel free to ignore it.

---

### Post by dorris on 2007-03-16
WOW, what a quick response, I was just coming back  to say it is fixed finally.
u were almost spot on the money.

i copied the whole damn dpkg folder, then tinkled
deleted all stuff in updates, and renamed a -old and it worked, 

```

root@doram-laptop:/var/lib# cp -arf dpkg dpkg.bak
root@doram-laptop:/var/lib/dpkg# rm -rf updates/*
root@doram-laptop:/var/lib/dpkg# dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 MSDOS EOF (^Z) in field name `'
root@doram-laptop:/var/lib/dpkg# ls available
available      available-old  
root@doram-laptop:/var/lib/dpkg# cp available available.bak
root@doram-laptop:/var/lib/dpkg# cp available-old available
root@doram-laptop:/var/lib/dpkg# dpkg --configure -a
###WHOA, no errors, lets try apt-get install <package>
root@doram-laptop:/var/lib/dpkg# apt-get install samba
Reading package lists... Done

```


thanks for the prompt assistance.

note to all users out there, if u disable acpid, and have no batstat, ensure power is on when charger is connected to powersocket when installing apps :)

---

### Post by Arby on 2007-03-16
Glad you got it fixed

---

### Post by sikanrong on 2007-09-12
Hey - I was getting a very similar message after a corrupt dpkg operation. Kept giving me an error about /var/lib/dpkg/available and the stupid MSDOS EOF char. God only knows what causes this. All i did was this: 

$ su
# cd /var/lib/dpkg
# rm available
# touch available

And there it was - perfect again :) Hope this helps

---

