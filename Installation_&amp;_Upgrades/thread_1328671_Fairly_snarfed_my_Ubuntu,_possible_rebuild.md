---
title: "Fairly snarfed my Ubuntu, possible rebuild?"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by WASHAD on 2009-11-16
I absolutely love how flexible Ubuntu is and I have been taken full advantage of it by trying different desktops, different distros, partitioning, etc. With that kind of power, though, comes great potential to reck havock - which I have done. 

Basically, I have a few things behaving oddly. The following two are the ones I care about the most. 

- Internet doesn't work, wired or hard-wired. It used to work, it doesn't anymore.
- Everytime that open/close an application, my speakers pop. 
- Aside from that, things are missing from my desktop, etc..

I would like to repair Ubuntu without reinstalling and loosing my files and (LAMP Server) setup. What should I do to troubleshoot my problems, or repair my install. 



Here is my path to distruction:
- Started with Kubuntu
- Tried VMPlayer, with Windows. 
- Played with GParted, and resized hard drive a few times. 
- Installed Ubuntu desktop (I think I got the studio version)
- Upgraded to Ubuntu 9.10

Obviously, there is more there, but that is the high level.


Thanks, 

SteveJ

---

### Post by audiomick on 2009-11-16
All your config stuff and all your files are in /home. If you back that up, you can "paste" it back into a new installation.
If you already have /home as a seperate partition, you can mount that into a new installation. When you get all your programs re-instlled, it should all be there again.
When you do a fresh install, it is worth thinking about creating a sperate partition for /home for exactly that reason.

---

### Post by Hadeda on 2009-11-16
If you say
  *Internet doesn't work, wired or hard-wired. It used to work, it doesn't anymore.*
Could you be more specific?
Under Network Connections, do you see eth0?
If yes, have you set your IPv4 settings?
You might have issues with the DHCP server in which case configure it manually.
Just a guess...

---

### Post by Hadeda on 2009-11-16
Washad, audiomick is right. It's probably best to re install.

When you do, follow presence1960 advice:

[http://ubuntuforums.org/showthread.php?t=1307204](http://ubuntuforums.org/showthread.php?t=1307204)

Good luck.

---

### Post by falconindy on 2009-11-16
/home might have user config, but /etc has **system** config where you may have changed things (fstab, X11/xorg.conf, hosts.*, etc) that you'll want to hold onto.

---

### Post by WASHAD on 2009-11-17
Allright, thanks all - it looks like a new install might be the best bet. I've been wanting to try Ubuntu Studio anyway :).

---

