---
title: "wine"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by fboxall on 2008-10-05
[SIZE="3"]My Windows XP Pro became unbearably slow (probably due to some form of malware) so I installed Ubuntu 8.04 within Windows.  It works well.  However, I want to install Free Rhapsody which does not have a Linux version.  So what do I do?  I think I can install a program called Wine which will enable me to install the Windows version of Free Rhapsody, but I am apprehensive that my limited computer skills may not be adequate to the task. So I welcome any comments, cautions, tips, alternative suggestions, or whatever.[/SIZE]

---

### Post by DrMega on 2008-10-05
If you install WINE from the repositories (using Synaptic, which is in the System->Administration menu, I think you'll find the default setup is about right for most people. Some people tweak it up, but I never had to.

---

### Post by mrtomservo on 2008-10-05
It looks like you'll have to install a couple of dependencies to install Rhapsody in wine.  I found this page that might be of some assistance to you.  It's worth noting that apparently the newest versions of Rhapsody won't work in wine, and you'll have to acquire an older version.

[URL="http://www.amjith.blogspot.com/2005/08/got-real-rhapsody-working-in-linux.html"]
http://www.amjith.blogspot.com/2005/08/got-real-rhapsody-working-in-linux.html[/URL]

Just take your time, and it'll probably be ok.  There's not too much you can do to damage your system playing around in wine.  A couple of times after a failed software install in wine, I just removed the .wine directory in my home folder and started over again.

---

### Post by haydnc on 2008-10-05
I would suggest you check out the wine website and add the repositories for the latest version of Wine.

[www.winehq.org](www.winehq.org)

Then take a look through their AppDB for any information on whatever version of Rhapsody you're trying to install.

The other option is just to install Wine and then give installing Rhapsody a go. If it doesn't work you can have a hunt around the net for instructions or suggestions on how to make it work, and if it does work straight up you've lost nothing and gained everything. 
;)

I can't remember what version of Wine is currently in the Ubuntu repositories so to get the latest advances installing from the WineHQ repositories might be a good plan.

---

