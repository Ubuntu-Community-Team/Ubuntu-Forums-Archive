---
title: "This application conflicts with other installed software"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by ulster_con on 2007-11-05
Hey all, 

sorry to bother you, im sure this aint too had to solve, but im not too experienced in linux yet. but i was using fiesty fawn for a month, then upgraded to gutsy gibbon, and i have encountered some problems.... 

when i try to download a codec to play sound, it looks to install Gstream, 
trying to install this gives the error: "This application conflicts with other installed software".

so, i switch to synaptic package manager, and i try to install it there (or amsn, vlc etc),
and it says... 

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

so, i read many other reports of similar issues and tried what i options were given to support, such as....

1. 
Applications -> Accessories -> Terminal
gksudo gedit /etc/apt/sources.list
Save it and run

sudo aptitude update
sudo aptitude install vlc

i get this return: 
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

(there is more, but not much point in adding a full page of it)

2. 
going to system/admin/software sources and changing the settings to:
community maintained open source software (universe)
proprietary drivers for devices (restricted)
software restricted by copyright or legal issues (multiverse)

3. 
ive tried downloading amsn + right clicking / run


have you any further suggestions?

the list of things that dont work are: 
the sound codecs, installing almost everything, and cubes (but, im not worried about the cubes bit yet)

thank you kindly 

Con

---

### Post by zvacet on 2007-11-05
```
gksudo gedit /etc/apt/sources.list
```

and  make your lines look like this

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Save and close.

```
sudo aptitude update
```

Go to the synaptic and in search box type** vlc** and when you find it install it.If you have any problem you can try **synaptic>edit>fix broken packages**

---

### Post by ulster_con on 2007-11-05
> **zvacet said:**
> ```
gksudo gedit /etc/apt/sources.list
```

and  make your lines look like this

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Save and close.

```
sudo aptitude update
```

Go to the synaptic and in search box type** vlc** and when you find it install it.If you have any problem you can try **synaptic>edit>fix broken packages**

thanks for the reply so soon,

but, the code u supplied is the same as the code i used, but the results do not match yours, also, often when i try to install something, it says...

This application conflicts with other installed software. To install '*******' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


so, there is something preventing me installing these programs, 
and hopefully there is simply a setting to edit or a command to complie. :D

and this brings me back to square one.

oh, the edit broken packages option didnt work either :(

---

### Post by ulster_con on 2007-11-06
have you or anyone any more suggestions... ? 

im outa luck! 

:(

---

### Post by bulldog on 2007-11-06
You have the answer already.
There are conflicting packages installed,probably this happened in Feisty,you have to uninstall them first.
When you upgrade from Feisty to Gutsy it could be wise to uninstall all the software which you have downloaded from outside the official repo's first,before the upgrade.
The upgrade will ignore this packages but it can conflict with packages you want to install.

With aptitude you get a list with options,you have to make a choice what is the best solution for you.
```
sudo aptitude install vlc
```
Read carefully what the output tells you.

---

### Post by ulster_con on 2007-11-06
thanks, 

i do 

and the result is as follows:

The following packages are BROKEN:
  amsn tcltls 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3520kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 which is a virtual package.
        Depends: tk8.4 which is a virtual package.
  tcltls: Depends: tcl8.3 which is a virtual package. or
                   tcl8.4 which is a virtual package.

so, i go to synaptic package manager, and try to fix broken packages, 

and i try to install tcl8.4, but i can only locate + install tclx8.4

and i try to install tclx8.3 but it wont install as it says its unstable.

tcltls wont install either as its says its unstable too .

---

### Post by bulldog on 2007-11-06
Go into synaptic and choose to remove amsn completely,with a little luck it will uninstall all the unwanted stuff.
If not try to do it manually,and if done reinstall amsn from the repo's.

---

### Post by ulster_con on 2007-11-06
> **bulldog said:**
> Go into synaptic and choose to remove amsn completely,with a little luck it will uninstall all the unwanted stuff.
If not try to do it manually,and if done reinstall amsn from the repo's.

amsn is not installed, it never was.....
i used fiesty before this, but i didnt upgrade,
i decided to start fresh, so created new partitions + loaded up gutsy.

ever since it has been loaded, i cannot install almost everything.

i understand there is something conflicting, and preventing the install,
but im not sure what.
uninstalling amsn, if it was installed probably wouldnt affect all the other programs i want to install.. also, im missing audio codecs for movie + music players, it will play .ogg, not .mp3 etc, but i cannot install / update it, so this is most likely the same issue,

thank u

---

### Post by bulldog on 2007-11-06
Try in a terminal aptitude -h this will get you a bunch of options to use aptitude.
Like```
sudo aptitude -f remove amsn tcltls 
```
Or```
sudo aptitude --purge amsn tcltls 
```
Or```
sudo aptitude full-upgrade
```

---

### Post by ulster_con on 2007-11-06
[COLOR="Red"]removed amsn tcltls[/COLOR]

sudo aptitude -f remove amsn tcltls
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 

I did a full updrade in command line...

[COLOR="Red"]then i tried to re-instal amsn tcltls, but it failed,[/COLOR]
The following packages are BROKEN:
  amsn tcltls 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3520kB of archives. After unpacking 11.5MB will be used.
The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 which is a virtual package.
        Depends: tk8.4 which is a virtual package.
  tcltls: Depends: tcl8.3 which is a virtual package. or
                   tcl8.4 which is a virtual package.

[COLOR="Red"]
so, i installed via terminal, tcl8.3 + tcl8.4.
i tried again to install via terminal tcltls + this is the result:[/COLOR]

0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.9kB of archives. After unpacking 303kB will be used.
The following packages have unmet dependencies:
  tcltls: Depends: tcl8.3 which is a virtual package. or
                   tcl8.4 which is a virtual package.


thanks for assisting so far btw

---

### Post by bulldog on 2007-11-06
I did a search in synaptic and found all those virtual packages,but there's not one installed though.
You mentioned you had broken packages,can't you repair them with synaptic?
It should be an option under the edit tab.
Think that's the most common way to clear things.

---

### Post by ulster_con on 2007-11-06
well, see i cannot install tcl8.3 and 8.4, only tclx8.4 is intallable,
so as a result, i cannot install tcltls or amsn or vlc etc..

the broken packages are the tcl related ones, but are not installed, 
so, thats the delima i have got.

---

### Post by timcredible on 2007-11-06
you said you did a fiesty->gutsy upgrade?  looks like that left some files behind that is messing up.  if possible, backup your data somewhere and install gutsy cleanly from cd, and this problem will go away.

---

### Post by ulster_con on 2007-11-06
> **timcredible said:**
> you said you did a fiesty->gutsy upgrade?  looks like that left some files behind that is messing up.  if possible, backup your data somewhere and install gutsy cleanly from cd, and this problem will go away.

i used fiesty first, but i choose to create new partitions, so its a fresh install of gutsy, 
fiesty shouldnt inerfere 

but, im thinking reinstalling it might be an option,
ill consider that b4 the week is out

---

### Post by ashlakim on 2007-11-09
It seems that some 'components' aren't available or broken down during installation of ubuntu. Why not try download and install those components separately.

Get those three that your computer lacked off:

[http://packages.ubuntu.com/edgy-backports/net/vlc-nox](http://packages.ubuntu.com/edgy-backports/net/vlc-nox)
[http://packages.ubuntu.com/feisty/libs/libsdl-image1.2](http://packages.ubuntu.com/feisty/libs/libsdl-image1.2)
[http://packages.ubuntu.com/edgy/x11/ttf-dejavu](http://packages.ubuntu.com/edgy/x11/ttf-dejavu)

*Just go to the bottom of the right page and you'll find a Table. Choose which one suits your computer (How do you know it, just trial and error) But, Try installing the 1386 first see if works. if not then, try another one.

Good Luck. I hope I got just what you need.

(i just googled your missing/broken 'components' :P)

Best Regards, 
ashlakim

---

### Post by ashlakim on 2007-11-09
As for ulster_con:

Get those packages you're lacking off manually from below addresses i googled for you:

[http://packages.ubuntu.com/feisty/devel/expect-tcl8.3-dev](http://packages.ubuntu.com/feisty/devel/expect-tcl8.3-dev)
[http://packages.ubuntu.com/dapper/interpreters/tcl8.4](http://packages.ubuntu.com/dapper/interpreters/tcl8.4)
[http://packages.ubuntu.com/feisty/source/tclx8.4](http://packages.ubuntu.com/feisty/source/tclx8.4)

*Just go to the bottom of the right page and you'll find a Table. from there, try trial and error. 

Good Luck.I hope I got just what you need.

Best Regards,
ashlakim

---

### Post by dESAI on 2007-12-30
I have the same problem with a fresh install of Gutsy. Never had this problem before this install.

Why is this happening? This is stupid and very disapointing...

I've also just installed ubuntu on my dads pc after recommending it.

---

### Post by Stonedancer on 2008-04-12
Don't worry you're not insane. I'm experiencing exactly the same "application conflicts" problem with a FRESH install of 7.10 on a toshiba Tecra M2 laptop with 1.5ghz and 768mb ram. I've never had problems like this on the other 7 or 8 installations I've done. even on the same spec of laptop.  

Surely someone can suggest something at the synaptic/OS level that could be causing this rather than suggesting other ways of installing the wanted apps? Please someone?

---

### Post by pbpersson on 2008-04-12
Well.....I am way out of my comfort zone here......but my understanding is that deep inside the OS for package management you use dpkg and apt-get.

So.....what happens if you type dpkg -l amsn*

Does it find anything?

If it does, can you remove it by typing 

sudo apt-get remove <package name>

The entire experience of low-level package management is not a world where I have yet ventured but I am planning to take that journey in the near future.

---

