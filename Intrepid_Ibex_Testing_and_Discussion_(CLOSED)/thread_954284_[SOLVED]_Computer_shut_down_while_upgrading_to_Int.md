---
title: "[SOLVED] Computer shut down while upgrading to Intrepid! HELP!"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Saint Angeles on 2008-10-21
So yeah... i was upgrading to intrepid using "sudo update-manager -d" and my computer just turned off. It might have overheated or something stupid.

so now i try to boot into the hardy kernel and it keeps saying its a read only filesystem so i cant get anything to work! (you dont even wanna know what happens when i try to run the intrepid kernel)

i can't seem to get it to start x at all and any command i type into the shell is basically useless. what do i do?! i really dont wanna reinstall hardy again.

---

### Post by zolookas on 2008-10-21
Why do you think booting intrepid kernel is going to damage your system?

---

### Post by Saint Angeles on 2008-10-21
> **zolookas said:**
> Why do you think booting intrepid kernel is going to damage your system?
no thats not it... i tried booting the intrepid kernel and after freekin out about what video mode to use, it had a kernel panic.

---

### Post by zolookas on 2008-10-21
My guess is that you need to mount your root partition using live cd and then chroot to folder where your partition is mounted and run "dpkg --configure -a"

---

### Post by Saint Angeles on 2008-10-21
> **zolookas said:**
> My guess you need to mount your root partition using live cd and then chroot to folder where your partition is mounted and run "dpkg --configure -a"
would a hardy live CD be ok? i dont have an intrepid one because all my "700mb" CD-Rs are actually like 650 and they suck.

---

### Post by zolookas on 2008-10-21
> **Saint Angeles said:**
> would a hardy live CD be ok? i dont have an intrepid one because all my "700mb" CD-Rs are actually like 650 and they suck.
Every live cd should work as long it has chroot application. Or you can try booting into recovery mode if it allows you to write something to disk and running "dpkg --configure -a" (without quotes)

Steps you need to do in live cd:
1. Mount your root partition (easiest way is to click on your partition in places menu).
2. Open terminal and type "sudo chroot /media/disk" (replace /media/disk with path where your root partition is mounted if needed, it will probably be mounted at /media/disk).
3. Type "dpkg --configure -a" and wait until it finishes updating.
4. Reboot into intrepid and see if it works.

---

### Post by Saint Angeles on 2008-10-21
> **zolookas said:**
> Every live cd should work as long it has chroot application. Or you can try booting into recovery mode if it allows you to write something to disk and running "dpkg --configure -a" (without quotes)
that doesnt work. keeps saying its a read only file system.

sorry i cant post the output as i've only got one computer and i had to boot into windows to post this.

it sucks so hard. and now for no reason, my hardy CD is gone!

---

### Post by zolookas on 2008-10-21
Try to download some small distro like puppy linux and burn a cd or write it to usb flash drive.

---

### Post by Saint Angeles on 2008-10-21
problem solved!

i allowed my computer to rest overnight and opened it up just for kicks. i found a THICK (1-2cm) layer of dust between the CPU fan and heat sink! I got it all out and restarted. I booted into the recovery console.

i selected "dpkg" from the menu and it finished all the upgrades for me. there was still a little tweaking to do once i booted up the intrepid kernel. it took me a while to get the network manager applet going but now everythign is in perfect working order!

thanks for the help!

---

