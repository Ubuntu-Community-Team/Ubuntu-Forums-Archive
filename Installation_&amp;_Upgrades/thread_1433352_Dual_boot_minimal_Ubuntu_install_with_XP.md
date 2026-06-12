---
title: "Dual boot minimal Ubuntu install with XP"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2010-03-18
I'd like to do a minimal install of 10.04 when it comes out, then install lxde or a minimal gnome on top of that myself, and then dual boot it with Windows XP.

Will the partition tool that comes with the Ubuntu Alternate/Minimal CDs let me do this the way the standard Ubuntu disc will?

---

### Post by zvacet on 2010-03-19
I never used minimal CD so only thing I can tell you is if doesn't work with it download [Gparted live CD]("http://gparted.sourceforge.net/") and partition with it.Format ubuntu partition as ext4.

---

### Post by imperius69 on 2010-03-19
> **javyn999 said:**
> Will the partition tool that comes with the Ubuntu Alternate/Minimal CDs let me do this the way the standard Ubuntu disc will?

yes it will, it will detect other OS. But all is in txt mode so can be a bit confusing.

---

### Post by javyn999 on 2010-03-19
> **imperius69 said:**
> yes it will, it will detect other OS. But all is in txt mode so can be a bit confusing.

Thanks guys.  I'll take a crack at it then.  I don't mind text mode, but even after a year of use, I still consider myself a Linux newb and am more concerned about getting broadsided by questions and terms that I do not understand during the process.

Is there a tutorial or walkthrough with pics on how to dual boot with a Minimal Install?

I think I'm more than capable, a few months ago I installed Slackware into a Virtual Machine with no problem.  It didn't seem any harder or more confusing than when I was installing Windows 95 and 98SE back in the day.

---

### Post by zvacet on 2010-03-19
You can find useful links [here.]("https://help.ubuntu.com/community/Installation#Minimal installations") if you want to install LXDE from synaptic install lubuntu-desktop or from terminal

```
sudo apt-get install lubuntu-desktop
```

---

### Post by phillw on 2010-03-20
> **javyn999 said:**
> I'd like to do a minimal install of 10.04 when it comes out, then install lxde or a minimal gnome on top of that myself, and then dual boot it with Windows XP.

Will the partition tool that comes with the Ubuntu Alternate/Minimal CDs let me do this the way the standard Ubuntu disc will?

Hi,

lubuntu has just launched the beta. You may like to give it a try. I've seen it reported that it is leaner, than a minimal install with lxde put on top of it.

I've done some pretty 'horrible' stuff to mine (like putting a full LAMP server onto it; I have my reasons) and it still boots really quick. With all the 'extras' on it, and nearly 1 GB of desktop files copied over, it still only uses 2.8 GB of Hard-disk space and uses (bearing in mind i have the LAMP server) 700MB RAM (out of 1GB, swap not being touched), and that's with the browser open and 8 tabs on it. Pidgin running AIM, MSN and Yahoo! chats along with 5 x IRC Channels open. 

I think you'll be hard pushed to find something leaner and meaner than that, with full GUI ;)

I've got an Intel Celeron M Processor 440 (typical laptop processor), coasting along at 85 - 90% idle.

Regards,

Phill.

---

### Post by javyn999 on 2010-03-20
Thanks Phil, grabbing the torrent now!  If that's the case and the Lubuntu is faster than a minimal with lxde on top, I'm definitely going for that!

If the beta just came out, does that mean that by April 29 we can expect an official version?

---

