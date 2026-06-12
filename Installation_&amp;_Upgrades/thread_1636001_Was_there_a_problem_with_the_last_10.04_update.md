---
title: "Was there a problem with the last 10.04 update?"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by dvfreelancer on 2010-12-02
Ever since the last round of updates on Lucid my system performance has been dismal.  Chrome performance has tanked, internet connection is now sketchy where it flew a couple days ago.  

Any way to undo an update and see if it's related to the update or some coincidental internet issue?

---

### Post by Crazedpsyc on 2010-12-02
To downgrade a package just open the Synaptic Package Manager, choose the package, open the package menu, and select Force Version. Then choose a lower version there, click OK and finally apply the changes.

I have a fully updated 10.10 and everything is fine for me, so I don't know what happened to yours

---

### Post by dvfreelancer on 2010-12-02
The menu option is there but it's greyed out. And I can't tell what I'm forcing.  The package manager doesn't seem to list out the updates to roll back.  It's just showing me individual applications. 

Lost audio as well.  Chrome has started giving me all kinds of problems.  This is really annoying.

---

### Post by Crazedpsyc on 2010-12-02
Hmm, Well the grayed out part is because the particular package you selected has not been updated at any point. Just search for the package you think is causing the problem (possibly Chrome itself) and the menu option will become available. While you're in the package manager search for and install "padevchooser" (Pulse Audio Device Chooser) to help diagnose and fix the sound problem
Finally, post the output of
```
lspci
```in a CODE block (like "[ CODE ] output [ / CODE ]") (without the spaces)

if chrome just updated, try uninstalling it and install something like midori or firefox to see if that helps

---

### Post by dvfreelancer on 2010-12-03
Looks like I'm not the only one having problems:

[http://www.reddit.com/r/Minecraft/comments/efuhm/anyone_else_running_into_problems_on_ubuntu_after/]("http://www.reddit.com/r/Minecraft/comments/efuhm/anyone_else_running_into_problems_on_ubuntu_after/")

I had to power down my machine and unplug it to get the internet connection working again.  Restarting didn't work, power cycle without unplugging it didn't work.  

Something in that last update was not good.

---

### Post by Crazedpsyc on 2010-12-03
Can you contact ubuntu with your system specifications, or file a bug report then?
I fully updated my 10.04 system and have no such problems. Do you have any extra repositories enabled? What about the pre-released or unsupported updated in the software-sources gui?

---

### Post by dvfreelancer on 2010-12-03
Every time I've done that has been a waste of time.  Here's how it goes.  I spend my time filling out a bug report and gathering information.  Don't hear anything for weeks.  Then the Ubuntu developers blame another piece of software and close the issue. 

Big waste of time.

---

### Post by Crazedpsyc on 2010-12-03
> I fully updated my 10.04 system and have no such problems. Do you have  any extra repositories enabled? What about the pre-released or  unsupported updated in the software-sources gui?Just making sure you see that :)

If you do try checking what updated in those in the past few days.
You should be able to find the history in Synaptic Package Manager>File>History

---

