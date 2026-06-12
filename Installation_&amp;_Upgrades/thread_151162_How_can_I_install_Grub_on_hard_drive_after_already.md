---
title: "How can I install Grub on hard drive after already making boot floppy?"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by mitch50 on 2006-03-27
Hello.
I'm new to here and glad to be here....

Ok, I just got done installing Kubuntu in a dual boot with Xp on a 80 gig hard drive partitoned into two..

Durring the Kubuntu install, I decided to install Grub to a floppy thinking that if I didn't have the floppy in the floppy drive, Xp would boot up fine. I was wrong..
I still have to have the floppy in to boot either Kubuntu or XP...
Both os's are running fine and I love the way Kubuntu looksl..

My question is, did I do something wrong durring the install?
Also, can I just put Grub on the hard drive now with out using the floppy  and if I can, how would I do it...

Thanks..

Mitch50

---

### Post by aysiu on 2006-03-27
I don't know how to transfer Grub from the floppy, but you can always try reinstalling Grub to the MBR:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by ajgreeny on 2006-03-27
I'm surprised that what you did won't let you boot windows without the floppy as this is what I did before I was certain about linux or ubuntu.  I was running Win98 at the time not XP, but it all worked exactly as you expected but didn't get.
Anyway to get to a normal mbr grub, from a running Kubuntu do
sudo grub-install /dev/hda
or whatever the disk is named as in /boot/grub/device.map
This should put the grub into the mbr of windows.  If something goes wrong you will at least still have the floppy to use.  Good luck.

---

### Post by mitch50 on 2006-03-27
Thanks so much for the reply. It's appreciated..

Ajgreeny, I did what you said and it worked like a charm..

Now I have to read up on how to install apps for my 5.10 Kubuntu..

Thanks again...

mitch50

---

### Post by ajgreeny on 2006-03-28
To install applications use synaptic.  It is totally brilliant; a better way to get things even than in windows.  I've been on (K)ubuntu now since July last year and hardly ever boot into windows now as ubuntu does everything I need, and of course, does it safely!

---

