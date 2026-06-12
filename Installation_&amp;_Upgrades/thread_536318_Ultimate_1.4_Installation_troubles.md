---
title: "Ultimate 1.4 Installation troubles"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by JeeOweDee on 2007-08-27
Hey all, 

    I recently tried Ubuntu for the first time. My first impression was "Holy...what have I been missing all these years." And I'm now in love with it. I have a ton to learn of course, and had a few questions for you gurus. 

First, the original Ubuntu 7.04 installation worked great, easy as cake. I fooled around with it, and decided to try Ultimate 1.4 (cd version). After installing Ultimate, I rebooted and it tells me that the X server or something of the kind wont function and what not. It then takes me to a black screen terminal where I'm able to enter commands if I wanted to. The question is, is there anything you know that might help me get around this so I can boot up the OS?

Second, When I installed Ubuntu for the VERY first time, I went the 'custom' installation route, and chose my own partitions and file types and such. The installations after that I just chose the HD that I wanted it to install fully on. I noticed quite a bunch of file types to choose from, and I was wondering if you guys had a preference on file types, being the one with the fastest performance I suppose.

Any help would be greatly appreciated. 


Thanks:biggrin:

---

### Post by spd106 on 2007-08-28
I've never used any of the Ultimate disks so I can't answer with the utmost certainty, but the usual cli incantation to get X up again is this
```
sudo dpkg-reconfigure xserver-xorg
```

If that fails you will have to post some error messages from the /var/log/Xorg.0.log file or just simply go back to the official cd and reinstall.

As far a file system types are concerned you can't really go wrong with the default EXT3. Some recommend Reiserfs or Reiser4, but it's not being actively developed any more and many kernel devs don't like it at all. The only other alternatives worth mentioning are XFS, which is designed more for servers, or VFAT, which is only useful if you need windows access (e.g. dual boot).

---

### Post by JeeOweDee on 2007-08-28
> **spd106 said:**
> I've never used any of the Ultimate disks so I can't answer with the utmost certainty, but the usual cli incantation to get X up again is this
```
sudo dpkg-reconfigure xserver-xorg
```

If that fails you will have to post some error messages from the /var/log/Xorg.0.log file or just simply go back to the official cd and reinstall.

As far a file system types are concerned you can't really go wrong with the default EXT3. Some recommend Reiserfs or Reiser4, but it's not being actively developed any more and many kernel devs don't like it at all. The only other alternatives worth mentioning are XFS, which is designed more for servers, or VFAT, which is only useful if you need windows access (e.g. dual boot).

Thank you for the help, It's up and running. 

Now another issue is getting KDE to run instead of GNOME, I've downloaded and installed KDE, i'm booted into it, yet GNOME taskbars still load up :/

---

### Post by spd106 on 2007-08-28
There are a few threads that discuss this if you look around the forum e.g. [http://ubuntuforums.org/showthread.php?t=490462](http://ubuntuforums.org/showthread.php?t=490462)

I'm a Gnome only person, so I can't really help you with this. I think there is a way of doing this by selecting the session type at the GDM login screen, though you've probably already done that.

---

