---
title: "Wich distro would be better for my potato?"
date: 2021-03-27
forum: Installation &amp; Upgrades
---

### Post by barni117 on 2021-03-27
Hey there, i need some help.
I have this old notebook with an intel atom core (N270 1.60 GHz) and 1.48 gb of ram. It's super old, but its reliable and its still working. Currently i have it with Windows XP and Ubuntu 10.04 and the thing is is none of those OS can load properly some content on internet and they are all out of support. Im thinking about setting up a new installation with a more recent OS. I dont know wich distro would be better for it tho. I would appreciate any help. Thanks in advance.

---

### Post by TheFu on 2021-03-27
I had an N270 600p notebook.  TinyCore is the OS I'd run. No Ubuntu is lite enough.

---

### Post by guiverc on 2021-03-27
I have a 
```

asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
```

which I use in testing.

It's x86 (i386 in Debian & Ubuntu terms; i686 in linux kernel terms) or 32-bit in somewhat normal human terms.

It was last used in August-2020 in the testing of Lubuntu 18.04.5 LTS, so I know it runs pretty good on that (though it was also used to test releases up to and into the 19.04 cycle, but they're EOL now too)

Lubuntu 18.04.5 LTS however has only 3 years of full support (from release in 2018-April, thus the 18.04) which ends next month. The Ubuntu base comes with 5 years of support yes, but that's the issue with Lubuntu 18.04 LTS.

I still use it on rare occasion (the eepc has great battery life, portable etc), and I think mine has Debian on it (I test Debian too, and thus used it for testing Debian Buster (*non-free* anyway; i can't recall if I tested *free* using it).

I'd opt for a light DM or WM personally; I know I have a number installed on mine (mine has 160GB of disk space so I've got a number of DEs, WMs installed and select what I use at login time, but it's usually a WM (window manager) directly or if I use a desktop it'll be LXDE usually (like Lubuntu offers) or LXQt (if I want to use Qt apps).  With only 1GB of ram, I select the DE at login depending on what I'll do that session, ie. I worry less about the space used by multiple WM/DE's on disk, but opt for what runs fastest with my intention for the session.

If you plan on using it for some time longer, Debian 10/*Buster* has more life than 18.04/*bionic* has.

---

### Post by DuckHook on 2021-03-27
Welcome to the forums barni117,

I'm going to depart a bit from the good advice you've been given by TheFu and guiverc.

Depending in how comfortable you are with the command line: Have you considered running this old gem purely as a command line server of some sort?

That is how I've revitalized some of my ancient laptops in the past and, once you eliminate the GUI, whole new avenues open up, mostly as servers and server-type services. Without a GUI, these old boxes get a new lease on life.

---

### Post by yancek on 2021-03-28
One of the best for older computers is AntiX, discussed at the link below, download at the second link.  MXLinux is similar.

[https://www.technewsworld.com/story/86942.html](https://www.technewsworld.com/story/86942.html)

[https://antixlinux.com/download/](https://antixlinux.com/download/)

[https://mxlinux.org/](https://mxlinux.org/)

---

### Post by mikewhatever on 2021-03-28
While it is still easy to find a distro that runs well, nothing will make that machine suitable for the internet. It was underpowered in 2008, and now it is also old. There are very limited usage cases I can think of that it won't struggle with. 
A text editor could run slowly, but acceptably well, but forget about internet browsing or video streaming.

PS: +1 for a server suggestion.:popcorn:

---

### Post by barni117 on 2021-03-28
> **guiverc said:**
> I have a 
```

asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
```

which I use in testing.

It's x86 (i386 in Debian & Ubuntu terms; i686 in linux kernel terms) or 32-bit in somewhat normal human terms.

It was last used in August-2020 in the testing of Lubuntu 18.04.5 LTS, so I know it runs pretty good on that (though it was also used to test releases up to and into the 19.04 cycle, but they're EOL now too)

Lubuntu 18.04.5 LTS however has only 3 years of full support (from release in 2018-April, thus the 18.04) which ends next month. The Ubuntu base comes with 5 years of support yes, but that's the issue with Lubuntu 18.04 LTS.

I still use it on rare occasion (the eepc has great battery life, portable etc), and I think mine has Debian on it (I test Debian too, and thus used it for testing Debian Buster (*non-free* anyway; i can't recall if I tested *free* using it).

I'd opt for a light DM or WM personally; I know I have a number installed on mine (mine has 160GB of disk space so I've got a number of DEs, WMs installed and select what I use at login time, but it's usually a WM (window manager) directly or if I use a desktop it'll be LXDE usually (like Lubuntu offers) or LXQt (if I want to use Qt apps).  With only 1GB of ram, I select the DE at login depending on what I'll do that session, ie. I worry less about the space used by multiple WM/DE's on disk, but opt for what runs fastest with my intention for the session.

If you plan on using it for some time longer, Debian 10/*Buster* has more life than 18.04/*bionic* has.


From an easy to use point of view, wich os would be better? Debian or Lubuntu??

---

### Post by barni117 on 2021-03-28
> **TheFu said:**
> I had an N270 600p notebook.  TinyCore is the OS I'd run. No Ubuntu is lite enough.
What about puppy? Is there any difference between tiny core and puppy when you go online and try to load some newer content (google drive, docs, youtube, dropbox,etc)??

---

### Post by ajgreeny on 2021-03-28
I would recommend Debian 10 Testing for that 32 bit machine, installed with the netinstall system from [https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso](https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso) which allows you to choose just about everything that is installed.
I would also suggest you forget about using any full DE, even LXDE will be a bit heavy so if you can manage with just a window-manager add openbox or fvwm both of which can give you a useful but very low resource using system.

This is what I use sometimes on a similarly specified clone machine with same CPU as yours but with merely 1G ram; it is fine for email, browsing using a browser such as epiphany, not chromium or forefox both being too big and heavy, and office type work but using abiword and gnumeric rather than libreoffice which is also far too cumbersome for that machine.

Puppy, as suggested above is a posibility, but I could never get it installed and working, and did not wish to use it as a live system only so I gave up on that.

---

### Post by barni117 on 2021-03-28
> **DuckHook said:**
> Welcome to the forums barni117,

I'm going to depart a bit from the good advice you've been given by TheFu and guiverc.

Depending in how comfortable you are with the command line: Have you considered running this old gem purely as a command line server of some sort?

That is how I've revitalized some of my ancient laptops in the past and, once you eliminate the GUI, whole new avenues open up, mostly as servers and server-type services. Without a GUI, these old boxes get a new lease on life.

I dont really know how to do that. I dont even know what is a command line server or what to do with one

---

### Post by barni117 on 2021-03-28
> **ajgreeny said:**
> I would recommend Debian 10 Testing for that 32 bit machine, installed with the netinstall system from [https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso](https://cdimage.debian.org/cdimage/bullseye_di_alpha3/i386/iso-cd/debian-bullseye-DI-alpha3-i386-netinst.iso) which allows you to choose just about everything that is installed.
I would also suggest you forget about using any full DE, even LXDE will be a bit heavy so if you can manage with just a window-manager add openbox or fvwm both of which can give you a useful but very low resource using system.

This is what I use sometimes on a similarly specified clone machine with same CPU as yours but with merely 1G ram; it is fine for email, browsing and office type work but using abiword and gnumeric rather than libreoffice which is far too cumbersome for that machine.

So wich options should i check/uncheck during the installation to make it work smoothly? And anything like puppy, tiny core and antix would do just as good or is there any difference with debian 10??

---

### Post by TheFu on 2021-03-28
> **barni117 said:**
> I dont really know how to do that. I dont even know what is a command line server or what to do with one

Anything that doesn't need a GUI would be useful.  That's almost any server process.
[LIST]
[*]print server
[*]storage / backup server
[*]web server
[*]calendar server
[*]read-it-later server (wallabag is the name of the project)
[*]nextcloud/owncloud/seafile server
[*]DNS/DHCP server
[*]pi-hole DNS filter system - a central ad blocker for your LAN
[/LIST]
Those are off the top of my head.

There are hundreds of other choices that would work on the system, but none can run a current Ubuntu because Canonical decided to drop non-64-bit OSes.  You'll want an OS that supports 32-bit Linux.  TinyCore isn't usually for "servers", and the package manager is nothing like APT.  If you are tied to APT (which I like), then look at a minimal Debian Server install. It won't have any GUI, so no point-n-click for anything. You'll want another computer with a GUI to make managing the Debian Server easier.

I just threw out TinyCore because it will fly on your hardware. I use it for online banking for better security. It is read-only, so when I'm done, if forgets everything.

---

### Post by grahammechanical on 2021-03-28
> none of those OS can load properly some content on internet

Which content is this? You may need to install some non-free or proprietary video or audio drivers. Which is a different question. Or, it may be as stated by someone else that many web sites now have resource demands beyond that hardware.

Regards

---

### Post by barni117 on 2021-03-28
> **grahammechanical said:**
> Which content is this? You may need to install some non-free or proprietary video or audio drivers. Which is a different question. Or, it may be as stated by someone else that many web sites now have resource demands beyond that hardware.

Regards

google apps (drive, docs, etc) youtube and some pages with a protocol that firefox 20 (on ubuntu) & 64 (on XP) simply cannot understand

---

### Post by TheFu on 2021-03-28
> **barni117 said:**
> So wich options should i check/uncheck during the installation to make it work smoothly? And anything like puppy, tiny core and antix would do just as good or is there any difference with debian 10??

You'll have to try each to know. We don't have exactly the same hardware.

---

### Post by ajgreeny on 2021-03-29
I think you can forget about youtube as the hardware will not be good enough for most of that; a few low resoluttion  ones might play but I suspect not many.

I've no idea about google-docs etc, as I've never used it so try it yourself and you'll soon see.

---

### Post by TheFu on 2021-03-29
VP9 w/hi-def won't work.  My N270 couldn't handle any video higher than 600p. It doesn't have any hardware decoding for video, so all video display has to be handled by the CPU.  I don't use youtube directly much - not in a browser - but there are ways to request specific formats from the service. As long as 480p is requested, then either vp8, vp6 or h.264 should be sent.

New versions of firefox sometimes have issues with websites that the developers only test using Google's Chrome browser. In my world, when that happens, I generally decide that content isn't something I need to see if the web-devs can't be bothered to follow HTML standards without Google's proprietary extensions.

---

### Post by barni117 on 2021-03-30
Thank you all for your answers, i really appreciate it

---

### Post by ActionParsnip on 2021-03-30
Could use the shell and house a raspberry pi :)

---

