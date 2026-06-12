---
title: "Can't loggin anymore"
date: 2004-12-30
forum: Installation &amp; Upgrades
---

### Post by James_Black on 2004-12-30
Hi,

I can't login with my account anymore. The guest account, does work. Everytime I try to login with my account I get this error:

```
Your session only lasted less then 10 secconds. If you have not 
logged out yourself this could mean that there is some installation 
problem or that you me be out of diskspace. Try loggin in with one 
the failsafe sessions to see if you can fix this problem.
``` 

When I try to login with Gnome failsafe session, I get the same error. However, I can loggin with the terminal failsafe session, but I don't know what to do. Can somebody please help me?

---

### Post by Rancoras on 2004-12-30
I always fallback on the same question.....what changed recently?  Undo or fix that and 99% of the time the problem will go away.

---

### Post by James_Black on 2004-12-30
Well, I didn't change anything recently. The only thing I did yesterday night, was burn a cd with K3b. Afterwards, I shut down my computer. When I started my computer this morning, I suddenly got this error.

There's also a logview, this is what is says:

```
/etc/gdm/pression/default: Registering your session with wtmp and utmp 

 /etc/gdm/pression/default: Running /usr/bin/x11/ seureg -a -w /var/log/utmp -x -l " " -l :" "james" 

 /etc/gdm/xsession Begin session setup.... ** (gnome session): warning **: unable to read ICE Authority file /home/james/.ICEAuthority
```

---

### Post by Rancoras on 2004-12-30
Sounds like K3B messed with the ownership of your .ICEauthority file.  Boot into recovery mode and run this:

```
sudo chown user:user .ICEauthority
``` 

Where "user" is your username.  You may have to cd to where that file is located before you run the command.

---

### Post by James_Black on 2004-12-31
Thanks a lot! This solved my problem!  :D

---

### Post by LongTooth on 2005-01-30
How can one who is thinking about installing K3B head off this problem. I recall having the same problem sometime ago when working with K3B. Surfing through the forum, I read where some have success with K3B and other have nothing but trouble. I reinstalled my system to clear the same problem in this post but I've since stayed from K3B. If I can do something to prevent this I might install K3B again. From your post I think I shoud cd into K3B and do "sudo chown user:user .ICEauthority". What is the steps required? Thanks.

---

### Post by LongTooth on 2005-01-31
Willing to head this problem off at the pass. Anyone?

---

### Post by martijntje on 2005-02-01
I don't understand your question.

You want to give k3b another shot? Then do so. The solution posted here works.

---

### Post by LongTooth on 2005-02-01
Rather then address a problem when it come up, I wanted to head it off. Thus my question. If I can 'tweak' something and thus not have to address the no-log-in situation I'd much rather do that. But if there is no way, well, there is no way. I'll give it a try. If you hear someone screeming, that will be me.

---

### Post by barbarossa on 2005-02-01
k3b needs to be run with root permission to avoid messing with .ICEauthority.

Either:

sudo k3b

or download gksudo and use gksudo k3b as the menu command.

---

### Post by ubuntu_fan on 2005-02-01
This happened to me also...

I guess the problem is that it's tempting to run /usr/bin/k3b - instantly causing the problem, with no hint as to what has happened.

Hosing your X just from installing k3b isn't really great for usability.

---

### Post by barbarossa on 2005-02-01
Agreed.

---

### Post by derdewey on 2005-02-01
Wow, I had the same problem just now.  Thank goodness for this forum!  Good thing I thought of running firefox from the terminal.

Well, I had to do a slightly different syntax to get the chown to work (<-- linux newb!)

```
sudo chown user:user /home/user/.ICEauthority
```

did the trick.  Thanks again folks!

---

### Post by infinitee on 2006-01-06
well, I also join the bandwagon but I feel the prob isnt restricted to k3b but is also with any kde s/w (I had dloaded a bunch of kde s/w like kile and stuff) and it always led to this prob.. and changing ownership helped as suggested. thanks guys but do you think this was caused by KDE? (I had this prob 3 times and 2 times I ended up re-installing (:( yeah was damn naive)

-a newbie

---

### Post by RikkiD04 on 2006-01-10
[QUOTE=Rancoras]Sounds like K3B messed with the ownership of your .ICEauthority file.  Boot into recovery mode and run this:

```
sudo chown user:user .ICEauthority
``` 

Where "user" is your username.  You may have to cd to where that file is located before you run the command.[/QUOTE]


i have the same problem, and i tried to do what you said, but it then says "sudo: must be a setuid root"

---

