---
title: "build vs install with apt-get ???"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2007-01-24
I was just wondering what/if there would be any advantage to building your programs with apt-get rather than installing them?  What I mean is getting the source with apt-get and then having it install the source (this might not be the proper wording as I have never actually done it) vs.  just using apt-get install.  I think the other two commands are something like apt-get source   program and then apt-get build program .  Is there any advantage to that?  There must be something to it or it wouldn't even be a part of apt.  Can someone enlighten me a little?  Thanks!

Shane

---

### Post by mandrakethepenguin on 2007-01-24
Actually, the point to downloading package sources from apt is just to support the GNU General Public License philosophy. Which is of course, being able to freely download the source and modify it for any package licensed under the GNU GPL.

---

### Post by deanlinkous on 2007-01-24
no actually the point is for those that like to have their packages built from source yet still register in the package manager...

Thats right, if you want a source-based distro then debian can fill that slot also...

apt is a super-tool! DEBIAN the universal OS!

---

### Post by shane2peru on 2007-01-25
If you build it from source is it built around your machine, so it would theoretically have less bulk? or unnecessary files?  I could understand the point of having the source available for programmers to look through, that would make sense.  I guess what I'm looking for is does it make your machine more streamlined?  Does it make it even more stable?  Or isn't there any real difference between compiling the program (with apt, is that the same as building?)  just using apt-get install?  or is the package in the end the same if I don't change coding?  (which I don't know how to change coding anyway.)

Thanks.

Shane

---

### Post by deanlinkous on 2007-01-25
Try it and see..... :)
IMO all binaries ARE from source and quite likely you would not notice a difference, a benchmark test might but I doubt you would. There probably are arguments for building from source and I am sure some benefits come from compiling the code on the exact machine the code will be run on but I do not feel the time required to build everything would be a reasonable tradeoff.
Seriously though, try it and let us know what YOU think....that is what really matters!

---

### Post by shane2peru on 2007-01-25
Well, I don't know anything about bench testing.  I don't know how I would know if there was a difference either.  I was just curious about about the technical aspect of it.  Besides the fact of I really don't know the proper way to do that.  Are the commands:```
sudo apt-get source package name
``` and then ```
sudo apt-get build package name
```  I may give it a try and remove some of the packages I have and then build them, however my system is very stable, and runs well, I just wondered if that would help cut out some bulk.  Just a thought.  I have compiled a package or two, but by no means would I call myself good at it.  I appreciate the thoughts.

Shane

**EDIT:**  Ok, I removed bluefish since I have just installed it I thought it would be an easy one to learn on.  I ran ```
sudo apt-get source bluefish
```  Next I had to run ```
sudo apt-get build-dep bluefish 
```  and then finally switched to the bluefish directory that had been created, and dpkg'ed the deb file that had been created, and installed it.  I give all that detail because I don't know if that is the correct way of doing things.  I was just guessing and trying.  After all was said and done, I opened the program and it ran fine.  Then Ubuntu told me there was an update, I clicked the update thing, and it said that bluefish had an update.  I updated it, but did that just undo everything I just did?

PS.  I guess my whole question comes from reading about Gentoo, and how they say it is ultra stable, and fast because it is built around your system.  I don't really know.  I tried it once but didn't want to build everything from scratch, -  a lot of compiling!

---

### Post by deanlinkous on 2007-01-25
> **shane2peru said:**
>  I guess my whole question comes from reading about Gentoo, and how they say it is ultra stable, and fast because it is built around your system.  I don't really know.  I tried it once but didn't want to build everything from scratch, -  a lot of compiling!
Interesting isn't it... You can build practically everything from source on debian also if you wish. :)

[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

### Post by shane2peru on 2007-01-25
It seems that everything I build needs updated afterwards.  Does the build stay the same or is it just over written by a new deb?  What exactly is updated?  I'm assuming that building will make things smoother (not that it already isn't smooth.)  It is more challenging too.  I love a challenge.

Shane

---

### Post by deanlinkous on 2007-01-25
Thats strange....been a while since I did anything from source but I do not remember having trouble with it.

---

### Post by shane2peru on 2007-01-25
Ok, this is really annoying.  I have learned how to build the packages by source using apt-get source -b package.  Then sudo dpkg -i package.  I have built 3 packages, and every time afterwards the update notification pops up and it is the package that I have just built.  It also says that the update cannot be verified, and that malicious people could get a hold of my system and wreak havoc etc.   So what am I supposed to do?  I don't understand why everything needs to be updated.  :confused:

Shane

Oh the packages that I have built from source are:  1.  Bluefish  2.  Kopete   3.  Gnome-commander

---

### Post by deanlinkous on 2007-01-29
Sorry, forgot about this thread....
I was thinking about it and was thinking there was something I did to make sure my built packages were not shuffled by upgrades/downgrades.

found this....
[http://www.debian-administration.org/articles/332](http://www.debian-administration.org/articles/332)

enjoy!

---

### Post by shane2peru on 2007-01-30
> **deanlinkous said:**
> Sorry, forgot about this thread....
I was thinking about it and was thinking there was something I did to make sure my built packages were not shuffled by upgrades/downgrades.

found this....
[http://www.debian-administration.org/articles/332](http://www.debian-administration.org/articles/332)

enjoy!

Thanks for the link.  It is  a bit over my head.  I think I will just let Ubuntu do the work for me.   Thanks for the info.

Shane

---

### Post by deanlinkous on 2007-01-30
basically either 
increment your packages
pin your packages
hold your packages

or as you said - let someone else do the work :D

---

