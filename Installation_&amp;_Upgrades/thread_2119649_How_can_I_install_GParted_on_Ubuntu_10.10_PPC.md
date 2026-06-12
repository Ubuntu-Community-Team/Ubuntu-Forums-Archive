---
title: "How can I install GParted on Ubuntu 10.10 PPC"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by aurora72 on 2013-02-24
Hello
I have just installed Ubuntu 10.10 PPC on my Mac mini G4 and everything works fine except that I cannot install a simple application called "GParted" on Synaptic Package Manager. I guess I need to add some Repsitory path to the Synaptic and I have tried adding one or two, but they failed with "cannot find/download from the respository" or something like that.

I'd like to learn

if there's a working repository for the Ubuntu 10.10 PPC
if there's way to install GParted directly from Ubuntu 10.10 PPC DVD (GParted is included when I run it as live DVD)

Thanks.

---

### Post by grahammechanical on 2013-02-24
This must be the day of the month for people installing versions of Ubuntu that are out of life. Ubuntu 10.10 was supported for 18 months. The repositories for 10.10 are now longer available because the software packages in them are no longer maintained.

If you open Synaptic Package Manager and look for Settings or something like that you may find that is is possible to put the 10.10 install CD as a repository and with a bit of luck you might be able to install Gparted from there.

Of course, you can run 10.10 as a live session and use Gparted that way. I do not see much point in learning about an operating system that is not only out of life but also out of style with the way things are done on the latest versions of Ubuntu. 

Regards.

---

### Post by aurora72 on 2013-02-24
Hello

And thank you for the comment. Well I particularly use U 10.10 because I don't want to use the 12.04+ versions as they contain the Unity interface. I remember having issues finding "Terminal" in Unity, among others. 

Now I have managed to install GParted in the old way: Compiling it all from source. 

Putting the Live DVD as a repository in Synaptic PM didn't work out. I guess it's because Live DVD contains some sort of compression for all the files.

---

