---
title: "Old versions?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by pcal on 2011-10-20
Hi guys,

I'm trying to breath life into an old system as a bit torrent client. The hardware is surplus - brand new but a very long way from cutting edge. (VIA 1ghz)

I originally installed XBMC on the machine, but found the on board graphic engine only supports opengl 1.2, while 1.3 is the minimum for XBMC.

So, I've spent hours installing progressively older 32bit Ubuntu desktop releases until I found one that installed without crashing the machine part way through. It is now running on an old 7.04 I had on my NAS drive. Unfortunately, it seems the repositories aren't on-line any more so I can't install anything.

Every newer distro I tried (11.10, 11.04, 10.10, 10.04, 9.04, and Lubuntu 11.10) choked either immediately after the install option was selected if on a text menu, or as soon as the mouse hovered over the install button if on a gui.

Are there any suggestions out there which way I can go from here? I'm happy 7.04 is running, but with no updates and only distro default apps, its usefulnes is limited.

Thanks in anticipation,

pcal

---

### Post by howefield on 2011-10-20
Use [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) to change your software sources to the relevant release.

With an Ubuntu release reaching end of life the repositories are moved to old-releases.ubuntu.com. So edit your software sources:

In terminal type
```
gksudo gedit /etc/apt/sources.list
```

and change eg, 

```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main
```

to this:

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main
```

This will allow you to install software from the end of life repositories.

Although to be honest I'd never recommend using an unsupported release, there are light weight distros available that might give you something more current and also work well on your hardware.

---

### Post by nothingspecial on 2011-10-20
> **pcal said:**
> Hi guys,

I'm trying to breath life into an old system as a bit torrent client. 

Why not do a minimal install (no gui) and use rtorrent (or transmission-cli)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by westie457 on 2011-10-20
Hi have you tried any of the xubuntu releases. They are easier on resources than Ubuntu. I think there is a LTS version around as well.

You could try PuppyLinux even though I have never used it, some people will recommend it in a flash.

---

### Post by haqking on 2011-10-20
> **nothingspecial said:**
> Why not do a minimal install (no gui) and use rtorrent (or transmission-cli)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

+1

Here is a list of Distros which may work

[Light Linux Distros]("http://ubuntuforums.org/showthread.php?t=1582027")

---

### Post by mastablasta on 2011-10-20
> **pcal said:**
> Every newer distro I tried (11.10, 11.04, 10.10, 10.04, 9.04, and **Lubuntu 11.10**) choked either immediately after the install option was selected if on a text menu, or as soon as the mouse hovered over the install button if on a gui.

 
this might be due to an old processor. or something. i had a similar strange experience with Lubuntu 11.04, eventhoguh the previous worked. I would suggest you try Lubuntu 10.04 (if you have at least 192 MB ram). Another good option that has plenty things preinstalled is Crunchbang (based ondebian stable) and linux mint LXDE or Peppermint OS from same developer/packager.

---

### Post by shubham1 on 2011-10-20
what about puppy linux
damnsmalllinux

---

### Post by shubham1 on 2011-10-20
kolibrios tried?

---

### Post by pcal on 2011-10-20
:D Thanks guys for heaps of suggestions. I'll have to work through them all now - will report back (eventually) once I've settled on a solution...

---

### Post by pcal on 2011-10-21
> **mastablasta said:**
> I would suggest you try Lubuntu 10.04

Do you have a link to the iso? 11.10 is all I can find...

**Don't worry - found it. Thanks anyway**

thanks

---

