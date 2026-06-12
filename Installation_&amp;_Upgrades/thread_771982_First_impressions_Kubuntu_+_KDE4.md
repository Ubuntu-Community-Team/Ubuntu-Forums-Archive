---
title: "First impressions: Kubuntu + KDE4"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by needhelpplease on 2008-04-28
It's cool!  It looks very different from KDE3, and it's all better.  This thing is a viable competitor to any other desktop OS out there.  I'm waiting for about a month before I run it on my primary desktop system here, just to get any updates on packages that may be needed, but it's very cool.  I've already installed it on two systems.  For the first time in Linux, my webcam "just worked" when I installed v4l.  Also for the first time in Linux, openjdk was part of the repos, and I chose that as my Java environment.  This is a big deal for me because Java is what I work in all day long.  I know openjdk is under very active development.  The parts of it that are missing (sound, SNMP) are things that I don't need right now.  Hopefully, in the near future, sound support will be added, but it's not a common need for me.

Wireless networking works better.  I'm looking forward to trying the laptop features (suspend).

I just now installed it on another machine with an NVidia card, and it was amazing.  It said "restricted drivers are available to take full advantage of your hardware, install?" and I clicked a couple of times, and it's DONE.  That's the way this should be.  Now I'm about to see what the desktop effects look like...

---

### Post by russ18uk on 2008-04-28
Was tempted to install KDE4 version but I was under the impression KDE4 is still beta? Otherwise I'm interested :>

---

### Post by mutzinet on 2008-04-28
I've been running KDE4 on kubuntu for a few months now without any problems... almost. 

Suspend to RAM and suspend to disk do not work, whereas they do work (at least suspend to RAM) in 3.5.8 or 3.5.9.

Otherwise everything is fine.

---

### Post by nomeat on 2008-04-28
A lot of little things don't work so well or are missing but the major reason why I am considering deleting it is that it crashes when I log out or shut down.
Totally frozen, nothing to display just back screen, once even white screen.
None of my desktop settings are memorized.
Only thing left is hold the power button for 6 secs.

Some of the little issues:

I get very often an error window from "Plasma workspace" that displays after I open a random application:

> KDEInit could not launch "usr/bin/<name of application>
However the application did launch!

or when the application was open and I clicked on it on the task bar:
> KDEInit could not be reached via D-bus, error when calling start-service-by-desktop-path: empty
The system seems then frozen for 10 secs then the app re-appears normal.
One app where I can always reproduce that is Kword. 


Funny is that I can not find some of my fav apps in the Adept manager.
I installed Synaptic and all was fine again.

The system settings appears incomplete. I can not enable numlock on startup for instance.This actually makes me quite furious when I want to type in a number and the page disappears because positioning is activated instead. I have no display LED on my wireless keyboard.
I cannot understand why a number block is not numlock by default on start up. Bios settings are ignored too.
I also tried sudo kcontrol in a terminal which comes up but the numlock setting seems to be ignored.


The panel bar behaves erratic when I add extra applets like knewsticker for example and don't even think about superkaramba :eek:

I think it is probably better to wait for KDE4.1

BTW I downloaded UBUNTU-Studio 8.04 and installed it **on another machine**.
It is totally awesome but guess what... it won't shut down either!
It does log out and memorize the settings though.
Just freezes with the UBUNTU STUDIO logo.

All the former versions of UBUNTU have worked fine on both machines.
I also have OpenSuSE running on both with no problems and *cough* Windows which I hope to exterminate if UBUNTU STUDIO satisfies **all** my needs.

---

### Post by Kenobi on 2008-04-29
You are all so enthusiastic!

After 1 day of testing kubuntu I almost gave up so many little bugs...

how can it be that my panel has simply disappeared??? And it won't come back whatsoever?? Who can help me?

Screenshot provided...

---

### Post by needhelpplease on 2008-04-30
My enthusiasm about Hardy Heron KDE4 is dampened.  After installing a few things in Adept, I can no longer log in.  It takes my password and goes through a few steps of KDE initialization and then bounces me out.

I'm glad I didn't install this on my main desktop machine yet.

---

### Post by oui on 2008-04-30
Hi

I use Kubuntu 7.10 with KDE 4.0 remastered (540 Mo) since begin of Feb. 08.
Diverse bugs:
- terrible bug in Kpackage (the questions required by some software like JRE from Sun to ask for your acceptance of Sun's conditions or by language packages as they ask "which language" is your main language is not activated so that Kpackage crashes); don't use Kpackage without precautions! it is better to learn again how to use "aptitude" or "apt-get"! you can install synaptic and it works but bugs at the end: you can't quit the program
- the list of messenger providers is not available in Kopete in this old version (7.10)
- bug in the background management
- diverse icons are not available
- Konqueror don't recognize VLC

but delivered with a very large choice of new KDE 4 programms. It is easy to install Wine and it works very properly with real open sources goodies from the Windows world: MirandaIM 0.7.4ansi (as Kopete don't works), K-meleon 1.1.5 a real good Mozilla browser, really fast in Wine after the start, perhaps the best, but only for Windows or Wine, nPOPQ (micro email client with only 250 kbyte! nPOPQ can be linked in K-meleon without difficultie), VLC, etc. the use of windows-versions of open source software is naturally the easy way to install! no problem with Kpackage etc. one click and the installation runs!

I did try 8.04 alpha, beta, RC and actual end release with KDE 4.03. I miss a lot of KDE 4 programms that I know from the 7.10 remastered version. Kopete works but only libjasperl is preinstalled for the webcam (but the webcam needs also libjasper.runtime !)

The adjustement of the webcam in Kopete is bad. The push-pull buttons are less sensitive! It would really be better to enter directly a value: 60 % brightness, 55 % contrast etc. the color adjustment is very bad with my 2 webcams

The bug in Kpackage is not solved.

So I did reinstall 7.10 remastered :lolflag: and use it now with Wine and K-meleon (I am using K-meleon now)!

One avantage of this version is that it uses only Open Office Write. If find it is a kind of Microsoft-like-method to oblige us to install all the suite. I like for example Gnumeric and Magic Point and I don't need the drawing facility from OO !

see also [http://kmeleon.sourceforge.net/forum/read.php?3,79339](http://kmeleon.sourceforge.net/forum/read.php?3,79339)

I would be very interesting to upgrade this version 7.10 to 8.04 because I don't see some packages for KDE 4 in the Gutsy repositories, and I would be interesting to actualise my KDE without lose of the other programms that I have now and available in the official new version. I hope they don't will be erased by the upgrade :confused:

But I don't know the way to upgrade (to upgrade from 7.04 to 7.10 Kubuntu did give an additional upgrade starter).

Bye

---

### Post by mutzinet on 2008-04-30
> **needhelpplease said:**
> My enthusiasm about Hardy Heron KDE4 is dampened.  After installing a few things in Adept, I can no longer log in.  It takes my password and goes through a few steps of KDE initialization and then bounces me out.

I'm glad I didn't install this on my main desktop machine yet.



I got the same problem a few days ago. After a few tries I finally got some message saying that I had no write permission on the file .ICEauthority.
I logged in on the shell and changed the owner of that file from root to myself and that solved the problem. You might be facing the same problem?

---

### Post by russ18uk on 2008-05-01
I installed KDE4 on top of the 3.5.9 version and logged into it. Not fun manually installing each .deb for KDE4 BTW, and found it plain annoying. Granted I only gave it 10 minutes to take a look around, had no idea how to unlock the taskbar to be able to remove the new menu and move the old menu in its place. I'll see what kcontrol allows me to do later but so far not finding it blissful.

---

### Post by capink on 2008-05-01
> **russ18uk said:**
> had no idea how to unlock the taskbar to be able to remove the new menu and move the old menu in its place.

1. Right click on the icon of the menu and remove it from the panel.

2. Press the add widget plasmoid in the **upper right corner of your desktop** "instead of right clicking the panel", this will open a list of avaiblable widgets. **Drag** the old menu widget to where you want to place it in the panel.

---

### Post by needhelpplease on 2008-05-01
> **mutzinet said:**
> I got the same problem a few days ago. After a few tries I finally got some message saying that I had no write permission on the file .ICEauthority.
I logged in on the shell and changed the owner of that file from root to myself and that solved the problem. You might be facing the same problem?

:guitar:

[COLOR="Red"][SIZE="6"]THANK YOU![/SIZE][/COLOR]  That solved the problem.  Now I can log in again.  This is probably a trivial bug but it has very very serious user impact.  Ubuntu should fix this ASAP.

---

### Post by Kenobi on 2008-05-02
Yeah... this is going to work....

if you are one of the few lucky users who actually have a panel :-(

BTW a little bit of bug-avoiding: as we all know you can't move a widget on the panel. Thats pretty annoying. But you can delete a misplaced widget and drag it on the right place. You don't get no preview so you will only know if the position is right when you release the mouse button and possibly you have to start all over again but well it works.

One thing I miss that is existing since Win98: I have to fill the panel with some useful applications. But the only place where everything is linked neatly is the start menu. I NEED to drag them on the panel, but this feature is still missing....

Yeah well ok you can probably create a link to a file dragging it from dolphin on the panel. But don't dare to change the icon - this tiny little link will be owned by ROOT!

I wonder if they actually want to keep simple people out of ubuntu?

---

### Post by Gaute65 on 2008-05-03
> **Kenobi said:**
> Yeah... this is going to work....

if you are one of the few lucky users who actually have a panel :-(



Try this: [http://anojrs.blogspot.com/2008/01/disappearing-panel-in-kde-4.html](http://anojrs.blogspot.com/2008/01/disappearing-panel-in-kde-4.html)

---

### Post by PseudoOne on 2008-05-03
> **Kenobi said:**
> You are all so enthusiastic!

After 1 day of testing kubuntu I almost gave up so many little bugs...

how can it be that my panel has simply disappeared??? And it won't come back whatsoever?? Who can help me?

Screenshot provided...

I had this problem before, my solution was to login via Failsafe, and then ```
sudo rm -rf .kde4
```

to remove your KDE4 settings folder, and restores it to default.

---

### Post by mutzinet on 2008-05-07
Some new problems here... 
I always do all the daily upgrades and got some new kde4 packages lately. Since then, every now and then logging in kde4 brings up a corrupted kwin. Only one virtual desktop (should be 4), no frame on the windows, and no switching between windows. 
Has anyone encountered the same issue lately?

---

