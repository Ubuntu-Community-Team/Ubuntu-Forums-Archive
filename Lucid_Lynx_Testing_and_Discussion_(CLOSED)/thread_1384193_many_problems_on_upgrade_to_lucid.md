---
title: "many problems on upgrade to lucid"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2010-01-18
hi I just upgraded to lucid from karmic and I have run into many problems

1.
I think I have run into dependency hell
 this Is the output of my sudo apt-get upgrade
[http://pastebin.ubuntu.com/358413/](http://pastebin.ubuntu.com/358413/)
somebody please help

2. now i have no codecs it seems. though all gstreamer installed and medibuntu enabled. maybe this is related to 1.
when i play a movie in totem it tells me that codec has to be searched and then it searches but doesnt find anything even for common codecs.

3. i have a nvidia 6200 graphics card. when ever i start my computer i get it without a window borders (without window manager) and when i go to pref->appearance->visual effects and then select normal then i get window settings (like max,min,close etc) bar

but i have to do this everytime i restart my computer.

Please help.

---

### Post by mc4man on 2010-01-18
You may or may not have been caught in a partial update

Note  that there was an update tonight to the ffmpeg libs that's not complete yet - if you get the new libavcodec52 then the gstreamer bad plugin must be removed and can't be re-installed yet

 or if the gstreamer bad plugin is installed then libavcodec52 can't be updated or possibly for you installed ( nor anything that depends on it

Not sure if that's your problem, a little time in synaptic may tell you

---

### Post by benny.kallstrom on 2010-01-18
Update-manager offered a partial upgrade today that would remove gstreamer bad plugins, and that would stop playing most videos on ubuntu.

---

### Post by tgpraveen on 2010-01-18
> **benny.kallstrom said:**
> Update-manager offered a partial upgrade today that would remove gstreamer bad plugins, and that would stop playing most videos on ubuntu.

glad to know i am not the only one with the prob then.

---

### Post by mc4man on 2010-01-18
What you should be able to do to get your upgrade, players ect. back on track is to install the 'regular' versions of ffmpeg libs (libavcodec52, libavformat52, ect.

The extra versions cannot be installed with the gstreamer bad plugin due to a split of the dirac library which hasn't been enabled/built into gstreamer yet.

You'd need to initiate this from synaptic by searching ffmpeg and marking libavcodec52 for install (apt-get may work also but synaptic is better suited

Hopefully that would start the ball rolling, otherwise you'd need to remove all the ffmpeg libs first and then re-install your players, plugins and the regular ffmpeg libs

At what point gstreamer-bad will be re-built with the new dirac libs I don't know, could be soon or may take a while

---

### Post by tgpraveen on 2010-01-19
i manually uninstalled all the packages which were causing error and reinstalled them and now i have my video playing abilites back now the only problem i have is that when i do sudo apt-get upgrade i get:

```

praveen@praveen-desktop:~$ sudo apt-get upgrade
[sudo] password for praveen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  python-qt3
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up swell-foop (1:2.29.5-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing swell-foop (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 swell-foop
E: Sub-process /usr/bin/dpkg returned an error code (1)
praveen@praveen-desktop:~$ 

```

oh and problem no. 3 still exists

---

### Post by ranch hand on 2010-01-19
Have you run;
```

sudo dpkg --configure -a

```
to see if that will fix it or at least tell you what the problem is?  May or may not do any good but you probably should try it.

For all these problems - Welcome to Alpha testing.  Have FUN.  This is a long way from a stable release yet.

We have had some kind or another xorg update twice a day for the last few.  Things are changing fast.  Some things are behind the curve, others ahead of it.

Start being careful what you upgrade.

---

### Post by jppr on 2010-01-19
run...

sudo aptitude update

sudo aptitude -f install

sudo dpkg --configure -a

sudo aptitude dist-upgrade

---

### Post by tgpraveen on 2010-01-19
> **ranch hand said:**
> Have you run;
```

sudo dpkg --configure -a

```
to see if that will fix it or at least tell you what the problem is?  May or may not do any good but you probably should try it.

For all these problems - Welcome to Alpha testing.  Have FUN.  This is a long way from a stable release yet.

We have had some kind or another xorg update twice a day for the last few.  Things are changing fast.  Some things are behind the curve, others ahead of it.

Start being careful what you upgrade.
didnt help
and yeah its my first time testing this early in cycle
in jaunty i tried from alpha 4 or 5.

but this time i just jumped in.

---

### Post by mc4man on 2010-01-19
The gnome-games issue is separate from the ffmpeg libs and players deal, you probably can take care of it manually.

I'd use synaptic and ck. on the versions you have of some of the packages and see what you can work out.
gnome-games-common would be one to look at

(the game swell-foop is a lucid only game

For referencing versions use this page to access info on packages involved, ect
[http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gnome-games](http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gnome-games)

Shouldn't be that difficult to to work out what's blocking the install/upgrade

(though again you could remove and re-install (gnome-games-common is the key package 

( which nvidia driver is/was the 6200 using now and when on karmic (if you know)

---

### Post by tgpraveen on 2010-01-19
> **mc4man said:**
> The gnome-games issue is separate from the ffmpeg libs and players deal, you probably can take care of it manually.

I'd use synaptic and ck. on the versions you have of some of the packages and see what you can work out.
gnome-games-common would be one to look at

(the game swell-foop is a lucid only game

For referencing versions use this page to access info on packages involved, ect
[http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gnome-games](http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=gnome-games)

Shouldn't be that difficult to to work out what's blocking the install/upgrade

(though again you could remove and re-install (gnome-games-common is the key package 

( which nvidia driver is/was the 6200 using now and when on karmic (if you know)

i have solved the codecs issue with a lot of remove and install.

the games problem seems to be of improper packaging/some corruption on my side or soemthing. stil working on it.

the nvidia diriver i was using on karmic was the last one the 185 series iirc it was the recommended one. the latest one.

---

### Post by mc4man on 2010-01-19
On my lucid installs while there were some games installed, gnome-games wasn't, so went ahead and installed. (actually took 3 attempts, keep failing on some of the swell-foop dep.'s, though no errors

Anyway if it won't let you install or remove a little fooling around suggests you could probably resolve that with some editing in either /var/lib/dpkg/status or /var/lib/dpkg/info/, the former being more straightfoward

---

