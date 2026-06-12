---
title: "problems upgrading to ubuntu 11.04: unity and gnome freezes or won't start"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by laerub18 on 2011-05-07
hi,

i upgraded from ubuntu 10.10 to 11.04, and everything went fine until i rebooted. when i tried to login, the computer just froze (unity as well as ubuntu classic). the only one that worked was the safe mode. 
So what i did next (logging in under safe mode), was installing gnome 3 and i had the same problem with it. i tried some stuff (edited **/etc/default/grub** and typed in **sudo grub-mkconfig --output=/boot/grub/grub.cfg**) to make gnome 3 work, but now when i try to log in, i get a "failed to load session 'gnome' error message.

i still have access to a terminal

my computer i an asus eeepc 1001PX, my graphics card is Intel corporation N10 family Integrated Graphics controller

i would like not having to erase all the disk and reinstalling ubuntu if possible :)

hope you can help !!

---

### Post by Not unique on 2011-05-07
It sounds like maybe your video card is not enough for Unity 3d, It should take you to the log on screen where at the bottom it will have an option for normal Ubuntu mode OR you could install Unity 2d via safe mode that worked for me.

---

### Post by Not unique on 2011-05-07
Unity 2d PPA for Maverick: 
deb [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu) maverick main


Unity 2d PPA for Natty: 
deb [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu) Natty main 
deb-src [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu) Natty main

OR type these into your terminal + press enter for Natty:
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily
sudo apt-get update
sudo apt-get install unity-2d-default-settings

Hope this helps should be better than Gnome 3d.

---

### Post by rubbershirt on 2011-05-07
I upgraded from 10.1 to 11.4 recently too.  When I start up, the BIOS screen lists "Ubuntu with Linux 2.6.38.8 generic" on top.  If another option is not selected from the list, the start up process simply fails - going to a purple screen (I haven't actually left it long enough to see how long it would take maybe eventually to take me to the desktop).  So I soft re-booted, and next time selected "previous versions" from the BIOS list and then can start up successfully.

I note also that in system, my current version of Ubuntu is Release 11.04 (Natty) 2.6.35-28, and not what appears at the top of the BIOS list?

At the moment it is manageable but a bit of a pain!  Any way I can improve the situation, or even revert to 10.1??

---

### Post by Not unique on 2011-05-07
rubbershirt can you get in at all ?
and do you actually mean the BIOS or the GRUB screen for dual booting ?

---

### Post by rubbershirt on 2011-05-07
Yes - but I have to select "previous" versions" in the set up screen.  This takes me to what I thought was / is the current version (i.e. 11.04).  At the top of the set up screen is this 2.6.38.8 generic version - that is what stalls and wont start up.

---

### Post by rubbershirt on 2011-05-07
Mmmm, you can probably tell I'm a bit new to Ubuntu!  Probably the Grub screen.........

---

### Post by Not unique on 2011-05-07
Thats cool no ones born with knowledge you've gotta learn ya know,
Well I always use Ubutu tweak to clean up (Like Ccleaner for Windoze) but it's a bit middle to pro so try the built in cleaner first at system - administration - Computer Janitor.

Edit---

Hold on sorry can I have more info first before you do anything i.e. was it new install or updated from Ubuntu 10.10?

---

### Post by rubbershirt on 2011-05-07
Updated from 10.10

---

### Post by smithcts on 2011-05-07
Having a very similar issue. Boot stalls at the Ubuntu splash screen (I've left it there for over 5 mins. It never sent me to the desktop). Mouse operates but system will not recognise a CTRL-ALT-DEL. Hit the reset button and it boots normally. Its done this 3 or 4 times now. Upgraded from 10.10.

When we get to some serious troubleshooting, will be happy to contribute. Just in case, is there a tutorial on how to downgrade to the previous version? Is it possible?

---

### Post by Not unique on 2011-05-07
OK yeah you also updated your Linux headers etc. (whatever they exactly are) and it leaves the old ones I have always used Ubuntu tweak to clean these up automatically with no fuss.
To install easily download it from the main Ubuntu tweak site and double click (you know the drill) then go to the cleaner tab on left and then the kernel tab on the right to clean the old kernels up this should hopefully sort it as it has always worked for for years now

Its about time some more time was spent on grub for dual booters to help wean people over to Ubuntu.

---

### Post by Not unique on 2011-05-07
Let me know how it goes (for others to look at for future advice) rubbershirt
and sorry for highjakking your thread laerub18

---

### Post by Not unique on 2011-05-07
I'm looking for a file on downgrading now but personally I just re installed Ubu 10.10 CLEAN only took 30 mins and every thing is fine again there&#8217;s nothing new to Ubu 11.04 for me and if you want Unity try Unity 2d especially if you have aN older or inbuilt/on-board video card.
Ubuntu 11.04 is the worst Ubu yet after 5-6 years of ubu use I'm sad to say, but not having a good video card doesn't help.

Ubuntu downgrade help:   [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

Also refer to this for a little more info:   [http://ubuntuforums.org/showthread.php?t=284111](http://ubuntuforums.org/showthread.php?t=284111)

---

### Post by laerub18 on 2011-05-07
not sure the graphics card's too weak. ubuntu normal mode did not work either, i had the same problem. i know the card can run the normal mode as ubuntu 10.10 was running perfectly.

now i've install gnome 3 (through the PPA) so i don't have the unity 2D option anymore, only 'ubuntu', 'ubuntu gnome shell desktop' and 'user defined session'
and none of them work; i get the 'failed to load session ' error.

i read somewhere else reinstalling the graphics card driver could help, any idea how i would do that ?

---

### Post by laerub18 on 2011-05-07
> **Not unique said:**
> I'm looking for a file on downgrading now but personally I just re installed Ubu 10.10 CLEAN only took 30 mins and every thing is fine again there’s nothing new to Ubu 11.04 for me and if you want Unity try Unity 2d especially if you have aN older or inbuilt/on-board video card.
Ubuntu 11.04 is the worst Ubu yet after 5-6 years of ubu use I'm sad to say, but not having a good video card doesn't help.

Ubuntu downgrade help:   [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

Also refer to this for a little more info:   [http://ubuntuforums.org/showthread.php?t=284111](http://ubuntuforums.org/showthread.php?t=284111)

well the advantage of 11.04 is being able to install gnome 3 :) which IMO is better than unity and looks pretty nice

---

### Post by Not unique on 2011-05-07
If you REALLY want Ubuntu 11 with Gnome3 then the only advice I have is to reinstall video drivers like you said but if you cant get in how would you do that? 
Can you access safe mode?

---

### Post by laerub18 on 2011-05-07
yeah i've got acces to a terminal, after installing gnome 3, i have a recovery console option at login

---

### Post by rubbershirt on 2011-05-07
> **Not unique said:**
> Let me know how it goes (for others to look at for future advice) rubbershirt
and sorry for highjakking your thread laerub18

Brilliant - that certainly seems to have solved the problem!  Although in the clean kernels tab, there was nothing listed to clean.  I think I cleaned the relevant linux kernels from the clean config tab?  As I said - I'm new to this!  Thanks again.

---

### Post by MAFoElffen on 2011-05-07
> **laerub18 said:**
> hi,

i upgraded from ubuntu 10.10 to 11.04, and everything went fine until i rebooted. when i tried to login, the computer just froze (unity as well as ubuntu classic). the only one that worked was the safe mode. 
So what i did next (logging in under safe mode), was installing gnome 3 and i had the same problem with it. i tried some stuff (edited **/etc/default/grub** and typed in **sudo grub-mkconfig --output=/boot/grub/grub.cfg**) to make gnome 3 work, but now when i try to log in, i get a "failed to load session 'gnome' error message.

i still have access to a terminal

my computer i an asus eeepc 1001PX, my graphics card is Intel corporation N10 family Integrated Graphics controller

i would like not having to erase all the disk and reinstalling ubuntu if possible :)

hope you can help !!
To all jumping in with this problem-  Please, slow down and back up... Seems like you are rushing, installing "more" and adding to problems.  You may or not be able to run Unity 3D or Gnome 3, but we don't know that yet, right?  Installing different and alternate desktops is not going to change your graphics "not displaying," if that is the problem.

Your "original" problem was a suspected kms problem that could have been diagnosed and corrected here:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Once your video problems are resolved enough to get a GUI, then you can figure out whether it will run untiy or not right?  (Unity compatibility utility).

Please visit the sticky (above) and follow the troubleshooting flowchart to see what is working -- and what is not.  There is lots of info there and lots of things to try, without going in blind or adding more problems that you might have to back out of.

---

### Post by laerub18 on 2011-05-10
okay i reinstalled ubuntu 11.04, and it works, IF wifi is disabled. During the ubuntu installation, if i tried to connect to the internet, it would freeze, so in installed it offline. Now if i try to connect, the computer just goes into text console and says something about a kernel panic. ethernet connection is not a problem, just wifi.

so probably the reason why earlier the computer froze when i logged in and not before, is that it tried to connect to the internet. Since i did an upgrade, it had saved all connection data and could do it automatically. So to others experiencing that problem, before logging in, disable wireless first.

plus i know it is not about the video card not bieng able to run unity or gnome 3, since unity now works after clean install, and i tried a liveUSB of the new fedora which comes with gnome3 by default, and it runs perfectly (once again with wireless turned off)

**tl;dr   :  the wifi driver causes a kernel panic.**

the wireless card in cause is the atheros card (for me at least, maybe people with other cards are experiencing the same problem)

from what i read, unlike in previous versions, ubuntu 11.04 comes with a driver for atheros cards, and obviously it's not functionnal.

okay so the new question is how can i delete the native driver, and install another ?

---

### Post by laerub18 on 2011-05-10
hurray problem fixed !

solution : install this (kernel 2.6.38-9-generic) [https://launchpad.net/~kernel-ppa/+archive/pre-proposed?field.series_filter=natty](https://launchpad.net/~kernel-ppa/+archive/pre-proposed?field.series_filter=natty)
 thanks to all who helped !

---

