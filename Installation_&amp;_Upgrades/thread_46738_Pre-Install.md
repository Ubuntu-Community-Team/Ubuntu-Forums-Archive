---
title: "Pre-Install"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by SilentGreg on 2005-07-05
Hello everyone, first post! First off I would like to say that I am not new to Linux but I am new to Ubuntu and apt-get. I am coming from a solid Gentoo background but lately I have become very annoyed with the compile errors that I am running into. So, for a short-while I am switching to Ubuntu until I get around to getting a full Gentoo system running where I don't have to remove every single hair strand off of my scalp; attempting to complete the install. 

I have a few questions pertaining to apt-get and Unbuntu in general.

1. I have an on-board ethernet controller. I know from experience that there is no built-in default modules for my kernel. With that said, I will install Ubuntu without my ethernet controller; however, since I will not have internet access, how will I go about getting the Linux Headers (and for that matter, GCC) so I can compile the needed module for my ethernet controller? Any ideas? Maybe if I were to download and then burn them to CD prior to install?  :-? 

2. Similar to the above question, is GCC included in the install off of the CD or will I have to run apt-get install gcc?

That's it for now, thanks for any help!

Greg

---

### Post by Sye d'Burns on 2005-07-06
1. You nailed it. It'd be best to download the headers prior to install.

2. You'll want build-essential and GCC as well. They're not on the install disc. 

Good luck :)

---

### Post by SilentGreg on 2005-07-06
[QUOTE=Sye d'Burns]1. You nailed it. It'd be best to download the headers prior to install.

2. You'll want build-essential and GCC as well. They're not on the install disc. 

Good luck :)[/QUOTE]

How would I go about getting the headers, and then putting them back? I don't know where I can get the exact version that comes on the install CD, but I guess I would put them back in /usr/src/linux.

Also how would I, just like the headers, get GCC onto a CD and the build-essintial package?

Thanks.

Greg

---

### Post by darkmatter on 2005-07-07
You should also grab the Unofficial Ubuntu Add-Ons CD from one of the links in this thread [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147).

It has the build-essentials packages (for gcc, etc.) as well as the most needed applications for your Ubuntu system.

---

