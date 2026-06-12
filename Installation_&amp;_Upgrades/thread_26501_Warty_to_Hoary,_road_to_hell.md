---
title: "Warty to Hoary, road to hell"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by matgorb on 2005-04-13
Yesterday I decided to update my work machine from Warty to Hoary, a little visit in Synaptic to change de repositories, and update.
First of all, the download keeped  making errors, I had to relaunch it several times to be able to download all the package.
Then I got incompatibility issues on my firestarter settings, which disappeared only after I decided to lose my settings! But finally it updated, I rebooted, everything "seemed" fine so I went home.
This morning, boot, mozilla, try play some audio in the browser...nothing, try to launch skype...no sound, impossible to connect, apparently they can't find my /dev/dsp anymore.

What the? This does not qualify as an upgrade for me, it does less than before. I have to boot into xfce, which I like so it will be fine until a fresh install, to get some sound. Is it just me, or what?

---

### Post by dusu on 2005-04-13
Hi,

there have already been many posts about sound issue in hoary.
Basically, in Gnome :
- either you have to make sure your programs (like xmms) use the esd output plugin
- or you have to disable the sound server on startup in Gnome, and then use the Alsa output plugin.

---

