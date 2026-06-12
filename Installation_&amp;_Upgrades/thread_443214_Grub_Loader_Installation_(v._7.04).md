---
title: "Grub Loader Installation (v. 7.04)"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by nsivin on 2007-05-14
I use a PC workstation on which I just installed Edgy 7.04, double-booting with already installed Win2K. I did not want to use the Grub loader, but rather PQBOOT, a PartitionMagic utility that lets you log in consistently to one OS or the other without having to choose between them (in other words, it changes the active partition on the fly). 

According to _Beginning Ubuntu_ (2006 ed., for v. 6), during installation Ubuntu asked whether you want to install the Grub loader to the master boot record. I aimed to say no. The problem with v. 7.04 is that it no longer offers a choice, but does the whole installation in one go. 

Is there any way I can get the Grub loader out of the master boot record? I haven’t found any discussion of this question. If necessarily, I am willing to uninstall and reinstall Ubuntu, but I want to make sure that next time I can control the location and functioning of the Grub loader.

---

### Post by bulldog on 2007-05-14
You can just over write it with another bootloader.
But think again,what's the problem with GRUB?
Can PQboot more than GRUB?
I should give it a try,and if it's not working for you,you can replace it.

There are many options in the menu.lst you can change.
It boots ubuntu by default,but that can be easily changed in windows.
You can hide the GRUB menu if you like.
You can set the default 10 seconds before it boots in any OS to 3 for example.

But it's your choice :) just do what you want.

---

### Post by nsivin on 2007-05-17
I have indeed been using the Grub loader since, as I reported, Ubuntu 7.04 installed it in the Master Boot Loader without asking my leave. It will, as Heimo ways, do the job, but not the way I want to do it. 

Partition Magic offers two approaches to dual-booting, both of them as independent utilities. Bootmagic does very much what the Grub loader does. PQBoot is a very small utility that simply changes the active partition on the fly. What that means is that I can set the computer to keep starting up Ubuntu as soon I turn it on, with no need to choose anything. It will keep doing that until I need to use Win2K for something, and will then keep rebooting the latter until I change the setting again. 

That is exactly what I want, so that I can work in Linux until I need some MS function, which I may have to use over several reboots. As soon as I can, of course, I want to kick Windows off the machine entirely, but that can’t happen until the range of Ubuntu software expands a little more. The Gimp, for example, is quite an adequate replacement for Photoshop, but I need to use the sophistication of Illustrator for vector illustration as well. 

By the way, is there somewhere I can get detailed instructions on how to edit the Grub loader to change the choices it offers? I have found that “e” offers an editing screen, but there is no explanation about how to make what choices.

Thanks,

NS

---

