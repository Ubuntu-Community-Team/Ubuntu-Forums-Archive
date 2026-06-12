---
title: "WARNING RE LATEST UPDATE: Broken dependency: linux-image-generic"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Trebaruna on 2007-02-08
I just booted my PC to Edgy, and the update icon was sitting in the tray. So, like roughly every other day, I click it to install yet another update. But not this time.

It appears from what I can see that there is a new kernel for ubuntu: 2.6.17-11 (whereas the one I have is -10). Linux-image-generic has been bumped and now depends on said new version, but the dependency cannot be satisfied because the actual image is not in the repo. 

After some trying it appears I was able to remove the dummy packages linux-generic and linux-image-generic but the actual kernel image files cannot be updated, and as a result said packages cannot now be reinstalled.

Is this a known thing? Have I broken something? Is it a bug?

---

### Post by yhotg on 2007-02-08
sorry, i wrote same post twice

:(

---

### Post by yhotg on 2007-02-08
same thing here,
 hope it doesn't broke anything. i got kind of little obsessed and started cleaning old linux-images and restricted modules and headers.

the problem seems to be on the headers-generic and in the restricted-modules-generic too.

if it is a problem. hope no, cos i don't want to be all next weekend getting it all alright after removing packages... 

:(

---

### Post by Tanker Bob on 2007-02-08
Same problem here with Kubuntu 6.10.  Adept updated three packages, but three are set to "no change": linux-headers-generic, linux-image-generic, and linux-restricted-modules-generic.  When I try to change them from "no change" to "update", only one can be changed and it changes to "BREAK (update)" in red font.  To me, that says leave it alone, but Adept Updater remains in the system tray saying there are 3 updates.  What's the deal and what should I do?

---

### Post by gray380 on 2007-02-08
Hi there!

I have a strange trouble wile try to update (with update manager).

linux-image-generic:
 Depends: linux-image-2.6.17-11-generic  but it is not installable

Add. info:
Current ver.: 2.6.17-10
Last ver.: 2.6.17-11

Any assistance?

brg,
Serhiy.

---

### Post by yhotg on 2007-02-08
nothing? LOL

if u didn't start getting packages out and in like i did then u should wait 'till someone fix it. 
in my case i think i'll boot to see what happens. lol

---

### Post by amelyst on 2007-02-08
Same here with kubuntu 6.10 edgy.

After some digging around i am sure now that the repo was not setup correctly.
If you directly look at the Packages.gz file at [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/) you see that the generic kernel parts are still klisted as of version 2.6.17.10 whereas the specific versions all have version 2.6.17.11.

Moreover looking at [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/) you find there all the packages needed like linux-image-generic_2.6.17.11_i386.deb all having a modification date of today.
So this suggests some glitch in the preparation of the repository :( .

Being a security fix and not a feature upgrade i think glitches of this kind must not happen.

I haven't updated anything yet and are waiting for the problem to get fixed.

---

### Post by blueglow on 2007-02-08
I too have this problem.

In the Software Updates popup there are four listed, with the top two (linux-headers-generic & linux-image-generic) un-tickable whilst the bottom two (restricted modules and xorg fglrx) are fine.

Synaptic also shows the updates but they aren't installable:
> linux-headers-generic:
 Depends: linux-headers-2.6.17-11-generic  but it is not installable
linux-image-generic:
 Depends: linux-image-2.6.17-11-generic  but it is not installable


Seems a bit of a poor show by the release people for such a fundamental system component.

---

### Post by PartisanEntity on 2007-02-08
Several updates were ready to be installed today but two were held back:

[IMG]http://i17.tinypic.com/43d9wkn.png[/IMG]

I went into Synaptic and when I mark either of them for install manually I get this message:

[IMG]http://i10.tinypic.com/4clk7f6.png[/IMG]

Now when I try to install the package on which these packages depend, namely: **linux-image-2.6.15-28-386** I can't find it.

Is this due to an error on my end?

Here are the contents of my **sources.list**:

```
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://at.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://at.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

#nvidia through tseliot site
deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/

```

If I try to sudo apt-get update in the terminal I get this:

```
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:3 http://at.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://at.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:5 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://at.archive.ubuntu.com dapper Release
Get:7 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:8 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://at.archive.ubuntu.com dapper-updates Release
Get:9 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://at.archive.ubuntu.com dapper/main Sources
Hit http://at.archive.ubuntu.com dapper/restricted Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper-security Release
Hit http://at.archive.ubuntu.com dapper-updates/main Packages
Hit http://at.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://at.archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://www.getautomatix.com dapper Release
Hit http://at.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://www.albertomilone.com binary/ Release.gpg
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Ign http://www.albertomilone.com binary/ Release
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://www.albertomilone.com binary/ Packages
Fetched 9B in 1s (9B/s)
Reading package lists... Done
```


I am not sure what to do next, thank you in advance.

---

### Post by Tanker Bob on 2007-02-08
I rebooted and the Adept icon appeared in the system tray at first but then disappeared after a few seconds.  I'm not changing anything until a knowledgeable individual offers sage advice.  Just because I'm paranoid doesn't mean that they aren't out to get me. :)

EDIT: I rechecked the kernel version and it is still 2.6.17-10-generic.  That confirms what grub had listed.  So, it looks like the actual kernel update did not take place.

---

### Post by Paul41 on 2007-02-08
I am using a different kernel than you but got the same errors today. It looks to me like not all of the files were added to the repository yet.

---

### Post by dr_d on 2007-02-08
hi i'm having the same problem... i think it's something to do with the fact that we both have the nvidia drivers installed but apart from that i have no idea what the problem is or how to fix it.

---

### Post by PartisanEntity on 2007-02-08
@  Paul41: Thanks for the quick reply, that is kind of what I was thinking.

@ dr_d: Think it has something to do with the method we used to install our nvidia drivers?

---

### Post by Paul41 on 2007-02-08
I don't know if it makes any difference, but I also have the nvidia drivers installed.

---

### Post by Flatwinder on 2007-02-08
Same situation here. I have the NVidia drivers installed also. I don't have a clue as to what I should do. I'm so green I wouldn't have even thought about the NVidia drivers might have something to do with it.

But it's just a matter of time until a seasoned veteran sees these posts and helps us out.

---

### Post by Joviannm on 2007-02-08
I also have this problem and I have an onboard intel video card.  I tried uninstalling all third party codecs and automatix to see if that helped but it didnt.

---

### Post by Famicommie on 2007-02-08
I'm using the ATI drivers and I got the same thing. I don't think it has anything to do with your video card.

---

### Post by dr_d on 2007-02-08
Now I'm really not sure about any of this, but here's my theory:

The nvidia drivers somehow depend on linux-restricted-modules... and when a new version of the restricted modules come out, synaptic wont install it because nvidia-glx depends on the old version. Or something remotely like that.

All I know is that last time I had package problems it was because of the dependencies of nvidia-glx and linux-restricted-modules was involved.



Also this time, the problem (for me) was caused when I **updated**:
linux-generic
linux-restricted-modules-common
nvidia-glx

The following packages were **held back**:
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic


So in conclusion, I have absolutely no idea what is going on, but I think it's a fair guess that the nvidia drivers are involved.

Oh and btw PartisanEntity I don't think it's a problem relating to the method used to install nvidia drivers. idunno about you but I got mine directly from the ubuntu repos (apt-get install nvidia-glx).


I hope we get this fixed before feb 20th... I want my computer in top form for Beryl 0.2.0 :)


EDIT: Joviannm , Famicommie: I just read your posts.. This seems to prove my theory wrong....

---

### Post by PartisanEntity on 2007-02-08
As far as I know, the nvidia drivers should not prevent the update from being carried out. Also, once the update has completed one has to reinstall the nvidia drivers (i think).

Lets see what the experienced users will say :)

---

### Post by Paul41 on 2007-02-08
> Oh and btw PartisanEntity I don't think it's a problem relating to the method used to install nvidia drivers. idunno about you but I got mine directly from the ubuntu repos (apt-get install nvidia-glx).

I also got the nvidia drivers from the repos and I have updated these packages several times with no issues previously so I don't think the install method has anything to do with it. I am not fully convinced that the nvidia drivers have anything to do with it anyway.

---

### Post by dr_d on 2007-02-08
Here's another guy who seems to be having the same problem. The funny thing is that he also mentioned something about the nvidia drivers...

[http://ubuntuforums.org/showthread.php?p=2123504#post2123504](http://ubuntuforums.org/showthread.php?p=2123504#post2123504)

---

### Post by tonyr1988 on 2007-02-08
Just wanted to say what my update manager told me this morning. It said I had the following updates:

linux-headers-generic
linux-image-generic
linux-restricted-modules-common

Only the restricted modules was check-marked - the others were going to be held back. I didn't attempt to update (out of fear :D).

I also have the binary nVIDIA drivers and MadWifi drivers (if I remember right, that's why I got the restricted modules package).

I update my system whenever it asks, so that shouldn't be a problem, and those are the only 3 updateable packages.

---

### Post by MLX on 2007-02-08
Same problem here and I am NOT using the nvidia drivers.

---

### Post by Xyhthyx on 2007-02-08
I just got this same problem. I checked the related packages for recomended installations and they suggested the following: nvidia-glx, lilo, avm-fritz-firmware-2.6.17-10.

I installed nvidia-glx (even though I have a Radeon IGP) to see if it helped and no go.

---

### Post by banditti on 2007-02-08
I too am having the same problem with ATI drivers.

---

### Post by Vorian on 2007-02-08
There are dependency issues with the latest kernel build.

---

### Post by ratherbsailing on 2007-02-08
I have the same problem, I don't think it's nvidia releated.  

Synaptic says: 

linux-image-386 installed version: 2.6.15.25 latest version: 2.6.15.26

Linux kernel image on 386.
This package will always depend on the latest kernel image available
for 386.

When I hit "Mark For Upgrade"

linux-image-386:
 Depends: linux-image-2.6.15-28-386  but it is not installable

This is wierd, if the latest version is 2.6.15.**26** how can it depend on 2.6.15.**28**

---

### Post by Vorian on 2007-02-08
Because the newest linux-image has yet to be released.

---

### Post by John.Michael.Kane on 2007-02-08
Threads merged..

---

### Post by banditti on 2007-02-08
can you merge with this one too?

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

---

### Post by banditti on 2007-02-08
So, it is a broken release?

---

### Post by Xyhthyx on 2007-02-08
I see, so the metapackages to do the upgrade is available but not the actual upgrades? Confusing..

---

### Post by jnj on 2007-02-08
Same issues, except now my system is completely locked up and I can not do anything.

Suggestions welcomed on how to recover at least terminal access to the machine....

(Jumped to this thread from another similar thread to consolidate)

---

### Post by croc1 on 2007-02-08
have you tried Ctrl+Alt+Backspace

---

### Post by jnj on 2007-02-08
To be very specific about the system lockup symptoms:

    - the system runs through the normal Ubuntu start
    - the desktop is displayed
    - the mouse moves the cursor on the screen
    - only the initial click of the mouse results in an apparent click - but nothing happens and subsequent clicks have no effect, but the mouse still moves the cursor
    - the keyboard does not work at all - no key strokes are recognized
    - the only way to restart is to power down and restart with the on/off button

Not sure how to proceed - is there some way to revert to the last workable config?

Thanks,

---

### Post by banditti on 2007-02-08
I am not sure if this is related to your issue, but I have beryl and put in a fix for the Beryl Shift + backspace issue ([http://ubuntuforums.org/showthread.php?t=354396&page=2](http://ubuntuforums.org/showthread.php?t=354396&page=2)) and it quit working after the updates this morning.  

I am not looking for feedback on that issue in this post, just throwing it out there for other potential related problems.

---

### Post by dr_d on 2007-02-08
Thanks for the info Vorian. Do you have any idea when the new linux-image will be released?

---

### Post by Vorian on 2007-02-08
> **dr_d said:**
> Thanks for the info Vorian. Do you have any idea when the new linux-image will be released?
When it gets fixed. :)

so sit back and have some popcorn :popcorn:

---

### Post by spamzilla on 2007-02-08
I have just turned on my laptop, and got a message saying I need to update ' linux-image-386' and 'linux-restricted-modules-2.6.15-28-386.' Ok fine. I ran 

```
sudo aptitude dist-upgrade
```

in terminal and I got the following output:

> 
matt@matt:~$ sudo aptitude dist-upgrade
The following packages are BROKEN:
  linux-image-386 linux-restricted-modules-2.6.15-28-386
The following packages will be upgraded:
  linux-restricted-modules-386
2 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8186kB of archives. After unpacking 22.1MB will be used.
The following packages have unmet dependencies:
  linux-image-386: Depends: linux-image-2.6.15-28-386 which is a virtual package.
  linux-restricted-modules-2.6.15-28-386: Depends: linux-image-2.6.15-28-386 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-image-386 [2.6.15.25 (now)]
linux-restricted-modules-2.6.15-28-386 [Not Installed]

Downgrade the following packages:
linux-restricted-modules-386 [2.6.15.25 (now) -> 2.6.15.22 (dapper)]

Score is -81

Accept this solution? [Y/n/q/?]


This is where I get confused. What should I do? Do I downgrade 'linux-restricted-modules-386' or keep the packages current version?

Any help is greatly appreciated :)

Cheers

---

### Post by PartisanEntity on 2007-02-08
> **Vorian said:**
> When it gets fixed. :)

so sit back and have some popcorn :popcorn:

Thanks for the info so far Vorian, I too have a question, the only update that was carried out on my Dapper installation today was linux-386 from 2.6.15.**25** to 2.6.12.**26**.

If I restart, will the system be functional even though this is the only part of the update that was carried out or should I rollback this update until all packages can be installed?

Thanks :)

---

### Post by MrHorus on 2007-02-08
> **spamzilla said:**
> 

This is where I get confused. What should I do? Do I downgrade 'linux-restricted-modules-386' or keep the packages current version?

Any help is greatly appreciated :)

Cheers

It *looks* like you have a more recent version of a package that is a dependancy for what you are installing and since that depends on the previous version, this is asking you to regress to the older version so that you can install whatever it is you are trying to install/upgrade.

You are probably in that lag period between things benig compatable with the newest version so I would say you should be okay just to downgrade to get this installed.

---

### Post by dr_d on 2007-02-08
Is it just me, or does that sound suspiciously like something 3D Realms would say about Duke Nukem Forever  ;)

---

### Post by jnj on 2007-02-08
I had the same partial update and on reboot the system is locked up -- proceed with high caution!

---

### Post by ComplexNumber on 2007-02-08
there seems to be some dependency problems with the new update, apparently. i'm waiting for some assurance that nothing is going to break before i update. one of the dependencies hasn't been updated yet. 

my advice is to hold off for a bit.

---

### Post by Aberrix on 2007-02-08
So I logged into my server today, did a 'sudo apt-get update' then a 'sudo apt-get upgrade' and it looks like there is an update so I accept it but I get this message now;

```
aberrix@norad:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

whats happening? why is it not upgrading that package? thanks in advance.

---

### Post by PartisanEntity on 2007-02-08
Since it updated linux-386 from 2.6.15.25 to 2.6.15.26 I have been trying to find a way to rollback this update to the previous version to prevent a lock-up in case I need to restart. The only thing I found was a 'force version' feature in Synaptic > Packages. But it only allows me to choose between 2.6.15.22 and 2.6.15.26.

Anyone have any other ideas?

---

### Post by Medieval_Creations on 2007-02-08
If it's been held back it's usually for a reason *(not sure why though)*.

You could always try```
sudo apt-get dist-upgrade
```

---

### Post by Aberrix on 2007-02-08
> **Medieval_Creations said:**
> If it's been held back it's usually for a reason *(not sure why though)*.

You could always try```
sudo apt-get dist-upgrade
```

```
aberrix@norad:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by neymac on 2007-02-08
Same problem to update linux-headers-generic and linux -image-generic from version 2.6.17.10 to 2.6.17.11.
It refuses to update, but my system is working normal with beryl and nvidia legacy driver without XGL.

---

### Post by bellaLI! on 2007-02-08
same here
on a client install, 3 kernel-related packages are not upgraded 

(need to reboot to ubuntu to check exact packages name)

---

### Post by K.Mandla on 2007-02-08
Hold off on your updates for a little bit. It seems there's a broken dependency in a kernel package, and it could be the reason for the messages you're seeing. It will take a little time to iron out.

There's more about it [here]("http://ubuntuforums.org/showthread.php?t=356235"); there's also an announcement at the top of the ABT forum.

---

### Post by navneeth on 2007-02-08
Thank you!

---

### Post by Ambimom on 2007-02-08
Whew!  I thought I was the only one with this problem.  At least I'm not alone :lolflag: 

I'm not doing anything.  It's probably going to be resolved since so many of us are experiencing this.

---

### Post by CheeseQueen452 on 2007-02-08
Glad to know I'm not the only one to experience this issue! Sorry to hear about the system lock-ups... I even removed the 3 packages, rebooted, & no problems. Gutsy move, I know.... I also shut down & still no problems after booting up. Guess I'm one of the lucky ones.... Maybe it's because I didn't install any video card drivers, as some have indicated in this thread? At least everything is working for me.... If it ain't broke, don't fix it ;)

---

### Post by wog on 2007-02-08
I tried Update Manager. It tells me three packages are held back and were not installed. 

I tried Synaptic, with mark all upgrades. It marks them, but will not allow me to apply them.
They are:
linux-image-386
linux-image-k7
linux-restricted-modules-k7

I tried ```
sudo apt-get dist-upgrade
``` as instructed by Update Manager. It gives the list of those three packages and tells me they have been "kept back".

I went back into Synaptic again, figuring I'd mess with linux-image-386, since I'm theoretically using k7. If I need to uninstall linux-image-386 in order to install the upgraded version, I can do that, and then switch to using that image while I upgrade the other two.

Synaptic removes linux-image-386 and then when I mark it for re-installation, it tells me this:
"Depends: linux-image-2.6.15-28-386 but it is not installable"

Okay, I don't know what to do next. What do I do?

---

### Post by Edho on 2007-02-08
Same here.

Rebooted, all normal i think.

Running Update-manager , it's sayng again it can 't be done.

Waiting for instructions from exp. people.:confused:

---

### Post by Johan! on 2007-02-08
> **K.Mandla said:**
> Hold off on your updates for a little bit. It seems there's a broken dependency in a kernel package, and it could be the reason for the messages you're seeing. It will take a little time to iron out.

There's more about it [here]("http://ubuntuforums.org/showthread.php?t=356235"); there's also an announcement at the top of the ABT forum.
Your link doesn't work.
The links in the announcements don't work either:confused:

---

### Post by Trebaruna on 2007-02-08
Wow, just got back to see if there was an answer and all hell seems to have broken loose! teehee.

For the moment I would recommend uninstalling the dummy packages, at least then Synaptic will calm down and not worry about not finding the kernel update. Of course, remember to reinstall them when all is well again...

Also, things going awry with updates seems to happen more often with Ubuntu, don't they? Or is it just me? Last minute hiccup here, or a problem with quality control..?

---

### Post by Efwis on 2007-02-08
I just recently had to reinstall Ubuntu on my comp, not because of the update issue but because of my own mistakes, needless to say, the Kernel version that installs with default 6.06 install, doesn't allow my optical mouse to work, so after I updated the system as usual, the last stable kernel that worked, won't install because the system wants these packages. 

With the number of people switching into ubuntu, I think it would be a good idea if that package was removed from the repos until the bugs are ironed out. otherwise this will screw up new ubuntu users and prevent them from using this distro.

Luckily I was able to get into synaptic and install the latest stable kernel, but someone completely new to Linux may not know which one to grab. or even how to get it.

---

### Post by candtalan on 2007-02-08
I seem to be getting someting very similar - refusal to update linux image 386 and linux restricted modules 386

---

### Post by dodongo on 2007-02-08
> **K.Mandla said:**
> Hold off on your updates for a little bit. It seems there's a broken dependency in a kernel package, and it could be the reason for the messages you're seeing. It will take a little time to iron out.

There's more about it [here]("http://ubuntuforums.org/showthread.php?t=356235"); there's also an announcement at the top of the ABT forum.

Confirming this (hey, it's like we're on Launchpad!)

Specifically, I have a problem with a kernel package [NAME]-2.6.17-11 which doesn't exist.  The package is [NAME]-2.6.17.11

Whoops  :oops:

---

### Post by loserboy on 2007-02-08
yay, i'm glad i checked before I tried the update....

i mean sorry for you guys  :)

---

### Post by houstonbofh on 2007-02-08
After the last few issues, I never update the kernel on the release day...  Sad that I expect it now.

---

### Post by jnj on 2007-02-08
For those like me whose system was locked up, I am back up after doing the following:

-  Restart the machine with the on/off button;

- when the logon screen comes up click on the icon "Options" in the lower left corner of the screen;

- click on the Select Session item;

- click on Failsafe Terminal;

- at the terminal prompt type in "sudo aptitude dist-upgrade"

- I selected the Y option to reload some, hold back or replace other modules;

- I selected the Y option again to proceed; it took a while to download +26M of files and run them.

- When the process finsihed - type "exit" at the prompt.

- You will have to restart your computer to complete the process.

Everything seems to work but not sure if more will need to be down when the update patch is corrected.

Good luck

---

### Post by PartisanEntity on 2007-02-08
> **jnj said:**
> For those like me whose system was locked up, I am back up after doing the following:

-  Restart the machine with the on/off button;

- when the logon screen comes up click on the icon "Options" in the lower left corner of the screen;

- click on the Select Session item;

- click on Failsafe Terminal;

- at the terminal prompt type in "sudo aptitude dist-upgrade"

- I selected the Y option to reload some, hold back or replace other modules;

- I selected the Y option again to proceed; it took a while to download +26M of files and run them.

- When the process finsihed - type "exit" at the prompt.

- You will have to restart your computer to complete the process.

Everything seems to work but not sure if more will need to be down when the update patch is corrected.

Good luck

Would this apply to my dapper installation? I don't want to upgrade to Edgy, hence I am wondering about the dist-upgrade command.

---

### Post by reiki on 2007-02-08
heheh... I toasted my Edgy install this morning before work when this happened. I removed the nVidia drivers thinking that was the problem because I got switched from the generic to the 386 one (no SMP!) and ran out of time 'cause I had to leave for work.

Now I'm at work reading this. Fortunately I have an untouched Dapper install so I can just boot to that while this gets straightened out. I will just ignore the update notification until it's fixed. :)

Either that or I'll have to rsync my World of Warcraft install over to my OTHER drive with Feisty and play it there... *sigh*... trials and tribulations.

This is, however, a good reason for me to keep a stable release on the machine and NOT upgrade everything immediately all the time. :)

---

### Post by jnj on 2007-02-08
Yes - I am running Dapper too.

---

### Post by PartisanEntity on 2007-02-08
> **jnj said:**
> Yes - I am running Dapper too.

I don't think that is going to work for me, wifi is my only access to the internet, I don't have Ethernet in this room, and I am assuming that wifi is not logged on at this point (it usually requires me to enter a password in order to connect to my wifi network).

---

### Post by maraz on 2007-02-08
I'm trying to install Edgy off minimal-cd (on usb disk) as I'm writing this. Base system installation proceeds to the point where I can choose a kernel. I've already tried a few (386 and 686/smp kernels), but with no luck. I guess the dependency problem is consistent within the different kernels?

Is there any way I can get this system up and running other than wait for the packages to be fixed?

---

### Post by Buck2348 on 2007-02-08
> **PartisanEntity said:**
> Would this apply to my dapper installation? I don't want to upgrade to Edgy, hence I am wondering about the dist-upgrade command.From a non-expert:  I don't think the dist-upgrade command will try to upgrade your system to a newer release unless you have changed your sources.list to the new release.  It will try to "intelligently" handle dependency problems.

Buck

---

### Post by hometoast on 2007-02-08
I have some packages that can't be installed, but keep showing as an "update available". They are not selectable from Synaptic, so I tried them from the command line.

What has happened?

```
hometoast@blargbuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
hometoast@blargbuntu:~$ sudo apt-get install linux-headers-generic linux-image-386 linux-restricted-modules-386
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.17-11-generic but it is not installable
  linux-image-386: Depends: linux-image-2.6.17-11-386 but it is not installable
  linux-restricted-modules-386: Depends: linux-restricted-modules-2.6.17-11-386 but it is not going to be installed
E: Broken packages
hometoast@blargbuntu:~$

```

---

### Post by cookfromfrozen on 2007-02-08
> **houstonbofh said:**
> After the last few issues, I never update the kernel on the release day...  Sad that I expect it now.
Me too.  I never install updates as soon as I see the orange icon unless they fix serious remotely exploitable holes or something of that nature.  I wait a very long time before I install an update that could (and often does) break the system, such as a kernel update, X server update etc...

---

### Post by frogotronic on 2007-02-08
Yep, me too on Dapper Drake.

Here's my original post:

[http://ubuntuforums.org/showthread.php?p=2124616#post2124616]("http://ubuntuforums.org/showthread.php?p=2124616#post2124616")

 maybe this can be merged with this (current & ongoing) thread


     :guitar:

---

### Post by jnj on 2007-02-08
> **Buck2348 said:**
> From a non-expert:  I don't think the dist-upgrade command will try to upgrade your system to a newer release unless you have changed your sources.list to the new release.  It will try to "intelligently" handle dependency problems.

Buck
Also a non-expert, but agree with Buck.  The dist-upgrade did not change my Dapper system to Edgy and was smart enough to pull in the correct files and replace or hold back the "bad" files.

I have not had any experience with wifi on Ubuntu so can not comment on that.

Good luck

---

### Post by bapoumba on 2007-02-08
> **Buck2348 said:**
> 
From a non-expert: I don't think the dist-upgrade command will try to upgrade your system to a newer release unless you have changed your sources.list to the new release. It will try to "intelligently" handle dependency problems.

> **jnj said:**
> Also a non-expert, but agree with Buck.  The dist-upgrade did not change my Dapper system to Edgy and was smart enough to pull in the correct files and replace or hold back the "bad" files.

That is correct. dist-upgrade won't upgrade to a newer release unless sources.list is changed accordingly. 
 > **man apt-get]dist-upgrade
              dist-upgrade  in addition to performing the function of upgrade,
              also intelligently handles changing dependencies with  new  ver&#8208 said:**
> 

[QUOTE=man aptitude] dist-upgrade
              Upgrades installed packages to their most recent version, remov&#8208;
              ing  or  installing  packages as necessary. This command is less
              conservative than upgrade and thus more likely  to  perform  un&#8208;
              wanted  actions. Users are advised to either use upgrade instead
              or to carefully inspect the list of packages to be installed and
              removed.


---

### Post by Floppyjoe on 2007-02-08
I updated one of my systems(Ubuntu Edgy 6.10) with two of the five available updates and this has no ill effect on that system. I can reboot and do everything as before. Does this mean it will work the same for my other computers(Edgy 6.10) or should I wait till these supposed problems are sorted out?

---

### Post by asnd16 on 2007-02-08
The only issue I have after this mornings updates, seeing that I didnt discover this thread till after the fact. . . but here are some screen shots of my current issue, I eneded up following the first error by going into the terminal and doing the apt-get thing . . then refreshed the updates and got sevreal I allowed them to install, but I got two that are just light grey faded that I cant check/install. . See screen shot. [IMG]http://asnd16.com/shiz/screenshots/updaterepositoriesB.png[/IMG]
[IMG]http://asnd16.com/shiz/screenshots/updateissueA.png[/IMG]

---

### Post by scrooge_74 on 2007-02-08
What Ubuntu version are you running and what repositories are you using?

---

### Post by Paerez on 2007-02-08
same as me i am on edgy.

No need to worry, these are virtual packages. They will probably sort this out soon. No need to panic.

---

### Post by wog on 2007-02-08
no change.

I have Dapper.

I rebooted.
I went to Options on the login and chose Fail Safe terminal.
I logged in.
I got a terminal window in the lower right corner.
I typed in ```
sudo aptitude dist-upgrade
```
I pressed Y twice.
I typed "exit".
I restarted.

When I went back into Synaptic to see that it had the new version numbers, it was still telling me there was an dist-upgrade that it couldn't install. I still can't reinstall linux-image-386.

---

### Post by bapoumba on 2007-02-08
Hello,
see :
[http://ubuntuforums.org/showthread.php?t=356408]("http://ubuntuforums.org/showthread.php?t=356408")
and just wait it gets fixed ;)

---

### Post by FuturePilot on 2007-02-08
I'm getting the same message too.
```
nick@LinuxBox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
Isn't the Linux-image-386 a kernel update?
Why is this happening. I'm running Dapper by the way.

---

### Post by bapoumba on 2007-02-08
Just check the thread I've linked, there is a dependency issue. You should wait it gets fixed.

---

### Post by CarpKing on 2007-02-08
I also seem to be having this problem (no Nvidia drivers involved).  When I open the update manager, all the linux-386 and linux-k7 packages are checked, and the linux-generic packages are shown but can't be checked.  The linux-k7 packages all say "obsoleted by linux-generic."  I don't plan on trying to install any of it until this seems to be sorted out.

---

### Post by FuturePilot on 2007-02-08
Thanks for that link. I though it was only my computer. I guess I'll just wait for them to fix it.:popcorn:

---

### Post by smithman89 on 2007-02-08
So yea, same story as others, I get home, see the update icon, then see the error before updating.  I guess im just going to wait it out, im hoping it will be fixed in a few days.  Also, its a lucky thing that i did see this post before updating :D

---

### Post by phansiizwe on 2007-02-08
Can't things like this be tested in some "virtual" environment, it seems that the problem is pretty generic and not bound to some special setup...

---

### Post by Linuturk on 2007-02-08
FYI

Dapper Drake 6.06 Server has similar messages.

---

### Post by klato on 2007-02-08
Weird...I woke up this morning (got myself a gun...) and flipped on my laptop...saw the update sitting there in the tray...and something told me to hold off on it.

---

### Post by P235 on 2007-02-08
Hi, is there a page with information meant to be presented to newbs and Linux beginners to make sense of all this information?  Something to explain what these upgrades are meant for and the various methods that can be taken in the event of a failure?

---

### Post by Vorian on 2007-02-08
> **smithman89 said:**
> So yea, same story as others, I get home, see the update icon, then see the error before updating.  I guess im just going to wait it out, im hoping it will be fixed in a few days.  Also, its a lucky thing that i did see this post before updating :D

That is the best course of action....

and have some popcorn:popcorn:

---

### Post by EnterDaMatrix on 2007-02-08
Same problem here. Coincidentally I just got a new graphics card, so it the error for me is when I try and install nvidia-glx. I used to have an ATI card. Also synaptic seems to recognize the problem and doesn't ask for a kernel upgrade, although when installing nvidia-glx it always fails. Lame. I gotta author a dvd for school and I'm not gonna be able to without this fixed.

---

### Post by eapache on 2007-02-08
I was actually in the middle of reading this thread when the updater popped up, so I haven't updated yet. What I have been able to pull out of this massively long thread is the following:

- there was a new linux kernel released today (2.6.16.11)
- there is a problem with the updater, in that the metadata for this kernel is available, but not the file itself
- updating the available files may or may not break something
- the best course of action is to sit tight, don't update, and wait for them to fix it.

Just one question: Does anyone know how long it will take them to fix it?

---

### Post by Kateikyoushi on 2007-02-08
> **klato said:**
> Weird...I woke up this morning (got myself a gun...) and flipped on my laptop...saw the update sitting there in the tray...and something told me to hold off on it.

I did the same just right before sleep.

I held back updates after the last time it broke me few packages, yesterday the number of available updates reached 70 so said well lets do it, then again seems I am cursed or something with these updates. :(

---

### Post by Nda on 2007-02-08
Six hours ago I was working on two machines at once (my own with 6.06, k7 kernel, my partner's with 6.06, i386 kernel) when the automatic updates came through simultaneously.  In a hurry, I downloaded the updates then, even more carelessly, performed the apt-get dist-upgrade on both of them with similar results to previous posters.  They both carried on working ok though, and I've just checked again that they will work.

While none of us can complain too loudly because we haven't paid for the OS, it is very disappointing to see these difficulties not long after the problems with X.  There is obviously a need for a far more rigorous testing regime to be put in place before updates to such major components are released.  I'm fortunate in that I have more than one machine to work on, but someone who has only one machine that doesn't dual-boot with another OS is at serious risk in these circumstances.  It isn't very confidence inspiring to look at the automatic update indicator and have to think: 'Should I or shouldn't I?'

I am writing this from my laptop (6.06, i386 kernel) and, strangely, it hasn't invited me to perform an update yet...  Have they been switched off at source?

---

### Post by blueglow on 2007-02-08
I have tend to agree with Nda. I have been very impressed with Ubuntu over the last month of usage to the extent it has replaced XP for all work and day-to-day usage. For that I'm thankful and for that reason I also am careful with my (hopefully constructive) criticism:

This faulty update pertains to the the *kernel* after all; this is a potentially - actually for some unfortunate people - a system-disabling mistake that can leave many users without deep knowledge of packages and kernels  without a usable system.

I just reloaded the package sources and the faulty items are still there. 12+ hours later I and probably thousands of others still have the potential to break their systems with a few clicks. If Microsoft did this (as I believe they accidentally have on a few occasions a some years back), they would rightly be ridiculed and derided.

In the spirit of Ubuntu, I think this mistake can be turned into a strength by ensuring the communication between forums, support staff, package managers and ultimately the update utility is improved to allow update releases to be safer and pulled back quickly.

---

### Post by yangeryanger on 2007-02-08
:) Did the same, was actually reading on how to install beryl and it recommended a dist-upgrade ... aptitude dist-upgrade worked, but this occured ;|

bummer.

anyways, is there a way to just "roll back" to 2.6.16-10? like ignore 2.6.16-11?

Either way.. will just wait and feed myself with :popcorn: :)

D

---

### Post by aidanr on 2007-02-08
same

updated:
linux-generic

not installable:
linux-headers-386
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic

rebooted after updating linux-generic, haven't had any problems yet

---

### Post by marko_4454 on 2007-02-08
well probably this doesnt help, but I also have it with my computer. I am still hoping someone can answer this problem as soon of possible ;)

```

The following packages have unmet dependencies:
  linux-image-386: Depends: linux-image-2.6.17-11-386 but it is not installable
E: Broken packages

```

---

### Post by EnterDaMatrix on 2007-02-08
Yeah, the problem is that theres a bunch of helper packages pointed at one that doesn't exist. You'd think that they would be able to fix this quickly, but maybe they put the packages up before they had the kernel ready. See its like this:

Package linux-generic depends on linux-image-generic which depends on linux-image-2.6.17-11-generic which is the actual kernel. This string of packages is supposed to make it easier for users to keep up to date, but it only works if they actually put the kernel up too. And it sucks the most because nvidia-glx and I think other drivers look for modules in the newest restricted modules package, which can't be installed without the newest kernel. Otherwise it would be usable.

Also they have a completely different set of packages for each architecture, so theres so many points where it could (and did) break.

Lemme know if I was right. ;-)

---

### Post by punkybouy on 2007-02-08
Happend to me too just a few minutes ago,  Somebodya has some 'splainin to do.

---

### Post by punkybouy on 2007-02-08
9 times out of 10 updates run well.  I rebooted my pc and it appears to work ok but good thing this not a production machine.  I hope the powers that be see these messages and fix it.

---

### Post by ianare on 2007-02-08
it's been telling me to upgrade for the past couple days now, each time the file can't be found.

I find it completely unacceptable to come to the forum and there is a big 'look here for update problems' but THE UPDATER IS STILL TRYING TO INSTALL THE NON EXISTING PACKAGE !!

Ubuntu is a commercial project. Granted, I am not paying for my home PC, but at work we have a bunch of Mandriva/Red Hat servers and lots of XP workstations. I was about to start making a case for switching over some servers to Ubuntu  6.06 and some of our workstations to 6.10 but how can I go to my boss and say I am confident the system will work when something like this happens? We would be getting some sort of support contract, so this hurts Canonical directly.

This is a HUGE oversight.

---

### Post by j5tixc on 2007-02-08
I've upgraded everything but linux-image-386 & linux-restricted-modules-386. Is it safe to reboot or turn of the computer? :confused:

---

### Post by EnterDaMatrix on 2007-02-08
> **ianare said:**
> it's been telling me to upgrade for the past couple days now, each time the file can't be found.

I find it completely unacceptable to come to the forum and there is a big 'look here for update problems' but THE UPDATER IS STILL TRYING TO INSTALL THE NON EXISTING PACKAGE !!

Ubuntu is a commercial project. Granted, I am not paying for my home PC, but at work we have a bunch of Mandriva/Red Hat servers and lots of XP workstations. I was about to start making a case for switching over some servers to Ubuntu  6.06 and some of our workstations to 6.10 but how can I go to my boss and say I am confident the system will work when something like this happens? We would be getting some sort of support contract, so this hurts Canonical directly.

This is a HUGE oversight.

You might want to consider Debian for a server. It's like Ubuntu except that they take a couple months of furious testing before they add anything to their repos. Oh and it's faster, although in my experience was ill suited for workstation. I would never use Ubuntu in a work environment; it's clearly more suited for desktop use, LTS or otherwise. Anyway this is off topic.

---

### Post by garenasix on 2007-02-08
all i know is there prob working on it and it will be fixed in afew days if not sooner .. still all in all the support is alot better then some other operating systems

---

### Post by Tanker Bob on 2007-02-08
To help put this event into perspective, Microsoft "security" updates progressively broke my stable XP setup over the last five months.  I lost sound, Bluetooth, etc., with no recovery even after uninstalling the Windows updates.  They have no real help to offer in these circumstances.  According to their limited "forums", these problems just don't happen.  And that's a multi-billion dollar company.

Granted that the kernel-update breakage this morning was disconcerting, but it didn't break my 6.10 system in any discernable way.  The updater was smart enough to see that some packages were broken and bypassed installing them to avoid harm.  That a large group of volunteers can build and maintain a complex system like Kubuntu is amazing on its own.  If a multi-billion-dollar company like MS can make a continuous stream of broken updates that pith users systems, I think that I can cut the Ubuntu crowd some slack when things don't always go as planned.  JMHO.

---

### Post by magichsjx on 2007-02-08
have the same problem. as if after all this anyone wants to hear it. i have been holding back for sometime and i have been getting this error froa few days now, hope it goes away. smile.:popcorn: :popcorn:

---

### Post by garenasix on 2007-02-08
> **Tanker Bob said:**
> To help put this event into perspective, Microsoft "security" updates progressively broke my stable XP setup over the last five months.  I lost sound, Bluetooth, etc., with no recovery even after uninstalling the Windows updates.  They have no real help to offer in these circumstances.  According to their limited "forums", these problems just don't happen.  And that's a multi-billion dollar company.

Granted that the kernel-update breakage this morning was disconcerting, but it didn't break my 6.10 system in any discernable way.  The updater was smart enough to see that some packages were broken and bypassed installing them to avoid harm.  That a large group of volunteers can build and maintain a complex system like Kubuntu is amazing on its own.  If a multi-billion-dollar company like MS can make a continuous stream of broken updates that pith users systems, I think that I can cut the Ubuntu crowd some slack when things don't always go as planned.  JMHO.

yep i feel the same way they do an outstanding job here and there will be some bugs here and there but still all in all they do get fixed

---

### Post by eapache on 2007-02-08
Does anyone with connections to the powers that be have an idea when we can expect a fix? Correct me if I'm wrong, but it sounds like all they have to do is upload the kernel to the servers... that wouldn't generally take the half-day that this board has been functional.

---

### Post by Polygon on 2007-02-08
greyed out for me in the package manager. hope they fix it soon :D

---

### Post by jklick on 2007-02-08
I have the same problem after running Update Manager today.

---

### Post by Vorian on 2007-02-08
We will make an announcement the moment the kernel dependencies are fixed.

---

### Post by j5tixc on 2007-02-08
> **Tanker Bob said:**
> 
Granted that the kernel-update breakage this morning was disconcerting, but it didn't break my 6.10 system in any discernable way.  The updater was smart enough to see that some packages were broken and bypassed installing them to avoid harm.  That a large group of volunteers can build and maintain a complex system like Kubuntu is amazing on its own.  If a multi-billion-dollar company like MS can make a continuous stream of broken updates that pith users systems, I think that I can cut the Ubuntu crowd some slack when things don't always go as planned.  JMHO.

> **eapache said:**
> Does anyone with connections to the powers that be have an idea when we can expect a fix? Correct me if I'm wrong, but it sounds like all they have to do is upload the kernel to the servers... that wouldn't generally take the half-day that this board has been functional.

Yeah, we shouldn't be to hard on them because of one mistake. But what I think is really bad is the amount of information. There's been practically no information about this, when will it be fixed, what are the repercussions, is it safe to reboot if you're partially upgraded and so on. That's just plain bad.

---

### Post by ndefontenay on 2007-02-08
Same here.

I saw yet another update i the system tray but this time it seems to be a kernel upgrade.
but it won't some dependencies return an error and the packages are set to no change.
As it has been said before:

Don't mess up with it, wait somebody knowledgeable to fix it. :popcorn: You might have more trouble playing with links after it's finally fixed ><:confused:

---

### Post by NT4usB on 2007-02-08
So, I've only been at this Linux thing for 6 months and I broke my install a couple times by charging into a kernel upgrade.

Only took a couple (doh!) to teach me the following upgrade proceedure:
A. Have some popcorn and wait a couple days before updating.
B. Check the boards to see how others are getting on with the upgrade.
C. Refresh my old, crs crippled memory on how to recompile the special bits I have installed, when they break after the upgrade.


Of course, if everyone did this it would just take longer for any bad news to come out. 
With that in mind, a big **thank you** to all you early adopters!

---

### Post by Hobbsee on 2007-02-08
Hey guys.

We do know about it, the fix is in progress.

It's a bug in the releasing software - so it wont screw up your computers.

Please see [https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976) for status updates (ie, fix committed, and fix released)

---

### Post by marko_4454 on 2007-02-08
Thanks for the update Hobbsee, keep up the good work :)

---

### Post by FrozenFOXX on 2007-02-08
Thank you for the update.  I just switched to Kubuntu from Gentoo yesterday and was worried it'd be a bad omen.  I'm glad to hear it's not, thank you.

---

### Post by j5tixc on 2007-02-08
> **Hobbsee said:**
> Hey guys.

We do know about it, the fix is in progress.

It's a bug in the releasing software - so it wont screw up your computers.

Please see [https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976) for status updates (ie, fix committed, and fix released)

Thanks! Now I can safely go to bed. :)

---

### Post by dr_d on 2007-02-08
Thanks for the link Hobbsee... It's nice to know that this bug won't screw up our boxes. Keep up the great work :)

---

### Post by Exile29 on 2007-02-08
Good thing I didn't follow through with my first instinct and remove the generics.
I just installed a dual-core a few days ago and I thought that somehow my attempt to install the SMP version (which I now know is unnessesary) screwed up the version count somehow.

Don't ask. It's been a REALLY long week. :(

---

### Post by houstonbofh on 2007-02-08
One question...  Why not pull the broken packages?  I have been waiting 2 days now to install a new system with an Nvidia graphics card.  I understand a fix takes time, but leaving the repository broken for 2 days?

---

### Post by clickwir on 2007-02-09
> **houstonbofh said:**
> One question...  Why not pull the broken packages?  I have been waiting 2 days now to install a new system with an Nvidia graphics card.  I understand a fix takes time, but leaving the repository broken for 2 days?

Because it has nothing to do with nvidia and causes no problems?

Several people have posted that they have rebooted after the partial update and things are working fine.

I, am one of them. It breaks nothing, so why mess with it more. When it's fixed, it's fixed.

---

### Post by Hoffmann on 2007-02-09
> **Aberrix said:**
> ```
aberrix@norad:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I almost got the same:

> sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade...Done
The following packages have been kept back:
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by scrooge_74 on 2007-02-09
What would be a solution? to downgrade the image back to what people had?

From what i see is only Edgy users affected right?

---

### Post by clickwir on 2007-02-09
> **scrooge_74 said:**
> What would be a solution? to downgrade the image back to what people had?

From what i see is only Edgy users affected right?

Not to be like a broken record. But they said they would post a solution. Since it breaks nothing, that I've seen in this thread, there is no need to do anything until an update is ready.

---

### Post by Kream on 2007-02-09
Can anyone link to any launchpad bug on this?

---

### Post by marko_4454 on 2007-02-09
> **Kream said:**
> Can anyone link to any launchpad bug on this?

Is this what you mean? You just want the link of LaunchPad?

[https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976)

---

### Post by clickwir on 2007-02-09
> **Kream said:**
> Can anyone link to any launchpad bug on this?

[https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976) was posted a few pages back.

---

### Post by Kream on 2007-02-09
Thanks, marko_4454 and sorry clickwir, after about 4 pages of "me toos" I skipped ahead to the last few pages to see if the launchpad link was there. Maybe the bug number should be inserted in a)  the topic or b)  the first post.

cheers,

Aniruddha Shankar

---

### Post by brazzmonkey on 2007-02-09
wow, when i saw adept was about to update kernel, i thought "let's browse the forums beforehand...". it looks like i was right to do so...

/me thinks about my old archlinux desktop computer running kernel 2.6.19 without troubles...

---

### Post by lptr on 2007-02-09
same troubles here: held back packages
linux-headers-generic, linux-image-generic, linux-restricted-modules-common

(need/ed to install vncserver and it didn't) so: Trying to solve the conflict simply uninstalling packages and reinstalling them later (at least this was the plan). Everything seemed fine after uninstalling that ones.

Then I restarted X ctrl-alt-backspc and tried to rerun adept - it does not start anymore. Other KDEsu things I tried don't working now, too. So for others (hopefully reading this BEFORE experimenting around) DON'T DO THIS what I tried!

```
The following steps I did:
# apt-get install linux-headers-generic
...
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  linux-headers-generic: Hängt ab: linux-headers-2.6.17-11-generic ist aber nicht installierbar
E: Kaputte Pakete
```

E: Kaputte Pakete -> means damaged packages.

The last step i tried until now was this:

```
# apt-get install linux-headers-2.6.17-11-generic
...
Paket linux-headers-2.6.17-11-generic ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket linux-headers-2.6.17-11-generic hat keinen Installationskandidaten
```

E: translated means linux-headers-2.6.17-11-generic has no install canditate

To the experienced ones here on board - what steps do I have to provide to solve that conflict before a final fix will hit us? Any indepth insights are welcome.

rob*

---

### Post by MaXqUE on 2007-02-09
Hello:

I've just switched to Ubuntu from another distro. I installed about 4 days ago so I've just now caught up with all the updates and trying to customize what I want to.

I got the kernel update to the 2.6.17.10 generic kernel. It went off without a hitch. The thing that seems different in my case is that I've ignored the update manager completely and used only apt-get (actually Wajig --which is a  superset of all the debian command-line tools). I've noticed that the people using the graphical interface seem to run up against this type of problem more often than I do. That's not to say I haven't encountered them using apt-get, how ever the number of incidents seems exponentially lower.

I know that while the repositories are the same, apt and synaptic do not follow the same update stream. They end up in the same place but there is something different in the way they have chosen to do updates and proceed with things like secure apt. 

On the implementation of secure-apt, synaptic is further ahead than apt is. So last year, some people using synaptic had problems with gpg keys that people using apt had not encountered.

Perhaps something of the same thing is happening here. From another incident, I've learned (the hard way) not to upgrade the kernel just because an update is offered. Check things out first, and see for yourself what problems might occur. Usually kernel upgrades are not crucial. On rare occasions there have been security issues at steak but that is the exception rather than the rule.

Cheers,
MaXqUE

---

### Post by frodon on 2007-02-09
@MaXqUE, synaptic is just an apt-get front end so it does basically the same thing than apt-get commands alone.
Here the problem just come from this update which seems incomplete, it is really not related to synaptic or apt

---

### Post by surhudm on 2007-02-09
For me too on ubuntu edgy, I updated without seeing the forums. Three of the updates were not tickable, that should have made me suspicious. But I went ahead.

linux-headers-generic linux-image-generic linux-restricted-modules-generic

were held back. I rebooted and it was safe. Hoping that things will be fixed soon. The launchpad link should perhaps be kept on the front page because this thread has grown too big...

---

### Post by lptr on 2007-02-09
> **lptr said:**
> same troubles here: held back packages
linux-headers-generic, linux-image-generic, linux-restricted-modules-common

(need/ed to install vncserver and it didn't) so: Trying to solve the conflict simply uninstalling packages and reinstalling them later (at least this was the plan). Everything seemed fine after uninstalling that ones.

Then I restarted X ctrl-alt-backspc and tried to rerun adept - it does not start anymore. Other KDEsu things I tried don't working now, too. So for others (hopefully reading this BEFORE experimenting around) DON'T DO THIS what I tried!


Answering myself because I found a partial solution. I could revert to 2.6.17-10 using this

```
#aptitude install linux-headers-generic
#aptitude install linux-image-generic
```

linux-restricted-modules-common I could not get back using the shown method.

Synaptic working again. Same with superuser console.

With aptitude I could get vncserver installed, too. Could anyone explain me why it works with aptitude but not with apt-get?

rob*

---

### Post by Mark76 on 2007-02-09
I recently got a new hard drive and graphics card (both second hand) from a friend.  First I installed Breezy Badger from the CD I had and then updated to Dapper Drake via the Update Manager.  All was fine and dandy until I tried to tried to install the graphics card.  It didn't work.  So I asked for advice and tried again.  It didn't work again.  But this time I had to reinstall the OS from scratch. 

Anyway, I was determined not to give up with the card so I tried a few more times, and each time I had to reinstall the OS.

And now the OS doesn't work on my new HD.  I get as far as the loading screen, but the progress bar doesn't appear and then it goes in to some kind of failsafe mode which ends with me being asked for my log in and password

---

### Post by Strider42 on 2007-02-09
Hi,

I had an updater message telling me that updates were available and I proceeded to install them (linux-kernel-2.6.17-11-generic).  All went smoothly, I think, as no errors were returned.

I rebooted, but when I run uname -r from a terminal window it returns 2.6.17-10-generic.

I then checked Synaptic and 2.6.17-11 is definitely installed.  How do I get the system to boot with 2.6.17-11?

Many thanks
Paul

---

### Post by cash1981 on 2007-02-09
Hello.

I have experiences some real strange behavior from ubuntu the last few months, but today the strangest thing happened which got my alarm bells running.

I think the problem started when I tried to stream video from firefox, and I followed some tutorials and stuff. Then suddenly my package manager, the one under Applications suddenly got removed, and I cannot find it again.

Then I kept using ubuntu for a few months, because I really didnt care so much about the package manager. 
But today a software update appeared, and I tried to install it. Then I got an error saying I had broken packages which needed to get fixed first.

[B]Then I ran apt-get -f install and it removed the 
linux-386 and linux-restricted-modules-386.[/B]

The following packages will be REMOVED
 linux-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 106kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ...
dpkg: serious warning: files list file for package `mozilla-firefox-locale-en-gb' missing, assuming package has no files currently installed.
178894 files and directories currently installed.)
Removing linux-386 ...
Removing linux-restricted-modules-386 ...

**Then I tried to install the packages again and got the following message:**
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-restricted-modules-386: Depends: linux-restricted-modules-2.6.15-28-386 but it is not going to be installed
E: Broken packages 

**Then I tried to isntall linux-restricted-modules-2.6.15-28-386 and got this error message:**
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-restricted-modules-2.6.15-28-386: Depends: linux-image-2.6.15-28-386 but it is not installable
E: Broken packages

**Then I tried to install  linux-image-2.6.15-28-386 and got this error message:**
 Package linux-image-2.6.15-28-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-image-2.6.15-28-386 has no installation candidate 

**Now I am afraid to reboot the computer. What can I do?**

---

### Post by Kobalt on 2007-02-09
Haven't you seen the announcement on top of the Home page or this section ? Check out this thread for this problem : [http://www.ubuntuforums.org/announcement.php?f=73](http://www.ubuntuforums.org/announcement.php?f=73)

---

### Post by Strider42 on 2007-02-09
Totally missed it Kobalt.  Thanks for pointing that out.

Must say though, pale blue doesn't really stand out.  Maybe the admins should use red for important messages.  Just a thought.

---

### Post by tormod on 2007-02-09
> [https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976) was posted a few pages back.
Would be nice if this link was edited into the first post, or included in the notice on the Forum front page.

---

### Post by Mark76 on 2007-02-09
Is that why my last two attempts to reinstall Dapper have ended in failure (and why I'm now back on the puny 4 gig HD my computer came with)? :?

Sort it out chaps :p

---

### Post by talikarng on 2007-02-09
Hi, I have just reinstalled 6.06 from the live cd and i would like to update the kernel from the 386 version to the 686-smp version. 

Is there any way I can do update to an earlier version of the 686-smp kernel (i.e before the dependency problem)?

Thanks in advance.

---

### Post by frogotronic on 2007-02-09
I had a bad dream last night.  I bought VISTA and I couldn't get past the M$ Validation,...then I was locked out every hour.

THERE WAS NO ONE TO FIX THE ISSUE.

Then I woke up, realised it was all a nightmare and that the Ubuntu community/developers were fixing the update issue; they were was on it, and I could chill.

L8R

:popcorn:

---

### Post by bapoumba on 2007-02-09
[http://ubuntuforums.org/showthread.php?t=356408]("http://ubuntuforums.org/showthread.php?t=356408")
Hello, please check that thread, there are dependencies issues with current kernel updates. Just wait it gets fixed, the upgrade cannot go through and you should be fine for now.
What does return **uname -a** in a terminal ?

---

### Post by cash1981 on 2007-02-09
uname -a returns:

Linux cash 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

It seems that I am using 2.6.15.27 and the one which could not be installed was 2.6.15.28 so looks like I am ok?

Also /boot/grub/menu.lst looks ok.

---

### Post by Mark76 on 2007-02-09
I just reinstalled my new HD so I could see what error message came up.

And here it is

> Failed to start the X Server

X Window System version 7.0.0
Release date: November 21st 2005
X Protocol version11, Revision 0, Release 7.0
Build OS Linux 2.6.15.7, i686
Current OS Linux cpc1, etc, 2.6.12-10-386 #1 Wed February 7th 03:38:41 UTC 2007 i686
Build Date: March 16th 2006
Module Tracker: Present
Markers (--) probed, (**) from config. file, (==) default setting, (++) from Command Line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log"
(==) Using config file "/etc/x11/xorg.conf

Is it possible that I downloaded the kernal for an i686 machine? :|

---

### Post by tormod on 2007-02-09
> **Mark76 said:**
> Is it possible that I downloaded the kernal for an i686 machine? :|

> Current OS Linux cpc1, etc, 2.6.12-10-386

What is this? Are you running a kernel museum? :)
It seems like you are not installing Dapper from scratch at least. Please take your troubles to another thread or forum.

Tormod

---

### Post by bapoumba on 2007-02-09
Yes, you're ok.
In addition, check the launchpad bug report to keep informed:
[https://launchpad.net/soyuz/+bug/83976]("https://launchpad.net/soyuz/+bug/83976")

---

### Post by Mark76 on 2007-02-09
I downloaded it from the Update Manager immediately after reinstalling and updating Breezy Badger.

I think that qualifies as "from scratch" :p

---

### Post by mommebu on 2007-02-09
I got 2 questions, if s.body is able to answer:

-I did a system update, didn't receive any errorrs and don't see any unusal behaviour, can I reboot safely?

-I also considered undoing the update, so I checked the histrory in synaptic. It says:
Upgraded the following packages:
linux-amd64-generic (2.6.15.25) to 2.6.15.26
linux-restricted-modules-common (2.6.15.12-1) to 2.6.15.12-28.1
xorg-driver-fglrx (7.0.0-8.25.18+2.6.15.12-1) to 7.0.0-8.25.18+2.6.15.12-28.1

But when I try to remove linux-restricted-modules-common version 2.6.15.12-28.1, I am asked to remove also all the old versions, which clearly enough I reject, so I can't remove the update.  What is the correct way, if there is one?

Cheers.

---

### Post by hometoast on 2007-02-09
Thank you for the link, bapoumba.

---

### Post by ardchoille42 on 2007-02-09
I am on Ubuntu 6.06.1 LTS and I only use aptitude to install/update/upgrade/uninstall packages. I never compile anything and I never install .deb's outside of the package manager.

That said, please look at the attached picture. It seems that I have broken packages and unmet deps. If there are indeed broken packages and unmet deps, then the package manager broke them. Why isn't the package manager doing a better job at managing the packages? What do I do now?

See screenshot:

---

### Post by bapoumba on 2007-02-09
You're welcome.
Keep an eye on the launchpad bug report too ;)
[https://launchpad.net/soyuz/+bug/83976]("https://launchpad.net/soyuz/+bug/83976")

---

### Post by jdm2 on 2007-02-09
I just did the new updates that ubuntu had and it tells me to upgrade, so I don't what to do now.  I will attach a picture that will show what it said and when I do it in synamptic I get an erro message.  Thanks for the help.  In the help2.txt file is the error and the terminal output for the command in the picture.

I just added the output for sudo apt-get update
cmdline.txt

I'm using drapper

---

### Post by mendingo84 on 2007-02-09
adept notifier signals 3 packages as upgradeble:
[B]linux-restricted-modules-generic
linux-image-generic
linux-headers-generic[/B]
i tried adept updater and also dist-upgrade and upgrade but it didn't work. any ideas?

---

### Post by Balaam's Miracle on 2007-02-09
> **mendingo84 said:**
> adept notifier signals 3 packages as upgradeble:
[B]linux-restricted-modules-generic
linux-image-generic
linux-headers-generic[/B]
i tried adept updater and also dist-upgrade and upgrade but it didn't work. any ideas?

Please look here: [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408) . It deals with this problem in great detail.

---

### Post by DougieFresh4U on 2007-02-09
> **mendingo84 said:**
> adept notifier signals 3 packages as upgradeble:
[B]linux-restricted-modules-generic
linux-image-generic
linux-headers-generic[/B]
i tried adept updater and also dist-upgrade and upgrade but it didn't work. any ideas?

Just from curiosity, how were you trying to update? Just an idea:::** sudo apt-get update ** then  **sudo apt-get dist-upgrade**  then  **sudo apt-get -f install**  and finally ** sudo dpkg --configure -a**    And a **restart** is usually required after a kernel upgrade-good luck, Dougie:popcorn:

---

### Post by tormod on 2007-02-09
> **Mark76 said:**
> I downloaded it from the Update Manager immediately after reinstalling and updating Breezy Badger.

I think that qualifies as "from scratch" :p
Sorry, no, from scratch would be using the Dapper installation cd. You are doing an upgrade, not an installation. Why are you installing Breezy first? Why not install Edgy from scratch? Please take your troubles to another thread or forum.

---

### Post by ocdude on 2007-02-09
This doesn't seem to be affecting Fiesty Server, as far as I can tell. I'm running a version on QEMU and I am running the update right now as I'm typing this. So far, I haven't gotten any errors or missing dependencies.

My actual machine running Edgy, though, does have the issue. Glad I just bought that pack of :popcorn: I guess.

---

### Post by mendingo84 on 2007-02-09
DougieFresh4U i tried your way but it didn't work

---

### Post by finer recliner on 2007-02-09
my system tried to upgrade itself this morning with only limited success. i was given the following error message from update manager:

> Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

The following updates will be skipped: 
linux-image-386
linux-image-686
linux-restricted-modules-386
linux-restricted-modules-686



i opened synaptic and clicked "mark all upgrades" as recommended, but nothing got checked (so the "apply" button stayed grayed out)

i also tried running the recommended shell command:
```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-image-386 linux-image-686 linux-restricted-modules-386
  linux-restricted-modules-686
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
$

```


what gives?

---

### Post by bapoumba on 2007-02-09
> **tormod said:**
> Sorry, no, from scratch would be using the Dapper installation cd. You are doing an upgrade, not an installation. Why are you installing Breezy first? Why not install Edgy from scratch? Please take your troubles to another thread or forum.
@ tormod: breezy is still supported and, as far as I can tell (please someone tell me if i'm wrong) can be concerned by this kernel update dependency problem.

---

### Post by cpsalvestrini on 2007-02-09
Same issue in here, I'll just wait out until the nice developers at ubuntu.com fix the thing, the I'll update the image.

---

### Post by bapoumba on 2007-02-09
[http://ubuntuforums.org/showthread.php?t=356408]("http://ubuntuforums.org/showthread.php?t=356408")
Please check front page announcement ;)
Thread merged.

---

### Post by Balaam's Miracle on 2007-02-09
Please see [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408) where this problem is dealt with in great detail.

---

### Post by DougieFresh4U on 2007-02-09
> **mendingo84 said:**
> DougieFresh4U i tried your way but it didn't work

Sorry, just a suggestion. Any error message??

---

### Post by bapoumba on 2007-02-09
Thread merged ;)

---

### Post by ubu-for on 2007-02-09
> **jdm2 said:**
> I just did the new updates that ubuntu had and it tells me to upgrade, so I don't what to do now.  I will attach a picture that will show what it said and when I do it in synamptic I get an erro message.  Thanks for the help.  In the help2.txt file is the error and the terminal output for the command in the picture.

I'm wary about updating "linux-386", too because I'm waiting for 7.04 and don't want a dist-upgrade now.

---

### Post by shironeko on 2007-02-09
I got two packages installed:

Linux-image-2.6.17-10generic (Version: 2.6.17.1-10.34) (This is the latest version)

Linux-image-generic (Version: 2.6.17.10) 
But this one is marked for actualization to 2.6.17.11

And I can't update that last package because it tells me the following:

> 
linux-image-generic:
 Depends on: linux-image-2.6.17-11-generic  but it is not installable 

Also I wonder, why do I have two Kernel Images? 

Thanks

---

### Post by Vorian on 2007-02-09
> **ubu-for said:**
> I'm wary about updating "linux-386", too because I'm waiting for 7.04 and don't want a dist-upgrade now.

There are a few kernel tweeks between Distro Upgrades.  It's usually not a big deal.

---

### Post by OrangeCrate on 2007-02-09
^,

Being new to Ubuntu, just a procedural question... Rather than continuing to watch this thread, and the bug report, do I assume that the balance of this upgrade will come automatically as an additional system update when it's ready?

---

### Post by ola on 2007-02-09
Hi! Have you been using any repositories other than the standard Ubuntu repositories?

Can you try to install the packade linux-image-2.6.17-11-generic first?

By default the kernel you are currently running is "backed up" so you can return to that kernel if the new you are downloading, for some reason, fails. So that you are having multiple kernels is nothing strange.

---

### Post by ajm2005 on 2007-02-09
so I guess this problem can only be fixed by the powers that be at ubuntu/ canonical/ whoever maintains the repositories? it's not something that can be fixed at my end?

---

### Post by Vorian on 2007-02-09
> **OrangeCrate said:**
>  do I assume that the balance of this upgrade will come automatically as an additional system update when it's ready?
Yes :)
> **ajm2005 said:**
> so I guess this problem can only be fixed by the powers that be at ubuntu/ canonical/ whoever maintains the repositories? it's not something that can be fixed at my end?
Your guess is correct :)  just sit back, and enjoy the show.

---

### Post by OrangeCrate on 2007-02-09
^, > **Vorian said:**
> Yes :)

Thanks.

---

### Post by AAJ on 2007-02-09
Hi guys,

I can not select any update from update manager to install them.

Please have a look at attached file.

Cheers,

---

### Post by Patrick-Ruff on 2007-02-09
I think you may need more details, perhaps there could be conflicting packages that will not allow you to install those in particular?

I assume you've just ran into this problem because there's only 3 updates instead of 130.

---

### Post by TitanKing on 2007-02-09
Try :

~>sudo apt-get update

then

~>sudo apt-get upgrade

---

### Post by Vorian on 2007-02-09
It involves the big green banner announcement on the front page of the forums

see this thread

[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by Vorian on 2007-02-09
Just hold on...    :)
[]("http://ubuntuforums.org/showthread.php?t=356408")

---

### Post by grazie on 2007-02-09
I had a very similar [problem]("http://www.ubuntuforums.org/showthread.php?t=344240") a couple of weeks ago which left me without sound for a week. I reported  [Bug #81626]("https://launchpad.net/ubuntu/+bug/81626"), but fixed the problem by re-installing about a week later, however it's obvious the problem arose due to the missing kernel-image in the repos on an update. The bug was then marked fixed released without any action being taken. I HOPE THIS DOESN'T HAPPEN AGAIN.

---

### Post by stig on 2007-02-09
Could some kind person put a sticky with a warning about the problem at the top of the Beginners' Forum like was done when we had that horrific X update problem some months ago?

[Sorry.......someone just pointed out to me that it's in a coloured banner! my eyes must be failing!]

---

### Post by bimmerd00d on 2007-02-09
What would it take to get the previous version installed.  I JUST bought a new laptop and I want my fglrx :(  Would a previous version even work right?  I just need something as far as restricted modules!

---

### Post by MepisReign on 2007-02-09
The problem is not only with the kernel updates, there are also serveral packages that can not be updated. In my case Transcode, Mjpegtools, etc. I hope this problem gets resolved soon, I don't use Guindow$ anymore, at least in my case I depend on my Kubuntu box 100%

My System:
Dell Dimension 9150
Geforce 7300 LE Video Card
Pentium D 2.8 GHZ processor
1 GIG of RAM
Seagate 160 GB SATA II HDD
MAXTOR 250 GB SATA II HDD

Regards,

MepisReign

P.S.: I got installed the latest NVIDIA Drivers from their website, version 1.0-9746


[IMG]http://img.photobucket.com/albums/v297/darth1968/snapshot1.jpg[/IMG]

---

### Post by clickwir on 2007-02-09
> **MepisReign said:**
> The problem is not only with the kernel updates, there are also serveral packages that can not be updated. In my case Transcode, Mjpegtools, etc. I hope this problem gets resolved soon, I don't use Guindow$ anymore, at least in my case I depend on my Kubuntu box 100%

P.S.: I got installed the latest NVIDIA Drivers from their website, version 1.0-9746
[ IMG ]http://img.photobucket.com/albums/v297/darth1968/snapshot1.jpg[/IMG]

[https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976)

Yes, there are known issues and they are working on them.

---

### Post by esaym on 2007-02-09
Today I turned my computer on and adept came up with some updates.  After I applied them I noticed that the icon the the task bar did not go away.  I opened adept up again and saw that it did not install some kernel updates:

[IMG]http://la.gg/upl/kernel1.jpg[/IMG]

I am not sure what is going on.  I know some nvidia restricted modules installed yesterday.  Today it's this.  I don't know why it says current installed version is "2.6.15.25",  All I have on my computer is 26 and 27.  If I click "request update" then is just displays "BREAK(upgrade)"

Anyone got any tips before I totally hose my system? :-D

---

### Post by lugburz on 2007-02-09
Hi,
   yesterday I received an alert by aptitude about the new kernel for ubuntu: 2.6.17.11. Unfortunately adept and aptitude are unable to find kernel image, headers and restricted-modules for generic architecture at this version. Some one know what's happened in the repositories?

Thanks in advance

---

### Post by jd65pl on 2007-02-09
see this link [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by jd65pl on 2007-02-09
See this link [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

---

### Post by Darth Trix on 2007-02-09
> **Vorian said:**
> Just hold on...    :)
[]("http://ubuntuforums.org/showthread.php?t=356408")

I hold on, but please make a post when the bug is fixed.

---

### Post by Vorian on 2007-02-09
> **Darth Trix said:**
> I hold on, but please make a post when the bug is fixed.

You got it :)

---

### Post by esaym on 2007-02-09
> **jd65pl said:**
> See this link [http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)


Oh thank you!  I guess it's not my fault after all.  

So I guess we just wait it out? :popcorn:

---

### Post by bimmerd00d on 2007-02-09
> **Vorian said:**
> You got it :)

Any chance there's a way to install the previous version of the restricted modules?  I gotta get this ATI card working soon, low res is driving me nuts, and i refuse to boot into windows!!!:lolflag:

---

### Post by freaz on 2007-02-09
i thing that best way is wait... and will see..

---

### Post by stulesnett on 2007-02-09
I have also received the same message and attempted to update using Synaptic without success.  I then attempted to use the second method (sudo-apt-get dist-update) which alos failed.

Any ideas

---

### Post by jdackle on 2007-02-09
> **bimmerd00d said:**
> Any chance there's a way to install the previous version of the restricted modules?  I gotta get this ATI card working soon, low res is driving me nuts, and i refuse to boot into windows!!!:lolflag:

I fyou can find the .deb package you want, you can install it again with "**dpkg -i**", even if "downgrading"...

So:
1. Get the .deb you want from wherever it may be.
2. ```
sudo dpkg -i <package path and name>
```

That should work, I think...

---

### Post by Tanker Bob on 2007-02-09
> **stulesnett said:**
> I have also received the same message and attempted to update using Synaptic without success.  I then attempted to use the second method (sudo-apt-get dist-update) which alos failed.

Any ideas
If you will skim through this thread, you will see that there's nothing you can do, no damage has been done to your system, and the 400 lb. brains are working on it.  They will post here when the dependencies are fixed.

I believe that there was also mention of popcorn... :popcorn:

---

### Post by houstonbofh on 2007-02-09
Now what do I do...

I have a client who just called and they had a computer stolen.  I have been talking them into trying Ubuntu, and now they are willing.  I need to deliver a system **Today** or they will get one at Fry's.  They want a real graphics card.  How can I install it with broken repositories?

Any way to make a Upgrade CD from my apt cache on a known good system?

---

### Post by mikerduffy on 2007-02-09
> **Tanker Bob said:**
> Same problem here with Kubuntu 6.10.  Adept updated three packages, but three are set to "no change": linux-headers-generic, linux-image-generic, and linux-restricted-modules-generic.  When I try to change them from "no change" to "update", only one can be changed and it changes to "BREAK (update)" in red font.  To me, that says leave it alone, but Adept Updater remains in the system tray saying there are 3 updates.  What's the deal and what should I do?

Same here. I was disabling 3rd party repos today to try and fix it.  There's just something about seeing BREAK in red letters on you screen...

---

### Post by kaminix on 2007-02-09
This break is really bad actually. I'm certain it's because of it I can't even install the system. See, I always use the alternate install and install xubuntu, kubuntu or ubuntu-desktop via aptitude. But it won't install anything, just keep on being stupid about score stuff.

sudo aptitude install kubuntu-desktop gives me something about leaving package statuses unchanged, and well, one of the packages is the kubuntu-desktop. So I can't install kubuntu. I'm stuck in bash. Yey.

I'm kind of dissappointed...

---

### Post by mimithebrain on 2007-02-09
Is this an issue that will be fixed automatically by apt-get update eventually, or is there something I need to do about it?

Thanks

---

### Post by K.Mandla on 2007-02-09
Hopefully, when the problem is resolved, a new package will be released and you'll be able to update to it. Glitches like this occasionally happen, but not generally with kernel packages. 

Try to be patient and a solution should be forthcoming. 

In the mean time, enjoy the popcorn smilie!

:popcorn:

---

### Post by Tanker Bob on 2007-02-09
> **kaminix said:**
> This break is really bad actually. I'm certain it's because of it I can't even install the system. See, I always use the alternate install and install xubuntu, kubuntu or ubuntu-desktop via aptitude. But it won't install anything, just keep on being stupid about score stuff.

sudo aptitude install kubuntu-desktop gives me something about leaving package statuses unchanged, and well, one of the packages is the kubuntu-desktop. So I can't install kubuntu. I'm stuck in bash. Yey.

I'm kind of dissappointed...

I had a similar problem in that after the update failure.  The Kubuntu package manager only listed my installed packages.  I told it to refresh the package list several times, but again it only loaded the installed list.

So, I went to the terminal and executed "sudo aptitude update", and the system reread the entire package list again.  It was much slower than normal, but it worked.  Now I have access to the usual new suspects.  YMMV.

---

### Post by G Morgan on 2007-02-09
I just disabled security updates temporarily and then everything works after an apt-get update. If anyone does this don't forget to re-enable them when this starts working again.

---

### Post by kakalaky on 2007-02-09
update appears to be working now.

---

### Post by Migs on 2007-02-09
I can also confirm that the broken packages are fixed. Happy updating!

---

### Post by kakalaky on 2007-02-09
Rebooted into new kernel, no problems.

---

### Post by houstonbofh on 2007-02-09
Was just waiting for posts from the brave. :)  Thanks!  Now I can make a sale.

---

### Post by brainsik on 2007-02-09
> **kakalaky said:**
> update appears to be working now.

Working here now for amd64 -server images. Currently running for i386 -server images. Looks like the dependencies are available now.

---

### Post by Indigo7 on 2007-02-09
I'm a new convert... 2 days old... how do you check what kernel version you're currently running?

---

### Post by jamesford on 2007-02-09
indigo7: uname -r in terminal

update smooth here too now, 64 bit/nvidia

---

### Post by Indigo7 on 2007-02-09
> **jamesford said:**
> indigo7: uname -r in terminal

update smooth here too now, 64 bit/nvidia

Sweet, Thanks!

---

### Post by eapache on 2007-02-09
All the packages are enabled now, so the bug appears to be fixed, but I'm still waiting for an OK from the powers that be before installing...

---

### Post by Daedalus on 2007-02-09
> **houstonbofh said:**
> Now what do I do...

I have a client who just called and they had a computer stolen.  I have been talking them into trying Ubuntu, and now they are willing.  I need to deliver a system **Today** or they will get one at Fry's.  They want a real graphics card.  How can I install it with broken repositories?

Any way to make a Upgrade CD from my apt cache on a known good system?

Yes, there is.

Try

[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)
[https://wiki.ubuntu.com/APTonCD](https://wiki.ubuntu.com/APTonCD)

Good luck!

---

### Post by lcohen999 on 2007-02-09
Hello All

In-direct question via the kernel update.

I did the update via update manager, and I guess because my nvidia drivers are compiled, it won't bott into gnome.  I rebooted and am using .10 so I can work.  When I did a sudo apt-get update nvidia-glx it tells me I am already on the latest version.

How can I get myself up and running again?

---

### Post by Migs on 2007-02-09
> **lcohen999 said:**
> Hello All

In-direct question via the kernel update.

I did the update via update manager, and I guess because my nvidia drivers are compiled, it won't bott into gnome.  I rebooted and am using .10 so I can work.  When I did a sudo apt-get update nvidia-glx it tells me I am already on the latest version.

How can I get myself up and running again?

I have exactly the same problem. I've the problem, please read this: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Upon_upgrading_the_kernel_at_a_later_time](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Upon_upgrading_the_kernel_at_a_later_time)

And now i can confirm that you have to re-install your nvidia drivers and it will work again!

---

### Post by lcohen999 on 2007-02-09
agreed

that was what I was about to post.  Get the latest drivers from nvidia and everything is good again

---

### Post by Vorian on 2007-02-09
*unofficial update*
**************
EDIT
**************
you can update, however:
Update at your own risk at this point

---

### Post by smithman89 on 2007-02-09
All i had to do is mess with the dependencies because it wouldnt finish checking my sources, then it is all fine, i no longer get the error message, and i am in the process of updating.  Thx guys!:popcorn: :popcorn: :popcorn:

---

### Post by Ambimom on 2007-02-09
I just tried again...still getting the error message when I try to update.

---

### Post by Vorian on 2007-02-09
you can either apt-get update or click the "check" button on your update manager.

---

### Post by brazzmonkey on 2007-02-09
i got the update installed, but X doesn't run with kernel 2.6.17-11. i've got an nvidia video card, works ok with kernel 2.6.17-10. any hints ?

---

### Post by soham on 2007-02-09
my grub is messed up

---

### Post by s6dalane on 2007-02-09
I, too, am having problems with NViDIA drivers after update. I tried reinstallation, but it didn't help.

---

### Post by ntt on 2007-02-09
Same here (Kubuntu 6.10, nVIDIA card); after updating to 2.6.17-11 the nvidia "closed" driver doesnt load any more.

Tried to load the nividia module by hand, but got a FATAL error complaining about something broken in the nvidia installer. go figure...

Anyway replacing "nvidia" with "nv" in the /etc/X11/xorg.con works, meaning that X starts (but of course without nvidia full 3D acceleration).

I've resorted to continue using the previous kernel (2.6.17-10), which still works fine with nvidia closed driver and luckily was still available in the initial grub menu.

Hope someone will come up with a fix for that.

---

### Post by StarsAndBars14 on 2007-02-09
(EDIT: never mind, I might just have been very stupid.)

---

### Post by PartisanEntity on 2007-02-09
Same issue here with the nvidia drivers, x-server wont load with the nvidia drivers, only with the nv drivers. Why is this happening? (Or how do we resolve this issue)

---

### Post by coreymon77 on 2007-02-09
so wait, is the bug fixed now? is it now safe to upgrade? has the dependency problem been fixed? can we upgrade to -11 now?

---

### Post by phenest on 2007-02-09
What bug? They simply put out the upgrade BEFORE the actual kernal install. Hardly a bug. Just be patient.

---

### Post by lcohen999 on 2007-02-09
with the nvidia issue.

This worked for me, perfectly

boot into your -11 kernel, get to a prompt


```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

make sure you have an internet connection, it will try and grab a binary, and if not, automatically build you an update.

That worked for me, and only took me 5 mins

---

### Post by Buddha443556 on 2007-02-09
Just finished rebooting after the upgrade and had no problems. However, I don't have any fancy drivers like nVidia - so it went smooth and I'm done. ;)

---

### Post by Vorian on 2007-02-09
> **Buddha443556 said:**
> Just finished rebooting after the upgrade and had no problems. However, I don't have any fancy drivers like nVidia - so it went smooth and I'm done. ;)

Thats good news :)

---

### Post by PartisanEntity on 2007-02-09
> **lcohen999 said:**
> with the nvidia bug.

This worked for me, perfectly

boot into your -11 kernel, get to a prompt


```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
su NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

make sure you have an internet connection, it will try and grab a binary, and if not, automatically build you an update.

That worked for me, and only took me 5 mins

Hello,

What do you mean with -11 kernel? 
Thanks

---

### Post by lcohen999 on 2007-02-09
grub gives you the option to boot your old kernel, but you can ignore that step and just let your system boot and get the X11 error.

Then goto alt-F1 login and follow..

---

### Post by Howlin' Hobbit on 2007-02-09
I got the same problem packages (and error messages) as PartisanEntity. I'm still new at this whole Linux thing so I'm wondering if the upgrades will automagically come through again when the repository problem is fixed or should I save the info on the missing packages and try it manually (when I hear the repo thing is fixed)?

Thanks!

---

### Post by phenest on 2007-02-09
> **PartisanEntity said:**
> Hello,

What do you mean with -11 kernel? 
Thanks

The same one everyone is talking about here: 2.6.17-11

---

### Post by StarsAndBars14 on 2007-02-09
> **lcohen999 said:**
> with the nvidia bug.

This worked for me, perfectly

boot into your -11 kernel, get to a prompt


```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

make sure you have an internet connection, it will try and grab a binary, and if not, automatically build you an update.

That worked for me, and only took me 5 mins

Yeah I thought so. :D

I'll try that now.

---

### Post by phenest on 2007-02-09
> **lcohen999 said:**
> with the nvidia bug.

This worked for me, perfectly

boot into your -11 kernel, get to a prompt


```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

make sure you have an internet connection, it will try and grab a binary, and if not, automatically build you an update.

That worked for me, and only took me 5 mins

It's hardly a bug. In the same way it wasn't a broken dependency.

---

### Post by lcohen999 on 2007-02-09
> **phenest said:**
> It's hardly a bug. In the same way it wasn't a broken dependency.

I stand corrected :)

---

### Post by PartisanEntity on 2007-02-09
I get this:

```
sudo: ./NVIDIA-Linux-x86-1.0-9746-pkg1.run: command not found
```

(I have dapper btw, this 'fix' apply to me?)

---

### Post by lcohen999 on 2007-02-09
sorry, you need to sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run first

editing my original post..

---

### Post by phenest on 2007-02-09
> **lcohen999 said:**
> sorry, you need to sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run first

editing my original post..

That's for permission. He said that the command wasn't found.

---

### Post by PartisanEntity on 2007-02-09
--

---

### Post by neymac on 2007-02-09
Now it worked fine.

:~$ uname -a
Linux (xxxx)  2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

To instal nvidia legacy driver I used the "envy" script from AlbertoMilone.
At [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by red_Marvin on 2007-02-09
> **PartisanEntity said:**
> I get this:

```
sudo: ./NVIDIA-Linux-x86-1.0-9746-pkg1.run: command not found
```

(I have dapper btw, this 'fix' apply to me?)

^ This worked for me after I had *chmod +x* -ed it

---

### Post by lcohen999 on 2007-02-09
> **phenest said:**
> That's for permission. He said that the command wasn't found.

permission and executable.

It does not get downloaded with the correct permissions, ubuntu doesn't see it as an executable file, 777 is the lazy I don't remember the more secure changing permissions on the file command :)

---

### Post by Paul41 on 2007-02-09
I am still not able to get the updates. Any ideas?

---

### Post by daff_ on 2007-02-09
In case your /boot directory is on its own partition don't forget to mount that partition before installing (or reinstalling) linux-image-generic. 

Initially I forgot that, so I had to mount /boot and reinstall linux-image-generic, linux-restricted-modules-generic and linux-restricted-modules-common.

After that everything worked again (nvidia and madwifi modules).

---

### Post by PartisanEntity on 2007-02-09
> **lcohen999 said:**
> permission and executable.

It does not get downloaded with the correct permissions, ubuntu doesn't see it as an executable file, 777 is the lazy I don't remember the more secure changing permissions on the file command :)

I don't know what I am doing wrong, I followed your instructions and then when I typed:

```
sudo: ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

But this time I got an error message saying that x-server is running?

p.s. can anyone point me to the official way of reinstalling the nvidia drivers after a kernel  update?

---

### Post by dpmccoy on 2007-02-09
> **lcohen999 said:**
> with the nvidia issue.

This worked for me, perfectly

boot into your -11 kernel, get to a prompt


```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

make sure you have an internet connection, it will try and grab a binary, and if not, automatically build you an update.

That worked for me, and only took me 5 mins

This worked like a charm for me too.  My wireless connection wasn't available via the CLI when I booted into the new kernel (because I use knetworkmanager w/WPA2 encryption), so I downloaded it in .10-generic before I rebooted.  
Thanks so much for the tip!

---

### Post by executor on 2007-02-09
working :)


ATI pcie200m
i had to fix /etc/X11/xorg.conf  to get opengl back

set driver to fglrx.

---

### Post by lcohen999 on 2007-02-09
> **PartisanEntity said:**
> I don't know what I am doing wrong, I followed your instructions and then when I typed:

```
sudo: ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

But this time I got an error message saying that x-server is running?

p.s. can anyone point me to the official way of reinstalling the nvidia drivers after a kernel  update?

check all your alt-Fx screens for any x11 screens or errors (even if they are character based)

---

### Post by PartisanEntity on 2007-02-09
Sorry I have to ask again, what is alt-Fx screens? Im a complete newb :)

---

### Post by PartisanEntity on 2007-02-09
The error I get:
[IMG]http://i13.tinypic.com/2qvyx01.png[/IMG]

And the error log file /var/log/nvidia-installer.log

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Feb  9 23:43:55 2007

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '4647'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
```

I did have nvidia 9746 installed prior to the kernal update.

---

### Post by OrangeCrate on 2007-02-09
All done...

1. Open Update Manager.

2. Click "Check" to update the repositories.

3. The two updates missing were downloaded and installed as part of a package of 10.

:)

---

### Post by lcohen999 on 2007-02-09
> **PartisanEntity said:**
> Sorry I have to ask again, what is alt-Fx screens? Im a complete newb :)

hold down the alt key and go through your function keys, linux has multiple sessions via function keys, like multiple desktops

---

### Post by PartisanEntity on 2007-02-09
> **lcohen999 said:**
> hold down the alt key and go through your function keys, linux has multiple sessions via function keys, like multiple desktops

Okay did that, held down ALT key and went through F1 to F12. F1 made the Applications menu drop down. ALT F2 called up 'Run Application'. All other ALT-Fx combinations did nothing (or i did not notice anything happening).

---

### Post by Paul41 on 2007-02-09
> **Paul41 said:**
> I am still not able to get the updates. Any ideas?

I was able to get them now. I noticed that the server was timing out so there must have been too much of a load on it at the time.

---

### Post by lcohen999 on 2007-02-09
> **PartisanEntity said:**
> Okay did that, held down ALT key and went through F1 to F12. F1 made the Applications menu drop down. ALT F2 called up 'Run Application'. All other ALT-Fx combinations did nothing (or i did not notice anything happening).

I honestly have no idea

I would reboot and start over (im driving and can't look right now)

---

### Post by RandomJoe on 2007-02-09
> **PartisanEntity said:**
> Okay did that, held down ALT key and went through F1 to F12. F1 made the Applications menu drop down. ALT F2 called up 'Run Application'. All other ALT-Fx combinations did nothing (or i did not notice anything happening).
You are in X (since you are running that in a Gnome term).  You can't compile the nVidia drivers with X running.

Since X is running, I assume you booted to an older kernel that works?  If so, I'm pretty sure you will need to boot into the broken/non-working kernel.  When you get a command prompt, run the compile from there.  The nVidia compiler works against the currently-running kernel.  (At least, last time I compiled it...)

Edit:
It occurs to me perhaps you edited your xorg.conf to use the 'nv' driver so perhaps you are running the new kernel.  In that case, boot to the 'safe mode' selection and run the compiler there, then make sure xorg points to the 'nvidia' driver when it's done.  That should bring you back up when you reboot to the normal selection.

---

### Post by Paulus on 2007-02-09
press **control and alt** and the f numbers.

so go control alt F1 all together

Log in with your username and pass.

type sudo killall gdm

sudo **sh** sh Desktop/NVIDIA-Linux-x86-1.0-9746-pkg1.run (theres no need for the chmod command, just use sh)

and follow steps.

then sudo gdm

:)

---

### Post by PartisanEntity on 2007-02-09
> **RandomJoe said:**
> You are in X (since you are running that in a Gnome term).  You can't compile the nVidia drivers with X running.

Since X is running, I assume you booted to an older kernel that works?  If so, I'm pretty sure you will need to boot into the broken/non-working kernel.  When you get a command prompt, run the compile from there.  The nVidia compiler works against the currently-running kernel.  (At least, last time I compiled it...)

Edit:
It occurs to me perhaps you edited your xorg.conf to use the 'nv' driver so perhaps you are running the new kernel.  In that case, boot to the 'safe mode' selection and run the compiler there, then make sure xorg points to the 'nvidia' driver when it's done.  That should bring you back up when you reboot to the normal selection.

Yes you are right, I was not logging out of X.

I understand how it works now, I was able to go through the nvidia installer outside of X. BUt it was missing files in order to compile the driver, here is the message I got:
[IMG]http://i13.tinypic.com/4idc1lz.jpg[/IMG]

So what do files do I need to install in order to proceed with the recompiling? (I am using linux-386)

Thank you

---

### Post by Paulus on 2007-02-09
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

---

### Post by dr_d on 2007-02-09
Sweet it's fixed!!

Well they're still working on it, but for all us non-developers it's fixed :)

> Ok, demoted to High priority, since we have *cowboyed* the required uploads into security.
Nonetheless, we have to fix the code before this issues shows up again (100 % sure it will happen again in the next kernel security upload, so we need to be fast)

---

### Post by maestrobwh1 on 2007-02-09
I updated also: I booted Edgy and my network card said "no air" and there was no sign of my adapter and no network access.

I use a Proxim (believe prism II) PCMCIA card with Netgear MA 301/401 PCI adapter (oddly, the combo of the 401/301 card and adapter never worked, even under windows, but each item works fine seperately... and the Proxim RangeLAN works... must have the same chip set.  

The kernel 2.6.17-11-generic disables it and the item does not show up in hardware in any network settings.

Fortunately, the upgrade saved the reference to kernel 2.6.17-10-generic in my grub menu.lst and everything works fine there and obviously I am able to post.

I am sure there is some goobly gook I could do to make the kernel 2.6.17-11-generic work with my Proxim card (maybe) from a shell, but there seems to be no gain in the new version so I was happy to comment out the start item using the new kernel in my grub menu.lst

Is this a bug or an omission of "obsolete" hardware.  I recognize that 11 MBps cards are old, but since net speeds have not exceeded that speed yet for the most part, I would hope there will be continued support for them.

---

### Post by ilantz on 2007-02-09
just (barely) survived this ...
i do hope this won't happen in next updates :) , just hate to start that nvidia installer each time hehe

ubuntu rox!

---

### Post by PartisanEntity on 2007-02-09
Well I got much further this time. It compiled the nvidia driver and installed it. But it also gave me a message about having to guess the X library path and the X module path mentioning also that should X fail to find the NVIDIA X driver I should install 'pkg-config' and X.Org SDK/development package and try the installation again, but it continued and finally told me that the driver had been install properly. 

I then rebooted, but again I got an error message that X server may not be set up correctly.

Any other tips or advice?

---

### Post by wpshooter on 2007-02-09
Can someone explain to me what this is all about ?

I got the same message that is shown in one of the posts on the first page of this thread and I followed the instructions that it gave me to run sudo apt-get dist-upgrade from the terminal and afterwards I rebooted my machines and to my knowledge I have NO problems at all.  Am I missing something ?

Thanks.

---

### Post by slimdog360 on 2007-02-09
I just upgraded to a new kernel via the update manager (different to the broken dependency problem, I got that the other day). And yet again for the 45th time it has broken my X. I think it has to do with my beta Nvidia drivers but am unsure at this time. If I were you Id put up a new warning telling everyone not to upgrade just yet.

The reason I haven't fixed it yet is that I set my grub to have 0 seconds delay so I cant boot into safe mode, also after I get the Xserver screen of death, it sends me to a nothing screen, I dont even a terminal. So Im arranging my plan of attack now with a live cd.

edit: Arghh, I cant mount the hard disk or rewrite the grub for some reason. Bugger it, Im going to download gentoo right now and install that. This is the 3rd or 4th time this has happened because of a kernel upgrade. The Ubuntu devs should test it on more then two machines.

Anyway if I was able to get to edit something it would have been the xorg.conf file and change the "nvidia" part ïn the screen section back to "nv". I think that should fix it. Thats just if someone wanted a  quick fix.

---

### Post by lyndb on 2007-02-09
Some files have been omitted from the repos.  It would appear that this is in the process of being fixed.   Not working for me yet, in any case.   Update Manager is still "holding back" on  linux-image-386 and linux-restricted-modules-386.

---

### Post by floke on 2007-02-09
Yay! Linux on the desktop, where official updates screw up your system....

For god's sake, why does this happen? When Linux has such a golden opportunity we shouldn't be mucking it up like this? I don;t know how the system 'works' (which it clearly doesn't), but it's gonna have to be miles better than this if bug #1 is EVER gonna get fixed!!!

---

### Post by marko_4454 on 2007-02-09
> **Steve.K said:**
> Yay! Linux on the desktop, where official updates screw up your system....

For god's sake, why does this happen? When Linux has such a golden opportunity we shouldn't be mucking it up like this? I don;t know how the system 'works' (which it clearly doesn't), but it's gonna have to be miles better than this if bug #1 is EVER gonna get fixed!!!

I dont think there is a good reason to be this mad, I mean they made a mistake wow...everyone does. Also, do you think that Windows do not make mistakes?? Think about it, when you have a Service Pack that is something like 100MB, not all of it is for "upgrade" they have MANY many fixes. So Just like windows and any other OS, developers will screw up at some point or another. If this is a "basic" bug for you, well, it may be...but if they (devs) made this mistake imagine if you or I were to do it.

Also, think about the price:
Windows: 300 + soul
Linux: free ;)
IMHO

---

### Post by p0g0 on 2007-02-09
Yesterday I couldn´t upgrade to the latest headers; today I could do it with out any problems after rebooting \\:D/

---

### Post by jamlc on 2007-02-09
> **PartisanEntity said:**
> Well I got much further this time. It compiled the nvidia driver and installed it. But it also gave me a message about having to guess the X library path and the X module path mentioning also that should X fail to find the NVIDIA X driver I should install 'pkg-config' and X.Org SDK/development package and try the installation again, but it continued and finally told me that the driver had been install properly. 

I then rebooted, but again I got an error message that X server may not be set up correctly.

Any other tips or advice?

This same thing happened to me. Did anyone find solution for this?

---

### Post by jharris on 2007-02-09
I just wanted to give a **very big thanks** for the all the tips on restoring the NVIDIA drivers, they saved my bacon. Thanks again!

---

### Post by PartisanEntity on 2007-02-09
I can't believe how much trouble I am having after this update, I just can't seem to get the nvidia driver to work *again*. Why on earth did I bother with this update? :(

I really appreciate all the help I have received so far, it is highly appreciated. Hopefully some of you will still have the patience and time to give me any more advice or help. If I can't get the drivers to work then I am just going to reinstall the whole damn OS.

---

### Post by m.musashi on 2007-02-09
Thinking maybe this was working I went ahead and upgraded (live dangerously I say). I didn't have any problem with the upgrade. Everything installed but now I can't boot. It booted once and x crashed. I kind of expected that with the nvidia driver not yet being updated. I planned to just reinstall from a command prompt. However, after x crashed I never got a command prompt. I rebooted and now it just hangs about 3/4 through the boot. I tried the recovery mode and that gives me a prompt but I can't type anything. As soon as I try I get an error about the keyboard. I can boot the old -10 kernel so it's not like I'm SOL. Anyone know what I might need to try to get at least a command prompt with -11 though?

Thanks.

---

### Post by jamlc on 2007-02-09
> **PartisanEntity said:**
> I can't believe how much trouble I am having after this update, I just can't seem to get the nvidia driver to work *again*. Why on earth did I bother with this update? :(

I really appreciate all the help I have received so far, it is highly appreciated. Hopefully some of you will still have the patience and time to give me any more advice or help. If I can't get the drivers to work then I am just going to reinstall the whole damn OS.

Do your drivers work if you just boot with the old kernel? I have the choice in grub and it does work just like it used to.

---

### Post by fergus on 2007-02-09
Just re-synced my source lists and it appears they have it fixed.. any one else dare to try it first? =)

fergus

---

### Post by frogotronic on 2007-02-09
everythings is all OKAY with the new kernel...


Thanks UBUNTU!

---

### Post by PartisanEntity on 2007-02-09
> **jamlc said:**
> Do your drivers work if you just boot with the old kernel? I have the choice in grub and it does work just like it used to.

It *did*, but while messing around trying to get them work in the new kernel I did something wrong and now only the 'nv' drivers will work with the old kernel.

---

### Post by P235 on 2007-02-09
Hi, newbie question again, when one changes the kernel, typically, will one have to wait for other programs to update from the old kernel to the new one?

---

### Post by Polygon on 2007-02-09
> **Steve.K said:**
> Yay! Linux on the desktop, where official updates screw up your system....

For god's sake, why does this happen? When Linux has such a golden opportunity we shouldn't be mucking it up like this? I don;t know how the system 'works' (which it clearly doesn't), but it's gonna have to be miles better than this if bug #1 is EVER gonna get fixed!!!

for a good portion of the people, they couldent just download the updates. It just appeared greyed out in the update manager. For other people, synaptic was smart enough to realize there was a problem and didnt apply the updates. And also, for the people who did manage to get the updates i dont think it screwed up anyones computer

and p235, the kernel is just what communicates with your hardware and stuff, programs dont rely on any specific version of the kernel

---

### Post by lyndb on 2007-02-09
> **marko_4454 said:**
> I dont think there is a good reason to be this mad, I mean they made a mistake wow...everyone does. Also, do you think that Windows do not make mistakes?? Think about it, when you have a Service Pack that is something like 100MB, not all of it is for "upgrade" they have MANY many fixes. So Just like windows and any other OS, developers will screw up at some point or another. If this is a "basic" bug for you, well, it may be...but if they (devs) made this mistake imagine if you or I were to do it.

Also, think about the price:
Windows: 300 + soul
Linux: free ;)
IMHO
I think this is an important perspective.   Behind these complex systems are folks who are just trying to make it work.  It's hard for them to be perfect, even collectively.

And, it's now working for me!  Bravo, Ubuntu People! :)

---

### Post by Cariboo1938 on 2007-02-09
> **fergus said:**
> Just re-synced my source lists and it appears they have it fixed.. any one else dare to try it first? =)
fergus
How does this work----"Just re-synced my source lists"----?????

---

### Post by Tanker Bob on 2007-02-09
> **Cariboo1938 said:**
> How does this work----"Just re-synced my source lists"----?????
At the terminal command prompt, type "sudo aptitude update" without the quotes.

---

### Post by pvossen on 2007-02-09
Just downloaded newest kernel during upgrade and Grub
would not boot up computer whatsoever. I even tried recovery
mode, and nothing worked. I am now reinstalling using older 
kernel.


Patrick

[COLOR="Red"]Using Edgy[/COLOR]

---

### Post by alphanerd on 2007-02-09
I had same issues.  I read the error msg and it said something about nvidia driver.  So I edited xorg.conf and change the device section driver from "nvidia" to "nv".   This is just a temp fix but it will get you into your gui

---

### Post by nexx on 2007-02-09
I installed 2.6.17-11 linux-headers and now I hhave this message from grub when I boot:

Error 18 : Selected cylinder exceeds maximum supported by BIOS.

I am still able to boot on the -10 linux kernel.

---

### Post by Tanker Bob on 2007-02-09
I just finished upgrading edgy to 2.6.17-11-generic using the Adept updater.  I first ran sudo aptitude update to ensure the update list was current.  A number of other related packages were added to the update list from this morning.  No problems with the kernel update process tonight.  Reboot was smooth as well.  I have an NVidia card running driver version 1.0-8776 and didn't encounter any difficulties at all, although I was prepared based on earlier reports.  Great fix, Ubuntu team!

---

### Post by MepisReign on 2007-02-09
For the ones that are having problems with the NVIDIA drivers installed from the NVIDIA's website before the kernel update.

- Power on the system
- You will get a text login screen
- Login as you were on the graphic (GUI) screen
- Make sure that X is completely dead by typing: sudo /etc/X11/kdm stop (if you are running Kubuntu, if the screen gets frozen just press CTRL + F1) or
sudo /etc/X11/gdm stop (for Ubuntu users)
- Go to the file where you have the NVIDIA driver (the place where u downloaded it the first time so you can install it) and type:  sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run --uninstall
Then:
- Type (if you are running on a 32 bits system and remember, one line at a time):
wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run) 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run

If you are running on a 64 bits system replace the 32 bits binary for the 64 bits one

I hope this helps

Greetings from Panama, Central America

MepisReign

---

### Post by blueglow on 2007-02-09
I'm pretty disappointed, after installing all the update (5 in total) and rebooting I now have the MESA graphics driver instead of the Fglrx fast one. Other stuff seems ok.

It's an ATI x600 mobility and it was running the 8.28 driver from the repository (rather than the ATI site).

If anyone has any idea how to get Fglrx back that would be much appreciated. MESA sucks badly.

Update: Here's what appears to be the offending part of /var/log/Xorg.0.log
> (II) fglrx(0): UMM area:     0xd0acb000 (size=0x07515000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by Tanker Bob on 2007-02-09
> **nexx said:**
> I installed 2.6.17-11 linux-headers and now I hhave this message from grub when I boot:

Error 18 : Selected cylinder exceeds maximum supported by BIOS.

I am still able to boot on the -10 linux kernel.

That message is usually caused by an older BIOS trying to boot a very large hard drive.  Grub is a simple program that doesn't intervene to compensate for the shortcomings of an older BIOS.  The fix is to put the boot portion of the OS on a small partition.  I had this problem with an old BIOS and a 320GB hard drive, so I created a 20GB partition for the Kubuntu system which works great.  10GB would probably have worked just fine.  

It just seems odd that the older kernel didn't encounter the same problem, as my understanding is that the issue is with the BIOS and Grub, not the kernel.

---

### Post by m.musashi on 2007-02-09
> **m.musashi said:**
> Thinking maybe this was working I went ahead and upgraded (live dangerously I say). I didn't have any problem with the upgrade. Everything installed but now I can't boot. It booted once and x crashed. I kind of expected that with the nvidia driver not yet being updated. I planned to just reinstall from a command prompt. However, after x crashed I never got a command prompt. I rebooted and now it just hangs about 3/4 through the boot. I tried the recovery mode and that gives me a prompt but I can't type anything. As soon as I try I get an error about the keyboard. I can boot the old -10 kernel so it's not like I'm SOL. Anyone know what I might need to try to get at least a command prompt with -11 though?

Thanks.

After a few tries I managed to get the -11 kernel to boot in recovery mode. If you have been using the nvidia driver make sure you have it downloaded somewhere. Boot safe and just follow the instructions for option 2 from the beryl how to on installing the driver
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
```
You won't need to do the gdm stop part as you will be at a command prompt anyway. The installed gives an error about running at init 1 but I just ignored it. It worked fine for me.

---

### Post by nexx on 2007-02-09
My computer is one 1½ years old, the BIOS is probably recent, if I uninstall the linux...-11, do you think that could help ?

---

### Post by xoai on 2007-02-09
I just updated the new kernel 2.6.7.11 but thank god, I am using kernel 2.6.19.1. I just installed it 1 week ago on my Macbook and now still have never boot with 2.6.7.11 so I dont see anything wrong.

---

### Post by lojic on 2007-02-09
SUMMARY: 2.6.17-10 --> 2.6.17-11 broke my wifi :(

I have an IBM Thinkpad A31 with an Actiontec Prism 2.5 Wavelan wifi. After booting with 2.6.17-11 my wireless adapter was not recognized. Fortunately, I noticed someone posting info about the 2.6.17-10 kernel being retained so I was able to choose that in Grub and it's working again - a life saver!

Any ideas of how to get my wifi back so I don't have to keep booting with 2.6.17-10 ? It seems that most of this thread is pertaining to the update dependency issue and people are saying it's fixed now, but there are apparently other problems with the update.

sudo apt-get update
sudo apt-get upgrade

shows nothing to install.

Thanks!

---

### Post by Cariboo1938 on 2007-02-09
> **Tanker Bob said:**
> At the terminal command prompt, type "sudo aptitude update" without the quotes.Thanks Tanker Bob, I got it! Question: What is your opinion --- can you recommend to do the latest update?

---

### Post by TwistesdTexan on 2007-02-09
I saw the problems with the update yesterday. I waited until today and updated. I will have the weekend to sort things out. I updated and it said that there was a syntex error in my xorg. I went to the grub (I accessed by pressing my Esc key repeatedly when the message was suppose to come up, Grub didn't pause) and sellected a previous Kernel. My boot went fine then. I rebooted and again grub didn't pause but I let the default Kernel load and everything went fine.
Question: Since I choose a different kernel once and acheived a good boot, did my next boot with out a selection use the older Kernel or the new problem child (i've notice a few gliches ie.. Title bars washed out no color even on buttons Max Min Close).

---

### Post by leeyee on 2007-02-09
So here the question is: Does the problem fixed?

I've just seen the update notification and also noted this issue post. I'm not sure if the problem has been fixed and should we start upgrade it as normal?

---

### Post by darclaird on 2007-02-09
I saw the update come up about an hour ago, update-manager broke,  and apt-get install -f removed my kernel but failed to install the new one, figuring this was I problem I checked this thread and as I was waiting update-manager info9rmed me the new kernel was ready for downloading, which after a reboot works fine, apart from my objection to the fact I cent seem to downlaod a k7 specific kernel, the fact everything still works (including, to my amazment the nvidia drivers) I would like to say, thansk to the forum users for their timely and sagely advice

---

### Post by clickwir on 2007-02-09
If you have any troubles with the Nvidia or ATI drivers, I'd give this script a try. Even if you are having some trouble starting X and suspect maybe theres a possibility that it could be driver related. I'd try this script.

Info: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

It will automatically download the latest version, compile it with everything it needs and do the config for you. I've run it on several systems and has been the easiest way to install a driver I have ever done.

---

### Post by MepisReign on 2007-02-09
> **clickwir said:**
> If you have any troubles with the Nvidia or ATI drivers, I'd give this script a try. Even if you are having some trouble starting X and suspect maybe theres a possibility that it could be driver related. I'd try this script.

Info: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

It will automatically download the latest version, compile it with everything it needs and do the config for you. I've run it on several systems and has been the easiest way to install a driver I have ever done.

That is completely right, just remember that my previous post is for the users that have installed the NVIDIA drivers from their website's binary :)

Greetz

MepisReign

---

### Post by clickwir on 2007-02-09
> **MepisReign said:**
> That is completely right, just remember that my previous post is for the users that have installed the NVIDIA drivers from their website's binary :)

Greetz

MepisReign

I had done that and failed. Had a half installed driver that I had downloaded from the website and tried to install. It didn't work. I ran envy and it corrected everything and reboot was flawless.

In fact I just upgraded via apt-get to the 2.6.17-11 and it failed to start X.
However before I chose to reboot I installed the deb file for envy, didn't run it, just installed it.
Then when the reboot failed, I simply logged in via console and ran envy. It got the latest driver, set it up and then I rebooted perfectly.

I think this script will be included in future releases.

---

### Post by vanshark on 2007-02-09
> **lojic said:**
> SUMMARY: 2.6.17-10 --> 2.6.17-11 broke my wifi :(

I have an IBM Thinkpad A31 with an Actiontec Prism 2.5 Wavelan wifi. After booting with 2.6.17-11 my wireless adapter was not recognized. Fortunately, I noticed someone posting info about the 2.6.17-10 kernel being retained so I was able to choose that in Grub and it's working again - a life saver!

Any ideas of how to get my wifi back so I don't have to keep booting with 2.6.17-10 ? It seems that most of this thread is pertaining to the update dependency issue and people are saying it's fixed now, but there are apparently other problems with the update.

sudo apt-get update
sudo apt-get upgrade

shows nothing to install.

Thanks!

I'm having the same issue with a ThinkPad R40 and same wireless chipset. No wireless after upgrading to 2.6.17-11. Hopefully this is fixed soon but in the meantime I've removed 2.6.17-11 and back using 2.6.17-10.

---

### Post by Vorian on 2007-02-09
> **Vorian said:**
> *unofficial update*
**************
EDIT
**************
You can update, However:
Update at your own risk at this point

just a reminder, and for those who missed it.

---

### Post by Arup on 2007-02-09
Had to start the update manager upon booting into Ubuntu 6.10 this morning, updates were not shown autimatically, the whole kernel update went smoothly, rebooted, X won't start, recompiled the nvidia drivers with Alberto's excellent ENVY, system booted into X and everything runs fine and smooth now, good work team Ubuntu.

---

### Post by Tanker Bob on 2007-02-09
> **Cariboo1938 said:**
> Thanks Tanker Bob, I got it! Question: What is your opinion --- can you recommend to do the latest update?

Well, it worked OK for me, even with the proprietary driver for my NVidia card.  I started with the command that I suggested to you to ensure that the package list was current.  After that, the normal update process worked fine.  The only issue was that I had to rerun the configuration script for VMWorkstation due to the kernel change, which in turn recompiles some support files.  Everything worked fine after that.

Each system is different, though, and some others had significant issues.  However, if all you do is run the updater, then you can always boot into the -10 kernel if things don't work out in -11.  If you are using a proprietary ATI or NVidia video driver, you should probably read the posts here on how to recover if it doesn't work upon rebooting after the update.

---

### Post by Linuturk on 2007-02-10
FYI, the updates fixed my Edgy laptop in my sig.

---

### Post by SuperD2000 on 2007-02-10
That last update did a number on my Wireless adapter.  Everything was working fine.  I got the updates and now my wireless is gone.

I have a Dell E1505, with the dell wireless card.

---

### Post by roberts3000 on 2007-02-10
> **clickwir said:**
> If you have any troubles with the Nvidia or ATI drivers, I'd give this script a try. Even if you are having some trouble starting X and suspect maybe theres a possibility that it could be driver related. I'd try this script.

Info: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

It will automatically download the latest version, compile it with everything it needs and do the config for you. I've run it on several systems and has been the easiest way to install a driver I have ever done.




Worked for me.

---

### Post by dgifford on 2007-02-10
Ok, I am on 6.06LTS  got the warnings and did NOT update.

read the thread.  went from 2 pending (the ones in question to 6)  did the reboot.

now have 10 updates with no warnings.

my system is an asus 3000n (stock) 

am I ok to do the update or what

confused....

THanks!

---

### Post by nrdlnd on 2007-02-10
Hello!
This latest update crashes the X11 server on my system! I cannot restart and have to choose another kernel! What to do?

:confused:

---

### Post by JohnnyVW on 2007-02-10
I just had a strange one...

I moved my Ubuntu from one hard drive to another, bigger one last weekend.  When I did the update tonight, it wouldn't boot.

What happened was the Grub menu reverted to my old hard drive's UUID.  I finally figured it out when I was trying to boot in recovery mode.  It just sat, waiting for root file system.  

I grabbed my Live-CD, did a sudo blkid to get my UUID's, mounted my Ubuntu disk (HDD1) and took a look-see at /boot/grub/menu.lst

Sure enough, the menu was pointing to the old hard disk's UUID.  I changed it to the new one and it works fine.  

So...  is there a way to keep this from happening again?  Where is that info stored and why did it revert back to my old disk's UUID?

---

### Post by Edho on 2007-02-10
Now the update seems working.

Rebooted, all ok now, i think.
"Your system is up to date"

Question :

How can i check wich version of kernel i am running?

Thanks.

---

### Post by mw888 on 2007-02-10
> **Edho said:**
> How can i check wich version of kernel i am running?

uname -a

---

### Post by Repent on 2007-02-10
I went back to kernel 10 but now I get the message,

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

should I ?

---

### Post by Eigenwert on 2007-02-10
My X Server was also broken by this update. The error message I got was
```

(EE) Failed to load module "wfb"

```
which caused the nvidia module to fail to load as well. As per a previous reply, I downloaded, installed and ran the Envy script and that took care of the X server. Unfortunately it broke my wireless. :mad: 

Just what I need a week before exams. ](*,) 

EW

---

### Post by Cable on 2007-02-10
I just updated to the latest kernel.  I had not updated when the problems were present, as I saw posts about it before making my decision to wait.  I noticed tonight that the problems seemed to be fixed, so I went ahead and updated.  All is well and no problems for me.

---

### Post by floke on 2007-02-10
> **marko_4454 said:**
> I dont think there is a good reason to be this mad, I mean they made a mistake wow...everyone does. Also, do you think that Windows do not make mistakes?? Think about it, when you have a Service Pack that is something like 100MB, not all of it is for "upgrade" they have MANY many fixes. So Just like windows and any other OS, developers will screw up at some point or another. If this is a "basic" bug for you, well, it may be...but if they (devs) made this mistake imagine if you or I were to do it.

Also, think about the price:
Windows: 300 + soul
Linux: free ;)
IMHO

Well I've had no issues with it (that I know of) but get mad when I see things like this which severely affect other people. Do we not (rightly) tear MS to pieces for this type of thing. Imagine if there had been a quick update for Vista and it caused these problems, we would love the PR. Now imagine if someone has just set Ubuntu up for the first time (I've just handed out some discs to some friends and family so could see this happening quite easily) and they encountered this borky update. Do you think they would be able to fix it, or that they would ever try Ubuntu again? What great PR for Linux this is.

Of course it's a mistake, and of course mistakes happen. I'm not necessarily trying to blame anyone for it, but it just pains me to see this happen - I've seen it happen before so it's not like this is the first time. Mistakes are fine as long as we learn from them, no? 

So, don't get me wrong: I love Ubuntu, and think the devs and everyone involved do a spectacular job (e.g. the way in which this problem is starting to be fixed for one) for which I am extremely grateful. At the same time though, there are standards. Just because an OS is free doesn't excuse it, it just reinforces the view that free software is rubbish. If Ubuntu is to make 'serious' inroads into the desktop then this type of amateurish cock-up simply cannot be allowed to recur. 

As I say, I'm not blaming anyone really, but consider this a passionate call for better systems checks on the update side of things.

I really hope anyone with any problems gets them fixed quickly, and that anyone who can help in any way will do so, as I'm sure they will.

Sorry for taking up so much space, but as you can tell, I do feel rather strongly about this sort of thing.

---

### Post by CarpKing on 2007-02-10
Held off until now, just updated and rebooted and everything seems to be in order.

---

### Post by bapoumba on 2007-02-10
From USN mailing list :
```
<snip>
A security issue affects the following Ubuntu releases:
Ubuntu 5.10
Ubuntu 6.06 LTS
Ubuntu 6.10

<snip> I skipped all the packages details to make it shorter
New packages version :
Ubuntu 5.10: 2.6.12-10.45
Ubuntu 6.06 LTS: 2.6.15-28.51
Ubuntu 6.10: 2.6.17.1-11.35

<snip>
After a standard system upgrade you need to reboot your computer to
effect the necessary changes.

**[COLOR="Red"]ATTENTION:[/COLOR]** Due to an unavoidable ABI change the **[COLOR="Red"]Ubuntu 6.06[/COLOR]** and [B][COLOR="Red"]Ubuntu
6.10 kernel[/COLOR][/B] updates have been given a new version number, [B][COLOR="Red"]which
requires you to recompile and reinstall all third party kernel modules
you might have installed. [/COLOR][/B]If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

<snip>
```

---

### Post by Tine on 2007-02-10
After updating to new kernel X-failed 
First i tried this:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

Installer complained something about pkg-config and didn't start. Then i tried this **envy** program and it **worked perfectly**:
i uninstalled the previous thing before using envy using this command
```
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run --uninstall
```

So if you are experiencing that pkg-config error, i suggest trying envy.

> **clickwir said:**
> If you have any troubles with the Nvidia or ATI drivers, I'd give this script a try. Even if you are having some trouble starting X and suspect maybe theres a possibility that it could be driver related. I'd try this script.

Info: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

It will automatically download the latest version, compile it with everything it needs and do the config for you. I've run it on several systems and has been the easiest way to install a driver I have ever done.

Thank you all, hope next time is easier

-Tine

---

### Post by David Valentine on 2007-02-10
I just updated with no difficulties as well--no broken X, no other messing around (I installed envy just in case), and beryl still works on my nvidia.  

All that said, I agree with the earlier poster that the difficulties some have been having will make Linux a tougher sell to those who might otherwise be receptive.  Perhaps a tiered release is in order, first to those Linux veterans who don't mind a broken X, then to the rest of us Windows refugees.

---

### Post by ozPATT on 2007-02-10
Wow, so I am at the end of 33 pages, but still not sure how I fix my problem :( 

After the updates, the only problem I seem to have at the moment is my wifi... as other people have mentioned, after rebooting, wifi disappears.

I am using Compaq Presario V3118AU Laptop, with broadcom wireless. Is there a solution here and I just missed it? If the solution has to do with bapoumba's post, then please can someone explain how i do this? I am still very much a newbie in the linux world. 

I also agree with Steve.K... In the Windows world, sure you get mistakes, and bugs etc, but nothing that cripples the whole windows community. I love Linux, I think it is great and has a lot of potential, but I struggle to use it sometimes, especially when an update breaks something, like this... How would someone who has never used it before, or knows even less than me, be able to rely on it? :( On top of this, when you first install it, there is so much work. I still dont have functioning mic or headphones on my laptop and I have had it since beginning of December. Ah well... hopefully I can get this wifi problem fixed. :)

Thanks

Patrick

---

### Post by floke on 2007-02-10
At the very least the dangers should be made clear. Although the above post clearly states that third party modules will need to be reloaded etc. - but the fact that this has to be posted in the middle of an ongoing thread on the Ubuntu forum shows that many many people were unaware of this for whatever reason. Not sure how you could do this through the synaptic system - maybe attach warnings to the descriptions of the packages to download?

---

### Post by ozPATT on 2007-02-10
so I do need to go through the whole pain of installing the wifi drivers again? :( i cant even remember how i did it... i just fluked it one day following a previous crash after an update

---

### Post by jamlc on 2007-02-10
Well, I have read all of what has been written on this subject but I still don't quite know what to do now. I had alberto milone's driver from his repo (9631). It of course did not work after the upgrade, I installed the nvidia package, still I can't boot into x with the new kernel, so I am just using the old kernel. This envy script installs the 9747 driver which I don't think I can use due to my geforce4 mx440 card. Any suggestions? Thanks to all those, who are trying to help

---

### Post by cb951303 on 2007-02-10
I've upgraded today and it went okay.
But I use the latest nvidia drivers from "http://nvidia.limitless.lupine.me.uk/ubuntu" repo (Version 9746). Note that these drivers are compiled for kernel 2.6.17-10 so with the latest ubuntu upgrade it won't work. Just a reminder :)

Actually you can still upgrade and wait till the nvidia repo gets an update. In the mean time just change the module name from "nvidia" to "nv"  in the /etc/X11/xorg.conf and disable compiz/beryl if you're using one...

---

### Post by Spr0k3t on 2007-02-10
I had to switch back to 2.6.17-10 due to my twinview setup.  With the -11 I couldn't use the second monitor.  Testing my lappy now.

---

### Post by brazzmonkey on 2007-02-10
or you can install the original nvidia drivers from their website. i confirm this now works for me, and that nvidia issue is related to some (3rd party ?) repos' nvidia drivers which need to be updated to work with newest kernel.

---

### Post by PartisanEntity on 2007-02-10
Thanks to everyone who is trying to help, it is very appreciated.

So, the saga continues, here is what I get using the envy script after I select option 1 (to install the nvidia driver):

(In this warning it mentions 'pkg-config' and 'X.Org SDK/development files'. I checked in synaptic and pkg-config was already installed. I looked for X.Org development files, I think I found them, but at least 6 dependencies cannot be installed for some reason).

[IMG]http://i11.tinypic.com/2ldvslj.jpg[/IMG]

Then this error appears:

[IMG]http://i5.tinypic.com/3z9yv88.jpg[/IMG]

After envy has finished doing its thing it tries to start X server and this is what I get:

[IMG]http://i15.tinypic.com/2u8bc00.jpg[/IMG]

If I click on 'Yes' to view the output this is what it tells me:

[IMG]http://i7.tinypic.com/4gqvtqs.jpg[/IMG]

I have the feeling that ever since this kernel update X server cannot 'find' the nvidia driver? (excuse my newb way of describing this).

If someone could decipher what all these messages mean I would really really appreciate it :)

Thanks again.

---

### Post by phansiizwe on 2007-02-10
Could it be that a lot of people have problems with the Nvidia drivers while, like me, they have both the nvidia-glx package installed AND compiled the Nvidia driver from the Nvidia website?

Last time, I updated the nvidia-glx package, the system found the self-compiled Nvidia drivers without any trouble. When I read through this post, I guess this will not happen when I install the updates.

Anyways, I'll be holding back on the updates for a little while, also because I get "failed to fetch security.ubuntu.com" errors from Update-Manager, are some of the servers down?

---

### Post by Mark76 on 2007-02-10
This is the kind of thing that makes me wish Ubuntu could auto-detect new hardware and pull the appropriate drivers out of the repository, if they were available.

---

### Post by cb951303 on 2007-02-10
PartisanEntity:
It seems that you have another nvidia drivers installed on your system. First make sure that you uninstall/delete all the nvidia drivers on the repo and then retry using envy...
don't forget to "sudo nvidia-installer --uninstall" before reinstalling with envy....

---

### Post by Hallvor on 2007-02-10
Don`t have any problems. Had to download and reinstall the ATI driver, however.

---

### Post by ozPATT on 2007-02-10
> **Hallvor said:**
> Don`t have any problems. Had to download and reinstall the ATI driver, however.

haha, thanks for letting us know :D oh to be problem free :( i like the auto-detect idea by the way.. that would be cool.

---

### Post by PartisanEntity on 2007-02-10
> **cb951303 said:**
> PartisanEntity:
It seems that you have another nvidia drivers installed on your system. First make sure that you uninstall/delete all the nvidia drivers on the repo and then retry using envy...
don't forget to "sudo nvidia-installer --uninstall" before reinstalling with envy....

I think I don't have any nvidia drivers installed, I looked in the repo and the ngividia-glx was not marked. Tried envy again and still same issue.

I keep getting this error that the installer had to guess the location of the modules, could this be the problem? It might explain why X server cannot find the nvidia drivers once they have been installed. What could cause this?

I looked for pkg-config in the repos, it is installed, but the xserver-xorg-dev is not installed and one of the dependencies wont be installed for some reason:

[IMG]http://i10.tinypic.com/2r6mfeq.png[/IMG]

---

### Post by reiki on 2007-02-10
I had teh 9746 nvidia drivers from a 3rd party repo before teh updates. I got the same errors as posted above with all the pictures. A mismatch between the kernel module and the X module.

I tried a few things to fix it, but..... they weren't working. So I went into my package manager, UNselected that 3rd party repo, and then highlighted the nvidia-glx package and told Synaptic to prefer packages from ubuntu-security. I uninstalled nvidia-glx and tehn refreshed repos. Instaled nvidia-glx from ubuntu repos.

TA-DA! I have a working system again. HOWEVER.... this set me back to the 8776 driver.
In all honesty, I don't think I NEED a newer driver right now so I'm going to leave this alone. If you go OUTSIDE the official repos, you WILL have issues when they update kernel images/restricted modules.

---

### Post by jamlc on 2007-02-10
> **reiki said:**
> ... So I went into my package manager, UNselected that 3rd party repo, and then highlighted the nvidia-glx package and told Synaptic to prefer packages from ubuntu-security. I uninstalled nvidia-glx and tehn refreshed repos. Instaled nvidia-glx from ubuntu repos.....

Now this sounds very good. But how do you do this in adept? Even though I disabled the repo that had the new driver, I don't seem to be able to tell adept to downgrade the driver from the official repo. It really looks like only those who are using driver that did not come from the official ubuntu repository have a problem. Thanks

---

### Post by nrdlnd on 2007-02-10
Hi,
There is an easier fix for this. I couldn't start the X-server after the kernel upgrade. After reading this forum I thought there were some problem with the NVIDIA-drivers. I booted with the old kernel and opened Synaptic and searched for "NVIDIA". I then saw that the restricted modules for the new "11"-kernel were not installed. Installed them and restarted the computer with the new kernel - and now everything works again!

---

### Post by markofealing on 2007-02-10
[I][QUOTE=Trebaruna;2123092]I just booted my PC to Edgy, and the update icon was sitting in the tray. So, like roughly every other day, I click it to install yet another update. But not this time.

It appears from what I can see that there is a new kernel for ubuntu: 2.6.17-11 (whereas the one I have is -10). Linux-image-generic has been bumped and now depends on said new version, but the dependency cannot be satisfied because the actual image is not in the repo. 
[/I]

I'm on Kubuntu 6.10 Edgy on my laptop and had the same problem yesterday, with 3 upgradeable but uninstallable packages.

This morning I did an update and it found a few extra packages which it installed, but the remaining "orphan" packages existed. Got Adept to do another update and it found 6 additional packages not previously installed (2.6.17), in addition to the 3 "orphaned" packages. The install completed okay and everything is now correctly up to date.

Looks like somewhere someone screwed up their change management and released a few packages a bit too quickly!

I've just fired up my two desktops which run Ubuntu 6.10 Edgy, the other Kubuntu, to see if the upgrades goes through okay. Neither PCs have been updated for about 5 days. It found 6 Additional packages, 28 updates, in all it totaled 128Mb, A similar figure applied for Ubuntu plus a Wine update. The updates went through without any problems.

So all is well again! :)

---

### Post by ozPATT on 2007-02-10
so... currently, if I run the -10 kernal, everything works. If I run the -11 kernel, my wifi doesnt... 

Will there be an update that I can just click and it magically fixes everything? Or am I unable to ever update my computer again until I re-install my wifi somehow?

---

### Post by PartisanEntity on 2007-02-10
> **reiki said:**
> I had teh 9746 nvidia drivers from a 3rd party repo before teh updates. I got the same errors as posted above with all the pictures. A mismatch between the kernel module and the X module.

I tried a few things to fix it, but..... they weren't working. So I went into my package manager, UNselected that 3rd party repo, and then highlighted the nvidia-glx package and told Synaptic to prefer packages from ubuntu-security. I uninstalled nvidia-glx and tehn refreshed repos. Instaled nvidia-glx from ubuntu repos.

TA-DA! I have a working system again. HOWEVER.... this set me back to the 8776 driver.
In all honesty, I don't think I NEED a newer driver right now so I'm going to leave this alone. If you go OUTSIDE the official repos, you WILL have issues when they update kernel images/restricted modules.

Thank you! It worked :)

I too am now on the somewhat older driver than the one I had before the kernel update, but at this moment I don't care, I'm just glad its working :)

I had originally installed the 9746 driver so I could get rid of a bug that made Google Earth unusable.

Wow, in German we would say that this was a 'schwere Geburt' (a hard birth)...

---

### Post by ozPATT on 2007-02-10
> **PartisanEntity said:**
> Wow, in German we would say that this was a 'schwere Geburt' (a hard birth)...

ein schwere Geburt ist aber, viel besser als kein Geburt... nicht wahr? :( 

still no wifi...

---

### Post by wislon on 2007-02-10
I've had better luck than some, for which I am glad! Once the repos started working properly again, I did my update for the kernels. Had a minor oops with the nVidia 8776 driver (coz of the new kernel modules), so figured this would be a good time to try upgrade anyway. 

Downloaded the 9746 driver, ran the installer, restarted with my new 11 generic kernel and am back in business. Thank goodness! :)

---

### Post by Ferrat on 2007-02-10
-11 broke wifi, didn't install right and for some reason edited my grub to search in the wrong place for my boot >_<

---

### Post by Stef@n on 2007-02-10
Ok, i'm quite a unexperienced Ubuntu user. After doing an update last night the nvidia-driver (9746) doesn't work anymore (and from what i understand is what this thread is all about). To get this to work again I have to install  NVIDIA-Linux-x86-1.0-9746-pkg1.run.from the Nvidia-site  (right?).  I used the commands bellow from someone a couple of post earlier.

wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run) 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run

When I enter the last command, I get the message that xserver is still running. So I kill xserver with sudo killall gdm. After that the command doesn't work anymore (no such file). 

Can somebody please explain to me how I can install this driver properly?

Thanks in advance!

---

### Post by bollix47 on 2007-02-10
Try:

sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run

---

### Post by PartisanEntity on 2007-02-10
> **Stef@n said:**
> Ok, i'm quite a unexperienced Ubuntu user. After doing an update last night the nvidia-driver (9746) doesn't work anymore (and from what i understand is what this thread is all about). To get this to work again I have to install  NVIDIA-Linux-x86-1.0-9746-pkg1.run.from the Nvidia-site  (right?).  I used the commands bellow from someone a couple of post earlier.

wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run) 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run

When I enter the last command, I get the message that xserver is still running. So I kill xserver with sudo killall gdm. After that the command doesn't work anymore (no such file). 

Can somebody please explain to me how I can install this driver properly?

Thanks in advance!

You need to enter those commands *outside* of the window environment. I usually open up a terminal and type sudo /etc/init.d/gdm stop

Then you will see a terminal only (you may have to log in again) without any window environment. Here is where you enter the commands:

```
wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run) 
sudo chmod 777 NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo ./NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

Some things to ponder first:

Did you initially have the nvidia-glx drivers installed through the ubuntu repository?
And did you use a 3rd party method to install later nvidia drivers?

If yes, then this method could mess up as it did in my case. Read through this thread carefully before you mess with it.

---

### Post by Pinniped on 2007-02-10
[COLOR="DarkOrchid"]I'm finally back to the way things were before this update :roll: ](*,)  thanks to the Envy script at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) \\:D/ [/COLOR]

---

### Post by TheEHMan on 2007-02-10
Looks like mine updated everything this morning w/o any problems.

---

### Post by PartisanEntity on 2007-02-10
> **Pinniped said:**
> [COLOR="DarkOrchid"]I'm finally back to the way things were before this update :roll: ](*,)  thanks to the Envy script at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) \\:D/ [/COLOR]

Are you using Dapper or Edgy?

---

### Post by Mark76 on 2007-02-10
I was getting the x-server problem and I don't even have an Nvidia card installed :?

---

### Post by Vorian on 2007-02-10
OK gang, here's the official word.  I am closing this thread.

> ATTENTION: 

Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

---

