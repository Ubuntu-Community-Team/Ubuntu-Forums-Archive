---
title: "Nvidia help."
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by Grabbe on 2012-12-19
I just installed Ubuntu 12.10, and I've got a graphics card that Ubuntu-details doesn't recognize. It's a Nvidia 610M.

I have NOT installed any Nvidia or Nouveu drivers yet. But one of my games works already?!? It's not a low-performance game, neither high though.

Did I by any chance get the drivers preinstalled somehow?

Can I check this out somehow? I'm not so good with drivers etc.
What should I do? I've had troubles with bumblebee before, I don't want to do things without expert help. :) I don't have bumblebee right now, checked in synaptic.

---

### Post by Bashing-om on 2012-12-19
Grabbe; Hi !

I have no experience with 12.10, However, 12.04 install has the option to install 3rd party software upon installation. Perhaps 12.10 also presents this option ?
In any event, to see graphics card and related info; terminal codes:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```These outputs may answer your questions.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Grabbe on 2012-12-19
"External" card:

	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

Internal card, guessing some built into the mborad:

	Kernel driver in use: i915
	Kernel modules: i915

Thank you! Yeah, I check something about 3rd party soft. at install.

Just to be 100% sure, are these the correct drivers? The external card is correct according to the displayed model.

---

### Post by mysteriousdarren on 2012-12-19
It doesn't show up in additional drivers? You could just get them from the synaptic and install that way.

---

### Post by pierceTN on 2012-12-19
> **mysteriousdarren said:**
> It doesn't show up in additional drivers? You could just get them from the synaptic and install that way.

[http://ubuntuforums.org/showthread.php?t=2092472](http://ubuntuforums.org/showthread.php?t=2092472)

---

### Post by Grabbe on 2012-12-19
1. I can't bring up the "additional drivers" anylonger. o.O wtf...

2. mdarren: What drivers "should" I install? Don't the ones I have cut it??

---

### Post by Grabbe on 2012-12-19
The thing is that my 3D works... o.O but it doesn't recognize it somehow.

---

### Post by Bashing-om on 2012-12-19
Grabbe; 

Ah shucks,
Your 610M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: (bet ya gota install bumblebee to make it work correctly):
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)
[INDENT][INDENT]let us know how things work out <== BDQ

[/INDENT][/INDENT]

---

### Post by Grabbe on 2012-12-20
So you are telling me that it doesn't recognize it, everything else works correctly - but I would need to install bumble for EVERYTHING to work correctly? :(

---

### Post by grahammechanical on 2012-12-20
May I give some clarification?

The Nouveau (open source) video driver is the default video driver that is always installed. That way it is hoped that we get something like a working system. I found that from 12.10 the Nouveau driver was good enough to give me Ubuntu Unity 3D. I believe this is now true for 12.04.1. I do not have a hybrid video system.

Also, I have noticed that when we tick to install the third party software we also get the proprietary video driver installed and activated. Does that explain things a little bit?

You may have a working system but the video drivers do not take advantage of the hybrid video technology in that machine. Nvidia has not produced even an experimental driver for Nvidia Optimus technology. It has only recently announced that it is working on such a driver.

So, those with Nvidia Optimus technology have to turn to the Bumblebee project.

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

[http://bumblebee-project.org/install.html#Ubuntu]("http://bumblebee-project.org/install.html#Ubuntu")

[https://wiki.ubuntu.com/Bumblebee#Installation]("https://wiki.ubuntu.com/Bumblebee#Installation")

[http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html]("http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html")

Regards.

---

### Post by Bashing-om on 2012-12-20
Thanks grahammechanical; Well put.
(if it ain't broke, don't fix it)

---

