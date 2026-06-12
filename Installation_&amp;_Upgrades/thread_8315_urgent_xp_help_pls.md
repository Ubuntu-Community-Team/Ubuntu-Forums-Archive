---
title: "urgent xp help pls"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by vic on 2004-12-16
i had a multiboot xp system (hp pavilion). Tried to install ubuntu from cd to a new disk partition. Installation aborted with an error. System refuses to boot xp from disk. Can only boot from windows setup cd. How to regain xp from disk ?
Many thanks in advance

---

### Post by Rancoras on 2004-12-16
Without knowing what the error was, there's not much we can do.  Does grub start?  If so, can you press ESC and get the menu?  If so, what happens when you select Windows XP?  The more information you provide, the better we can help.

---

### Post by wulf on 2004-12-16
What was the Ubuntu installation error and how far through the process had you got? It's possible that you have some other problem with the disk that has come to light with the new install but which would have got you in the end. A while ago I remember working with Win2K on a new machine and getting lots of problems. Frustrated, I stuck Linux on - I still got problems, but this highlighted some serious problems with the disk itself, which Win2K didn't make so explicitly clear.

The solution in that case was a new disk, Linux on it from the start ( ;) ) and forward from there. If you've got data you need on your XP partition(s), it might be more tricky in your case... perhaps a LiveCD of some flavour could boot the machine and let you see what's going on with the hard drive?

Wulf

---

### Post by vic on 2004-12-16
I am not sure where the installation process ended, but it was very soon after specifying the installation disk. Believe it was installing packages.
The error I am currently getting is ...

quote
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
unquote

Not sure who or what is generating this.

Thanks again

---

### Post by vic on 2004-12-16
i have been able to boot fro; the live cd. I can not detect anything wrong with the hard disk. all ideas appreciated.

---

### Post by gheorghe_pop on 2004-12-16
hello!
it's not a disaster.
you have 2 solutions:
1.try and reinstal ubuntu,or another linux distribution
2.try to install another boot loader(search with google for it)
keep in touch!

---

### Post by vic on 2004-12-16
tried to re-install ubuntu. Same error again. This time I wrote it down  =D> 

quote
install the base system
base system installation error
the debootstrap program exited wiht an error (return value 1)
Check var/log/messages or see virtual console 3 for the details
unquote

Should I skip to 'install the lilo boot loader on a hard disk ???

Cheers

---

### Post by vic on 2004-12-16
Skipping to the lilo boot loader didn't work, so  :confused: again, completely

---

### Post by Juergen on 2004-12-16
Try booting the XP install-cd and then going to the 'R'epair-console.
AFAIK you have then two commands, fixmbr and another fixblah (don't remember). Try fixmbr.

After that I'd suggest to burn a new Ubuntu-CD, maybe you have a read-error somewhere. Then (try to) install Ubuntu again.

---

### Post by vic on 2004-12-16
Thanks.

On XP, I tried the obvious recovery tricks ; fixmbr, fixboot, copy ntloader, ... . To no avail.

Tried to install suse linux. It got stuck in its install as well.

It have the impression that the ubuntu installation has set a partition on the cd as 'active partition'. It must have done this somewhere on the harddisk, but I can't locate where.


Help Pls

---

### Post by Juergen on 2004-12-16
On the live-cd should be something like 'cfdisk'.
With that you can look at the flags of your partitions.

But the installer doesn't change this, normally.

---

### Post by gheorghe_pop on 2004-12-16
if cfdisk doesen't work try this:
boot from the windows cd and run fdisk
Check your partition table.
See that you don't have erors in alocating partitions.See wich is your primary partition.


What version of ubuntu are you installing?

---

### Post by adbak on 2004-12-16
Have you tried installing WinXP on the second partition?  Give that a try.  If there's still a problem, there's probably an error on the disk.  But, if you do manage to find a way to boot your first partition Windows up, then make sure you backup all your necessary files before doing anything else.

---

