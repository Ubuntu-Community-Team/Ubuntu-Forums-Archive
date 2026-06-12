---
title: "New installation: Unable to load operating sys"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2006-11-11
"Error loading Operating System"

I had too much difficulty downloading a version of 6.10 that matched the official MD5 check so I went back to 6.0.6.1. I installed it on the pata disk which does not have windows. It is a blank disk. I changed the bios settings for the boot order. Everytime I try to run linux I get the error loading system message and it fails. 

The other drives are a mirrored raid pair with windows on them, and a HD with my data on it. The linux boot drive is a slave.

My MB has only two sata connection on it. I would be surprised if this is a manefestation of the sata problem because on the other board  the Ubuntu would not install at all. On this one it has installed and it is not a jmicron HD/ raid controller.

I suspect the only solution is to install Ubuntu on the raid drive but I am fearful of breaking the raid connection. I have switched it on in the bios. Will the automatic installation deal with the raid drive? There is some warning that comes up on boot up about notusing the standard linux raid driver with the eprom rade setup.

Robin

Robin

---

### Post by Robbyx on 2006-11-11
Re Raid:
This is the actual warning:

If you want to install the Linux default partition Raid driver please do not use the Oprom creation operation.

Does this mean that having set up the pair of drives as raid mirrors via the bios I can not use the Ubuntu raid driver that comes with the installation disk?

I hope someone can help me out of my problems.

Robin

---

