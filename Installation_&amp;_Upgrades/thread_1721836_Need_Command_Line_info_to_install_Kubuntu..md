---
title: "Need Command Line info to install Kubuntu."
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Pepse3 on 2011-04-05
For reasons unknown I cannot install Kubuntu 8.04LTS.  When I run the Live CD and click to install it gets me the box that should show me my hard drives and possible partitions but the box is empty.  I get the same when booting to the Live CD and clicking on install.  I have had this CD since Kubuntu 8.04 was released.  So not knowing what might be wrong I figure I will ask here for what to type in a command line to install it.  I know it is an old version but it is the last one with KDE 3.5.  I really do not like KDE 4.x

Pepse3.

---

### Post by mörgæs on 2011-04-05
Like it or not, you will soon have to upgrade, since 8.04 is running out of support in a month.

---

### Post by snowpine on 2011-04-05
Can you browse to your hard drive in the Places menu?

Check out the Trinity Project for how to use KDE3 in Lucid/Maverick: [http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)

Support for 8.04 ends this month.

---

### Post by Pepse3 on 2011-04-05
Wow, I like the option of this Trinty.  I did a quick read but heck if I can get me a CD of Maverick with KDE 3.5.xx it will keep me up to date with Buntu and still have my KDE 3.5.xx.  Great, thanx.

Pepse.

---

### Post by Pepse3 on 2011-04-06
Snowpine, No I can't see any hard drives in the Places menu.  I had 2 hard drives hooked up and nothing shows.

Pepse.

---

### Post by Quackers on 2011-04-06
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mastablasta on 2011-04-06
what is so different in KDE 3.5? 
 
Did you know classic look is also possible in 4.x? If main menu is bothering you just right click K and select classic menu.

---

### Post by Pepse3 on 2011-04-11
First to answer mastablasta; I've been aware of "Classic Mode" ever since KDE 4.1 .  All I ever noticed is the KDE Start icon and such are like KDE 3.5.xx.  I do not care for the Plasma Desktop and its doo-dads.  I have always used 4 windows, each with its own wallpaper; can't do that with KDE 4.x.  Other than those items I think it would be okay.

  Now for snowpine;  I went to and downloaded and installed Trinity's Kubuntu Maverick 10.10.  So far I am happy with it.  I got a couple bugs with it but I plan on joining their forum and get at least 1 bug fixed.  And  the GRUB sees my windows 7 HDD and I can access it like I did when I had win XP.

  This is what I like.  A newer Kernel with the KDE 3.5.x desktop.

Later.  Pepse.

---

