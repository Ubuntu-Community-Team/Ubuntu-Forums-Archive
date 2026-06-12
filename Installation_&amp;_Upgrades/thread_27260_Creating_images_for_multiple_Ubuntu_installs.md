---
title: "Creating images for multiple Ubuntu installs"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by ckr on 2005-04-15
I'm wondering if anyone has any thoughts on a good process to create images of Ubuntu systems for "cloning" a set up system onto multiple systems with the same hardware.

We have tried doing so with Norton Ghost, but unfortunately at reboot grub does not seem to work. ](*,)   While that is probably recoverable, it is not ideal.  Actually doing a hard drive copy does work, but again it would be better to have an installable image.

Thanks,

---

### Post by accuser on 2005-04-15
You can burn an image of an install, but you will need to initialise grub for each to ensure that the disk is bootable.

Another way to achieve this is using the automated installation tool. I can't recall the location of the information about this, but search the main ubuntu wiki for this and I'm sure you will find what you are looking for.

---

### Post by ckr on 2005-04-18
Thanks for your response.

By initialize, do you mean something like grub-install or update-grub?

Is that something you could do from the live CD?

Thanks again.

---

### Post by RaverDK on 2005-04-26
I was reading on a other artikel on the net, and did fall ovre a link that might come you handy'
[http://www.systemimager.org/](http://www.systemimager.org/) 

Hope you and any one else can use this for cloning/system copying...

//RaverDK

---

