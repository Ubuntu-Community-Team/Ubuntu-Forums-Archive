---
title: "[SOLVED] Why can't Live CD be used for upgrading ubuntu ?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by cyneuron on 2007-10-20
Hello there

i know that Live CD can't be used for upgrading existing ubuntu system. But i want to ask why is that so ?

Won't that be great if Live cd could allow this ?

downloading separate alternative installation cd or upgrading using synaptic takes extra downloading time and bandwidth specially for people whose download speed isn't high.

And as most of people have Live CD's, using Live CD for upgrading as well should be the most obvious way to upgrade Ubuntu, rather than other two methods.

I want to know Why haven't Ubuntu developers given attention to this problem ? Because as far as i think it should not be a great challenge technically to make Live CD work as upgrade cd as well.

---

### Post by Sef on 2007-10-20
> i know that Live CD can't be used for upgrading existing ubuntu system. But i want to ask why is that so ?

It can be.  You can install from either the Live CD or the alternate cd.

---

### Post by cyneuron on 2007-10-20
> **Sef said:**
> It can be.  You can install from either the Live CD or the alternate cd.

Thanks for replying...

Ubuntu official site doesn't tell a single way of upgrading Ubuntu with Live cd, read here : [Upgrade Ubuntu]("http://www.ubuntu.com/getubuntu/upgrading")

Neither have i read it anywhere anywhere in forums...

can you tell me the way you know to use Ubuntu Live cd to upgrade Ubuntu...

---

### Post by cyneuron on 2007-10-20
can anybody expert enough explain....

---

### Post by Gossar on 2007-10-20
> **cyneuron said:**
> downloading separate alternative installation cd or upgrading using synaptic takes extra downloading time and bandwidth specially for people whose download speed isn't high.
I can't address your LiveCD issue (my machine only has 256MiB RAM and won't run the LiveCD :( ) but I can point out that using jigdo to download the alternate CD saves time and bandwidth.  Jigdo allows you to only download the parts that are different, so if you already have a LiveCD, you won't have to re-download much of that data, just the special alternative bits.

[https://help.ubuntu.com/community/JigdoDownloadHowto](https://help.ubuntu.com/community/JigdoDownloadHowto)
[http://www.debian.org/CD/jigdo-cd/](http://www.debian.org/CD/jigdo-cd/)
[http://atterer.net/jigdo/](http://atterer.net/jigdo/)

---

### Post by HokeyFry on 2007-10-20
well you *could* do it the old upgrade way, download the live CD, change the cdrom entry  in /etc/apt/sources.list to the gutsy info, then upgrade in that manner.

also, i thought that if you popped in a live cd of a greater version of ubuntu while you are running your current version that it asks if you would like to upgrade?

---

### Post by cyneuron on 2007-10-20
> **HokeyFry said:**
> well you *could* do it the old upgrade way, download the live CD, change the cdrom entry  in /etc/apt/sources.list to the gutsy info, then upgrade in that manner.

also, i thought that if you popped in a live cd of a greater version of ubuntu while you are running your current version that it asks if you would like to upgrade?


It doesn't upgrade even if you add it to source list. How did you assume that ? try it. it doesn't work like that....

i am also saying that it should be like this only. You just insert latest cd in your system, be it Live CD or alternate... and you simply upgrade it that way....

like you upgrade windows xp to vista...

whats the point of making Live cd incapable of upgrading system, when almost every user has Live cd, and not alternate install cd.....

and when alternate cd can upgrade system, why can't Live cd......? any technical reason ? anybody....

---

### Post by HokeyFry on 2007-10-20
well thats how a while back i upgraded from breezy to dapper, and when i popped in the cd it asked if i wanted to upgrade

ive also upgraded using the repo method i just mentioned so yes i have tried it, and it *did* work for me


thinking about it now though, i may have not have used the live cd, but it was a long time ago since i upgraded a system so....

---

### Post by qamelian on 2007-10-20
> **Sef said:**
> It can be.  You can install from either the Live CD or the alternate cd.

You can install but you can't upgrade from both CDs. When you put the alternate CD in your drive, the update manager detect it and offers to upgrade. It doesn't do this with the Live CD. The reason would be, I guess, that the alternate CD is essentially just a bunch of packages with and installer. The live CD contains a fully working Linux environment, but very few installable packages.

---

### Post by cyneuron on 2007-10-20
> **HokeyFry said:**
> well thats how a while back i upgraded from breezy to dapper, and when i popped in the cd it asked if i wanted to upgrade

ive also upgraded using the repo method i just mentioned so yes i have tried it, and it *did* work for me


thinking about it now though, i may have not have used the live cd, but it was a long time ago since i upgraded a system so....

may be this provision was available in previous versions.... but not now anymore.... But why ????

it doesn't work in Gutsy at least.....

---

### Post by HokeyFry on 2007-10-20
personally though id wait a few months before upgrading to gutsy. seems many users are encountering problems with it,  and if feisty is working well for you, then why upgrade? unless you are ADD/OCD like me and have to keep you computer upgraded to the fullest for entertainment ;)

---

### Post by aysiu on 2007-10-20
The Desktop CD does not contain the packages needed for an upgrade. When you install from the Desktop CD, it just makes a direct copy of the live session on to your hard drive.

The Alternate CD contains the actual .deb packages needed for an upgrade. When you install from the Alternate CD, it unpacks and installs each individual .deb file.

---

### Post by cyneuron on 2007-10-20
> **aysiu said:**
> The Desktop CD does not contain the packages needed for an upgrade. When you install from the Desktop CD, it just makes a direct copy of the live session on to your hard drive.

The Alternate CD contains the actual .deb packages needed for an upgrade. When you install from the Alternate CD, it unpacks and installs each individual .deb file.

That looks really nice info.....thanks for that...

But why has this been done so.....packages are definitely there on Live CD as well.....so is it not possible for Ubuntu developers to to make Live CD such that it may be used for upgrading as well....? and if not, then why ?

---

### Post by aysiu on 2007-10-20
> **cyneuron said:**
> That looks really nice info.....thanks for that...

But why has this been done so.....packages are definitely there on Live CD as well.....so is it not possible for Ubuntu developers to to make Live CD such that it may be used for upgrading as well....? and if not, then why ?
There are a *few* select packages that exist on the Desktop CD, but it's not all the packages needed for an upgrade. It's a space issue. You can't have the live session *and* **all** the packages needed for an upgrade all stored on one CD. A DVD maybe, but not a CD.

---

### Post by cyneuron on 2007-10-20
> **aysiu said:**
> There are a *few* select packages that exist on the Desktop CD, but it's not all the packages needed for an upgrade. It's a space issue. You can't have the live session *and* **all** the packages needed for an upgrade all stored on one CD. A DVD maybe, but not a CD.

got what you meant, but still a little bit of confusion....

A little hypothesis of mine :

packages/softwares on Live cd are packaged/compiled in a format different that .deb(the format needed for upgrading existing .deb), so the packages on Live CD are present but they can be used for new installation only, not for upgrading the older version of same package....

Hope this hypothesis is not a blunder....

Will be good if you could explain in a little bit details & technical terms.....

really curious now to know the differences....

---

### Post by aysiu on 2007-10-20
No, the software on the Desktop CD isn't packaged/compiled in a different format. It's just not in package form. When you install from the Desktop CD, it just copies the entire live session over to your hard drive. It is not copying individual packages.

---

### Post by cyneuron on 2007-10-20
Ok....thanks for all that info.....But i think there should be some way to use Live CD as upgrade CD as well......may be it will be possible in future releases....

---

### Post by renatosilva on 2007-12-23
> **cyneuron said:**
> Ok....thanks for all that info.....But i think there should be some way to use Live CD as upgrade CD as well......may be it will be possible in future releases....

I agree. I'm on a dialed connection and frustrated to have to reinstall totally the system. And no, backing up home is not enough!

---

