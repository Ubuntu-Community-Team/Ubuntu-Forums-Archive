---
title: "emerald ubuntu 11.10 11.04"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-10-27
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

please donate @
[http://apps.facebook.com/fundrazr/ac...d840a83be656d6](http://apps.facebook.com/fundrazr/ac...d840a83be656d6)
as i do treat this as a full time job.... yes its a $25,000 bat house fund raiser... lol its a generic drop box for donations.

[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)

first off thanks to this guy i stole 90% of his thread......

alt + f2

gnome-terminal

run

then drop this block of code
```

sudo apt-get install git autoconf libtool libwnck1.0-cil-dev libwnck-dev intltool libdecoration0-dev gawk

```

then nab this file in your browser... save it in $HOME/Downloads
[http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.4.tar.gz](http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.4.tar.gz) for ubuntu 11.10 (possibly 11.04)
[http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.5.tar.gz](http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.5.tar.gz) for ubuntu 12.04


then drop this block of code....

```

cd $HOME/Downloads
tar -xf emerald-*
cd emerald-*
./autogen.sh && make clean && make distclean && ./configure --prefix=/usr && make && gksu make install
cd ..
rm -rf emerald-*
rm -rf emerald-*.tar.gz

```

[http://compiz-themes.org/CONTENT/content-files/140954-Originalseed-DarkOne.emerald](http://compiz-themes.org/CONTENT/content-files/140954-Originalseed-DarkOne.emerald)

is the emerald theme im rocking....

listen to this filthy dubstep tune....
[http://youtu.be/EnJs6mDKteI](http://youtu.be/EnJs6mDKteI)

then reboot your computer / fusion-icon...

[img]http://img534.imageshack.us/img534/1512/emeraldud.jpg

moar good dark themes....
[http://compiz-themes.org/CONTENT/content-files/146386-Moises%20Negro.emerald](http://compiz-themes.org/CONTENT/content-files/146386-Moises%20Negro.emerald)
[http://compiz-themes.org/CONTENT/content-files/146131-WolfeEmerald.emerald](http://compiz-themes.org/CONTENT/content-files/146131-WolfeEmerald.emerald)

original block 2 code unpatched...

upon a fresh install of 11.10, i failed to note that compiz plugins and settings manager need installed via synaptic / repository...

```

sudo apt-get install compizconfig-settings-manager compiz-fusion-bcop compiz-plugins-main-default fusion-icon compiz-plugins-extra

```

---

### Post by setsuna on 2011-10-28
i'm that guy :p (abz)
hehehe..

thanks for made some correction..
i never try this before, on oneiric
and never realize that emerald unsupported out of the box, hahaha

maybe i'll try later

is it work for oneiric both unity and gnome-shell??

thx..

---

### Post by setsuna on 2011-10-28
just confirm my last question, hehehe

it works! just in unity.

and emerald-0.9.4 works well
NOT for latest emerald (0.9.5)

thx :)

---

### Post by boblizar on 2011-10-31
uhhh it worked on ur page for 11.04, but broke @ 11.10  i use xfce and do not concern myself with the gnomes on my system...  yes 9.5 was broken on my end also....  but i do version shuffles and step back and forward until i get something that goes....

---

### Post by typhoon_tip on 2011-11-16
Hey pal, worked brilliantly here !!! Finally I can get rid of the annoying focus bug of my windows:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/885941)

Albeit the scaling bug was fixed by a proposed update of compiz.

I am running 64 bits.

Only a couple of issues tough:

- When maximizing and then restoring windows, buttons are missing, but button command is there ! Just rendering of the buttons is not there anymore. If you resize the window on the width, icons reappears.

- When using Synaptic or any other applications that has buttons which could trigger a dynamic window resize, sometimes the entire border is not resized and remains on the original size.

Anyway, for me, is far less annoying than the focus bug.

---

### Post by typhoon_tip on 2011-11-24
> **typhoon_tip said:**
> When maximizing and then restoring windows, buttons are missing, but button command is there ! Just rendering of the buttons is not there anymore. If you resize the window on the width, icons reappears.

BUG fixed. Not the most elegant solution ever implemented, but it works brilliant. Intercepted event from Unity of restore window (somehow is not the Emerald button) and do a refresh of the title-bar only within the code itself.

For those who are interested in using Emerald in Unity perfectly integrated, download and replace the file **main.c** into the /src subfolder of the 0.9.4 version of Emerald source, then compile with the instructions at the beginning of this thread. If you have already installed it, uninstall first with:
```
cd emerald-0.9.4
sudo make uninstall
```

:P

---

### Post by boblizar on 2011-11-24
lol im having far more severe problems than you are.  i cant get the theme manager to load anymore from the fusion icon...

alt + f2

emerald-theme-manager

run 2 solve that......  a little quick on the "solve" im getting repeated segmentation faults from the emerald theme command.

i also am running ubuntu AMD64....

---

### Post by typhoon_tip on 2011-11-25
> **boblizar said:**
> lol im having far more severe problems than you are.  i cant get the theme manager to load anymore from the fusion icon...

alt + f2

emerald-theme-manager

run 2 solve that......  a little quick on the "solve" im getting repeated segmentation faults from the emerald theme command.

i also am running ubuntu AMD64....

No worries, I get a lot of seg fault too when starting the Theme Manager. Do it from Terminal. After a while, it goes away and you can start it... :)

---

### Post by typhoon_tip on 2011-11-25
> **typhoon_tip said:**
> - When using Synaptic or any other applications that has buttons which could trigger a dynamic window resize, sometimes the entire border is not resized and remains on the original size.

*Fixed* !!! :popcorn: This much more elengantly fixed than the other one, albeit is not very precise as a fix, it works brilliantly and does intercept only the right combination of events (motion event without the "send_event" flag set).

Attached is the **main.c** for who is interested, now Emerald is 100% perfect in Unity.

---

### Post by boblizar on 2011-12-02
can u plz format your post to wget the link to your fixed main c insert it into the sources compile and so forth so a patron passing by can take the block of code and 2 second copy paste?  i originally setup my post to quickly duplicate my settings to a laptop so i would not have to fumble around in sources or terminal for hours....  if you setup a code block like i have formatted in the first post, ill make a section of the main.c repairs youve implemented....  (however im refusing to refix the source as i fixed it the way i did the first time lol)

---

### Post by typhoon_tip on 2011-12-03
> **boblizar said:**
> can u plz format your post to wget the link to your fixed main c insert it into the sources compile and so forth so a patron passing by can take the block of code and 2 second copy paste?  i originally setup my post to quickly duplicate my settings to a laptop so i would not have to fumble around in sources or terminal for hours....  if you setup a code block like i have formatted in the first post, ill make a section of the main.c repairs youve implemented....  (however im refusing to refix the source as i fixed it the way i did the first time lol)

Sorry I don't understand what you want me to do loll :)

This is the file main.c under ~/src when you unpack **0.9.4** (and valid only for **0.9.4**). Simply replace the entire file before re-compiling to fix the bug. If you have modified it yourself, I have to check because there are quite several places that has been changed, is not just a couple of lines.

You mean you would like to have something like a guideline "at line xxx replace this block of code kkkk with nnnn" ?

Let me know, I see what I can do.

---

### Post by typhoon_tip on 2011-12-03
OK, being dumb enough today, I got what you mean.

I uploaded the code to my site, here are the extra instructions to add the patch *before* compiling:

```
cd src
wget http://www.learn-digital.com/ubuntu/emerald-0.9.4/src/main.c
cd ..
```

Put this code exactly before compiling and after unzipping to install the Unity patch, so that the total installation cycle will look like this:

```
wget http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.4.tar.gz
tar -xf emerald-0.9.4.tar.gz
cd emerald-0.9.4
cd src
wget http://www.learn-digital.com/ubuntu/emerald-0.9.4/src/main.c
cd ..
./autogen.sh && make clean && make distclean && ./configure --prefix=/usr && make && gksu make install
cd ..
rm -rf emerald-0.9.4
rm -rf emerald-0.9.4.tar.gz
```

Cheers,
Simone

---

### Post by shantiq on 2011-12-07
> **boblizar said:**
> if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)

first off thanks to this guy i stole 90% of his thread......

alt + f2

gnome-terminal

run

then drop this block of code
[code]
sudo apt-get ins[/url]


**thank you:KS**

---

### Post by boblizar on 2011-12-21
> **typhoon_tip said:**
> OK, being dumb enough today, I got what you mean.

I uploaded the code to my site, here are the extra instructions to add the patch *before* compiling:

```
cd src
wget http://www.learn-digital.com/ubuntu/emerald-0.9.4/src/main.c
cd ..
```

Put this code exactly before compiling and after unzipping to install the Unity patch, so that the total installation cycle will look like this:

```
wget http://cgit.compiz.org/fusion/decorators/emerald/snapshot/emerald-0.9.4.tar.gz
tar -xf emerald-0.9.4.tar.gz
cd emerald-0.9.4
cd src
wget http://www.learn-digital.com/ubuntu/emerald-0.9.4/src/main.c
cd ..
./autogen.sh && make clean && make distclean && ./configure --prefix=/usr && make && gksu make install
cd ..
rm -rf emerald-0.9.4
rm -rf emerald-0.9.4.tar.gz
```

Cheers,
Simone

almost correct typhoon_tip...  there already exists a main.c that is defective and needs removed....  ill patch it up and repair the 1st post to include the patch

---

### Post by typhoon_tip on 2011-12-21
> **boblizar said:**
> almost correct typhoon_tip...  there already exists a main.c that is defective and needs removed....  ill patch it up and repair the 1st post to include the patch

Have you tested it too ? So far I have only tested on 5 different installs (Desktop and Laptops). It works on all.

---

### Post by boblizar on 2011-12-22
i think its having strange side effects from the patch, i dont use unity...  i use xfce...  i just patched and built and tested the links, day 1 of it, strange effects visual echos in seamonkey right now....  im personally going to revert back to the original unpatched 9.4

i just scouted out this rogue link again to see if i had any newer versions to play with....

[http://cgit.compiz.org/fusion/decorators/emerald/](http://cgit.compiz.org/fusion/decorators/emerald/)

---

### Post by neu5eeCh on 2012-01-08
OK, this didn't work for me. The compiz fusion icon doesn't show up in Unity's system tray. No one else is complaining, so what is it that I don't get?
[B]
EDIT:[/B] OK, solved that issue. Installed dconf and white listed fusion-icon: desktop -->unity-->panel Then write in 'fusion-icon' and reboot.

**EDIT 2: **The larger problem is that emerald doesn't display correctly. There is  no transparency and window shadows are solid black - as if compositing  were turned off. I'm using an  ATI Technologies Inc Mobility Radeon HD 3650. The guide, at least for this video card and system (Unity 11.10 64bit), doesn't seem to work.

---

### Post by typhoon_tip on 2012-01-09
> **VTPoet said:**
> **EDIT 2: **The larger problem is that emerald doesn't display correctly. There is  no transparency and window shadows are solid black - as if compositing  were turned off. I'm using an  ATI Technologies Inc Mobility Radeon HD 3650. The guide, at least for this video card and system (Unity 11.10 64bit), doesn't seem to work.

Display **is** correct. The theme is a bit bugged in Unity. You may try to use the one that I corrected and attached here. I also have ATI :)

---

### Post by neu5eeCh on 2012-01-10
:KS> **typhoon_tip said:**
> Display **is** correct. The theme is a bit bugged in Unity. You may try to use the one that I corrected and attached here. I also have ATI :)

Thanks Typhoon. I'll give it a try when I get back to my other system. I swear, the day I buy my next laptop will be the day I throw ATI and NVIDIA out with the #%@$! baby! O:) ATI hates Linux - or maybe it's the other way around. I don't know...

---

### Post by boblizar on 2012-01-12
im in college now, and away from my 11.10 machine, i have 10.10 on here, and the original was written with a nvidia 9600 gt gig edition... and a 1280x1024 CRT monitor....

---

### Post by typhoon_tip on 2012-01-12
> **boblizar said:**
> im in college now, and away from my 11.10 machine, i have 10.10 on here, and the original was written with a nvidia 9600 gt gig edition... and a 1280x1024 CRT monitor....

I think Emerald is like this. Indeed, the theme is not "bugged", is just that it may appear a bit different depending on rendering of the openGL driver. I tweaked that one on my ATI for a 1280x800 display.

---

### Post by neu5eeCh on 2012-01-16
Just now responding. Typhoon, Emerald works beautifully on my Unity desktop. You were correct.

However (and this isn't a deal breaker) I notice that if I login to a "Cario Dock" session, (rather than a Unity session) emerald doesn't "engage"; that is, the session doesn't want to hand over control to emerald, or so it seems. Any quick ideas?

---

### Post by boblizar on 2012-01-16
i just switched to cairo dock last night, instead of running it under gnome or ubuntu or unity, try running your cairo dock under LXDE or XFCE...  my approach towards issues like that is to recursively test desktops and figure out what works with what.. on my 10.10 machine, cairo dock works like a charm with xfce, though i did have to tweek xfces startup to tell cairo dock to start only once.

---

### Post by neu5eeCh on 2012-01-16
> **boblizar said:**
> i just switched to cairo dock last night, instead of running it under gnome or ubuntu or unity, try running your cairo dock under LXDE or XFCE...  my approach towards issues like that is to recursively test desktops and figure out what works with what.. on my 10.10 machine, cairo dock works like a charm with xfce, though i did have to tweek xfces startup to tell cairo dock to start only once.

That's good advice Boblizar, and I was actually beginning to think along the same lines. The *only* thing, at this point, that I like about gnome (the base), more than XFCE, is nautilus and that nautilus manages the desktop. I just tried Gnome Classic, removed both panels, and booted up Cairo Dock. That worked. I got precisely the same desktop as with Cairo Session except that I can now use Emerald.

By the way, when you mention a tweak like that, do this idiot a favor (referring to me). Describe exactly what you did so I don't have to come back and chase you down.;)

All in all, XFCE has easily become my favorite DE. Once they start managing the desktop with their file manager, I ain't never gonna' look back. I've tried to like G3 and Unity. Honest. I really have, but there's no advantage to either DE and any number of disadvantages.

---

### Post by searchfgold6789 on 2012-01-21
How do you uninstall?

---

### Post by boblizar on 2012-01-23
to uninstall, build the source up, and stop at "sudo make install" or "gksu make install"  at that point run "sudo make uninstall" or "gksu make uninstall" instead.

and i run nautilus under xfce also....  though thunar is a hair lighter.  lxde is also another good light alternative to xfce.

---

### Post by xc3RnbFO8P on 2012-05-01
I ran into some problem installing Emerald in 12.04 but I think this solved it:
[http://ubuntuforums.org/showpost.php?p=11896313&postcount=27]("http://ubuntuforums.org/showpost.php?p=11896313&postcount=27")

---

