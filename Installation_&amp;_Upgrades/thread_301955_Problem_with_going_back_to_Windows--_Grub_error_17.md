---
title: "Problem with going back to Windows-- Grub error 17"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Dawnshadow on 2006-11-17
I tried Kubuntu on my laptop, and (after several tries) couldn't get my wireless card to work, even with NDISwrapper. So I re-formatted the hard drive (it was too small to make dual-booting a feasable option) and reinstalled Windows XP from the system restore disks, then started the computer. Unfortuately, the restore CD didn't seem to restore the original boot functions, and it now gives me an error message. 

"Grub loading, please wait... Error 17."

Is there a way to restore the Windows boot options, or else set up Grub to work without a Linux installation? I've tried using a boot CD to go into the Windows Repair Console (and used 'fixboot') and that didn;t work. I found a plain, garden-variety XP disk, and am now installing from that (if it works, I'll just re-do my restore CDs over it) and it might work. I'll edit if it does.

---

### Post by adwait on 2006-11-17
Try running the windows rescue CD and use the command ```
fixmbr
```.

---

### Post by Dawnshadow on 2006-11-17
OK. I might've just used the wrong command.... ._.; Hold on; I decided to reinstall Kubuntu on a tiny partition instead of being patient and I'm waiting for it to finish....

I'll edit once I get to try this.

---

### Post by Dawnshadow on 2006-11-17
Um... I can't figure out how to edit. ^^; But this seems to have worked, aside from the commputer asking me if I want to start Win XP or Win XP when I start it. Both options start the same OS.

I'll have to try the next version of Ubuntu and see if it supports my network card. Thanks for the help.

---

