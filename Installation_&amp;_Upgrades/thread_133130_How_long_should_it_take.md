---
title: "How long should it take?"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by bokodasu on 2006-02-19
I'm installing on a Dell Inspiron 3800 laptop with a 5GB HD and 256 MB RAM.

It starts the installation - gets through the network setup and the partitioning and starts "Installing the Base System". Which, at this rate, seems like it should take several days. It is doing stuff - the filenames change, anyway - but it's said "6%" for about four hours now. 

I tried a few different things (since I started this process last night, and got suspicious when it spent more than an hour at 6%) - setting the bios to not do any power managment and changed the partition manually when I read the note about it halting abruptly with <256 swap partition (it automatically configured it to be something like 240). Hasn't seemed to make a difference. Should I just wait for it to do... something? What should I be looking for?

Thanks for the help.

---

### Post by az on 2006-02-19
No, it should not take that long.  You can check the cd's integrity.  If it has trouble reading a particular area, it may just take a long time before it fails - I dunno.

Once you boot the installer and pick your keyboard, you can select the cancel option (not continue - I forget what it's called) and that will drop you to a menu.  Pick the check cd integrity option and see if that is your problem.

If that does not reveal anything, you can go ahead with the install and switch to the error console to see if there is anything noteworthy there:  CTRL-ALT-F3 9CTRL-ALT-F1 to get back - F2 is a shell)

---

