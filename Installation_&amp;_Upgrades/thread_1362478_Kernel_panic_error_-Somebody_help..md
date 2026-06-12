---
title: "Kernel panic error -Somebody help."
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-12-23
I was using my computer few minutes ago, thenIshut it down, now I am trying to start it I am getting the following errorr.
[6.638104] Kernel panic not syncing.
VFS:Unable to mount root FS on unknown-block(8,2).
What shall I do ?
I have forgot to mentionned I have run updae manager to update some files.

---

### Post by ajgreeny on 2009-12-23
Was there a new kernel in the updates?  If so choose the older kernel from grub and see if that boots OK.  If you get no grub menu, either hit esc when you see "starting grub" for legacy grub, or shift for grub2.

---

### Post by hoboy on 2009-12-23
when I start there is something called Generic 16 when I run that I get the following error.
[6.638104] Kernel panic not syncing.
VFS:Unable to mount root FS on unknown-block(8,2).
Generic 14  bellow boots.
what shall i do ? to run generic 16 witch is the first one when ubuntu start.

---

### Post by hoboy on 2009-12-23
I have tried to run recovery mode of generic 16.
I get the following error:
Wn-block(8,2)
Pid: 1, comm: swapper not tainted 2.6.31-16-generic #ubuntu

---

### Post by hoboy on 2009-12-23
I am a  desperate

---

### Post by hoboy on 2009-12-23
Bump

---

### Post by ajgreeny on 2009-12-23
I am fairly sure that karmic came with a 2..6.31-14 kernel when installed so there should be an older kernel you can try to boot ie the generic.14 (or anything other than generic.16) which should show in the grub menu.

---

### Post by hoboy on 2009-12-24
> **ajgreeny said:**
> I am fairly sure that karmic came with a 2..6.31-14 kernel when installed so there should be an older kernel you can try to boot ie the generic.14 (or anything other than generic.16) which should show in the grub menu.

waht do you mean by "try to boot ie the generic.14 (or anything other than generic.16) which should show in the grub menu." ?

---

### Post by ajgreeny on 2009-12-24
> **hoboy said:**
> waht do you mean by "try to boot ie the generic.14 (or anything other than generic.16) which should show in the grub menu." ?
When your grub menu appears it should show more than the original two options for ubuntu.  The installed version was ubuntu kernel 2.6.31-14 and you would have had the chance to boot to that as normal user or in recovery mode.

When you updated at some point the newer kernal 2.6.31-16 was added to your system, and you should now have four options to boot, the first two will be the 2.6.31-16 kernel in user and recovery mode, and just below that the 2.6.31-14 kernel should be available also in user and recovery modes.  Using the cursor arrow keys go down to the 2.6.31-14 kernel and then hit enter to boot it.  Ignore the recovery modes at the moment, justv use the normal boot mode.

If you do not see a grub menu at boot time, when you see "starting grub" on screen, quickly hold down the shift key and the menu should appear.  If using legacy grub hit esc key to see the menu.

EDIT:
OK, silly me!  I have just seen that you already said the 2.6.31-14 kernel will boot for you, which I missed before.

If I were in your position, I would simply boot to the older kernel and then use synaptic to remove the newer kernel and continue with the older 2.6.31-14 version.  There is really no great disadvantage to the slightly older version, and as it will boot but the new one won't, there is no real choice.

---

