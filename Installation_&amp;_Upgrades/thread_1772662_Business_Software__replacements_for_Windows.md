---
title: "Business Software / replacements for Windows"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-05-31
Well, all of those in business know that we will never be able to completely dispose of Windows - Linux just doesnt support business that well, as there arnt the number of users.

However, does anybody know of any packages (free or commercial for Ubuntu) that will replace any of the following:
email maketing similar to Group Mail (Windows)
web stats program like Web Position (Windows)
web button design tool like Xara Webstyle (Windows)

Also, are there any shopping carts out there that work like Actinic? OK, I know there's oscommerce and Zen Cart, but they are a setup nightmare compared with Actinic for setting up ecommerce sites, albeit they are free (which is always good).

Thanks.

---

### Post by linuxinstalledfromhdd on 2011-05-31
You may want to try it in Wine and install those windows applicaitons in Ubuntu, if you really need them. Here is a guide to playonlinux to get you started:

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

---

### Post by SeijiSensei on 2011-05-31
There are a number of alternatives for summarizing Apache logs to determine web usage patterns.  My favorite is [analog]("http://www.analog.cx/").  [Awstats]("http://awstats.sourceforge.net/") also has an excellent reputation.

I haven't a clue what web server software you're running, but if you're on Windows it's probably IIS.  I don't know what kinds of logs it writes, but to use the packages I mentioned the logs generally need to be in the "common log format."  Even if you stick with Windows, you might want to give Apache a try.

---

### Post by Mark Phelps on 2011-06-01
Personally, I would recommend against using Wine, or any of its add-ons, if you're really trying to migrate AWAY from MS Windows.  Installing MS Windows apps using Wine just continues the dependency, and in nearly all cases, the Wine version does NOT support all the features that folks are accustomed to using in MS Windows.

If you want to do some research, go to the WineHQ website and use their search tool to look through their compatibility ratings for the Windows apps you want to replace.  If you see Platinum or Gold ratings, then Wine will work fairly well for you.  Anything less (IMHO) is a waste of your time.

---

### Post by geidorei on 2011-06-04
Hi - for the time being I use the windows programs via VirtualBox - wine has proved be less than useless for the windows software i am using, and very buggy too. Leaves loads of dependencies when you uninstall anything.

Re webstats will have a look at analog. Awstats.

My main issue is email marketing - there is something called JPEE, but have to play with it - it is a commercial product £23.99 but that isnt an issue.

---

### Post by geidorei on 2011-06-04
Hi - for the time being I use the windows programs via VirtualBox - wine has proved be less than useless for the windows software i am using, and very buggy too. Leaves loads of dependencies when you uninstall anything.

Re webstats will have a look at analog. Awstats.

My main issue is email marketing - there is something called JPEE, but have to play with it - it is a commercial product £23.99 but that isnt an issue.

---

