---
title: "Keyboard/Mouse bug after upgrade to feisty"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Thomas Rasmussen on 2007-04-26
Hi

I have finished upgrading my edgy box to feisty fawn (actually an xubuntu which have ubuntu-desktop package installed afterwards).

If I boot up the computer the mouse and keyboard is VERY unresponsive in Gnome (I have autologon enabled), if I type a little fast half of the letters doesn't ge recognized. Mouse jumps a lot because it doesn't update.

If I then switch to a VT (CTRL-ALT-F1) then all (and I mean every single) keyboard inputs are recognized twice! (thus making text-mode logon impossible). If I login via SSH this works fine. If I boot my  old kernel (2.6.17-13) the keyboard and mouse works fine, but then network doesn't work (wireless via ndiswrapper) so this doesn't seem to be a solution .-(

The keyboard and mouse is USB wireless logitech, so guess there is some bug that does this?

What can I do? I really really need my box back (its my musicbox/cdplayer)
Thomas

---

### Post by Thomas Rasmussen on 2007-04-26
OK, apparently disabling ACPI in the bios solves the problem somewhat... however now it won't do suspend-to-disk which I'm using very much on this computer.... there must be a bug somewhere in the kernel?

solutions are welcome!

(just for the record, the keyboard works fine in bios, grup ad so on.

Thomas

---

### Post by Mongoose on 2007-04-26
Search [https://bugs.launchpad.net/ubuntu/feisty/](https://bugs.launchpad.net/ubuntu/feisty/) and make sure this bug is still filed.  I noticed several known UPSTREAM bugs in the kernel marked 'closed' with no fix/patch done for the ubuntu packages.  It's kind of annoying.  The worst example is a SiS kernel bug for PS/2 was waived because an Unbuntu dev tested on a 440BX and said "Works for me".  I don't know how this kernel managed to break input for so many motherboards and no one noticed until now?  It just proves sweeping bugs under rugs helps no one.  ;)

I guess I'm saying get ready to fight for your fix.  There are several input bugs out there, so you may want to google or search lkml for your issue.  If you find an upstream bug use that in your bug report to avoid the tail chasing the other bugs caused.  Good luck.  ^_^

---

### Post by Thomas Rasmussen on 2007-05-08
Just for info, read in this thread a possible solution to the problem: [http://ubuntuforums.org/showthread.php?t=414152&page=2](http://ubuntuforums.org/showthread.php?t=414152&page=2)

And it actually works fine for me... just added it (remember it must be on the actual line where defoptions is listed, ie:

# defoptions=quiet splash acpi=force irqpoll

(yes the #-sign is important) 

Thomas

---

### Post by Thomas Rasmussen on 2007-05-09
Apparently everything doesn't grow into heaven... found that the 'important' part was enabling irqpoll, unfortunately this will make hibernate stop working, which I use a lot on this particular computer...

I regret having upgraded it to feisty and kernel 2.6.20 as everything actually was working pretty good with edgy :-(

---

