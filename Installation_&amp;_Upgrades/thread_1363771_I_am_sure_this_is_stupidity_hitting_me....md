---
title: "I am sure this is stupidity hitting me..."
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by MaDD_TeXaN on 2009-12-24
I am new (obviously) to the linux thing and unfortunately a tech too.. bear with me.. I like the linux experience i am used to STEALING software... THIS IS GREAT... anyway I have tried all the Ubuntu distros on 1 machine (MORON) and have several things good to say about all I started with Ubuntu then went to Kubuntu.. now have Xubuntu and I like this most of all.. I can make it look like windows...(helps the marriage).. anyway how can I disable all the apps I dont want.. mainly the network manger for Xubuntu I can do it manually.. but lets say my wife wakes up at 4am (SHE DOES THAT!!!) and I am sleeping if she reboots everything is FUBAR'D no internet..... please help waking up at 4 is not what I wanna do..(Just going to sleep)..


thanks for any help.....

P.S. THIS FORUM ROX thx to everyone...
Michael

---

### Post by lisati on 2009-12-25
I'm sure many of us here can appreciate the challenges of keeping a harmonious relationship with a "significant other" and keeping your sanity intact when it comes to things technical.

Maybe once you have your system how you like it you can make a backup with [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), making it easier and possibly quicker to recover if you have a matrimonial misunderstanding.

---

### Post by cascade9 on 2009-12-25
One thing you will learn with linux is that there are sometimes lots of ways of doing the one task. 

Probably the easiest way of removing packages is from terminal. But you really need to know the package name- 

sudo apt-get remove *package name*

There several GUI methods of doing this, but the easiest IMO is via synaptic. Theres several ways of doing things just within synaptic, and I'm not going to go through them all (I'm just too lazy) 

Start synaptic, and then click on 'all' in the list (on the far left of the window). Then it will show you all the packages current (on the right hand side). If you scroll down a bit, you will see most of the checkboxes are blank, but some are green. Green = installed. If you click on the top of column that has the blank/green checkboxes, it will restack the the list so that the installed packages are at the top, and uninstalled at the bottom. 

Just scroll down the list till you find the package you want to remove, then click on the green checkbox. A menu will pop up with options. Select the 'mark for removal' box, then click on 'apply (in the section above the list). 

Done! 

BTW, you will find other ways of doing this, its easier to just search for the package (if you know the name) I am suggesting doing it this way as an exercise, so you get an idea of some of the less common, but very powerful ways to use synaptic.   

Also, if you have enjoyed playing with various different ubuntu versons, I would suggest trying a minimal install of ubuntu (especially for xubuntu). Nothing wrong with xubuntu the way it comes, though I dont like how many gnome programs it uses, I perfer to use a lot of the Xfce native programs instead myself. A minimal install uses a lot less RAM than the stock version, and if you enjoy tinkering with your system its nice. Once you have used a few different programs its easier to to get what you like, and setting things up exactly how you want them while not have to remove what you dont like.

---

### Post by kerry_s on 2009-12-25
you can put the commands in a script & ceate a launcher, i did that for my mom as the wireless would drop every now & then, she then just clicked the icon & bam, connected again. :)

---

