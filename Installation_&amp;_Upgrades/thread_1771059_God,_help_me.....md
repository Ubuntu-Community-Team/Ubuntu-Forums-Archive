---
title: "God, help me...."
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by anonymoususerindenver on 2011-05-30
This is so astonishingly frustrating.  I had a beautifully running installation of Kubuntu 10.10, and then made the incredible mistake of "upgrading" to 11.04.  EVERYTHING broke.  What happened to testing? 

My wireless doesn't work, and I've downloaded the proprietary drivers.  My wired connection is running at such slow speed that it's frightening.  Windows are flaking out--I run a dual monitor, and if I open a browser on one screen, it minimizes the windows on the other screen.  If I click on an application, it minimizes all the firefox browsers.  This happens with VLC, and anyyyy application, it seems.  

This is just what I've found to start....

This should rile the community up, but thank-god the Windows installation on here works perfectly.  

HOW CAN I ROLL THIS POS BACK?  

Dell inspiron e1505

---

### Post by Quackers on 2011-05-30
There is no "rolling back" with Ubuntu. If you want to go back you need to backup what you need then re-install your previous version and restore your data.
It is a good idea to do some enquiries before jumping to a new version - especially when that new version includes major changes, such as Unity.

---

### Post by akand074 on 2011-05-30
> **anonymoususerindenver said:**
> This is so astonishingly frustrating.  I had a beautifully running installation of Kubuntu 10.10, and then made the incredible mistake of "upgrading" to 11.04.  EVERYTHING broke.  What happened to testing? 

My wireless doesn't work, and I've downloaded the proprietary drivers.  My wired connection is running at such slow speed that it's frightening.  Windows are flaking out--I run a dual monitor, and if I open a browser on one screen, it minimizes the windows on the other screen.  If I click on an application, it minimizes all the firefox browsers.  This happens with VLC, and anyyyy application, it seems.  

This is just what I've found to start....

This should rile the community up, but thank-god the Windows installation on here works perfectly.  

HOW CAN I ROLL THIS POS BACK?  

Dell inspiron e1505

Upgrades are pretty much 50/50 on whether you'll get a perfectly working system or complete chaos. I recommend always doing a clean install. You should likely find most of your problems solved.

---

### Post by grege on 2011-05-30
You could try creating a new user then logging into a clean account and see if it is working nicely. If it does work ....

then you need to rename your current /home folder to something else and make a new one.

eg if your user name is fred change /home/fred to /home/fred.old

You will need to run Dolhin as sudo to do this. Open a terminal and type sudo dolphin and put in your password when prompted.

now create a new /home/fred and change the ownership of the folder to fred (right click -> properties -> permissions)

Then log into the new clean fred 

All of you old documents and music etc are still sitting in /home/fred.old but still have ownership fred - so you can just drag and drop (or cut and paste) to the new folder leaving the old config files behind. Enable "show hidden files" in Dolphin and bring across .mozilla if you want to retain your bookmarks etc. Look in .config for Google Chrome. Some program data is in .config and some is in .local

Leave behind all the kde config that is causing issue.

If running the new clean user does not solve the issues then all you can do is back up your data and reinstall. If you are going to do that then I would install Kubuntu 11.04. It runs beautifully on my machine, but then I always do a clean install with new versions.

---

