---
title: "Empathy and latest updates"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2009-09-01
Has anyone else who uses Empathy notice that after the updates this morning, it always crashes when you open it?

---

### Post by steeleyuk on 2009-09-01
Just applied the updates about 5 minutes ago, seems to be solid here (MSN, GoogleTalk and Bonjour).

You using any other IM networks?

---

### Post by zoomy942 on 2009-09-01
> **steeleyuk said:**
> Just applied the updates about 5 minutes ago, seems to be solid here (MSN, GoogleTalk and Bonjour).

You using any other IM networks?

i went to add facebook and now it crashes over and over.  

can i remove that facebook one somehow?  i tried reinstalling empathy to no avail

---

### Post by 243kof on 2009-09-01
When I try to apply the updates, synaptic requires that I remove empathy. Is this normal?

---

### Post by zoomy942 on 2009-09-01
it removed mine too.

---

### Post by jpeddicord on 2009-09-01
> **zoomy942 said:**
> it removed mine too.

> **243kof said:**
> When I try to apply the updates, synaptic requires that I remove empathy. Is this normal?

Something weird in the dependency handling caused it to want to remove empathy instead of upgrading/installing new backend libraries. Just re-install Empathy and you'll be fine.

---

### Post by steeleyuk on 2009-09-01
Just allow Synaptic to mark Empathy as removable, then select the new dependencies and mark Empathy to be reinstalled.

I've had to do that a couple of times now for Empathy, seems to occur every time theres a major upgrade to Telepathy.

---

### Post by Joe_Bishop on 2009-09-01
Huge regression in my opinion. Gtalk for my google apps account doesn't work. Something stupid was done with accounts manager - it's unintuitive how to reconnect account, old one was much cleaner.

---

### Post by zoomy942 on 2009-09-01
And no one elses Empathy is unstable?  Mine will sometimes open and close repeatedly before it stops and works fine.

---

### Post by Joe_Bishop on 2009-09-01
> **zoomy942 said:**
> And no one elses Empathy is unstable?  Mine will sometimes open and close repeatedly before it stops and works fine.
Yeah, I have it too. But these guys from ppa didn't make dbg packages, so I can't do a backtrace. I loved Empathy, but I'm getting sceptical about it. These guys seem to be better talkers than programmers. Since 9.04 I didn't see any significant improvements in Empathy, only regressions. First, I got this stability bug. Second, voice chat have never worked well, six month ago it turned not to work at all and it doesn't work now completely.    Unintuitive interface for accounts manager today, although UI always was very logical, but they managed to break it too. So, only 1 significant improvement in last 12 month - adium theme support. But it too hard to install one, so most people won't use adium themes.

---

### Post by zoomy942 on 2009-09-01
here is what Empathy says in the terminal after this mornings update

```
zimmerman@Karmic-Tablet:~$ empathy
Segmentation fault (core dumped)
zimmerman@Karmic-Tablet:~$ 

```

---

### Post by lsrg on 2009-09-01
Hi,
in my case, empathy works OK with my msn, google talk and jabber accounts.. 
Ah! the upgrade also worked..

Lsrg

---

### Post by 243kof on 2009-09-02
After the recent updates, empathy crashes whenever I try to call a contact that uses gmail. And if the gmail contact tries to call me, the call is terminated before it begins with an error on their side. What's up?? :confused:

---

### Post by taavikko on 2009-09-02
I'll suspect that problems have arised since the older telepathy-mission-control was replaced by the newer 5 version.

They should be able to co-exist, but atm not happening.

Testing it later tonight...

---

### Post by eilios on 2009-09-03
I can confirm this bug, it's annoying me too =(

EDIT: Running it with "gksudo empathy" works because it's a segmentation fault, but that's not exactly ideal. I changed my empathy settings and themes over to the root home directory, and it does run very well. The problem is of course you shouldn't run your programs as root.

---

### Post by puccaso on 2009-09-03
slightly different issue here but
DOESNT empathy let you BLOCK contacts?!??

---

### Post by zika on 2009-09-05
For several days I have:```
The following packages have been kept back:
  empathy libempathy-common libempathy-gtk-common 
```...?

---

### Post by Copernicus1234 on 2009-09-05
What was wrong with Pidgin? People honestly felt it was complicated?

---

### Post by taavikko on 2009-09-05
> **zika said:**
> For several days I have:```
The following packages have been kept back:
  empathy libempathy-common libempathy-gtk-common 
```...?

Propably running "safe-upgrade"...
they're held back since they depend on the libempathy29 rather than the previous version which depended on libempathy27
Or libempathy-gtk27 than the previous version depended on libempathy-gtk25

w00t :D

---

### Post by kaligus on 2009-09-05
> **Copernicus1234 said:**
> What was wrong with Pidgin? People honestly felt it was complicated?
At this point in time having just installed Empathy, upgraded from the repository listed in another thread, etc.  I agree

I was hoping to get the chance to view others webcams as well as use mine on yahoo.

I can not get Empathy to connect to *ANY* yahoo server by name or IP number even after having pidgin off for an hour.

For now my choice is to be able to chat with my friends and patiently wait for mythical voice/video services to become real.

My current gripes with empathy etc.

1) where are all of my awesome pidgin plugins that I rely on like the spam stoppers and response predictor?

2) can NOT connect to Yahoo.

3) it doesnt tell me why I cant connect to Y!, nor even give me a clue saying only "network error"

---

### Post by gnomeuser on 2009-09-05
> **zoomy942 said:**
> here is what Empathy says in the terminal after this mornings update

```
zimmerman@Karmic-Tablet:~$ empathy
Segmentation fault (core dumped)
zimmerman@Karmic-Tablet:~$ 

```

[https://bugs.launchpad.net/bugs/424255](https://bugs.launchpad.net/bugs/424255)

---

### Post by zika on 2009-09-05
> **taavikko said:**
> Propably running "safe-upgrade"...
they're held back since they depend on the libempathy29 rather than the previous version which depended on libempathy27
Or libempathy-gtk27 than the previous version depended on libempathy-gtk25

w00t :D
No, all the types of upgrade except "apt-get dist-upgrade" hold them ... dist-upgrade gives:```
The following packages will be REMOVED:
  empathy libempathy-gtk25 libempathy27
The following packages will be upgraded:
  libempathy-common libempathy-gtk-common
``` which I don't think is the right solution ... Since I do not use empathy I am not in a hurry ...

---

### Post by kaligus on 2009-09-06
New kink for mine after reinstalling the upgrades from 
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) jaunty main #telepathy

Empathy will connect to yahoo almost every time if pidgin is running when I start empathy.

It will connect randomly without pidgin connected first. But mostly connects after reinstalling the upgrades.

After several other pieces of software were installed and upgrades from other third party repositories empathy connects every time to yahoo.

Now I gotta look back through my logs to see what I added or changed in the last 24 hours but I cant imagine anything affecting empathy since it was amateur radio software, wine update, etc.

---

### Post by Sophont on 2009-09-06
> **Copernicus1234 said:**
> What was wrong with Pidgin? People honestly felt it was complicated?

AFAIK this is not about Pidgin itself. Empathy runs on the Telepathy platform and that's more versatile in the long run.

When Empathy is made the default you can still install/keep Pidgin instead if you prefer.

---

### Post by bapoumba on 2009-09-06
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/422920](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/422920)

This is the bug I've been subscribed to.

---

