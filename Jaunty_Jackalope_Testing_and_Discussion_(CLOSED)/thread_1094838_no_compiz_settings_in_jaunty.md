---
title: "no compiz settings in jaunty"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdwinder on 2009-03-13
Anyone know how to add compiz settings in 9.04?

i tried going to synaptec and just searching for compizsettings, but i get nothing...does it even exist?

---

### Post by cariboo on 2009-03-13
I have asked the mods to move this to the proper place. You are probably looking for compizconfig-settings-manager.

Jim

---

### Post by michael37 on 2009-03-13
Make sure that compizconfig-backend-gconf and compizconfig-settings-manager packages are installed.

Works for me.

---

### Post by nyarnon on 2009-03-13
> **sdwinder said:**
> Anyone know how to add compiz settings in 9.04?

i tried going to synaptec and just searching for compizsettings, but i get nothing...does it even exist?

Just search on compiz and they all will appear. Even better and safer you use: 

```

sudo apt-cache search compiz | sort
```

---

### Post by rburkartjo on 2009-03-13
michael did what you said but still have to manually start ccs with each restart or login and when i open any apps the window on the apps i start is messed up and ideas for now i just dont use ccs and have no problems.

---

### Post by sdwinder on 2009-03-13
thats the problem, when i search for compiz, the only packages i get are ones that are already installed...the compizbackend is already there, but the settings manager is nowhere, its not installed, and nothing else that i dont already have shows up.

---

### Post by Pat L.I. on 2009-03-13
Compiz-settings-manager is crashing for me whenever i try to click on "wobbly" in order to get to the preferences. 

Im trying to turn off snap inverted. Can anyone help me do this by the command line?

---

### Post by michael37 on 2009-03-14
> **sdwinder said:**
> thats the problem, when i search for compiz, the only packages i get are ones that are already installed...the compizbackend is already there, but the settings manager is nowhere, its not installed, and nothing else that i dont already have shows up.

What does 
```

sudo apt-get update; sudo apt-get install compizconfig-settings-manager

```
produce?

---

### Post by michael37 on 2009-03-14
> **Pat L.I. said:**
> Compiz-settings-manager is crashing for me whenever i try to click on "wobbly" in order to get to the preferences. 

Im trying to turn off snap inverted. Can anyone help me do this by the command line?

Sounds like your compiz settings are severely broken.  Still, doesn't sound like a jaunty-specific issue -- more like compiz itself. Take a look at this thread: [thread]259831[/thread]

---

### Post by jocko on 2009-03-14
> **sdwinder said:**
> thats the problem, when i search for compiz, the only packages i get are ones that are already installed...the compizbackend is already there, but the settings manager is nowhere, its not installed, and nothing else that i dont already have shows up.
Are you using the **Search** function or the **Quick Search** function in synaptic?
Only the **Search** function will actually search through the entire package database. **Quick Search** just removes the packages that does not match the search string from the list of packages.

---

### Post by rburkartjo on 2009-03-14
this is how i got compiz to work in 9.04 open smp
do a search for compiz
and then make sure the following are installed if not install
compiz
compiz-core
compiz-gnome
compiz-ccsm

and if someone will tell me how i can paste a .png file in a post i will include it shows all the compiz files i have installed. and compiz works like a charm for me no problems/tks

---

### Post by michael37 on 2009-03-14
> **rburkartjo said:**
> this is how i got compiz to work in 9.04 open smp
do a search for compiz
and then make sure the following are installed if not install
compiz
compiz-core
compiz-gnome
compiz-ccsm

and if someone will tell me how i can paste a .png file in a post i will include it shows all the compiz files i have installed. and compiz works like a charm for me no problems/tks

compiz-ccsm package does not exist in 9.04

It's either simple-ccsm or compizconfig-settings-manager.

---

### Post by taavikko on 2009-03-14
> **rburkartjo said:**
> this is how i got compiz to work in 9.04 open smp


and if someone will tell me how i can paste a .png file in a post i will include it shows all the compiz files i have installed. and compiz works like a charm for me no problems/tks

Why use an image, when you can copy&paste from terminal...

Something like
```
dpkg -l |grep compiz
```
will list all installed packages containing compiz...

---

### Post by rburkartjo on 2009-03-14
taa, tks
okay here is what i have install and compiz works great

ray@ray-desktop:~$ dpkg -l |grep compiz
ii  compiz                                                                       1:0.8.2-0ubuntu3                        OpenGL window and compositing manager
ii  compiz-core                                                                  1:0.8.2-0ubuntu3                        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                                                  0.8.2-0ubuntu1                          Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                                                   0.8.2-0ubuntu1                          Collection of plugins from OpenCompositing f
ii  compiz-gnome                                                                 1:0.8.2-0ubuntu3                        OpenGL window and compositing manager - GNOM
ii  compiz-kde                                                                   1:0.8.2-0ubuntu3                        OpenGL window and compositing manager - KDE 
ii  compiz-plugins                                                               1:0.8.2-0ubuntu3                        OpenGL window and compositing manager - plug
ii  compiz-wrapper                                                               1:0.8.2-0ubuntu3                        OpenGL window and compositing manager, wrapp
ii  compizconfig-backend-gconf                                                   0.8.2-0ubuntu1                          Settings library for plugins - OpenComp

---

### Post by moomba89 on 2009-04-22
This may be a bit late, but for anyone looking for the cure, there's a bug with synaptic at the moment that's causing search functions to miss out information - see: [here]("https://bugs.launchpad.net/ubuntu/+s...ic/+bug/288797") and [here]("http://ubuntuforums.org/showthread.php?t=1015138")

In summary, to fix the issue, run:
```
sudo update-apt-xapian-index
```

OR if that doesn't work:
```
sudo apt-get update
sudo rm -fr /var/lib/apt-xapian-index
sudo update-apt-xapian-index
```

Worked for me :)

---

### Post by zevans on 2009-04-22
It may be that you have compiz installed correctly but you have a graphics chipset with a known bug. Could you post the output of ```
lspci | grep VGA
``` please?

---

