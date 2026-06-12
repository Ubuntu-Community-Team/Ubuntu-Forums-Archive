---
title: "Firefox 2.0 kills internet"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by cjm5229 on 2006-10-29
As soon as I updated my Edgy Partition to Final Firefox started shutting down my Internet connection, DSL, with three other computers in the network. It just disconnects mine. I have to reboot to get back online, I installed Mozilla Browser, it works well. I used it to download Iceweasel, which also works great. I then Downloaded the Firefox 2.0 from Mozilla, and I have no problem with it either, but if I click on the system version, it stops my connection dead in it's tracks. stops downloads, updates, everything.  I did a complete clean install including the home partition. It is exactly the same. Edgy's Firefox doesn't work, everything else does. I filed a bug report, but I have not seen anyone else with this problem. Anyone else have it, or know how to fix it? It's not a show stopper for me because I still have Dapper on my main Partition, but I sure would like to fix it before I update that one and get this partition ready for Feisty Fawn.:-D
Carl

---

### Post by eeried on 2006-11-10
So the problem is with Edgy.

I installed FF2 manually from mozilla.com and absolutely no problem.

Edgy seems to have some bugs but they'll probably be solved as you update. I'm sticking with Dapper for a little longer-- I'll probably wait until Feisty...

I think the adjectives chosen for these two versions are revealing!

---

### Post by cjm5229 on 2006-11-10
Yes, the problem is Edgy's  version of Firefox. I have 2.0 installed manually in Edgy also and it works OK. The Ubuntu version is working sometimes now, but sometimes it will kill my internet connection on my entire network. We have four computers hardwired to my Verison DSL modem and all four will shutdown when it does it. I have to reboot my computer to fix it. Logging out and back in does not work. It's a complete mystery to me. It has to shut something down in my modem, but I have no clue how it can. It's a Westell DSL modem.:confused: I keep hoping an update will correct it soon. Other than that though, I have  no problems at all with Edgy. Works great on both my eMachines and my wifes blueberry Imac.  Her Firefox does not disconnect the modem, so I think it must be a compatability thing somewhere in my eMachines. Iceweasel works so well though that I don't even bother with Firefox 2.0 anyway. ;) I haven't heard of anyone else haveing this problem so it is apparently a very rare jssue.

---

### Post by bulldog on 2006-11-10
Did you try to remove your profile and create a new clean one?

I had some trouble with firefox and this solved my problems.

---

### Post by cjm5229 on 2006-11-13
Bulldog, 
Thanks, That worked. I wonder what it is that causes that.:confused: Anyway, I appreciate the help on that one.

---

### Post by AiBo on 2006-11-19
Ok,

Firefox 2.0 crashes quite frequently on my Edgy upgrade (though now my skype finally works properly AND i can type in Chinese and English ... another topic, but WA-HoO).  Actually it is my only complaint on Edgy.  Had to fall back to using Opera.  I would love to try resetting my profile, but do know how to do it.  Can anyone give me a heads up on how it is done?

> **cjm5229 said:**
> Bulldog, 
Thanks, That worked. I wonder what it is that causes that.:confused: Anyway, I appreciate the help on that one.

---

### Post by bulldog on 2006-11-20
Got to your /home folder and under tab view click show hidden folders.
Find the .mozilla folder,right click it and rename it to what ever you want.

Open firefox and it creates a brand new profile for you.
You have to import your bookmarks again so make a backup before you delete the  renamed .mozilla.

Just give it a try.

---

### Post by AiBo on 2006-11-20
Bulldog,

Thanks for the help.  It appears to working.

---

### Post by craiglarry on 2006-11-20
My problem not exactly the same, ubuntu 6.06 partially upgraded to Kubuntu, don't ask me why partial, I don't know. I installed firestarted firewall and I was dead in the water. Had to shut fstarter down to go online. Same thing with downloader d4x. If you don't load them internet is fine. Might check the relationships of these utils to firefox. 

> **cjm5229 said:**
> As soon as I updated my Edgy Partition to Final Firefox started shutting down my Internet connection, DSL, with three other computers in the network. It just disconnects mine. I have to reboot to get back online, I installed Mozilla Browser, it works well. I used it to download Iceweasel, which also works great. I then Downloaded the Firefox 2.0 from Mozilla, and I have no problem with it either, but if I click on the system version, it stops my connection dead in it's tracks. stops downloads, updates, everything.  I did a complete clean install including the home partition. It is exactly the same. Edgy's Firefox doesn't work, everything else does. I filed a bug report, but I have not seen anyone else with this problem. Anyone else have it, or know how to fix it? It's not a show stopper for me because I still have Dapper on my main Partition, but I sure would like to fix it before I update that one and get this partition ready for Feisty Fawn.:-D
Carl

---

### Post by AiBo on 2006-11-27
Update:

Firefox is still crashing.  It seems to be crashing on any website that has anything beyond straight html ... flash, java, etc.  all causes firefox to crash.  wish i had more time to look into it, but work has been keeping me too busy.  does anyone know a simple command line that will allows me to revert back to firefox 1.5?

---

### Post by cjm5229 on 2006-11-29
I don't think you can revert to FF 1.5. But you can install Iceweasel, Which is FF1.5 only all FOSS.  Go here,  [http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)
Download the file. unzip it to the folder of your choice. I created an Icewasel folder in my Home file, Open the file and you will see an executable file named "iceweasel" using "edit menus" create a shortcut to that file and you have Iceweasel installed. I haven't had any problem with 2.0 since I removed my profile and let it install a new profile.
Good luck.

---

### Post by mdognrdog on 2006-11-29
Huh.  This whole time, I never realized Firefox was the culprit.  I still have no idea HOW it could be doing it, but for days -- almost ever since the Edgy upgrade -- I've been losing my connection to the router every five minutes.  After reading this thread, and going to Epiphany, it's solid as a rock.

I can't believe they shipped a browser that does something like this.  What are they, Microshaft?

---

