---
title: "Can't upgrade from Oneiric, no new release found"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-06-06
I've been running Oneiric Kubuntu for quite a while, and I've never gotten the notification that Precise is available. My system is fully updated. When I try to retrieve Precise explicitly with **do-release-upgrade**, I get the message "No new release found".  I've tried various parameters to **do-release-upgrade**, such as```
do-release-upgrade -m desktop -f kde -d
```but nothing helps.  I've asked about this in the Kubuntu forum but have gotten no response.

Does anyone here know what the problem might be?

---

### Post by shadowmane on 2012-06-06
I'm having the same issue.  I simply cannot upgrade without ditching my current system (which I don't want to do) and doing a fresh install.  I'm using Ubuntu, but I have Kubuntu installed as well.

---

### Post by pwabrahams on 2012-06-06
I'm glad to know at least that I'm not the only one with this experience.  I've updated everything in sight with Muon, Synaptic, and apt-get.  Tried Long-Term Releases and Normal Releases.  Nothing helps.  It's as though Precise simply doesn't exist.

---

### Post by colin.p on 2012-06-08
I do not have an answer for you, but a friendly word of advice, I wouldn't be in too big of a hurry to upgrade just yet. As a matter of fact, the general concensus is to hold off until 12.04.1 comes out in August.

I have an old Athlon 1800+ that I use as a download server(running xubuntu 10.04) and xubuntu 12.04X386 will not install, it just stops part way through and sends me back to the live environment (I know the disk is fine as I successfully installed it into VB on my ubuntu 12.04X64 laptop).

I could try and install from the CD in 10.04, but I am a little hesitant as it may partialy install, quit and then bork the install, forcing me to re-install 10.04. So I will wait until update mgr lists precise as an upgrade, we still have almost a year.

---

### Post by piccobello on 2012-09-15
So August has passed and the issue is still present, at least for me!
What I found out is that muon "edit software sources" dialog is buggy: I had selected to dist-upgrade on normal releases as suggested, but checking file /etc/update-manager/release-upgrades it still listed the option prompt=lts .
Changing it manually to prompt=normal solved the problem for me, now do-release-upgrade -f kde -m desktop -c tells me about Precise. So I just have to do backup and upgrade now, wish me good luck..

Thanks to Alessandro for the suggestion given here:
[https://lists.ubuntu.com/archives/kubuntu-devel/2012-April/006043.html](https://lists.ubuntu.com/archives/kubuntu-devel/2012-April/006043.html)

---

### Post by piccobello on 2012-09-18
> **piccobello said:**
>  So I just have to do backup and upgrade now, wish me good luck..


Not much luck so far.. Update was ok but precise is too darn heavy for my laptop. Kontact is horribly slow and eats up much of my CPU, which is more than 10C warmer than usual, and sometimes goes up to 80C..
update: identified and removed the responsible (ktimetracker). Feels still heavier/slower than oneiric but tolerably so.

---

