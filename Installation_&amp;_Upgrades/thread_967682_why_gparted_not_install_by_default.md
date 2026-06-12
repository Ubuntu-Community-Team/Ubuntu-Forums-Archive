---
title: "why gparted not install by default ?"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by reallxry on 2008-11-02
i think this is very important partition manager apps.
and should not make manually install.

so, where is configured this settings?
i want fix this setting for my customize ubuntu DVD.

---

### Post by bulldog on 2008-11-02
You maybe right about this,but to install gparted manually isn't so hard to do.

---

### Post by lukjad on 2008-11-02
The reason that GParted is not installed by default is that resizing partitions can be very dangerous if you don't know what you are doing. Also, if you keep resizing partitions you will most likely start to lose data. Creating new partitions and resizing old ones are best done once and then left alone.

---

### Post by reallxry on 2008-11-02
yup,install gparted is very easy.
but if user buy new media(like USB,SD,HDD,SSD),it will need format or partitioning.
then user need 2steps(1:install gparted,2:format by gparted) or use CUI.
is this familier for users? i dun think so.

lukjad007 says right too.
managing partition is very dangerous.
but both Windows and Machintosh already has this function by default on GUI.
if Ubuntu wanna be more familier for peaple, gparted should be install by defaul i think.

now im customizing UbuntuDVD and wanna make gparted install by default not manually after install.
[COLOR="Red"]where is the settings refuse gparted for default install.[/COLOR]

---

### Post by lukjad on 2008-11-02
Well, one thing to mention is that there is a security model. Maube the Ubuntu Devs locked it down and made it as hard a possible to make it easy to damage your computer.

---

### Post by pastalavista on 2008-11-02
I didn't install it manually. It was right there in System > Administration > Partition Editor. I could partition anywhere except / . I'm using Intrepid upgraded from the beta 4

---

### Post by lukjad on 2008-11-02
Are you sure that isn't just the live CD? I don't see that on any PC I've installed Ubuntu on.

---

### Post by pastalavista on 2008-11-02
you're right.. my mistake. I ran it for a long time from the beta from a flash drive installation before installed it to the hard disk. But I do remember now adding it to the menu and a package manager running. The point is trivial actually. I usually use a boot disk to reformat a drive anyway.

---

### Post by lukjad on 2008-11-02
Ah, I see.

---

### Post by oldos2er on 2008-11-02
> **lukjad007 said:**
> Well, one thing to mention is that there is a security model. Maube the Ubuntu Devs locked it down and made it as hard a possible to make it easy to damage your computer.

 cfdisk is there by default, as well as "rm" and other potentially damaging programs.

---

### Post by lukjad on 2008-11-02
> **oldos2er said:**
> cfdisk is there by default, as well as "rm" and other potentially damaging programs.
I believe that in hardy, the ```
[censored so as not to get in trouble] rm -rf /
``` command is now unavailable. I won't be trying it just to prove my point though... ;)

---

### Post by oldos2er on 2008-11-02
> **lukjad007 said:**
> I believe that in hardy, the ```
[censored so as not to get in trouble] rm -rf /
``` command is now unavailable. I won't be trying it just to prove my point though... ;)

 The point I was trying to make is that I don't think there's a "nanny-I-know-better-than-you-do" reason that gparted is not installed by default, but simply that one can't have every useful tool or program preinstalled.

---

### Post by lukjad on 2008-11-02
True, but there must be a line drawn in the sand to stop people from hurting themselves while still giving them a measure of freedom and flexibility. Where this line is drawn is up to the Ubuntu Devs. Remember, this is a "user friendly" Distro, and will be used by a lot of people who don't know what they are doing. In a sense we need to protect those users from themselves and yet give others the possibility to do whatever they want. In the end, since it can still be installed, the point is moot.

---

### Post by reallxry on 2008-11-03
if dev think gparted is dangerous, why include that in live packages?
terminal is more dangerous too,but will install and exist on menu.
just hide on menu is more friendly that for people needed on desktop.
using gparted is dangerous i know, but there is prompt "maybe this is damage for your settings."
so no need to reject on desktop installed ubuntu.
gparted must be install by default.
this is defact standard on the earth.

important thing is 
"[COLOR="Red"]i want make my customized ubuntu which install gparted by default. and how to settings on terminal?[/COLOR]"

---

### Post by lukjad on 2008-11-03
Well, GParted is on the CD because you need it. If you didn't have it, you couldn't install Ubuntu easily. As for your question, couldn't you compile it from source or a .deb file and package it with your CD?

---

### Post by reallxry on 2008-11-03
nop.

ubuntu LiveCD has Gparted.
installed ubuntu on HDD doesnt have gparted.<- [COLOR="Red"]this point i wanna customize.[/COLOR]

not to install gparted after ubuntu install on HDD.

almost of u think "just install after ubuntu install,do it 1 line <sudo apt-get install gparted>"
that is nonsence.

when i install ubuntu to HDD,i want include gparted too.

---

### Post by lukjad on 2008-11-03
What I mean is, If you are trying to repackage the CD, just install what you want from another source, and then repackage it. Then there should be no problem. I have never tried this so I'm just giving this my best guess.

---

