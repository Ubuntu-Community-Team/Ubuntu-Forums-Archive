---
title: "synaptic packager manager"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by gwardlow on 2007-08-12
I have ubuntu 704 standard; when I try to open synaptic package manager It gives me the following message.



E: Type '--07:13:11--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Type '--07:13:11--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

---

### Post by forestpixie on 2007-08-12
open a terminal

enter the following it will open atext editor - paste the contents of that here

gedit /etc/apt/sources.list.d/medibuntu.list

that assumes you're using Ubuntu - if not change gedit to the text editor you use

---

### Post by gwardlow on 2007-08-12
> **forestpixie said:**
> open a terminal

enter the following it will open atext editor - paste the contents of that here

gedit /etc/apt/sources.list.d/medibuntu.list

that assumes you're using Ubuntu - if not change gedit to the text editor you use

gwardlow, reply, synaptic package manager still wont open;--07:13:11--  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list)
           => `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

    0K                                                       100%   23.54 MB/s

07:13:11 (23.54 MB/s) - `feisty.list' saved [233/233]

---

### Post by forestpixie on 2007-08-12
can you paste the contents of the file in the thread need to know exactly what it looks like

or does it actually say this

```

gwardlow, reply, synaptic package manager still wont open;--07:13:11-- http://medibuntu.sos-sts.com/sources.list.d/feisty.list
=> `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

0K 100% 23.54 MB/s

07:13:11 (23.54 MB/s) - `feisty.list' saved [233/233]

```

---

### Post by gwardlow on 2007-08-12
[QUOTE=forestpixie;3177891]can you paste the contents of the file in the thread need to know exactly what it looks like

or does it actually say this


[CODE]
gwardlow, reply, synaptic package manager still wont open;--07:13:11-- http://medibuntu.sos-sts.com/sources.list.d/feisty.list
=> `feisty.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

0K 100% 23.54 MB/s

07:13:11 (23.54 MB/s) - `feisty.list' saved [233/233]

gwardlow; It actually says everything after the words still wont open..

---

### Post by ajgreeny on 2007-08-12
Try:-
gedit /etc/apt/sources.list
which should output your sources.list file which you can copy and show us here.  I can not understand the extra bits on the end of the file name and don't think they should be there at all.

---

### Post by forestpixie on 2007-08-12
ok then if that's what it says then we need to edit it, 

open a terminal 

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

it should open in the text editor again - you need to remove the 

```
--07:13:11-- 
```

from in front of the [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list)

then save 

then in terminal try to update 
```

sudo apt-get update
```

if the update fails post what it says - without typing in front of it - makes it easier to see what's going on :)

---

### Post by forestpixie on 2007-08-12
> **ajgreeny said:**
> Try:-
gedit /etc/apt/sources.list
which should output your sources.list file which you can copy and show us here.  I can not understand the extra bits on the end of the file name and don't think they should be there at all.
 think the problems with the medibuntu.list - never really understood where that extra bit comes from - but I've only been here couple of months

---

### Post by gwardlow on 2007-08-12
george@george-desktop:~$ sudo apt-get update
E: Type 'http://medibuntu.sos-sts.com/sources.list.d/feisty.list' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
george@george-desktop:~$

---

### Post by forestpixie on 2007-08-12
can you please post the contents of the file here so we can see it properly

---

### Post by gwardlow on 2007-08-12
> **forestpixie said:**
> can you please post the contents of the file here so we can see it properly

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe


# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

### Post by forestpixie on 2007-08-12
OK - that's not the same file thats /etc/apt/sources.list :) - but no matter 

we'll rename the file that's causing problems and put the medibuntu repo in this file.

open a terminal and paste this in

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.bak
```

to check that it's been renamed in a terminal

```
ls /etc/apt/sources.list.d/medibuntu.list
```

it should say no such file or directory - if it doesn't post back

then in a terminal paste these 2 commands separately - enter after each

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by gwardlow on 2007-08-12
Success; synaptic package manager opened fine, thank you. I messed it up trying to install a graphics driver but I had no idea exactly what i did or how to fix it. I have a nvidia geforce 8800 gts and on install if i let it install the driver it wants to ubuntu wont reboot, so i,m running on some generic driver it installed and it does'nt even have my resolution, the printer driver it installed wont run my printer either, so i don't know wheather i'm going to be able to use ubuntu or not. Thanks again i'm back to where i started. thanks very much.

---

### Post by forestpixie on 2007-08-12
Have you checked out the support for your printer - [http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

Have a look on the forum for your graphics card - usually nVidia work out ok.
Have you tried the restricted drivers management for the graphics card?

System >Admin > Restricted Drivers Management - if theres a tick box to install the driver you could do it that way.

Or there's [Envy]("http://albertomilone.com/nvidia_scripts1.html") - I myself never used it - but it seems to work for a lot of people.

Anyway - glad we sorted that :)

---

### Post by gwardlow on 2007-08-12
My printer is not listed on that site, My printer is a photosmart 3210 all in one. my graphics card is xfx nvidia gforce 8800 gts and i'm not even sure how ti install the drivers if i had one that would work. i havent been able to install anything except those listed in synaptic package manager.

---

### Post by fanofai on 2008-02-21
I also faced the same problem as gwardlow, and forestpixie's solution worked perfectly. Thanks a lot !

---

