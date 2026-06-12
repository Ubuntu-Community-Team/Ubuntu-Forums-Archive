---
title: "live cd broke my raid"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by chavy85 on 2010-02-24
First off i'm a little pissed off. the live cd SHOULD NOT TOUCH my hard drives.
i have a gigabyte ep45-ud3p with the ich10r. i have 2 320 gb drives in raid 0. so i want to try out this linux thing. boot to the live cd with "no changes to your computer" see that it's kinda ok.  try and reboot back to windows. and apon reboot get a message that i now have 2 offline members WTF?
your live cd is not supposed to touch my hard drives. i'm beyond pissed off. 

so any fixes?

---

### Post by PRC09 on 2010-02-24
I know nothing about raid but did you happen to change the boot order in your bios to enable boot from cd?

---

### Post by chavy85 on 2010-02-24
yes i know how to change my bios settings. it's always set to boot to cdrom first, then usb hdd then hdd. i know the bios is set right. i want to know why the live cd wrote metadata to my drives and killed my raid 0.?

i also what to know how to fix this and not loose everything.

---

### Post by TehCrucible on 2010-04-11
The live CD did not "break" your raid, ignorance did.

Now I'm no guru, but I'm guessing that you would have accessed your RAID drive(s) while playing around in the live CD.  As far as I understand it, you needed to install RAID related packages BEFORE accessing these drives so that ubuntu can understand what its looking at.  (I believe it sees them as two separate drives unless told otherwise)

How do I know? Because I did the same thing haha!  Anyway, you can find more information [here]("http://ubuntuforums.org/showthread.php?t=741209") and [here]("http://ubuntuforums.org/showthread.php?t=408461").

As for how to fix (assuming your still looking?), I don't know but I'm sure that being polite will get you a lot further in the future.

Good luck!
Jamie

---

### Post by iSTRONG on 2010-07-14
OP,

This is indeed a bug... a very annoying one too.
You didn't do anything wrong. I encountered the same problem & it scared the hell out of me. Thought i had lost my array.

more info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380138]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380138")

(P.S.): The fix is to turn off your computer on and off twice. (not just restart but on and off).

---

