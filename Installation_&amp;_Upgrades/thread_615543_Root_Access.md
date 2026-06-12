---
title: "Root Access"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by calelettus on 2007-11-17
I just installed the GUI for CLAMAV. The virus signatures are way out of date but when I go to update them it tells me it requires root access.

How can I get root access on my machine in order to use this tool?

I can su to root in a terminal window but that doesn't help me with this utility. Thanks.

---

### Post by bthoward on 2007-11-17
Use your menu editor and edit the menu item that you use to launch clam.  Add "gksudo" to the front of it...  

So if it says "clamav --some-option-here"

replace that with "gksudo clamav --some-option-here"

Now when you load it you will be asked for the root password (if it hasn't already gotten this from you on a previous occasion) and all should work for you.

Why are you so worried about having a virus scanner though?  Unless you're wanting to check files for your windows using friends you probably don't have much to worry about.

---

