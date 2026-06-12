---
title: "LTS Enablement Stack 12.04.2"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by on110 on 2013-02-15
Hello. I have 12.04.1 x86-64 installed and now I want to upgrade to 12.04.2 with LTS Enablement Stack. How to upgrade all my installed packages to their *-quantal version if there is any? I do not want to search them and upgrade one by one or install full xserver-xorg-lts-quantal metapackage with all drivers. Is that possible?

---

### Post by howefield on 2013-02-15
> **on110 said:**
> I do not want to search them and upgrade one by one or install full xserver-xorg-lts-quantal metapackage with all drivers. Is that possible?

Then do a fresh clean install with 12.04.2.

---

### Post by on110 on 2013-02-15
why should I? It's windows way, mate. btw why does moderator give such stupid advices?

---

### Post by howefield on 2013-02-15
> **on110 said:**
> why should I?

No one can answer that for you.

> It's windows way, mate.

Not sure I understand what you are saying, what is the "windows way, mate" ? Do you leave a note under your pillow asking the tooth fairy to do it for you whilst you sleep ? ;-)

There is sufficient difference between this point release of Ubuntu and the previous for me to consider it worthy of a fresh install and thereafter taking the updates as they come.

No different to what I'd do in Windows.

So that is what I'd recommend, others will most likely come along and give some other advice, so hang around. 

Paging Twinkle....

---

### Post by on110 on 2013-02-15
good. I'll try to explain. There's a known solution for every and each problem in windows world - reinstall. So I tried to say there's no need to reinstall ubuntu when the problem is just to upgrade some packages. It could be easily done, I'm just too lazy to search which packages to upgrade out of installed ones. Thought there should be some workaround.
Didn't understand the part about fairies and teeth, there's only bears and vodka and my kalashnikov here...

---

### Post by oldfred on 2013-02-15
I had not heard of Enablement Stack until this post. But I knew 12.04 was in effect going to have two versions. One based on original kernel and one using a newer kernel.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)
> Perform an update or upgrade to Precise from a previous Ubuntu release.  Only those installing from the 12.04.2 media will automatically receive a  newer hardware enablement stack by default. 
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal 

For anyone interested, the specifics regarding the  exact policies and procedures regarding the support, maintenance, and  upgrade paths for the hardware enablement stack has been documented at  the following location: 

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by dino99 on 2013-02-15
note: i already have tried it, but xorg/xserver need to accept ABI higher than 11 ;)

[https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413](https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413)

---

### Post by catnet on 2013-02-17
the correct way to upgrade is
```

sudo apt-get install xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal

```
I don't know why the officials mislead users.

---

### Post by Bobhuber on 2013-02-17
> **catnet said:**
> the correct way to upgrade is
```

sudo apt-get install xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal

```I don't know why the officials mislead users.
Thank you. On my system it broke x but did install correctly. I'm using a newer kernel  and an older version of nvidia which caused the problem but on a stock box it looks like it would update the kernel and xorg correctly. During the install its looking for nvidia 310.19 which I don't quite understand since the current drivers are 310.32 unless it's trying to update nvidia current.Either way your instructions were correct and very helpful.

---

### Post by presence1960 on 2013-02-17
> **on110 said:**
> why should I? It's windows way, mate. btw why does moderator give such stupid advices?

Howefield is a lot gentler than I would have been to that reply. Hint: Don't insult the people from whom you are asking for help!

---

### Post by catnet on 2013-02-18
> **Bobhuber said:**
> Thank you. On my system it broke x but did install correctly. I'm using a newer kernel  and an older version of nvidia which caused the problem but on a stock box it looks like it would update the kernel and xorg correctly. During the install its looking for nvidia 310.19 which I don't quite understand since the current drivers are 310.32 unless it's trying to update nvidia current.Either way your instructions were correct and very helpful.

Sorry to break your X, but it's mess now it ubuntu's repos. Neither nvidia drivers not vbox from repos work with current xserver and/or kernel. I've got intel video and this command upgraded x good. Now I have both xserver and kernel from quantal.
P.S. IMO there should be more testing before putting packages with broken dependancies into repos, else many companies leave ubuntu.

---

### Post by mcqueed on 2013-02-20
When I ran the "recommended" LTSEnablementStack update:

```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```everything seemed to be fine, until I disconnected the monitor to run headless.  On reboot the system stopped in the "**The system is running in low-graphics mode**" prompt.

I then ran:

```
sudo apt-get remove xserver-xorg-lts-quantal
```intending to reinstall the precise one, but I noticed that the normal remove said that it was going to install, what looked like, a neutral version on xserver-xorg, so I continued.

My headless server now boots correctly, auto login works and I am able to vnc into the machine.

Since I use this mainly as a server, only using the desktop via vnc for some administration, this solution is good for me.

BUT

When my replacement backup system comes in, I will be doing a fresh install.  While linux, at it's heart, is fine for in place upgrades, today's full fledge systems really need fresh installs to operate at their peak.

---

### Post by forcecore on 2013-02-21
> **catnet said:**
> the correct way to upgrade is
```

sudo apt-get install xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal

```
I don't know why the officials mislead users.

**libgl1-mesa-glx-lts-quantal**
Thanks, this solved my netboot build GPU acceleration issue too.

---

