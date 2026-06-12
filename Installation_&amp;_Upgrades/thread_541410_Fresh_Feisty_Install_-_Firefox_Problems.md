---
title: "Fresh Feisty Install - Firefox Problems"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by odel0022 on 2007-09-02
I just recently installed Feisty on a fresh partition and dual booting with XP.  When I loaded up firefox, mozilla.com and google.com loaded just fine, as well as the results of any searches I did.  However whenever I tried to navigate to digg.com the system just hung there doing nothing.  I did a ping in terminal to digg.com and it there was a response, so I believe it is a software issue rather than a network problem since i could go to google and use gaim as well.  

I searched and found a few similar cases which had me "about:config" and change the default ip6 settings but to no avail.

In addition to my firefox frusterations, it seems that the fiesty servers may being overloaded because i cannot use my update-manager, nor any apt-get from my sources.list without it hanging.


Any suggestions?

---

### Post by merlinus on 2007-09-02
Holiday weekend = lots of traffic.

Hurry up and wait....

-merlin

---

### Post by odel0022 on 2007-09-02
I was able to upgrade no problem on my feisty install on my desktop for my repository lists and firefox website problem.  Should I try another installation of feisty?

---

### Post by merlinus on 2007-09-02
So if you were able to upgrade and fix your firefox problem, why do you want to reinstall?

-merlin

---

### Post by odel0022 on 2007-09-02
i meant on my 2nd desktop the fiesty apt-get and firefox worked mine...but on my primary desktop i cannot resolve those issues

---

### Post by merlinus on 2007-09-02
You can alsway uninstall firefox completely using Synaptic, and then reinstall it.

But if apt-get is not working for anything, then I would agree that perhaps your installation did not go as it should.

You might look at /etc/apt/sources.list, however, to see if anything there seems untoward.

-merlin

---

### Post by odel0022 on 2007-09-03
the sources.list is fine....i even copied the same list from my other desktop running feisty but still didn't work.  I am also wondering if possibily if its an issue that I am giving this computer internet access through Windows Internet Sharing on my laptop (via wireless from laptop, crossover cable to Feisty Desktop) since I haven't quite figured out my DLink USB Wireless adapter for this machine.

I was reading through the forums and came across yet a another similar problem in which the firewall was blocking come transmission, but the user provided no solution just "i reconfigured my firewall and problem was fixed."  I am running both my Fiesty Desktops off the same network router, so it shouldn't be a hardware problem.

I will do a fresh install of feisty, if not I will install dapper, and upgrade like I did with my 2nd desktop.  I will post any updates.  Thanks!!

---

### Post by odel0022 on 2007-09-04
EDIT - Could it be a problem that i am giving my ubuntu desktop internet access via Window Internet Sharing from my Windows XP computer.  My router is too far away to connect with a ethernet cable, and just for the time being I am using WIC.  I  plan on using my USB DLInk wireless adapter on my ubuntu desktop once i get updates and ndiswrapper installed and working correctly on my ubuntu machine

---

