---
title: "Make Virtual Machine Out of Exsisting Ubuntu Installation"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by Propheis on 2010-09-01
I recently installed Ubuntu on my Computer, and i have make a bunch of changes to it, and one day I thought, wouldn't it be nice to have Ubuntu running in Virtual PC for windows 7?

I'm a student and i LOVE Ubuntu, but i need a lot of the MS programs like OneNote on demand.


Is there any way that I can make my existing Ubuntu installation into a virtual machine without having to start from scratch?

Any help would be greatly appreciated :D

---

### Post by quixote on 2010-09-04
Unfortunately, I think the short answer is no.  I use virtualbox quite a bit, and you can move virtual machines around with a bit of fancy footwork, but I've never heard of somehow copying a real one to virtual.  

I guess, if you could figure out how to make a custom install CD based on your current installation (something that should be built in to Ubuntu!), then you could use that to install a virtual machine.  I tried to figure out how to make custom install CDs but had to give up after a couple of weeks.  (I'm not very good at programming-type things though.)  Unless you already knew how to do it, it would definitely take less time to just do a new virtual install and re-customize!

Incidentally, I'd think you'd be better off virtualizing Windows within Ubuntu, rather than the other way around.  That way any viruses, rootkits, badly behaved software, etc., etc., are all limited to the virtual machine.  In my experience, Windows actually runs faster in virtualization under ubuntu than it does in its own partition.  No idea why.

---

### Post by uRock on 2010-09-04
You can copy configuration files from the /home folder for themes and such and use them with a virtual install.

---

