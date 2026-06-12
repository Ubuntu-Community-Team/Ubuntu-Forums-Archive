---
title: "request: idiot proof samba/filesharing configuration"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Zyphrexi on 2009-02-28
while i am sure there are many out there who might disagree, I believe the time is long overdue for an idiot proof method of setting up samba (or whatever). I've been trying to get samba to work for a couple years now, and really have had no luck. Tried swat, samba-config, and have no idea how to start up webmin. It really is a pain, and I'd like to see something for non-professionals. (or people who are just plain frustrated and confused)

---

### Post by | MM | on 2009-02-28
What are you trying to do? Just share folders, or more complex stuff?  But i agree, File sharing is not as easy as it should be!  That said i was playing with OS X and SAMBA integration is worse than in Linux from what i could tell...

---

### Post by Zyphrexi on 2009-02-28
well yeah, basically share a folder on ubuntu linux with my brother's vista laptop.

but i'm posting this as z feature request, not a request for support since I don't want to incur the wrath of the mighty mods.

also i've read so much stuff i have a headache. samba is a real pita

---

### Post by cariboo on 2009-02-28
This is not the place for a feature request, do that on Launchpad.

Have you had a look at this [howto]("http://ubuntuforums.org/showthread.php?t=202605")? Follow the instructions step by step and you will have a working setup. Sometimes using howtos I just try what I think will solve my problem, and ususally fail, but if I follow it step by step it works.

JIm

---

### Post by Zyphrexi on 2009-02-28
oh didn't realize feature requests didn't go here. Thanks.

yeah I read that link, but wasn't that guide written in 06?

---

### Post by ecosprog on 2009-02-28
Go to Synaptic and install system-config-samba, or apt-get install system-config-samba.

This is a GUI front-end for configuring samba file and printer sharing on a linux box.

---

### Post by btdown on 2009-02-28
> Go to Synaptic and install system-config-samba, or apt-get install system-config-samba.

This is a GUI front-end for configuring samba file and printer sharing on a linux box.Thanks dude...I coulda used this tip a week ago. ;(    I had my sharing shizit all working, then about a week or so ago, the updates broke it. I tried like hell to fix it, but it wasnt until my last batch of updates, where it started working again.

Thank you for the tip about system-config-samba, but I think some of the dependencies (python-libuser) is hosed on Jaunty and isnt letting me install.---yet!

---

### Post by Gina on 2009-02-28
ATM I'm running Win XP (sorry) on one of my machines (to run my weather station software - I'll be looking into Linux software shortly) and went to set up file sharing in XP - I failed!!  Trouble is, I've been running Ubuntu for so long now that I've got out of the mind-set of Windoze!  To me, Linux and particularly Ubuntu fits my way of thinking so much better.  Better not say any more :lol:

---

### Post by nanog on 2009-02-28
use NFS.

---

### Post by cariboo on 2009-02-28
Samba hasn't changed that much since 2006, mostly just bug fixes. 

Jim

---

### Post by cl333r on 2009-03-01
> **Zyphrexi said:**
> well yeah, basically share a folder on ubuntu linux with my brother's vista laptop.

but i'm posting this as z feature request, not a request for support since I don't want to incur the wrath of the mighty mods.

also i've read so much stuff i have a headache. samba is a real pita
I had also no clue, but it seems to already be integrated, however, not perfectly (no obvious point and click solution to specify the working group in Samba):
1) In Ubuntu right-click the folder you wanna share -> Sharing Options.
2) Choose "Share this folder" and "Guest Access".
3) Ubuntu will auto install and configure Samba, it will also ask for a session restart if needed.
4) Looks like Samba by default works only with XP boxes that are in "WORKGROUP" so you have to make sure XP is also using "WORKGROUP", reboot windows if needed.
5) After that windows listed (for some reason) 2 entries in the computer neighborhood, both of which had the name "samba" among other words, in one of them I found the folder that I was sharing from Ubuntu - which was what I needed. The 2nd entry - was something else that had no entries or didn't work - don't remember.
To check the name of your XP's working group, right-click My Computer->Properties->Computer name tab.

---

### Post by Zyphrexi on 2009-03-01
yeah I know most of those programs and features. 
recently I've been reading the samba's official guide.

even though I installed ubuntu on my brother's laptap, he's almost always playing guildwars on vista, so it's difficult to test things. (I even installed guildwars on ubuntu)

since this topic has been totally derailed, i'm going to mark it as solved and create a thread in the appropriate section -- EDIT: except i've no clue how to do that.

---

