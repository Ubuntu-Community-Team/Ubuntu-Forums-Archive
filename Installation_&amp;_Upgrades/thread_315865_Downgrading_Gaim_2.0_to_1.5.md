---
title: "Downgrading Gaim 2.0 to 1.5"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Pobega on 2006-12-09
I'm trying to downgrade my version of Gaim from 2.0 to 1.5, but I've got no idea how to go about doing that. A lot of the plugins I used to use worked way better with 1.5, and I personally prefered the preferences to what is offered on 2.0.*.

The Ubuntu distro I'm using came on my System76 laptop, and it won't allow me (Using the GUI, not terminal) to uninstall 2.0; What terminal command would I use to uninstall it, and how would I go about installed 1.5?

Thanks for the help,
Michael Pobega

---

### Post by pay on 2006-12-09
To uninstall it try ```
sudo aptitude remove gaim #or
sudo apt-get remove --purge gaim
```To install 1.5 try```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.x86.package
sudo sh gaim-1.5.0.x86.package
```If that doesn't work try ```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.tar.bz2
tar jxvf gaim -1.5.0.tar.bz2
cd gaim
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep gaim
./autogen.sh #or ./configure if that doesn't work
gmake
sudo checkinstall gmake install
```

---

### Post by Pobega on 2006-12-10
Thanks, that worked! Although I had to change a few things here or there, I got 1.5.0 working for me!

Thanks a lot

---

### Post by Pobega on 2006-12-10
Now that I have 1.5.0 on there, how do I tell Ubuntu that I don't want to upgrade it? It keeps telling me "There is 1 Update Available" and that update is Gaim 1.5 -> Gaim 2.0 (Which I don't want to do)

---

### Post by Pobega on 2006-12-12
Bump, I need help with this. It keeps telling me to upgrade it, what can I do about this (If anything)?

---

### Post by bulldog on 2006-12-12
You can lock your current version in synaptic.
Search for gaim and select it and lock version.

---

### Post by Pobega on 2006-12-12
I don't see an option for locking it in Synaptic. All I see is Mark for Upgrade/Mark for removal/Mark for complete removal/Properties.

---

### Post by bapoumba on 2006-12-13
Hello : > package > lock version ;)

---

### Post by Pobega on 2006-12-13
> **bapoumba said:**
> Hello : > package > lock version ;)

Maybe I'm blind, but I don't see the option to do it still. This is what my screen looks like:

[http://img329.imageshack.us/img329/3973/screenshotay5.png](http://img329.imageshack.us/img329/3973/screenshotay5.png)

---

### Post by bulldog on 2006-12-13
Hit the package tab at the top of your synaptic.
Choose lock Version and done.

Those tabs are there for a reason,they have all kind of options for you.:D 
Take a quick look and you'll be surprised.

---

### Post by bapoumba on 2006-12-13
Well ... Okay bulldog, I was soooo slow on this one. I made a screenshot for this, so I'll post anyway ;)

---

### Post by Pobega on 2006-12-13
Damn, sorry I asked such a stupid question. I'm so used to things being so hard to find in Linux that I forgot to look in the most obvious place.

Thanks for the help, although Ubuntu is still prompting me to upgrade (Maybe after a restart it won't though)

Thanks :)

---

### Post by Pobega on 2006-12-16
Hm, for some reason whenever I click "Lock Version" it doesn't save it. When I click on Gaim < Package < Lock Version, it just resets back to the initial screen and Gaim's version isn't locked.

---

### Post by scrooge_74 on 2006-12-16
if you look for the package again it should have a small lock next to the green square

---

### Post by Pobega on 2006-12-16
Not working for me.

[First](http://img505.imageshack.us/img505/2940/1zf4.png)
[Two (After I hit Lock Version)](http://img510.imageshack.us/img510/1699/2ke7.png)
[Yay, doesn't work](http://img283.imageshack.us/img283/3301/3uh8.png)

For some reason it doesn't want to lock anything, it's being weird.

---

### Post by bapoumba on 2006-12-17
Forcing apt not to show you the upgrade is not so easy. You have to create an /etc/apt/preference file :
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html"), section 3.10.

---

### Post by Pobega on 2006-12-17
So in [this area of the page](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin), I went to /etc/apt to find that there is no preferences file. So I created one. Will this file work, or is my system reading it's preferences off of an entirely different file?

**Edit:** [[IMG]http://img355.imageshack.us/img355/1025/screenshotko9.th.png[/IMG]](http://img355.imageshack.us/img355/1025/screenshotko9.png) It's still telling me that I have to update Gaim, although this is what I put in the file:

```
Package: gaim
Pin: 1.5.0*
Pin-Priority: 1001
```

---

### Post by bapoumba on 2006-12-17
Well, from the debian page, this is what I would have put in /etc/apt/preference file. I have never done this, and planned to run some tests.
You may need a reboot (I have already observed that proxy setups for ex. are not always taken into account by apt right away. I have not looked into this further. On my TODO list ;))

---

### Post by Pobega on 2006-12-17
> **bapoumba said:**
> Well, from the debian page, this is what I would have put in /etc/apt/preference file. I have never done this, and planned to run some tests.
You may need a reboot (I have already observed that proxy setups for ex. are not always taken into account by apt right away. I have not looked into this further. On my TODO list ;))

Rebooting is the first thing I did after putting the file there. That screenshot is directly after the I logged back on to Ubuntu.

---

### Post by bapoumba on 2006-12-17
I had a gdm security update today (along with a couple of language packs).
I'll run some tests, I do not understand why this is not working (works for mepis).

---

### Post by Pobega on 2006-12-17
Thank you, it's not like it's a big deal but having that window prompting me to update Gaim and having to untick Gaim everytime I want to update Ubuntu is very annoying.

---

### Post by bapoumba on 2006-12-17
I came across this looking up **man aptitude** :
```
 remove, purge, hold, keep, reinstall
              These commands are the same as ‘‘install’’, but apply the  named
              action to all packages given on the command line for which it is
              not overridden. The difference between hold  and  keep  is  that
              hold  will  cause a package to be ignored by future upgrade com&#8208;
              mands, while keep merely cancels any scheduled  actions  on  the
              package.
```
What about the hold option ?

---

### Post by Pobega on 2006-12-17
That seemed to work actually, thanks! I knew there was some type of hold function or something somewhere, I just couldn't find it (I had the latter part of the information I need).

Thanks again!

---

### Post by Pobega on 2006-12-18
> **pay said:**
> To uninstall it try ```
sudo aptitude remove gaim #or
sudo apt-get remove --purge gaim
```To install 1.5 try```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.x86.package
sudo sh gaim-1.5.0.x86.package
```If that doesn't work try ```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.tar.bz2
tar jxvf gaim -1.5.0.tar.bz2
cd gaim
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep gaim
./autogen.sh #or ./configure if that doesn't work
gmake
sudo checkinstall gmake install
```

I just reinstalled and tried this step, but it seems that Ubuntu-Desktop has become dependant on Gaim 2.0.0 being installed. Is there any way around this?

---

### Post by Pobega on 2006-12-19
Ugh, this is really pissing me off. I'm trying to do everything I can but Ubuntu won't let me have ubuntu-desktop and Gaim 1.5.0 installed at the same time!

---

### Post by _Matrix_ on 2007-05-06
WoW!!

The solution looks simple but when I tried it did not work. So my question to you Pobega is how in heaven's name did you get Gaim 1.5 downloaded and working using those commands?

Please explain.

---

