---
title: "Help will not load in Gnome, Evolution..."
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by nilou on 2006-11-15
I have Dapper Drake installed on an Thinkpad T43.

When I try to access the Gnome helpsystem I notice a little disc-activity and then nothing happens. F1 does not work either.. same problem. Evolution: same problem.  It seems like all Gnome applications help is not working (except for the links to online help).

I would really apreciate a polite hint about where to start looking, to fix this.

I have tried to install Yelp, but that didn'n bring me any further.
I have also tried to reinstall evolution.  Nothing new.

Kind regards
Michael.

---

### Post by leikao on 2006-11-16
Please set your shutcut keys in the "System -> Keyboard Shortcuts" menu.
And make the F1 key to work in your way.

---

### Post by nilou on 2006-11-16
My shortcut key f1 is set, and working.  In Firefox, the Firefox help pops up immidiately, so I think, there is something else that I have to look for.

Thank You, for Your quick reply.

Regards
Michael

---

### Post by nilou on 2006-11-16
When i choose Help in the menu, Gnome shows: "Starting help" in about 11 seconds, and then it just dissapears, and nothing happens.

Michael.

---

### Post by nilou on 2006-11-16
I have checked the keyboard shortcut and it contained the hex number for f1 key.  So I changed it... an now Firefox help cannot be brought up by pressing f1.  Though Firefox help is still accessible through the Firefox menu.  :o(

---

### Post by leikao on 2006-11-17
Does the "yelp" work fine in your system?

---

### Post by nilou on 2006-11-21
Aha.. 

yelp: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

It seems like many people is getting this problem... it seems to be connected to updating the version of Mozilla Firefox to version 2.0... This obviously removes 'the missing link'

Maybe the solution is to install Mozilla Thunderbird, to make Gnome work???  !!! 

Kind regards,
Michael.

---

### Post by nilou on 2006-11-21
Thunderbird didn't fix my problem... but reverting to Mozilla Firefox 1.5.08 fixed my problem, and updating today's update helped me fix yet another trublesome expirience I had with my wireless wpa2 connection at home.
Finally the networkmanager program seems to have agreed seeing my network without me having to spend numerous retries restarting the network with the command:  sudo /etc/init.d/dbus restart  every time i boot my computer.

Now, I am looking forward to seeing the latest Mozilla Firefox update dump in through the official channel... ;o)

Thanks to everyone who reply'ed helpfully..

I have a kind hope, that someone will some day, teach me the innermost secret of the Gnome/Ubuntu behavior... everyone that I asked for able solutions of this problem I had, (asking nerd's at University of Copenhagen's graded students in computer science running Linux themselves), have told me to scratch the system and reinstall... I thought You did that in the early days, on windows dos og even cpm systems... but.. :( their solution... This is the point that Linux and Ubuntu and others need to work to overcome... I thought we were beyond... ;o)

Kind regards,
Michael.

---

### Post by DonS on 2006-11-22
> **nilou said:**
> 
I have a kind hope, that someone will some day, teach me the innermost secret of the Gnome/Ubuntu behavior... everyone that I asked for able solutions of this problem I had, (asking nerd's at University of Copenhagen's graded students in computer science running Linux themselves), have told me to scratch the system and reinstall... I thought You did that in the early days, on windows dos og even cpm systems... but.. :( their solution... This is the point that Linux and Ubuntu and others need to work to overcome... I thought we were beyond... ;o)


The secret is: Ubuntu / GNOME is complex.  It is hundreds of components working together.  No-one (well, maybe 1 or 2 of the scary people) knows the secrets of all parts of the system.  The best you can hope for is that you find someone knowledgable in the ways of the particular component.  One hint to this is if they tell you to reinstall (without a very good reason), they probably don't know and you should probably look to someone else for help.

Unfortunately, even the best (people who know the component) can get stumped, if information is missing (for example, failing to mention the "upgrade" to firefox 2.0.  Yelp requires the system firefox.  Upgrading outside the repos will break things without a recompile).  It's difficult to know exactly what's relevant, but as you learn more (from using the system) and report bugs, you get an idea.

Also, if you find a bug (i.e. program not starting or crashing) you'll probably get more help using official bug reporting channels (launchpad) as developers are more likely to check there than crawl through the forums looking to help ;)

---

### Post by unisol on 2006-11-22
its just a wild guess but why dont you try reinstalling metacity

---

