---
title: "Does anyone have Ubuntu 14.04 working on Skylake CPUs?"
date: 2016-07-12
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-12
I installed Ubuntu 14.04 on my Skylake CPU (i7-6700k).  It mostly works, except for a few things: I can't get any settings in the Control Center to work (Keyboard Shortcuts, Displays, etc).  I also can't launch a gnome-terminal: there's no entry for it on the right-click menu.  Without a Gnome-Terminal, I can't do anything (I need this for a development workstation).  There are probably more problems, but I haven't uncovered them since I can't use this installation for anything.

Here is one of the errors I received:
```
unity-control-center crashed with SIGABRT in g_assertion_message()
```

Has anyone successfully installed Ubuntu 14.04 on a Skylake CPU?

NOTE: I have installed Ubuntu 16.04 and it works.  That's nice.  But I need Ubuntu 14.04 for my project.

---

### Post by oldfred on 2016-07-12
The first Skylake came out on August 5, 2015**.**

And normally it takes Linux a while to catch up with kernel, support software & drivers to work with new hardware. 

What is unique about 14.04 that you must have it?
About the only way to get it to work, it to update kernel, support software & drivers (using ppas), so you have most of 16.04 under the hood. Only then the distribution software is not updated.

I built my new Skylake system last spring before 16.04 was final, but only installed 16.04 and have had no issues.

---

### Post by T.J. on 2016-07-12
> **UserJB said:**
> unity-control-center crashed with SIGABRT in g_assertion_message()

That  normally indicates a problem with GTK toolkit.  You may be having a problem with it, your video driver or perhaps the Compiz compositor that the default Unity interface uses.  Have you tried using an different interface like XFCE (Xubuntu 14.04)?

It's probably *not* your processor, even if it is a Skylake CPU. You are probably using a generic kernel, which should work fine.


> 
NOTE: I have installed Ubuntu 16.04 and it works.  That's nice.  But I need Ubuntu 14.04 for my project.

In the absolute worst case scenario, you would use Qemu/Virt-Manager to host a copy of 14.04 in a window for your project.  There is always a way.

---

### Post by Bucky Ball on 2016-07-13
> **oldfred said:**
> I built my new Skylake system last spring before 16.04 was final, but only installed 16.04 and have had no issues.

Same. I installed 15.10 first which worked fine then installed 16.04 LTS a few days later, sometime before official release. Forget the 15.10 option, though, no longer supported, and go for 16.04, as oldfred suggests, if there's nothing holding you to 14.04. 

I also have an Intel 6700 something (I'm 750kms away from the machine at the moment, but suffice to say it is not the overclocking version). 

Good luck.

---

