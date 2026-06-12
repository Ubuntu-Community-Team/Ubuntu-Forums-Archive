---
title: "amarok 2 beta"
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by awakatanka on 2008-09-10
If i scan my collection of my usb hdd ( ntfs, need it in xp to ), it scan fine. I see artist name, i see album. But what i don't see is track names and can't play them. But if i load them with the file option it plays and show track information. Anyone got same problem? can't find bug report on launchpad but dunno if its a bug our something i oversee.

---

### Post by BackwardsDown on 2008-09-10
I've got exactly the same problem, and I could not find a bug-report eiter. I find Amarok-bugtracker not really intuitive.

---

### Post by awakatanka on 2008-09-10
I just made a bug report. You ca confirm it at [https://bugs.launchpad.net/ubuntu/+source/amarok2/+bug/268657](https://bugs.launchpad.net/ubuntu/+source/amarok2/+bug/268657)



edit : Lydia had a tip that solved it ```
 Lydia Pintscher wrote 8 minutes ago:  (permalink)  
Please delete your collection.db in ~/.kde/share/apps/amarok
 The database scheme has changed.
```

---

### Post by jlacroix on 2008-09-10
When it comes to Amarok2, I'm really confused on how to use it. It's the only media player I've ever used that I've struggled to figure out how to do basic things.

For example, if I put on random play, there is no way to make it play my whole collection randomly, just whatever I have loaded into my playlist. Pretty much all the other stuff I did in Amarok classic I can't figure out how to do here.

I'm sure I'll like Amarok2 when it's finished. I hope it's not another "Duke Nukem Forever", we've been waiting a VERY long time for this to come out. I hope it actually does.

---

### Post by awakatanka on 2008-09-10
> **jlacroix said:**
> When it comes to Amarok2, I'm really confused on how to use it. It's the only media player I've ever used that I've struggled to figure out how to do basic things.

For example, if I put on random play, there is no way to make it play my whole collection randomly, just whatever I have loaded into my playlist. Pretty much all the other stuff I did in Amarok classic I can't figure out how to do here.

I'm sure I'll like Amarok2 when it's finished. I hope it's not another "Duke Nukem Forever", we've been waiting a VERY long time for this to come out. I hope it actually does.LoL it will be surely not be a duke nukem fornever.  Was it possible without putting the files in playlist to paly them randomly in amarok 1? Amarok 2 for me does the job i need it for

---

### Post by jlacroix on 2008-09-10
> **awakatanka said:**
> LoL it will be surely not be a duke nukem fornever.  Was it possible without putting the files in playlist to paly them randomly in amarok 1? Amarok 2 for me does the job i need it for

With Amarok 1 my playlist was my entire collection. I would like to be able to do that in Amarok 2 as well.

---

### Post by awakatanka on 2008-09-11
> **jlacroix said:**
> With Amarok 1 my playlist was my entire collection. I would like to be able to do that in Amarok 2 as well.
i simply do a CTRL-A and drag it to playlist and all my numbers are in playlist. Sameway as i did in 1.  Don't know of anotherway thats why i asked maybe i could learn a new trick in version 1 ;-)

---

### Post by jlacroix on 2008-09-11
Is Amarok 2 going to be default in Intrepid? It might as well be, since it will probably come out this year, I hope.

---

### Post by BackwardsDown on 2008-09-11
> Is Amarok 2 going to be default in Intrepid? It might as well be, since it will probably come out this year, I hope.

It won't be ready for Intrepid, but for Jaunty it should be ready.

---

### Post by jlacroix on 2008-09-11
I hope when it is released, the Intrepid Amarok2 package replaces the Amarok1 package when you install it.

---

### Post by SunnyRabbiera on 2008-09-11
> **BackwardsDown said:**
> It won't be ready for Intrepid, but for Jaunty it should be ready.

I dunno, with the way that Amarok 2 looks it might not be ready for Zesty Zebra at this rate.

---

### Post by BackwardsDown on 2008-09-11
> I hope when it is released, the Intrepid Amarok2 package replaces the Amarok1 package when you install it.

That chance is next to zero. Ubuntu dev's only add bugfixes to released versions, there has to realy be a very very good reason to add extra functionality to a already existing version.

But Intrepid will have a "amarok2" package, so you can install it by yourself if you find it stable enough to use :)

---

### Post by jlacroix on 2008-09-11
> **BackwardsDown said:**
> That chance is next to zero. Ubuntu dev's only add bugfixes to released versions, there has to realy be a very very good reason to add extra functionality to a already existing version.

But Intrepid will have a "amarok2" package, so you can install it by yourself if you find it stable enough to use :)

Right, but my point is that if I do choose to install amarok2, I don't want both amarok1 and amarok2 installed at the same time. If I removed amarok1 it would probably want to remove kubuntu-desktop.

---

