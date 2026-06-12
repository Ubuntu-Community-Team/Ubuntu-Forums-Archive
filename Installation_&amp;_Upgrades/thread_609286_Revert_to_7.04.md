---
title: "Revert to 7.04"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by zmzach on 2007-11-10
So I installed gutsy and it's fine other than i'm having major problems with firefox freezing up when javascript is on, and even sometimes when it is not. It seems no one knows how to solve this, so I'd like to rever to 7.04, where everything worked fine.

What is the simplest way of doing this without having to wipe the drive etc . . .

---

### Post by Nano Geek on 2007-11-10
Before I start let me say this. I haven't tried these instructions so even though they should work, they might not. The worst that could happen is that you would have to reinstall.

Anyway, first type this into the command-line.```
sudo gedit /etc/apt/sources.list
```Do a find and replace replacing **gutsy** with **feisty**, save and close the file, then run this.```
sudo apt-get update
```Then open Synaptic and click **State=>Installed=>CTRL-A in the programs list=>CTRL-E=>Select Feisty instead of Now=>Click Mark all Upgrades. **That should to it.
Hope it works.

---

### Post by Nano Geek on 2007-11-10
Sorry, I got it wrong the first time. But it should work now.

---

### Post by MadMac on 2007-11-23
Nevermind, I had to do a clean install of 7.10.

Thanks anyway!

==============


Howdy!

I would like to try this, but I am confused about the bit with Synaptic.  I'm still a noob, so be gentle.  :)

Thanks!


> **asjdfwejqrfjcvm msz34rq33 said:**
> Before I start let me say this. I haven't tried these instructions so even though they should work, they might not. The worst that could happen is that you would have to reinstall.

Anyway, first type this into the command-line.```
sudo gedit /etc/apt/sources.list
```Do a find and replace replacing **gutsy** with **feisty**, save and close the file, then run this.```
sudo apt-get update
```Then open Synaptic and click **State=>Installed=>CTRL-A in the programs list=>CTRL-E=>Select Feisty instead of Now=>Click Mark all Upgrades. **That should to it.
Hope it works.

---

