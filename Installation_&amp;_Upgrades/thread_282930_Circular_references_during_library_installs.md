---
title: "Circular references during library installs?"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by tananaBrian on 2006-10-23
Finally got my dual-boot setup working (XP, Ubuntu) ...it was easier once I figured out that my old BIOS has an 8 Gb addressing limitation that required the 2nd OS to be within 8 Gb of the MBR ... it works now though! :mrgreen: 

Now the bum thing is that I spent a lot of hours this weekend downloading libraries so I could install my favorite apps ...Kate, DDD, and Eclipse.  I got DDD going just fine, but in the case of Kate and Eclipse, I ran into troubles.  I started by installing the libraries that I knew they needed and then following the package manager's hints on what dependencies weren't yet met.  I'd download, install, then download, then install etc, following the dependency tree up the list as guided by the package manager.  Note that I'm on a dial-up and doing things like downloading all of KDE just to make sure that I have all libraries installed is NOT an option.  In any case, just as things were getting close, I ran into circular dependency issues ...library 'A' needs library 'B', and library 'B' needs library 'A', and neither will install until they get it! :-k 

Is there something wrong in the way that I went about installing this stuff?  Is there a way to force installation in spite of dependencies not being met?  Or maybe install the pairs of dependent libraries together, at once?  Something's fishy in Denmark...

Thx,
Brian

---

### Post by christhemonkey on 2006-10-23
If there are two .deb files in a directory, an they both depend on each other, then you can install them through a terminal like this:
```
sudo dpkg -i ./*.deb 
```

(presuming you are in the right directory to install them with!)

---

### Post by TheWizzard on 2006-10-23
if possible, do not install anything by downloading stuff manually, but use apt. 
to install kate: 
```
sudo aptitude update
sudo aptitude install kate
```

more info: 
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by az on 2006-10-23
> **tananaBrian said:**
> Finally got my dual-boot setup working (XP, Ubuntu) ...it was easier once I figured out that my old BIOS has an 8 Gb addressing limitation that required the 2nd OS to be within 8 Gb of the MBR ... it works now though! :mrgreen: 

If your / partition extends beyond that range and you update your kernel in a little while, you may end up with the kernel image being beyond the point that is readable by the bios.  ow big is your partition?

> **tananaBrian said:**
> 
Now the bum thing is that I spent a lot of hours this weekend downloading libraries so I could install my favorite apps ...Kate, DDD, and Eclipse.  I got DDD going just fine, but in the case of Kate and Eclipse, I ran into troubles.  I started by installing the libraries that I knew they needed and then following the package manager's hints on what dependencies weren't yet met.  I'd download, install, then download, then install etc, following the dependency tree up the list as guided by the package manager.  Note that I'm on a dial-up and doing things like downloading all of KDE just to make sure that I have all libraries installed is NOT an option.  In any case, just as things were getting close, I ran into circular dependency issues ...library 'A' needs library 'B', and library 'B' needs library 'A', and neither will install until they get it! :-k 

Is there something wrong in the way that I went about installing this stuff?  Is there a way to force installation in spite of dependencies not being met?  Or maybe install the pairs of dependent libraries together, at once?  Something's fishy in Denmark...

Thx,
Brian

You should avoid installing packages by hand.  Use the package manager.

In this case, you will need to run

sudo apt-get -f install

to resolve the circular dependencies.

---

### Post by tananaBrian on 2006-10-23
How big is my partition?  Well, I've got XP living in 7 Gb at the beginning of the disk and have used the Tweak UI power tool to move the 'My Documents' folders to a different partition that has a lot of room on it (32 Gb.)  The ext3 partition for Ubuntu starts right after the XP partition, and is about 65 Gb in size if I recall.  The 2 Gb swap follows that, etc etc.

I'm not too worried about the BIOS limitiations v. kernel upgrades as I'm NOT going to do any.  We'll be buying a new machine within a couple of months so I'm just gittin' by with what I have for now.  After the new machine is here, then it's all rock-n-roll.  BTW, to resolve this issue you could also place a small boot partition as a first partition with XP in one right after that.  But I'm not going to mess with it any more ...it works for now and I'll have a new machine before too long.  This one has served me well, but it's time to move on.

And thanks for the noob hints on installing apps.  I'll go home, dial up the Internet (I'll have broadband within a month) and try an apt-get to fix things.. fingers crossed on humongousmondohuge downloads over a crrapola 28.8kbd connection... ](*,) 

Brian

---

