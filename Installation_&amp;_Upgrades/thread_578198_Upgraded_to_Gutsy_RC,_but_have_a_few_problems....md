---
title: "Upgraded to Gutsy RC, but have a few problems..."
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by onero on 2007-10-17
Whee, I upgraded to the Gutsy RC last night! Took some time though, and sometimes it asks for user input during the upgrade, so it can't be left unattended. Things worked out fine for the most part; I lost my compiz fusion settings, but I don't really mind. There are some minor bugs that I encountered, though:

1) The Appearance dialog opens, but is non-responsive and I can't really do anything with it. I click on the tabs, but nothing happens. The only button that works on the dialog for me is "Close" :)  Does this have anything to do with having compiz-fusion / ccsm enabled, or is this a known problem? If so, any suggested fixes?

2) I can't find the new user switcher applet to add to my panel, it's not in the list of applets :( How do I get it?


Like I said, I only upgraded yesterday so I haven't tested everything, but these are what jumped out at me. [For the most part, though, Gutsy is working pretty well, and I appreciate the GUI tweaks and suchlike :D]. 

Anyway, any suggestions? Do you guys need any logs for me to post? Thanks a lot!

---

### Post by onero on 2007-10-17
Did some searching, and I found a bug that sounded similar to what I was experiencing for the Appearance dialog, and they said it was fixed by removing the gtk-qt-engine package. I haven't tried it yet because I'm not at home, but I'll try it when I get back.

---

### Post by rogerp1 on 2007-10-18
I removed the gtk qt engine and this solved the problem with the tabs in "appearance".

The only other problem Uve come across is that my USB MP3+ soundblaster no longer works.

It didnt work very well in Feisty either but now it doesnt work at all!

I'll wait a few weeks to see what updates do though

---

### Post by onero on 2007-10-18
Yup, removing that package did solve it :D And I just installed the fast-user-switch-applet. Gutsy is working out great for me now :D

---

