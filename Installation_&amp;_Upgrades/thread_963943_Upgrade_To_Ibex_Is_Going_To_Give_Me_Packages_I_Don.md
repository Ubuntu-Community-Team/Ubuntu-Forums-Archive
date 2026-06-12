---
title: "Upgrade To Ibex Is Going To Give Me Packages I Don't Want Installed - Help!"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by taurusx5 on 2008-10-30
Before I tried to upgrade to the new Ibex in ubuntu, a window popped up and said that 314 packages would be installed. It lists many of the packages that I had removed previously and don't want, like, compiz-fusion, kde, etc. I don't understand this. If I had removed many of these unwanted packages before, why will it install them? I don't want them installed. 

How can I tell the Update Manager to keep certain unwanted packages from being downloaded and installed? Can it allow me the ability to download and install only the ones I want?

---

### Post by cariboo on 2008-10-30
It looks like your system is in a state where it needs some of the kde packages, for instance if you have Amarok installed you need the new libraries. Any kde program you are using will need the new files. If you really don't want the kde programs, you could always remove them after the update is done. Another way to do it is to do a clean installation and just install the base system, then add only the programs you want and need.

---

### Post by taurusx5 on 2008-10-30
> **cariboo907 said:**
> It looks like your system is in a state where it needs some of the kde packages, for instance if you have Amarok installed you need the new libraries. Any kde program you are using will need the new files. If you really don't want the kde programs, you could always remove them after the update is done. Another way to do it is to do a clean installation and just install the base system, then add only the programs you want and need.

cariboo, that's not the answer I'm looking for. I'm NOT going to do a clean installation and wipe out all my settings and files I have so far built up since my last upgrade. To do so would be idiotic. And, to correct you, my system is NOT in need of kde apps. As a matter of fact, I already have 4 kde apps that I use currently and don't need any more. SO, I really don't know what kind of answers you're providing at all.

Would anyone else like to provide me with an intelligent answer?

.

---

### Post by im_dan on 2008-10-30
With an attitude like that i'd be surprised if anyone helps you ever again.
if you are unsatisfied with the generous free community support visit this link [http://www.ubuntu.com/support/paid]("http://www.ubuntu.com/support/paid")
otherwise re-read the post and understand what was said.

---

### Post by taurusx5 on 2008-10-30
> **im_dan said:**
> With an attitude like that i'd be surprised if anyone helps you ever again.
if you are unsatisfied with the generous free community support visit this link [http://www.ubuntu.com/support/paid]("http://www.ubuntu.com/support/paid")
otherwise re-read the post and understand what was said.

im_dan, i think i was a bit too harsh. just understand that i've experienced alot of crap with ubuntu ever since i installed it early this year. i like the o/s, but i don't want to risk losing critical files and settings that i have so far saved. i want my ubuntu experience to be as issue-free as possible.

i apologize to you cariboo for my outburst. hope you guys understand.

and im_dan, i dont need to re-read the post. if you're going to point out my outburst that's fine. but, don't be condescending either. being helpful goes a along way, but 2 wrongs don't make a right. understand this so we don't end up biting each other. learn from this.

.

---

### Post by gohsthb on 2008-10-31
So cariboo907 was correct you have KDE apps that will need the new libraries.  Try removing them before doing the upgrade since you don't need them anymore.  Maybe then it stop trying to install packages that you don't want.  Do you have a small hard drive or something?  I don't see the problem with installing some extra packages.

---

### Post by taurusx5 on 2008-10-31
> **gohsthb said:**
> So cariboo907 was correct you have KDE apps that will need the new libraries.  Try removing them before doing the upgrade since you don't need them anymore.  Maybe then it stop trying to install packages that you don't want.  Do you have a small hard drive or something?  I don't see the problem with installing some extra packages.

gohsthb, re-read my question again because you're clearly off the mark. Forget kde, this isn't about kde. And, the question isn't about extra packages, it's about UNWANTED packages. 

.

---

### Post by anjilslaire on 2008-10-31
Re-read your own posts, taurusx5. You said you have 4 KDE apps. That will necessitate some kde libraries & files. gohsthb is not off the mark. 
If you have anything related to KDE, **which you admit**, then you can expect some new KDE packages to be installed. This is partially about KDE, as it involves some KDE packages your apps need, but you don't want.

The upgrade will grab & install anything it *needs* to maintain the functionality the current OS has, including any packages you already have and don't have, but may not be aware of.

If you're going to be that particular, then you should backup your /home and do a clean install. Better yet, move /home to a separate partition so you can wipe / with impunity, reinstall the OS cleanly, and still maintain all of your settings and customizations. I do full reinstall of th OS every time, and have never lost any settings yet, period.

---

### Post by paxmark1 on 2008-10-31
Think of it as a learning example.  One option is that you get to figure out how to save all of your nifty little configuration files from howvever long you have been upgrading and put them back into a clean install and then add the kde4 packages you want/need and not all the cruft and you totally own your system and fly along merrily.  That is one option.

That is where I am for my older computer where I did the beta process to see if I liked 8.10  I don't like 8.10 kubuntu on older machines.  It drags.  I strongly but respectfully made that known, and got no flak. So on that 5 year old machine I shifted gears to debian lenny testing with KDE 3.59 and a newer kernel and I am putting back in the old configurations that I like.  It really flies with lenny

I like smaller and lighter too, but it is always a balancing act.  There are always dependencies.  

We all get frustrated.  Hang in there

I still have 8.04 on my fast machine, and I will upgrade there when I feel like it.  Freedom. I decided I want to work on other things than learning KDE4 at this time and where KDE4 is at this point.  Later I will learn KDE4.  

peace, mark

---

### Post by taurusx5 on 2008-10-31
> **anjilslaire said:**
> Re-read your own posts, taurusx5. You said you have 4 KDE apps. That will necessitate some kde libraries & files. gohsthb is not off the mark. 
If you have anything related to KDE, **which you admit**, then you can expect some new KDE packages to be installed. This is partially about KDE, as it involves some KDE packages your apps need, but you don't want.
.

No, YOU RE-READ my original post. Obviously, you're experiencing basic comprehension issues. I'll reiterate it again: 

> Before I tried to upgrade to the new Ibex in ubuntu, a window popped up and said that 314 packages would be installed. It lists many of the packages that I had removed previously and don't want, *LIKE,* compiz-fusion, kde, etc.

The keyword here is "like". I used kde as an example of the many types of packages I don't want installed. See? Even a caveman can (understand) do it (duh!).  So, before you go ahead and try to be brave online - which any one with little guts can do - think before you speak. 

And do us all a favor... don't EVER comment on this and future posts of mine as you're done so disrespectfully. Doing so will mean a breach of terms of service on this forum and we'll have to report you.

Adios nina.

.

---

### Post by taurusx5 on 2008-10-31
> **paxmark1 said:**
> Think of it as a learning example.  One option is that you get to figure out how to save all of your nifty little configuration files from howvever long you have been upgrading and put them back into a clean install and then add the kde4 packages you want/need and not all the cruft and you totally own your system and fly along merrily.  That is one option.

That is where I am for my older computer where I did the beta process to see if I liked 8.10  I don't like 8.10 kubuntu on older machines.  It drags.  I strongly but respectfully made that known, and got no flak. So on that 5 year old machine I shifted gears to debian lenny testing with KDE 3.59 and a newer kernel and I am putting back in the old configurations that I like.  It really flies with lenny

I like smaller and lighter too, but it is always a balancing act.  There are always dependencies.  

We all get frustrated.  Hang in there

I still have 8.04 on my fast machine, and I will upgrade there when I feel like it.  Freedom. I decided I want to work on other things than learning KDE4 at this time and where KDE4 is at this point.  Later I will learn KDE4.  

peace, mark

Thanks for the reply. I really don't understand your obsession with KDE. I'll have to reiterate again what I'm looking for because apparently there's some communication problem existing here that even I, as smart as I know I am, can't fathom. OK, here is goes FOR THE FOURTH TIME... I'll type in bold print to help you understand better:

I  WANT TO UPGRADE TO IBEX. BUT IBEX HAS PACKAGES I  DON'T WANT INSTALLED BECAUSE I UNINSTALLED THESE SAME PACKAGES ALREADY AND DON'T WANT THEM INSTALLED AGAIN. 

KDE HAPPENS TO BE **ONE** IN A MILLION PACKAGES THAT IBEX WANTS ME TO INSTALL FOR THE UPGRADE. I **ONLY** USED KDE AS AN EXAMPLE. ANOTHER PACKAGE I DON'T WANT INSTALLED THAT I UNINSTALLED ALREADY IS COMPIZ-FUSION. ANOTHER PACKAGE IS VLC. ANOTHER PACKAGE IS BANSHEE. ETC. ETC. ETC.

Hopefully, this helps somehow.

.

---

### Post by tuskenraider on 2008-10-31
> **taurusx5 said:**
> No, YOU RE-READ my original post. 
.

Dude....  sit back... relax and please stop attacking the people on this board.  I can not offer any help in the situation your in, other than to say that yelling and using strong language is not the key to a pleasant and inviting supportive Ubuntu community.

Please reassess your tone and use of strong language. Thank you and i hope you get your issue resolved.

Tusken

---

### Post by LaRoza on 2008-10-31
I suggest some people re-read the Code of Conduct.

For the question, Ubuntu uses meta packages. That means sometimes you can't install individual packages without getting a bunch of them. This can be good, hunting down indivudal packages, and it can be a pain because it is hard to install individual packages.

Thread closed for review.

---

### Post by bapoumba on 2008-11-01
+1 to close for 24 hours.
The OP should look for the definition of a Linux distribution. Choices have been made by Ubuntu to bundle together certain packages in a distribution, and going to Intrepid is a distribution upgrade, not a simple upgrade.
Some other distributions will let you do everything by yourself. Depends on the time you have to devote to building a system that fits you and you only.

---

