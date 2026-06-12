---
title: "Auto Codec downloads after upgrade to feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by SomethingCronic on 2007-04-21
Hi all, (first forum post but lurker for year or so now)  since upgrading from edgy to feisty I've lost many of my codecs. I could play mpgs and dvx files before, but now I have an error using Totem (I have similar errors using other players)- 

---
Video codec ISO-MPEG4/OpenDivx is not handled

You might need to install additional plugins to be able to play some types of movies.
---

Everything was fine before the upgrade, but correct me if I'm wrong - isn't Feisty meant to find the codec you need and give you the option to download it?

Synaptic has 'gnome-app-install' installed, (I guess this is the application that auto-downloads codecs), I've tried reinstalling but to no avail.

On a side note, beryl doesn't feel as smooth as she used to. Anyone else noticed this or do I just need to look at xorg.conf?

Thanks,

---

### Post by amendt on 2007-04-24
"isn't Feisty meant to find the codec you need and give you the option to download it?" my words exactly, I was happy with Fiesty improvments so much that I forgot that we still had a legacy of Microsoft made proprietary codecs to deal with.

---

### Post by SomethingCronic on 2007-04-24
I've ran a clean install of feisty since my original message and all works now. The fact I'd used automatix on my previous install probably caused the problem. Oh well.

---

### Post by GeDaMo on 2007-04-24
In Applications > Add/Remove programs, set Show at the top right to All available applications then search for "gstreamer plugin". Enable all the Gstreamer Plugin options.

---

### Post by SomethingCronic on 2007-04-24
I had installed all the gstreamer related items in synaptic but still to no avail.

The fact it didn't 'let me choose' was the problem. Nevermind, all working now :)

---

