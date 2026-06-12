---
title: "Putting 10.04 beta on a second partition, am I on the right track?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MattP220 on 2010-03-20
I want to put the beta of 10.04 on a separate partition, just to play around and have a look at it. 

What I'm currently running is Karmic on an external hdd, and with a separate /home partition, so I'm figuring that should be a straightforward install:

1. Go through install process as per normal
2. Select manual partition at the prompt
3. Give the 10.04 install its space (it's a 1TB drive, so I've got plenty of unformatted space left)
4. Set /home to mount on my current /home partition, make sure "format" is NOT selected

Does that about cover it?

Also, should I just skip the step reinstalling the bootloader? I've already got Grub2 (or 1.97 beta, anyway) running on the external hdd.

I'm mainly just wanting to reassure myself I'm not missing a step or two in there. 

Cheers.

---

### Post by Mercury_Alpha on 2010-03-20
I wouldn't recommend using the same /home partition for multiple operating systems, even if it's just different versions of the same distribution. Your user directory contains configuration files along with user data. Those config files, and even directory structures, may change between versions of Ubuntu. This can cause system or application confusion when config settings conflict or when files are expected to be found in different folders.

Go into your home folder in Nautilus, press Ctrl+H, scroll down a bit, and you'll see all those application folders I'm talking about.

I'd recommend making a smaller temporary /home for Lucid, for testing purposes until you decide if you want to go forward with upgrading from 9.10 to 10.04.

In my experience, the best way to test out an operating system is through VirtualBox, or whatever virtual machine software strikes your fancy. However, Lucid has not been playing well with VBox.

---

### Post by lemming465 on 2010-03-20
I do parallel installs of different versions quite a lot.  A couple of suggestions:

* I usually like to put the bootloader for the new, experimental version directly on its own partition.  Your main OS bootloader can then chainload the new partition, more or less the same way you would dual-boot windows.  This both lets you test the new bootloader (if any), and means that reinstalls on the spare partition don't require making any further updates in your main bootloader.

* While it's OK to share a home directory between different versions, there are downsides.  The main issue is that if Gnome or Firefox or something has changed representations of data such as configuration files, the resulting conflicts will drive you batty.  I usually prefer not to.share home directories between different versions for this reason.

---

### Post by MattP220 on 2010-03-20
Cheers guys, that tells me exactly what I needed to know.

---

