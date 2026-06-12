---
title: "Clean Up Grub2 Menu"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by iseeuu on 2010-03-25
I want one Ubuntu and one Windows menu entry. How do I do that? Is there already a thread about that I can read?

First I know Grub2 is new ... no problem.
Second I know I can add menu entries and custom entries.
But I do not want to ***_add_*** anything, I want to get rid of all the crap that is there now and leave me with a minimal of menu items!

When I tried to install the [StartUpManager]("https://help.ubuntu.com/community/StartUpManager") it screwed me to the point I had to reinstall Ubuntu. Whenever I tried to update Grub2, it insisted I needed the file menu.lst and would not proceed without it. Therefore, none of my changes to the menu through etc/default/grub or etc/grub.d/40_custom ever had any effect. But editing these files only serves to add more crap to what is already there. I want less not more!

I would very much appreciate some easy tips on cleaning up the Grub2 menu?

Cheers!
Robert

---

### Post by oldfred on 2010-03-25
This is one way:

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

This is what I have done so far:
You can turn off almost all the automatic updating and only have your 40_custom.

I modified mine to only have 2 entires ( added line to script to limit to 2 kernels) and my 40_custom with no auto updates (30 turned off) on other systems - seems to work ok.

ranch hand's custom grub2 
[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553) 
drs305's hack to get hidden timeout to work: 
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by iseeuu on 2010-03-25
> **oldfred said:**
> This is one way:

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

This is what I have done so far:
You can turn off almost all the automatic updating and only have your 40_custom.

I modified mine to only have 2 entires ( added line to script to limit to 2 kernels) and my 40_custom with no auto updates (30 turned off) on other systems - seems to work ok.

ranch hand's custom grub2 
[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553) 
drs305's hack to get hidden timeout to work: 
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) This is an awesome reply! Thanks a bunch! I will take my time to give it all a good look!

Cheers!
Robert

---

### Post by smilingfrog on 2010-04-03
I really like the custom menu section. Much cleaner!

Suggestions:
[INDENT]
Make sure you are running grub 1.97~beta4!
```
grub-install -v
```
This will tell you what version of grub is running. Ironically, my 9.10 boots with 1.97, but due to upgrade/compatbility issues, grub 0.97 was running once booted. This makes using update-grub quite difficult. Use apt-get or synaptic to remove legacy grub and replace it with grub2. You have to manually update grub if you have updated from an older version of Ubuntu.
[/INDENT]

---

### Post by bean123 on 2010-04-03
You can try BURG, it has a feature called folding. With hot-key 'f', you can toggle between normal and folding mode. In folding mode, you can use hot-key F7 to popup a menu with all available items.

---

