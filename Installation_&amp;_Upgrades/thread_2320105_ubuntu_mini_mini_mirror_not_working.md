---
title: "ubuntu mini mini mirror not working"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by Christian_Smith on 2016-04-10
[COLOR=#111111][FONT=Ubuntu]My computer will only boot from Cd's so I was trying to install the minimal ubuntu. But it can't seem to find the mirror. I went with defaults. (United States, us.archive.ubuntu.com, blank proxy) It comes up "Bad archive mirror. An error has been detected while trying to use the specified Ubuntu archive mirror.....and some other stuff" I've tried several mirrors but am not sure I'm entering them right. I've tried direct ethernet connection and using a wireless adapter Machine is an HP Media Center 873n. Thanks


[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-04-10
Christian_Smith; Hello;

What release are you attempting to install minimally ?
Be aware you need to use the wired internet connection. Doubtful that the minimal will have the WIFI drivers .

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Christian_Smith on 2016-04-10
"[Ubuntu 14.04 LTS "Trusty Tahr"]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso")[COLOR=#333333][FONT=Ubuntu] 31MB" 
It seemed to work. It found my network. Named what I named it. I put in the password and it seemed to connect. [/FONT][/COLOR]

---

### Post by Bashing-om on 2016-04-10
Christian_Smith; Good deal ..

Are you comfortable making a minimal install ?
Are you aware that all you get is a booting kernel and networking with access to the software repository,,, It is your choice what else ( and all else ) that you install ?

[INDENT][INDENT]I happen to like it that way
[/INDENT][/INDENT]

---

### Post by Christian_Smith on 2016-04-10
> **Bashing-om said:**
> Christian_Smith; Good deal ..

Are you comfortable making a minimal install ?
Are you aware that all you get is a booting kernel and networking with access to the software repository,,, It is your choice what else ( and all else ) that you install ?
[INDENT][INDENT]I happen to like it that way
[/INDENT]
[/INDENT]


I would have rather done a full install but for some reason, this computer will only boot from cd-r's and not dvd-r's. So after some googling, the minimum install seemed doable. But this is my first time doing it this way. Was fine trying it a different way but so far it's not working out.

---

### Post by Bashing-om on 2016-04-10
Christian_Smith; K ..

There is everything right about a minimal install. But, you must have an idea of what you want the operating system to look like.
I do the minimal thing myself, and I sure like my results.

So, where are you at now ? Setting at a terminal and wondering what to do next ?

Do you want a desk top on this install ?
What applications do you require ?
What is your preferred browser - if this is to be a general purpose machine ? A server ?
Are we working with high end hardware .. low end ?? Such that resource usage is a factor .

Depending on what you want installed, there are some foundations to be laid .

This is real close kin to " roll your own " .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Christian_Smith on 2016-04-10
> **Bashing-om said:**
> Christian_Smith; K ..

There is everything right about a minimal install. But, you must have an idea of what you want the operating system to look like.
I do the minimal thing myself, and I sure like my results.

So, where are you at now ? Setting at a terminal and wondering what to do next ?

Do you want a desk top on this install ?
What applications do you require ?
What is your preferred browser - if this is to be a general purpose machine ? A server ?
Are we working with high end hardware .. low end ?? Such that resource usage is a factor .

Depending on what you want installed, there are some foundations to be laid .

This is real close kin to " roll your own " .
[INDENT][INDENT]'buntu[INDENT][INDENT][INDENT]you can have it your way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I guess I just banked on the install process to be straight forward enough to make it up as I go. 

Right now, I don't have it up. But the problem was, it couldn't seem to find the mirror to do it's thing. 

I just want something similiar to ubuntu 14.04. Regular dock, firefox, libre office. 
It's an old xp computer but it has 2 gigs of ram and a pentium 4. So it's adequate.

---

### Post by grahammechanical on 2016-04-10
Let us ask the oblivious questions to eliminate the obvious. Is the router switched on & connected to the ISP? Let us not leave out coincidence. Is the mirror site offline for maintenance? Could be. Try another mirror.

I have not tried the 14.04 mini ISO but I recently tried the 15.10 mini ISO. It was a lot simpler than I expected. At one point I got a screen where I could select & install software. That is where we have to make a careful choice. We could end up with a Linux command line & nothing more. We could end up with a very basic desktop environment. And it would be very basic. Or we could choose to install a desktop such as ubuntu-desktop or xubuntu desktop or one of the others.

That machine has adequate RAM and just about adequate CPU but what about the GPU? How much video memory does it have? Can it do hardware accelerated 3D rendering. The video adapter might not be capable of running Ubuntu with its Unity 3D user interface. Just a thought.

The nature of the minimum ISO makes installing from it not so simple. To start with it is a text based installer. Everything is installed by first being downloaded from the internet and so the one Minimum ISO image can be used to install all the different flavours of Ubuntu. So, installing becomes a bit more complicated. We have to make choices.

Regards.

---

### Post by Bashing-om on 2016-04-10
Christian_Smith; Hey ..

Lemme give ya some stuff to chew on:
[http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/) 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

If you did the preliminaries. giving the installer your location;
> 
 it couldn't seem to find the mirror to do it's thing. 

the installer should have found the "best" mirror.

And we discuss further what your desires/needs are .

[INDENT][INDENT]if you build it
[INDENT][INDENT][INDENT]they ...............
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Christian_Smith on 2016-04-10
> **grahammechanical said:**
> Let us ask the oblivious questions to eliminate the obvious. Is the router switched on & connected to the ISP? Let us not leave out coincidence. Is the mirror site offline for maintenance? Could be. Try another mirror.

I have not tried the 14.04 mini ISO but I recently tried the 15.10 mini ISO. It was a lot simpler than I expected. At one point I got a screen where I could select & install software. That is where we have to make a careful choice. We could end up with a Linux command line & nothing more. We could end up with a very basic desktop environment. And it would be very basic. Or we could choose to install a desktop such as ubuntu-desktop or xubuntu desktop or one of the others.

That machine has adequate RAM and just about adequate CPU but what about the GPU? How much video memory does it have? Can it do hardware accelerated 3D rendering. The video adapter might not be capable of running Ubuntu with its Unity 3D user interface. Just a thought.

The nature of the minimum ISO makes installing from it not so simple. To start with it is a text based installer. Everything is installed by first being downloaded from the internet and so the one Minimum ISO image can be used to install all the different flavours of Ubuntu. So, installing becomes a bit more complicated. We have to make choices.

Regards.

The router was plugged in and working. I was on my laptop on the wifi while I was messing with the desktop. 

I don't know about the part of the process where I would choose the software to install. I never made it that far. 

I don't know what the video card is but it's an HP Media Center. So I would assume it would be decent.

---

### Post by Christian_Smith on 2016-04-10
Here's a link to what it says

[http://imgur.com/xOsC4Jm](http://imgur.com/xOsC4Jm)

---

### Post by Bashing-om on 2016-04-10
Christian_Smith; Hey ..

I would suggest "change mirror". Maybe the present mirror is not currently updated . 

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by Christian_Smith on 2016-04-10
> **Bashing-om said:**
> Christian_Smith; Hey ..

I would suggest "change mirror". Maybe the present mirror is not currently updated . 
[INDENT][INDENT]maybe Yes
[/INDENT]
[/INDENT]


Ok. Then it asks for 
Archive mirror (us.archive.ubuntu.com) is default
HTTP proxy information  (blank)

I found the ubuntu mirror list online but every one I've put in hasn't worked. 
Not sure if I'm putting them in wrong or what

---

### Post by sudodus on 2016-04-11
It is possible that you have a bad version of the mini.iso. Which version is it?

I have found that versions via the following link work (better than some other versions),

[***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

-o-

You can get [almost] the same result, if you start from an Ubuntu Server iso file (even for desktop flavours: standard Ubuntu, Kubuntu ... Xubuntu).

---

### Post by Christian_Smith on 2016-04-11
> **sudodus said:**
> It is possible that you have a bad version of the mini.iso. Which version is it?

I have found that versions via the following link work (better than some other versions),

[***mini.iso***, minimal install, netboot iso]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730")

-o-

You can get [almost] the same result, if you start from an Ubuntu Server iso file (even for desktop flavours: standard Ubuntu, Kubuntu ... Xubuntu).

Ok I'll try that next. thanks!

---

