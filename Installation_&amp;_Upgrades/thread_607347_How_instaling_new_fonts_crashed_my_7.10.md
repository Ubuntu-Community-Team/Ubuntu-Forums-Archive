---
title: "How instaling new fonts crashed my 7.10"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by cchevy on 2007-11-08
I wanted to install some fonts from windows and i got my folder for install. quickly i figured that there was no way of installing them easy, so i read around and did this:

Alt-F2 to open the run dialog

**fonts://**
> 
The window that opens allows you to copy and paste new font files to install them.

as mentioned in [http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/](http://tombuntu.com/index.php/2007/10/15/how-to-install-fonts-in-ubuntu/)

and i did this and my pc froze. there weren't many fonts. i restarted and got nothing but wallpaper and NO menu. empty ubuntu...

please tell me i can fix this? why is it so hard to install new fonts?

can anybody tip me how to fix my system and install fonts ?

i am writing this post from xp and this is really embarrassing :(

---

### Post by bulldog on 2007-11-09
I only can advice to roll back your install [copy] action.
To install fonts:
Open synaptic and type in the searchbox:  msttcorefonts
Install this package and done.

---

### Post by cchevy on 2007-11-09
The thing is i did not have a menu, so no synaptic. I found a solution from the recovery mode terminal:

go to /home/username/.fonts

rm *.ttf or *.TTF

now i can work on my ubuntu, but still can't find a solution to install some other designer fonts...

cheers

---

### Post by bulldog on 2007-11-09
Go to add/remove applications in your menu.
At the top right enable all available applications,top option I use a Dutch version.
Refresh,so it load all applications and type in the search box msttcorefonts ,this should list one package with windows fonts,install it and here you go.

---

### Post by cchevy on 2007-11-09
i had this package before...what i want to do is to install some other macedonian fonts that i had in windows (ttf)

so when i did this my ubuntu crashed and i had to remove them

---

### Post by bulldog on 2007-11-09
This is all I know of fonts I'm afraid,it's sufficient to me,but there should be someone who can help you with more fonts I suppose.
Did you have a look at the tips and tricks forum?
Maybe it's posted allready,
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

[http://ubuntuforums.org/forumdisplay.php?f=16](http://ubuntuforums.org/forumdisplay.php?f=16)

---

### Post by scrooge_74 on 2007-11-09
All the fonts you can installed are in the repositories, but if you dont see them then you need to enable the other repositories.

And I don't think that method for installing fonts is a good one, you should always install things that come in a .deb package to avoid problems

If you can't find synaptic which should be in Admin>System (I am using Xubuntu so dont quite remember) then open a terminal and type gksudo synaptic.

In there there are a couple of fonts packages which start with xfonts-cronyx-isocyr-xxx which says they have support for Macedonian, Russian, and other Cyrillic fonts

---

