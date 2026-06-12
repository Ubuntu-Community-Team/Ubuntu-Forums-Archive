---
title: "Convert my Kubuntu install to a virtual machine?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by mrming on 2007-03-06
I'm new to Linux and have installed my Toshiba M400 tablet pc as dual boot Kubuntu and Windows XP Tablet PC edition.

It's taken me over a week to configure Kubuntu but now it's running sweet and the performance is knocking my socks off!

Unfortunately I can't do without proper tablet functionality (handwriting recognition etc) so I need to stick with XP tablet PC edition for the moment. I also need to run Adobe Photoshop and Illustrator (I'm a graphic designer).

So I've realised that what I need to do is run Kubuntu inside Windows XP Tablet PC Edition as a Virtual Machine. I've spent ages setting up my Kubuntu install for the M400 and the last thing I want to do is do it all again, So what I'd like to do is convert my Kubuntu install into a virtual machine and run it via vmware in Windows XP Tablet PC Edition. Has anyone converted a Linux install to a virtual machine for installation in Windows XP and if so how did you go about it?

Any hints or tips would be greatly appreciated...

:)

---

### Post by bcw on 2007-07-03
VMware has a free tool that abstracts an existing Windows install into a VM.  I haven't looked at it for several months, and don't know if it also will abstract a Linux install.

As a separate possibility, a knowledgeable VMware mechanic can set up VMware to run a native OS install, so that if you had a dual boot system, you might run the other OS in a VM.  A danger there is that you should avoid mounting the partition of the other OS at the same time to avoid cross-writing.  If you understand enough to do this, you understand the danger.  In this way, you could have access to both at the same time.

I did the reverse of what you did - I abstracted my Tablet XP install into a VM, and run it within Kubuntu (better security).  The handwriting recognition and speech recognition work.  I did a bit of experiment to get the TIP available in Kubuntu, but haven't looked at it for a while.

I use xstroke and xvkbd for text input directly in Kubuntu.  I tweaked the fitaly layout in xvkbd to get me access to all the punctuation (programming) characters I need, and I'm pretty happy with it.

Cheers,
Bret

---

