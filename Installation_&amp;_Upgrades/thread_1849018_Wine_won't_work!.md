---
title: "Wine won't work!"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by yotyoter on 2011-09-23
I installed WINE on my computer not to long ago from the Ubuntu Software Center. I put it on my launcher/dock (still not entirely sure what it's called) and when I go to run it, it won't run because the executable bit is not active and I can't find the folder where I would mark it as executable. 
:confused: If you can't tell I'm a little new to this. HELP!!! :confused:

---

### Post by Toz on 2011-09-23
Wine in and of itself is just a compatibility layer that allows you to run some MS programs under Linux. If you just installed wine, then I believe the only application available is notepad. Did you install another application/game that is not working?

You may also want to consider installing **PlayOnLinux** instead. It's a much more user-friendly front-end to wine. Its available in the Software Centre.

---

### Post by MAFoElffen on 2011-09-23
> **yotyoter said:**
> I installed WINE on my computer not to long ago from the Ubuntu Software Center. I put it on my launcher/dock (still not entirely sure what it's called) and when I go to run it, it won't run because the executable bit is not active and I can't find the folder where I would mark it as executable. 
:confused: If you can't tell I'm a little new to this. HELP!!! :confused:
???  Hmmm--- I've installed it this way on multiple boxes and never had what you are describing...  Rather what you are describing sounds like there was an install error.

I would go back to the software center, remove Wine... when finished > Install.

When it is done, what you should find is a new menu item under Applications > Accessories > WINE...

---

### Post by yotyoter on 2011-09-23
I've installed Play on linux now and it is not the most recent. How do I update it?

Also, how do I completely remove wine to re-install? 

Last question, how do you use wine once you get it working?

---

### Post by Mark Phelps on 2011-09-23
Fourth question you didn't ask -- the most important one -- what will work in Wine?

BEFORE you go to a lot of trouble to install Wine and get it configured properly, do yourself a favor and go to the WineHQ Application Compatibility database and look up the Windows apps and versions you want to run.

If they are not listed, or even worse, if they have ratings of Garbage or Bronze, then installing Wine is going to be a complete waste of time because your Windows apps are NOT going to work.

---

### Post by mocoloco on 2011-09-23
Slow down there dude, are you looking to start using lots of different apps and games, or do you just have a simple exe you need to run?  Wine does just fine for running one or two simple things.

That message about the executable bit was a controversial change in Wine as a security measure.  Since Unix systems determine if a program is executable by it's attributes (not it's extension) wine now requires the same.  Just right-click on your .exe file, in properties set it as executable.  Then double-click it and wine will open it.

---

### Post by Toz on 2011-09-23
> **yotyoter said:**
> I've installed Play on linux now and it is not the most recent. How do I update it?
Go to [http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html"), click on "Ubuntu" and follow the instructions for the version of *buntu that you have.

> Also, how do I completely remove wine to re-install?
From a command terminal, type:
```
sudo apt-get purge wine
```
You can also do this from within the Software Centre.

> Last question, how do you use wine once you get it working?
If you're using PlayOnLinux, simple click the "Install" button, select the app/game (or click the "Install a non-listed program" link and follow the instructions. 

For just wine, have a look at this link: [https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

---

