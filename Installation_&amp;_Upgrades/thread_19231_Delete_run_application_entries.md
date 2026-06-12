---
title: "Delete run application entries"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by Wombat on 2005-03-11
Does anyone know how I can delete non used entries in the drop down menu in run applications box.I can find no file where they are keep,Also I downloaded the 2.6.11k7 kernel to fix the auto shutdown problem,which it did,but now I can't use the printer and it works if I boot into the original i386 kernel,Thank you,Wombat

---

### Post by bored2k on 2005-03-11
[QUOTE=Wombat]Does anyone know how I can delete non used entries in the drop down menu in run applications box.I can find no file where they are keep,Also I downloaded the 2.6.11k7 kernel to fix the auto shutdown problem,which it did,but now I can't use the printer and it works if I boot into the original i386 kernel,Thank you,Wombat[/QUOTE]
 In warty you just enter applications:/// or in a terminal nautilus applications:///.

---

### Post by Wombat on 2005-03-11
Bored2k,
I don't want be ignorant,but this shows me the same as the application drop down menu.What I am after is the file that the things you type into the "run applications " box,they stay there in the drop down menu,and this is what I want to get rid of,Thanks,Wombat

---

### Post by bored2k on 2005-03-11
[QUOTE=Wombat]Bored2k,
I don't want be ignorant,but this shows me the same as the application drop down menu.What I am after is the file that the things you type into the "run applications " box,they stay there in the drop down menu,and this is what I want to get rid of,Thanks,Wombat[/QUOTE]
 Oh! Im sorry I thought you meant the applications tab in the upper panel, my bad dude/gal/mpaa agent.

---

### Post by Wombat on 2005-03-11
bored2k,
Does this last answer mean you don't where the entries are keep,be patient with me as I am still learning.I use Simplymepis on the other pc and these entries were in a hidden file called".kde",Thanks Wombat

---

### Post by bored2k on 2005-03-11
[QUOTE=Wombat]bored2k,
Does this last answer mean you don't where the entries are keep,be patient with me as I am still learning.I use Simplymepis on the other pc and these entries were in a hidden file called".kde",Thanks Wombat[/QUOTE]

Im afraid to say I don't know where is it stored.

I am looking for it as we speak, but chances are I wont get lucky. If i do find it, ill post back.

---

### Post by Wombat on 2005-03-11
bored2k,
Thanks as I have looked every where,even doing a google,with no luck.They have to be keep someplace.I like to run ubuntu over mepis as it is faster,Mepis uses KDE.And if you run into a answer on the k7 issue with the printer,you can  tell me how to fix.I'm thinking of going to i686 kernel but don't know if that shuts down like it supposed to,again thanks,Wombat PS I live in Boise,Id

---

### Post by bored2k on 2005-03-11
I **found** a solution :D

gconf-editor 
apps > gnome-settings > gnome-panel > history-gnome-run
double clic on it, and delete as desired !

---

### Post by Wombat on 2005-03-11
Muchas grasis,
That has been bugging me,as I could see it gettting a mile long.I saw this other thread and I might do a reinstall of the k7 kernel later on to see if that does anything.Again thanks for all your help,WombatPS bored2k in the same place ie the search box history ,so I deleted those as well,thanks

---

### Post by bored2k on 2005-03-11
[QUOTE=Wombat]Muchas grasis,
That has been bugging me,as I could see it gettting a mile long.I saw this other thread and I might do a reinstall of the k7 kernel later on to see if that does anything.Again thanks for all your help,Wombat[/QUOTE]
 Trust me, I helped myself there. I had been looking for this forever!

BTW, its Muchas Gracias ;).

edit > I just wanna point out how cool people on this forum are. I had to take an insult from a looks-like elite user on mIRC in order to get help :( .

---

### Post by Wombat on 2005-03-11
I can speak a little Spanish.but spelling is another story,now I know.And yes people are very differant here as in a good way.Now if you ever find out how to turn off that root file check at boot time ,which is default every 30 start ups,I would like it to do it every 30 days like Mepis does,Have a good night ,wombat

---

### Post by bored2k on 2005-03-11
[QUOTE=Wombat]I can speak a little Spanish.but spelling is another story,now I know.And yes people are very differant here as in a good way.Now if you ever find out how to turn off that root file check at boot time ,which is default every 30 start ups,I would like it to do it every 30 days like Mepis does,Have a good night ,wombat[/QUOTE]
 Every 30 boots is reasonable in my opinion. Its good the system has auto maintenance. Every 30 days might as well be 200 boots, or just 5. But if you want to change it ... well I dunno I let my Noir do its work :P

---

