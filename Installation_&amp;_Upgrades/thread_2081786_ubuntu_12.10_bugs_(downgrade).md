---
title: "ubuntu 12.10 bugs (downgrade?)"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by pierceTN on 2012-11-07
Hello all,

Okay, I recently upgraded to Ubuntu 12.10 from 12.04, and over all it has been very buggy, including the following bugs:

1. not being able to change desktop environments (i.e. changing from gnome to unity)
2. I cannot login from GUI mode,(it just redirects back to login page,I have to CTRL-ALT-F1 and login through terminal, then run starx)

3. I cannot logout, I have to restart.

4. wifi only works when it wants to.

and it is *very* slow, and choppy

to get these fixed:

_should I ther down-grade back to 12.04_ (if so, how?), or should the next updates fix these bugs?

I do not remember other non-LTS versions being this buggy.

Right now I'm stuck in using gnome (I think 3.6), i like the changes, but over all it is not usable. 

I am actually on a bootable drive right now...


Thanks for any help in advance,

-Pierce

---

### Post by Bucky Ball on 2012-11-07
Do an update now. Try in a terminal:

sudo apt-get update
sudo apt-get upgrade

This last command will NOT upgrade your OS, but the packages and software in it (if required).

There is no 'downgrade' option so going back to 12.04 LTS (if it ain't broke don't fix it) means a full reinstall.

---

### Post by pierceTN on 2012-11-07
> **Bucky Ball said:**
> Do an update now. Try in a terminal:

sudo apt-get update
sudo apt-get upgrade

This last command will NOT upgrade your OS, but the packages and software in it (if required).

There is no 'downgrade' option so going back to 12.04 LTS (if it ain't broke don't fix it) means a full reinstall.
I have updated and upgraded in the terminal.  ---to no avail

How often are updates released?

---

### Post by Bucky Ball on 2012-11-08
For 12.10? Often. It has only been out two or three weeks. I would set to update daily rather than weekly right now.

---

### Post by Inoki on 2012-11-08
Re-installing takes only about a few minutes and have 0 worries. Also, to avoid messy kernel updates refer to this guide: [http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)

---

### Post by 2F4U on 2012-11-08
> _should I ther down-grade back to 12.04_ (if so, how?), or should the next updates fix these bugs?

You cannot downgrade, the only option would be to do a fresh install of 12.04. Considering all your problems, it may be the better option. With respect to problems 1. and 2. I would assume that they could be related to the graphics card. What graphics card do you have and what driver do you use?

---

### Post by pierceTN on 2012-11-08
> **2F4U said:**
> You cannot downgrade, the only option would be to do a fresh install of 12.04. Considering all your problems, it may be the better option. With respect to problems 1. and 2. I would assume that they could be related to the graphics card. What graphics card do you have and what driver do you use?



when I go to settings>detils>graphics, it says my graphic driver is "Gallium 0.4 on llvmpipe (LLVM 0x301)"  I do not know what Grphics card it is. But It is on a Dell Latitude D630.  

Did graphic card requirements change with 12.10?

Before the upgrade, every thing was working fine. I think I'm going for a 12.04 fresh install.


@Anathaen

When I go to synaptic, it shows my kernel up to date.

and am probably going to do a re-install

---

### Post by 2F4U on 2012-11-08
> when I go to settings>detils>graphics, it says my graphic driver  is "Gallium 0.4 on llvmpipe (LLVM 0x301)"  I do not know what Grphics  card it is. But It is on a Dell Latitude D630.  
In order to find your graphics card, execute

```
lspci | grep VGA
```

in a terminal.

---

### Post by 2F4U on 2012-11-08
> Did graphic card requirements change with 12.10?

Yes, they did change. Unity requires 3D and OpenGL:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA5OTA](http://www.phoronix.com/scan.php?page=news_item&px=MTA5OTA)
[http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued](http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued)

---

### Post by pierceTN on 2012-11-08
> **2F4U said:**
> Yes, they did change. Unity requires 3D and OpenGL:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA5OTA](http://www.phoronix.com/scan.php?page=news_item&px=MTA5OTA)
[http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued](http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued)

this is what it gave me when I executed 'lspci | grep VGA':
"**00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)**"


also, I did not use unity 2D in 12.04, so would the same driver/graphics card work for the "regular" unity in 12.04, as it would for the "only" unity for 12.10?

I have not been able to use unity though in 12.10, because I was using the gnome desktop last when I upgraded, and it will not let me change.  so,apparently, I am stuck using gnome.   So I cant figure out if unity 3d will work or not.

---

### Post by Inoki on 2012-11-08
> **pierceTN said:**
> @Anathaen

When I go to synaptic, it shows my kernel up to date.

and am probably going to do a re-install
My suggestion, to avoid all this hassle, is to stick to a version that worked for you from the start. Even if it's an older version, but it's still supported, stick to it, until the new version has most of its bugs patched.

Do a fresh install of 12.04.1, it's LTS, you don't have to worry for several years. If everything works for you from the start, note what kernel you're using and refer to the guide I posted.

I've summarized the guide on how to do it with my current install of Ubuntu Studio 12.10 Quantal Quetzal, but it's the same for any Ubuntu version with minor differences in packages.

[Summarized guide]("http://anathaen.deviantart.com/#/d5kazs3")

---

### Post by pierceTN on 2012-11-08
> **Anathaen said:**
> My suggestion, to avoid all this hassle, is to stick to a version that worked for you from the start. Even if it's an older version, but it's still supported, stick to it, until the new version has most of its bugs patched.

Do a fresh install of 12.04.1, it's LTS, you don't have to worry for several years. If everything works for you from the start, note what kernel you're using and refer to the guide I posted.

I've summarized the guide on how to do it with my current install of Ubuntu Studio 12.10 Quantal Quetzal, but it's the same for any Ubuntu version with minor differences in packages.

[Summarized guide]("http://anathaen.deviantart.com/#/d5kazs3")

I actually meant "*reinstall*" as in installing what I had before I upgraded to 12.10, so yes, I'm going to do a fresh install of 12.04 LTS, unless it "all of the sudden" just gets better... :)

I actually just downloaded 12.04.1 LTS 

Thanks for the help,

Pierce

---

### Post by Bucky Ball on 2012-11-08
Yea, I'm thinking if you were in Gnome and you upgraded to 12.10, which only has Unity, that is going to make a mess and confusion. Guess Gnome would be waiting for updated dependencies and other stuff which never come, leaving it in limbo.

[QUOTE=2F4U]Yes, they did change. Unity requires 3D and OpenGL:[/QUOTE]

Maybe check you have OpenGL and all 3D requirements installed and satisfied.

Still failing, I'd reinstall, perhaps to another partition if you can. You can use the existing /home and /swap. That way you might be able to track the progress of 12.10 on your machine and use that install as a plaything for tweaking and experimenting. You won't be in such a rush to fix 12.10 issues if you have a stable 12.04 LTS boot, too. ;)

---

