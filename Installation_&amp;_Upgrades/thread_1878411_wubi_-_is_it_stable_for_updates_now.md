---
title: "wubi - is it stable for updates now?"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-11-09
I stopped helping newcomers to go in the wubi direction around the time of Grub 2 introduction because it seemed that some updates, possibly related to grub, were causing trouble and making life complicated. And I am now out of touch with wubi use.

What is the situation now? Is wubi seen as stable against updates please? If so, what is the current advice for wubi use - short term only? Why? not stable?

I ask, and would appreciate comments, because I am coming across newcomers, and wubi could easily be a candidate.

Tia

---

### Post by mastablasta on 2011-11-10
> **candtalan said:**
> I stopped helping newcomers to go in the wubi direction around the time of Grub 2 introduction because it seemed that some updates, possibly related to grub, were causing trouble and making life complicated. And I am now out of touch with wubi use.
 
What is the situation now? Is wubi seen as stable against updates please?
 
It is the same as before. the situation is easilly solvable by tunring off the updates that reloaded grub. otherwise the whole thing has to be restored. mor einfor is found in the wubi megathread here on forums. other updates are ok.
> 
 If so, what is the current advice for wubi use - short term only? Why? not stable?

 
it is ment to test the system not to run it continously and do upgrades, though i am sure it is possible.
 
the main issue is that Wubi loads everything into one virtual file on the windows system. if that files gets slighty corrupted you can loose everything you have stored in your wubi linux. so wubi is great to try out the OS, but it is not recommended for prolonged use. a side by side dual boot is much better solution in that case. 
 
side by side is easy. 
1. create empty disk space
2. install to largest empty disk space. the rest is automaticly done for you.

---

### Post by candtalan on 2011-11-10
Thanks for the comments!

> **mastablasta said:**
> 
2. install to largest empty disk space. the rest is automaticly done for you.

Is this 'largest empty space' install option now available again? (It was not in some desktop versions  not too long ago)
tia


==============
'Largest empty space' install option: have just run a live CD ubuntu 11.10 and the install options do not offer 'largest empty space'.
For ubuntu 11.10 alternate CD it is included, see attached image.

In this machine 'multiple operating systems on this computer' (and several HDs) I see offered only: 
install alongside, erase disk and install, something else (manual).
I wonder if I see different options if I use a machine using only a single HD?

---

### Post by Mark Phelps on 2011-11-10
> **candtalan said:**
> Is this 'largest empty space' install option now available again? (It was not in some desktop versions  not too long ago)
I believe that this option is no longer available -- unless they put it "back" for 11.10.  Removing this was a MAJOR source of problems when they did it because THIS option was the one that folks used most when trying to setup dual-boot machines.

---

### Post by darkod on 2011-11-10
I can't test right now, but did you check if it's offered in the next step maybe if you select "along side"?

For example, the option "erase and use whole disk" doesn't offer now to select the disk right away, but it does in the next step.

Installing onto unpartitioned space is along side in a way, so it might have been moved into a next step.

---

### Post by candtalan on 2011-11-11
> **Mark Phelps said:**
> I believe that this option is no longer available

Yes, thank you, as I found. 
It is NOT in the desktop version however 
it IS in the Alternate CD.

---

