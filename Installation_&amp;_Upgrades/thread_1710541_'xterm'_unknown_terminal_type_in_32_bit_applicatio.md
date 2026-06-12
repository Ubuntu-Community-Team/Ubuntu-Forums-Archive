---
title: "'xterm': unknown terminal type in 32 bit applications, most notable wine1.3"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by uzm on 2011-03-20
$ uname -a
Linux hostname 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux  

After I upgraded distributive to 10.10, wine1.3 no longer worked:  
wineuser@hostname:/lib32$ winecfg 
'xterm': unknown terminal type  

I tried wine1.3.16 maverick and old wine1.3.15 from lucid, but they both don't work. (wine1.2 works fine for some reason).   
I upgraded ia32-libs and lib32ncursesw5  but wine still says that 'xterm': unknown terminal type.  
I tried simple 32bit ncurses binaries and they say the same, so I blame terminfo database. 

As for now I found workaround: 

# cd /usr/share/terminfo/x/
# ln -s /lib/terminfo/x/xterm . 

(there was no xterm entry in /usr/share/terminfo)  
But I'm curious is there a more proper way and what and why was broken?

---

