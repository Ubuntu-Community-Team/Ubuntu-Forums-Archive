---
title: "Downgrade"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Peter Sommer-Larsen on 2006-10-28
Hey Ive just upgraded to Edgy, but I cant get my ATIdrivers working, and
it seems that i need to downgrade to dapper again. How do I do this ?

Is it possible to just go into my source.lst and chance all the the "Edgy"
to "dapper" and then run:

# sudo apt-get update
# sudo apt-get dist-upgrade

Well this is how i upgraded.. so is it possible to go the other way ?

---

### Post by Peter Sommer-Larsen on 2006-10-28
ok I found out, that it didnt work.. is there anyway, I can turn back to
dapper ?

---

### Post by frogotronic on 2006-11-06
> **Peter Sommer-Larsen said:**
> ok I found out, that it didnt work.. is there anyway, I can turn back to
dapper ?

[-( 


use SBACKUP to backup your data; copy the backups to CDRs; reinstall Dapper using a CD (i.e. erase your HDD and start over)

---

### Post by goldenatom on 2006-11-06
Whats the problem with the ATI drivers?

---

### Post by jgcamp99 on 2006-11-06
Don't give up on Edgy,

This wiki makes ATi drivers a snap !

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Bookmark these as well !

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

BTW, the latest xorg update sets your opnGLoverlay to "off" in the xorg.config file (see post # 7 for that fix).

[http://www.ubuntuforums.org/showthread.php?t=293161&highlight=xorg](http://www.ubuntuforums.org/showthread.php?t=293161&highlight=xorg)

Outside of a few glitches here and there, Edgy is as stable as Dapper in my  opinion. The goodies that come with the latest revisions of applications is well worth the learning curve with Edgy. My AMD Athlon XP 3200+ is just as solid and stable on Edgy as it is with Dapper, granted I'm not getting fancy with it and putting xGL or compiz on it, but I installed ATi drivers versions 8.28.8, 8.29.6 and now 8.30.3 in Edgy. Dapper went from 8.24.* to 8.29.6 just as easy using the wiki's and forum threads for Ubuntu.

I'm happy with Edgy !

---

### Post by jgcamp99 on 2006-11-06
BTW, re-enable root to logon gnome and all that additional sudo exercise in futility is really unnecessary:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can always go back and disable root to login at the login screen of gnome. Sudo has it's nuances. We've debated them, this works easy and if ou want to get it up and running in a hurry, this eliminates learning sudo, although sudo is a worthy aspect of Ubuntu to learn and know, personally, I'd just assume limit it to what the Synaptics Package manager asks for a password for. And this guide allows you to put it back the way you found it just the same.

---

### Post by easotokr on 2006-11-29
Please someone help me.. my "Edgy:-# " looks like become crazy... :???: I really want to downgrade but I even hava jail to run 32bits apps and fresh install is not an option.....

the most compelx problem came from something that looks like double X runningn on my PC, taking 100% of my processor and redirecting my Xorg to tty9... additionally I have fsck for ever and ever runing on a ghost terminal that I can't kill, yes that means, my hard drive is always spinning.#-o 


Please if someone knows how to solve this problems without re-install I really appreciate it.

bye

---

### Post by frogotronic on 2006-11-29
> **easotokr said:**
> Please someone help me.. my "Edgy:-# " looks like become crazy... :???: I really want to downgrade but I even hava jail to run 32bits apps and fresh install is not an option.....

the most compelx problem came from something that looks like double X runningn on my PC, taking 100% of my processor and redirecting my Xorg to tty9... additionally I have fsck for ever and ever runing on a ghost terminal that I can't kill, yes that means, my hard drive is always spinning.#-o 


Please if someone knows how to solve this problems without re-install I really appreciate it.

bye

I don't know what you mean by a ghost terminal, but you can kill any process by opening up a terminal:

```
xkill
```

and moving the skull and crossbones over the window terminal bar and then simply left click the mouse and the process should be killed.

---

