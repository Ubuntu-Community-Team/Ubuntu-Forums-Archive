---
title: "Issue: Keyboard Layout Bug Ubuntu 10.04"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by rbtman on 2014-01-21
I recently switched from Windows to Ubuntu and installed the spare copy of 10.04 I had lying around. I tend to use a custom phonetic keyboard for the Russian language and went about setting one up for Ubuntu. I edited the /usr/share/X11/xkb/symbols$ RU file to relocate the buttons for my preferable layout - this was rather annoying since the layout picture in Keyboard preferences appears to be a saved image (it is not updated and the cyrillic names for the letters aren't always predictable). To facilitate this installed Xkeycaps - which promised to give a GUI keyboard layout editor. Now the problem with Xkeycaps is the layouts it edits do not appear as separate layouts in Keyboard Layouts but are added as levels 3, 4 respectively to the current layout (which makes it impossible to detect by icon which language one has enabled). 
Unfortunately it seems nearly impossible do undo Xkeycap changes - I tried purge remove, setxkbmap -layout us - but I still have russian letters enabled on levels 3/4 without adding any additional layout. Opening the US symbols file it seems Russian phonetics is fully added onto that file (by Xkeycaps?) - I also suspect the later has messed with the special buttons on the laptop keyboard since Keyboard Layout finds Asus LaptopKeyboard, but Xkeycaps does not display that version and thus maps to a different Keyboard model. 
Optimally I think it would be easiest to simply restore all my model/config/language files to system default settings. How does one go about doing this without Reinstalling the OS? The problem is not pressing - but it is very annoying, since now if one tries to add additional layouts you end up with layout 1 - levels 1,2; levels 3,4; layout 2- levels 1,2; levels 3,4 etc. and thus switching between layouts becomes unnecessarily complicated. As a new user I'm not to fond of the way Linux GUI seems to interact with config files so far...

Edit: I tried switching to Canadian English to get rid of the layout modifications. The CA symbols files is in its original state, but russian letters are still accessed through alt-shift on level 3,4 - even though there should be no connection. 
This is what I get:
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [ca    multix]
 options = []
 model = asus_laptop

&#1072;&#1089;&#1081;&#1092;&#1093;&#1076;&#1075;&#1082;&#1081;&#1072;&#1082;&#1076;&#1094;/#(!()!

---

### Post by mörgæs on 2014-01-21
Hi, welcome to the fora.
10.04 is out of support, so bugs will not be fixed. You will be better off with a fresh install of 13.10.

---

