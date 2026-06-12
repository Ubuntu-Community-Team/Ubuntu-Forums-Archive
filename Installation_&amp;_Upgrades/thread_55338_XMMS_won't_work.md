---
title: "XMMS won't work"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by Steve1961 on 2005-08-08
I've just installed xmms using the unofficla guide unstructions on hoary.  The problem is that when I try to launch it with the console I get the following message:

Gtk-WARNING **: Unable to locate loadable module in module_path: "libpixmap.so"

If I try to launch it from the menu nothing happens at all.

I first tried using the package manager to install, but although I could launch xmms it crashed the system whenever I tried to play a file, so I uninstalled and followed the instructions in the guide.

I've installed all the relevant codecs but as I'm new to linux I'm not sure what to do next.  Has anyone got any advice?

---

### Post by buster on 2005-08-08
"I first tried using the package manager to install, but although I could launch xmms it crashed the system whenever I tried to play a file, so I uninstalled and followed the instructions in the guide."

I would guess that your first install was OK but you were asking the program to play a file it didn't have the codecs for. But this is a guess. Crashing is pretty drastic and may indicate something far more serious.When it crashed it might have been worthwhile to go into Synaptic and look for xmms files and add to your machine anything about playing music. And then try again. My xmms works quite well in Ubuntu but I did add stuff.

---

### Post by [pl]ice on 2005-08-09
xmms will crash, eg. for plugins, from synaptic itouch disabled my keyboard...(after reboot ok) then playing wma ,if you don't have codecs , crashes it...

---

### Post by stretched_lobes on 2005-08-10
I downloaded my xmms from synaptic. I did not have any error messages, but it would not play. XMMS then froze and I was forced to kill it. Today I found this:


 [https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary)
 I followed the instructions and it works fine now. The only real problems I have had was with sound configuration. Also if you are having problems with Flash working in firefox use that tutorial also. They both work perfectly now. I am using Ubuntu 5.04.
I hope this helps. :)

---

