---
title: "Inquiry in Installing Drapper"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-21
Is it normal that when installing Drapper, you need to select the Start or Install ubuntu as indicated on the snapshot?

[IMG]http://img146.imageshack.us/img146/7097/u606startat1.jpg[/IMG]

When I select that option, it takes time actually it eats up all my time waiting for this to appear and I really don't know what is happening. As far as I know, if I select this option, Live CD is being loaded (am I right?). Can I directly select the option to install the Drapper? :confused: 

Hoping for your response

Note: I am new to ubuntu, my apology for being such a noob.

---

### Post by mssever on 2006-09-21
If you want to use the Live CD, then yes. If you want to install directly, you can download the alternate install CD.

---

### Post by textguru on 2006-09-21
> **mssever said:**
> If you want to use the Live CD, then yes. If you want to install directly, you can download the alternate install CD.

Meaning I cannot install 6.06 from the cd that was shipped? I need to download the alternate cd?

---

### Post by sktx on 2006-09-21
No, you can install from the ShipIt CDs.  You just have to boot into the desktop first, which on some systems (slower PCs or slow/old CD/DVD drives) can take a bit of time.  

What mssever is saying is that if you want to install without having to boot the LiveCD, you have to download the Alternative CD Image and burn it to a CDR, and boot from that to install.

..*sktx*

---

### Post by textguru on 2006-09-21
So I just need to wait for Live CD to finish the loading? It takes me hours and still waiting for the loading. Is it the exact way on handling this using the cd that I have?

---

### Post by sktx on 2006-09-21
hrmm... It shouldn't take *hours* to boot the LiveCD... Are you sure you're not trying to boot it on a calculator?  :p

What're the specs of the machine you're trying to install on?

..*sktx*

---

### Post by mssever on 2006-09-21
If it's taking hours, then something's wrong. Maybe you don't have enough memory (the live CD requires a lot more memory than the installed version), or maybe you have a bad CD.

You can test the CD by choosing the option to test the CD brom the bootsplash (the screenhot you posted).

If the CD is bad, you might find some useful info on [this page]("http://psychocats.net/ubuntu/iso"), especially the part about md5sums.

---

### Post by textguru on 2006-09-21
> **sktx said:**
> hrmm... It shouldn't take *hours* to boot the LiveCD... Are you sure you're not trying to boot it on a calculator?  :p

What're the specs of the machine you're trying to install on?

..*sktx*

Your right, Im using low end hardware, Celeron 1GHz with 128MB of RAM. Does it mean that I cannot install Drapper on this PC?

---

### Post by textguru on 2006-09-21
> **mssever said:**
> If it's taking hours, then something's wrong. Maybe you don't have enough memory (the live CD requires a lot more memory than the installed version), or maybe you have a bad CD.

You can test the CD by choosing the option to test the CD brom the bootsplash (the screenhot you posted).

If the CD is bad, you might find some useful info on [this page]("http://psychocats.net/ubuntu/iso"), especially the part about md5sums.

I have tried many CDs but it seems that not enough memory (as posted on previous reply). I only have 128MB.

---

### Post by sktx on 2006-09-21
Yeah, 128Mb is pretty low.  I'm not sure what the requirement is for installation from the alternative CD, but any system running any OS is bound to run fairly cludgy with 128Mb... If you can, though, you could look into using a window manager with a smaller footprint, like XFCE or OpenBox.  Try searching these forums for Xubuntu, I used it for quite a while shortly after my introduction to Ubuntu, and really enjoyed it.  I still keep a copy of XFCE installed on my box when I feel like things aren't moving fast enough.

Anyway, RAM is fairly cheap nowadays, and you don't even have to leave your house to get a good deal... Check out newegg.com, they're bound to have a deal, if I were you I'd pick up a couple 256Mb or 512Mb sticks, it shouldn't be too hard on your wallet.

..*sktx*

---

### Post by textguru on 2006-09-21
> **sktx said:**
> Yeah, 128Mb is pretty low.  I'm not sure what the requirement is for installation from the alternative CD, but any system running any OS is bound to run fairly cludgy with 128Mb... If you can, though, you could look into using a window manager with a smaller footprint, like XFCE or OpenBox.  Try searching these forums for Xubuntu, I used it for quite a while shortly after my introduction to Ubuntu, and really enjoyed it.  I still keep a copy of XFCE installed on my box when I feel like things aren't moving fast enough.

Anyway, RAM is fairly cheap nowadays, and you don't even have to leave your house to get a good deal... Check out newegg.com, they're bound to have a deal, if I were you I'd pick up a couple 256Mb or 512Mb sticks, it shouldn't be too hard on your wallet.

..*sktx*


Do you think 5.10 will work on this hardware specifications?

---

### Post by sktx on 2006-09-21
Hrmm... I'm not too sure about the exact specs that any of the installs need,  but with a bit of tweaking, you can get linux installed on a toaster.  I'm  not sure it'd be a project for a beginner, however, with persistance it can be done and would probably be well worth it in the long run.  

Have you downloaded, burned and tried to boot the 6.06 Alternative CD?

---

### Post by unisol on 2006-09-21
you could try installing it in safe graphics mode but you would probably be better using xubuntu

---

### Post by mssever on 2006-09-21
The alternate install CD won't require a lot of RAM to install. You should be fine on that account. My desktop runs great on 256MB of RAM. But you'll want to make sure that you have a good-sized swap partition (at least 512MB in your case). You could look into using Xubuntu (XFCE).

[LIST]
[*][System Requirements for Ubuntu Dapper]("http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3")
[*][System Requirements for Ubuntu Breezy]("http://www.ubuntu.com/download/releasenotes/510#head-6f72ee538d799395f5febea99c08b3e85a14867b")
[*][System Requirements for Xubuntu Dapper]("https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-0ca89a2e16807e844ced26dd988f5ef7541d9b15")[/LIST]

Of course, you can probably get by with less if you really want to.

---

### Post by textguru on 2006-09-21
> **unisol said:**
> you could try installing it in safe graphics mode but you would probably be better using xubuntu
I have done this and it makes loading much faster. Thanks for the tip.

---

