---
title: "&quot;base Ubuntu system&quot; VS &quot;command-line system&quot; installation"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by limp on 2011-01-25
Hi all,

I have a small query regarding Ubuntu installation.

Is a "base Ubuntu system installation" the same as a "command-line system installation"? I guess it is but I would like to be sure about it.

Thanks a lot.

---

### Post by fabricator4 on 2011-01-25
> **limp said:**
> Hi all,

I have a small query regarding Ubuntu installation.

Is a "base Ubuntu system installation" the same as a "command-line system installation"? I guess it is but I would like to be sure about it.

Thanks a lot.

No, it's not, though it comes down to semantics the way you've worded it.  A base Ubuntu system installation give you a system that boots into command line only - no graphical system at all.  When you boot, it boots (very quickly!) into command line.

A command line system installation (ie installing using a command line installer) would be using the alternate CD installer to install a full version (or any other version if it come to it) of Ubuntu using the command line installer.

Semantics, as I said.

Chris

---

### Post by limp on 2011-01-25
> **fabricator4 said:**
> No, it's not, though it comes down to semantics the way you've worded it.  A base Ubuntu system installation give you a system that boots into command line only - no graphical system at all.  When you boot, it boots (very quickly!) into command line.

A command line system installation (ie installing using a command line installer) would be using the alternate CD installer to install a full version (or any other version if it come to it) of Ubuntu using the command line installer.

Semantics, as I said.

Chris

Thanks a lot for your quick reply Chris!

I see the difference know. I got confused by the following sentence: ```
https://help.ubuntu.com/community/Installation/LowMemorySystems

To **install a base system**, boot from any Alternate CD and 
choose "**Install a command-line system**."
```

What I want is a minimum Ubuntu system without the graphical GUI, so I guess a base Ubuntu System is what I want. Do you happen to know where can I find more info about what is included in a base Ubunty system? That is, I would like to know exactly what is installed (Linux kernel, X packages, etc).

Kind regards.

---

### Post by fabricator4 on 2011-01-25
> **limp said:**
> I got confused by the following sentence: 

What I want is a minimum Ubuntu system without the graphical GUI, so I guess a base Ubuntu System is what I want. Do you happen to know where can I find more info about what is included in a base Ubunty system? That is, I would like to know exactly what is installed (Linux kernel, X packages, etc).

Kind regards.

Oh, well the way that is worded, yes they mean the same thing! :-)

A base install would not have any X window system at all to start with.  The [Ubuntu documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") on installing on low resource machine deals with a base install and tells how to add things like basic X functionality. In it's most basic form you can even choose which shell to install, though bash would be installed with Ubuntu.

You could also do a base install of Debian from which Ubuntu is derived.  The Linux Bible (2009) by Christopher Negus might a good resource as it explains how to do this from scratch.  You might be able to download the PDF.

It's something I thought a lot about at one stage, but one of my requirements is fairly extensive photo editing capabilities which means gnome or KDE has to be available.  Add to this the excellent support from the Ubuntu community in the way of stable releases, maintenance and updates, plus the fact that Gnome is really quite streamlined and efficient and well... my minimalistic desires had to give way to reality.  I can certainly see the point for a server machine though.

I also get a kick out of showing people Linux on my EeePC.  While a minimal install would be good, it just wouldn't have the ooser appeal that gnome has.

Chris

---

