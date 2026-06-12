---
title: "Intall K/Ubuntu w/o Software"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by systemarpi on 2008-03-14
[SIZE="3"]Hi everybody, I have a problem, I am a Linux Developer, I am working in a ERP/CRM Open source Software for Linux right now, but sadly I discover that a lot (kind of ALL) people wants to use my software under Windows, since my project is not portable to that OS I was wonder to share my software under a K/Ubuntu VM.

The problem is that K/Ubuntu installs a lot of things that are not useful (for a VM), I mean, is there a way to install only the essential part? (I mean core + kde).

Rigth now I have setup a Freespire VM for some users of my software but that’s a 2GB VM for a 2mb + DB size software.

I need to work under a KDE or GNOME desktop, since my software was made for them.

Or, if you have a “better” way to share a no-portable app to M$ Windows users, please help
[/SIZE]

---

### Post by taurus on 2008-03-14
You can try

```
sudo apt-get update
sudo apt-get install kde-core xorg kdm
sudo /etc/init.d/kdm restart
```

That would give you the core of KDE.

---

### Post by systemarpi on 2008-03-14
> **taurus said:**
> You can try

```
sudo apt-get update
sudo apt-get install kde-core xorg kdm
sudo /etc/init.d/kdm restart
```

That would give you the core of KDE.

Is that going to remove all the software? If it does, would be very nice.

So… I need to install everything “normal” and then remove things?

---

### Post by taurus on 2008-03-14
What do you mean by removing all the software?  What are you running right now?  Are you running the full blow KDE--Kubuntu?

---

### Post by systemarpi on 2008-03-14
> **taurus said:**
> What do you mean by removing all the software?  What are you running right now?  Are you running the full blow KDE--Kubuntu?

I mean, I dont need video player, music player, text editors, graphics software, I need nothing else than the core and the desktop (I guess)

I mean, I want to share my app, for Linux users, my software can be downloaded and installed in a DEB package, but for Windows users, that&#8217;s no easy&#8230;. I was wonder to share a VM with K/Ubuntu with my app on it so Windows users could try my app, but in a VM the users need almost nothing&#8230; since &#8220;everything else&#8221; apart from my app would work in their &#8220;real&#8221; Windows machine.

What I want is the most compact way (in HD size) to install K/Ubuntu, so the people wouldn&#8217;t have to download a 2GB K/Ubuntu VM to try my software.

I am running another distro for my development; I have nothing right now for my VM

---

### Post by zvacet on 2008-03-15
Maybe [this](http://www.psychocats.net/ubuntu/minimal#barebones) is what are you looking for.After install follow taurus advice and run commands he provided.

---

