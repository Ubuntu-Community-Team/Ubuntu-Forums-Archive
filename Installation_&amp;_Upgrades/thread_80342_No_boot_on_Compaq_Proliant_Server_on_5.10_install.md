---
title: "No boot on Compaq Proliant Server on 5.10 install"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by dman535 on 2005-10-22
I am running a pII 450 Compaq Proliant 3000 - with a Compaq 3200 SCSI array. 

I am new to the ubuntu world - tried a 5.10 install, which worked fine. When the system went to reboot - I got the following errors:

Fatal: Error inserting fan...

Fatal : Error inserting thermal...

ALERT! /dev/ida/c0d0p1 does not exist. Dropping into shell.

Any ideas ? Have tried to reinstall about 4 times with the same result.

Thanks

Derek.-

---

### Post by paul{nl} on 2005-10-22
I think these threads should help you out:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)
[http://ubuntuforums.org/showthread.php?t=78892](http://ubuntuforums.org/showthread.php?t=78892)

I'm also have boot problems, I'm downloading the installation CD right now, and hope to fix it.

---

### Post by dman535 on 2005-10-23
I tried to reinstall grub - it took but didn't fix the problem. System boots up ok from the live cd. Still getting a /dev/ida/c0d0p1 does not exist. Dropping to a shell

Is it looking for a cd rom ? what is it that the o/s is looking for ?

Thanks

D.-

---

### Post by Jeroensum on 2005-11-10
I having the same problem on a Compaq ML350 (667 processor model) with a 221 smart array controller.

The bootmanager is looking for the first primary partition on the RAID device where the OS should be located.

My gueass is that the RAID driver for the Compaq Smart Array has been upgraded or has not been properly implemented on Breezy. The thing I'm trying to figure out right now is if there is a proper driver there and if I can use the driver from the Hoary release instead. I've installed Hoary (5.04) as a temporary rollback and it boots like a charm.

[EDIT]
-SOLVED!-
There is a proper driver there but somehow the installation is oblivious to it and doesn't add it to the /etc/mkinitramfs/modules

With a little help form the search and a BIG help from a guy named VJSHAH (he wrote a small how-to somewhere on the forum) I was able to fix the problem. The how-to he wrote however was a bit hard to follow so I'll post my own here. Hope he doesn't mind.

=======================================================================================================
1. Use your install CD to boot into rescue mode (insert CD and type "rescue" at the Boot: prompt).
-When I did this the CD wouldn't go into rescue mode and gave me an error. I then chose the "run a shell" option from the install menu.

2. mkdir /target; mount /dev/ida/c0d0p1 /target (or whatever is your root partition. NB I did not have to provide any options. I did not have my partition map handy so I just mounted every partition on an empty dir and viewed the contents to figure out what was in each partition.)

3. If you created separate boot and usr partitions, mount the partitions on /target/boot and /target/usr (you are recreating the required tree under /target). You don't need any other partitions.

4. add cpqarray to /etc/mkinitramfs/modules (nano /etc/modules and add "cpqarray" as the last line).

5. chroot /target (now it looks like you are in your installation).

6. /usr/sbin/mkinitramfs -o /boot/initrd.img /lib/modules/2.6.12-9-686/ (this will build the new initrd.img in /boot).

7. Cd to /boot and verify that you are happy (I just ensured the new img was larger than the old one). Then backup the old img and rename the new img to the same name as the old img (initrd.img-2.6.12-9-686 for me).

8. Reboot. Everything went smoothly after that.
=======================================================================================================

---

### Post by WOteB on 2005-11-12
I also have a Compaq Proliant. Several Linux distros tried (Trustix, Red Hat, SuSE), but no way, until I used Lilo in steed of Grub. Now I'm running my Compaq with Debian 3.1 Sarge/Stable already 3 months without any problem.
So I think Ubunto also will run with Lilo.

---

