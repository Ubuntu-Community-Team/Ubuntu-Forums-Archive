---
title: "Be careful this morning updates!"
date: 2009-11-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-11-06
It would like to remove a few things:
```
The following packages will be REMOVED:
  libcanberra-pulse{a} pulseaudio{a} pulseaudio-esound-compat{a} pulseaudio-module-bluetooth{a} 
  pulseaudio-module-gconf{a} pulseaudio-module-udev{a} pulseaudio-module-x11{a} ubuntu-desktop{a} 
```

---

### Post by Bunnybugs on 2009-11-06
I guess that I'll need to replace them with the apt-get functionality?

EDIT: packages are still in my system, not removed, did my updates

---

### Post by Kevbert on 2009-11-06
> **DougieFresh4U said:**
> It would like to remove a few things:
```
The following packages will be REMOVED:
  libcanberra-pulse{a} pulseaudio{a} pulseaudio-esound-compat{a} pulseaudio-module-bluetooth{a} 
  pulseaudio-module-gconf{a} pulseaudio-module-udev{a} pulseaudio-module-x11{a} ubuntu-desktop{a} 
```

Thanks. Sound was working fine. I'll remember to skip these packages.

---

### Post by dino99 on 2009-11-06
don't be worried, that's only pulseaudio  ):P

---

### Post by hikaricore on 2009-11-06
Some of us actually use pulse.  :p

---

### Post by Kevbert on 2009-11-06
Interesting...
```
The following packages have been kept back:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils 

```

---

### Post by VMC on 2009-11-06
> **DougieFresh4U said:**
> It would like to remove a few things:
```
The following packages will be REMOVED:
  libcanberra-pulse{a} pulseaudio{a} pulseaudio-esound-compat{a} pulseaudio-module-bluetooth{a} 
  pulseaudio-module-gconf{a} pulseaudio-module-udev{a} pulseaudio-module-x11{a} ubuntu-desktop{a} 
```

Doug, I remember you suggesting to use:
sudo aptitude update
sudo aptitude dist-upgrade
Now I think a better solution is "safe-upgrade". You can run dist or full, but Aptitude is smart enough to ask questions before commited.

What I did:
vmc@vmc-desktop:~$ sudo aptitude update && sudo aptitude full-upgrade
Reading package lists... Done
....
Current status: 45 updates [+45].

vmc@vmc-desktop:~$ [COLOR="Lime"]**sudo aptitude safe-upgrade**[/COLOR]
Reading package lists... Done
...
Resolving dependencies...
The following packages have been kept back:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils 
The following NEW packages will be installed:
  libntfs10{a} ntfsprogs{a} 
The following packages will be upgraded:
  at-spi brasero devicekit-disks espeak espeak-data gnome-orca 
  libasound2-plugins libatspi1.0-0 libbrasero-media0 libespeak1 
  libmagickcore2 libmagickwand2 libneon27 libpixman-1-0 libpopt0 libpth20 
  libquicktime1 libruby1.8 libsdl-image1.2 libsgutils2-2 libslp1 
  libstlport4.6ldbl libsysfs2 libtdb1 libtiff4 libtimedate-perl libwrap0 
  myspell-en-au psmisc python-pyatspi python-pycurl python-telepathy sed 
  tcl8.4 tcpd ucf 
36 packages upgraded, 2 newly installed, 0 to remove and 9 not upgraded.
Need to get 10.4MB of archives. After unpacking 807kB will be used.
Do you want to continue? [Y/n/?] y
...
Current status: 9 updates [-36].
vmc@vmc-desktop:~$ **[COLOR="Red"]sudo aptitude full-upgrade[/COLOR]**
Reading package lists... Done
The following packages are BROKEN: [COLOR="red"]<---I'm thinking this will be broken, if done???[/COLOR]
  pulseaudio 
The following NEW packages will be installed:
  rtkit{a} 
The following packages will be REMOVED:
  pulseaudio-module-udev{a} 
The following packages will be upgraded:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils 
9 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,118kB of archives. After unpacking 201kB will be used.
The following packages have unmet dependencies:
  pulseaudio: Depends: pulseaudio-module-udev but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
libcanberra-pulse
pulseaudio      [COLOR="Red"]**<---This looks like what will be BROKEN**[/COLOR]
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-x11

Leave the following dependencies unresolved:
gnome-media recommends pulseaudio
gnome-session-canberra recommends libcanberra-pulse
gnome-settings-daemon recommends pulseaudio
Score is -494

Accept this solution? [Y/n/q/?] [COLOR="Black"]**q**[/COLOR]

---

### Post by slakkie on 2009-11-06
Guess it is time for the partial upgrade thread once again..

safe-upgrade (or apt's upgrade) command will not remove those packages.

---

### Post by autocrosser on 2009-11-06
Agreed--remember people--only install things that WON'T remove large portions of your system unless you know EXACTLY what it will do.

---

### Post by ranch hand on 2009-11-06
I have 2 "Lizards" on here.  One I am using the other gets the updates to see what happens.  I am updating both.  I saw no problem with the first one at all.

Sound is fine.  Now I do have an Audigy1 5.1 card so that may be the difference between my box and others that may suffer.

There are 2 libs and pulse-utils being installed too.

---

### Post by novafluxx on 2009-11-06
Its because rtkit ... remember the issues in karmic?

---

### Post by philinux on 2009-11-06
> **novafluxx said:**
> Its because rtkit ... remember the issues in karmic?

I'm on karmic with a chroot terminal open. I'm just sticking to apt-get update for now. I will use dist-upgrade just to check whats going on now and then.

---

### Post by QQi on 2009-11-06
> $ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  [COLOR="DarkRed"]libcanberra-pulse pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev
  pulseaudio-module-x11 ubuntu-desktop[/COLOR]
The following NEW packages will be installed:
  [COLOR="Red"]rtkit[/COLOR]
The following packages will be upgraded:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio-utils
4 upgraded, 1 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B/362kB of archives.
After this operation, 5,116kB disk space will be freed.
Do you want to continue [Y/n]? 


What do I do?

---

### Post by novafluxx on 2009-11-06
O> **QQi said:**
> What do I do?

You wait for the other pulseaudio packages to be updated to not conflict with rtkit

---

### Post by sports fan Matt on 2009-11-06
Waiting pattern here too..although like kev, nothing was removed.

---

### Post by Bunnybugs on 2009-11-06
I've used the updatemanager, and the packages are also still here...

Guess that it didn't affect my system:)

---

### Post by philinux on 2009-11-06
Beware update-manager, there be dragons.

Ignore partial updates.

---

### Post by VMC on 2009-11-06
> **ranch hand said:**
> I have 2 "Lizards" on here.  One I am using the other gets the updates to see what happens.  I am updating both.  I saw no problem with the first one at all.

Sound is fine.  Now I do have an Audigy1 5.1 card so that may be the difference between my box and others that may suffer.

There are 2 libs and pulse-utils being installed too.

As for me, I'll keep pulseaudio. It works fine with my system.

---

### Post by Regenweald on 2009-11-06
rhiken@Horsford:~$ [COLOR="DarkRed"]sudo aptitude safe-upgrade[/COLOR]
[sudo] password for rhiken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[COLOR="DarkRed"]The following packages have been kept back:
  grub{a} grub-common{a} grub-pc libpulse-browse0{a} 
  libpulse-mainloop-glib0{a} libpulse0{a} pulseaudio 
  pulseaudio-esound-compat{a} pulseaudio-module-x11{a} pulseaudio-utils{a}[/COLOR]
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


PLEASE use [COLOR="DarkRed"]**aptitude safe-upgrade**[/COLOR]! :P pretty please....

---

### Post by VMC on 2009-11-06
> **Regenweald said:**
> rhiken@Horsford:~$ [COLOR="DarkRed"]sudo aptitude safe-upgrade[/COLOR]
[sudo] password for rhiken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[COLOR="rgb(139, 0, 0)"]The following packages have been kept back:
  grub{a} grub-common{a} grub-pc libpulse-browse0{a} 
  libpulse-mainloop-glib0{a} libpulse0{a} pulseaudio 
  pulseaudio-esound-compat{a} pulseaudio-module-x11{a} pulseaudio-utils{a} [/COLOR]
0 packages upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


PLEASE use [COLOR="DarkRed"]**aptitude safe-upgrade**[/COLOR]! :P pretty please....
Agreed or don't take the fun out of "flying by the seat of your pants". :)

I can see right now that this is going to be one of those topics that won't go away very easily.

[FONT="Courier New"]sudo aptitude safe-upgrade[/FONT] is what I use. I don't know about update-manager, since I don't have it installed.

---

### Post by ranch hand on 2009-11-06
This is why I have more than one test install.  If I just had one there is no way I would have given the OK for that udate, not a chance.

Two allow me to do that knowing I have another next door that will still work if I leave it alone.

---

### Post by LKjell on 2009-11-06
Hope this will be implemented [https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)

---

### Post by ranch hand on 2009-11-06
"Back in time" is in the repo.  I can't give how that is parsed in synaptic as I am on 9.04 now.

---

### Post by jerrylamos on 2009-11-06
> **ranch hand said:**
> This is why I have more than one test install.  If I just had one there is no way I would have given the OK for that udate, not a chance.

Two allow me to do that knowing I have another next door that will still work if I leave it alone.

Ranch hand,

I used your DD recommendations in I think the karmic thread to duplicate a karmic, not on a second drive as you wrote it, but on the same drive.

Thought is, boot one, try an update.  If it goes south i.e. breaks, then either boot to the second copy or else DD it in to wipe out the update.

Now, Grub seems to see only one of the two copies of karmic.  I'd hoped to start working with lucid......Somehow playing with 40_custom does change which one boots, but I don't get both on the grub menu.

?

Thanks, Jerry

---

### Post by ranch hand on 2009-11-06
Did you run update-grub?

And what in flinderation is DD?

---

### Post by jerrylamos on 2009-11-06
> **ranch hand said:**
> Did you run update-grub?

And what in flinderation is DD?

Oops, latest grub2 update I can pick which one to boot,  I think.  

DD is indeed flinderation.  Shouldn't work.  dd does.  Now to see what kind of trouble I'll get into with sources.list.....

........

Well, the sources.list update to lucid seems to have worked.  That means to me they haven't put very many (broken) changes in yet.  Give them time.....

Jerry

---

### Post by hugmenot on 2009-11-06
The problem with Pulseaudio is that they added a Conflicts: to pulseaudio-module-udev (because this package was merge with pulseaudio itself) but they left in the Depends: on the same package. An unsatisfiable situation. 

Just wait for them to upload an amended pulseaudio.

---

