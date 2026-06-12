---
title: "can't do anything after installation"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by mutte on 2008-04-27
Hi there, 

With the release of ubuntu 8.04 I thought this was a new opportunity to get rid of Windows on my Dell Optiplex 320 but it's not going that well.This means I'm quite new to Ubuntu. 

So I put my on board ati radeon xpress 200 as default in the BIOS.
Because from earlier Ubuntu installation attempts I knew that there was going to be a conflict with my ati X1300. 



So now I'm using the on board one and I'll try to get the x1300 working when this problem is solved(or has it still something to do whit it ?) 

With the on board ati, I could boot the Livecd (without having to go in "save graphics mode"), from there I installed ubuntu on my HD (I kept one ntfs partition with music and movies).

The installation seemed to finish without any problems, but when I reboot, I see right after the Grub boot loader,  a blinking cursor, and in the middle of my screen an  "F" character and a little green rectangle the computer doesn't respond to anything. 

When I go into recovery mode I get the same symptoms and the memtest isn't working either.

I tried the alternative cd as well, but the very same thing happened. 

I've been googling for 2 days now but I can't find a solution to my problem.

Can anyone give me some pointers on this ?

Maarten

---

### Post by mutte on 2008-04-27
a little update: removing quiet and splash and adding noacpi acpi=off in grub doesn't help, still getting a blinking cursor, an F character and 2 little green rectangles in the middle

I have absolutely no clue :confused:

---

### Post by zgoda on 2008-04-28
I have to upgrade my Optiplex 320 box at work, currently running Ubuntu 7.04 (7.10 refuses to boot kernel). My plan is to install from LiveCD, then try one of 2 scenarios, which worked for me before: either install GRUB2 or LILO as bootloader.

I tried LILO with Debian Etch and it worked. Then I tried GRUB2 with Ubuntu 7.04 and it worked too, although this experience is not consistent (my colleague at work still has to enter boot sequence by hand at grub2 prompt). I'm only hoping the problem with kernel present in 2.6.22 has gone and I'll be able to boot my machine at all...

---

### Post by mutte on 2008-04-29
Problem solved: I used the alternate cd and installed lilo instead of grub, works like a charm now 

apparently this is a common issue for the dell optiplex 320, didn't know I had to look in this direction

---

### Post by zgoda on 2008-04-29
> **mutte said:**
> Problem solved: I used the alternate cd and installed lilo instead of grub, works like a charm now 

apparently this is a common issue for the dell optiplex 320, didn't know I had to look in this direction

For reference, did you specify any special kernel boot options at installation time, like pci=nomsi I had to use when installing Debian Etch?

---

### Post by mutte on 2008-04-29
> **zgoda said:**
> For reference, did you specify any special kernel boot options at installation time, like pci=nomsi I had to use when installing Debian Etch?

nope nothing 
I did use the ati on board video controller(with the VGA in the bios set to ON BOARD) for the installion, though.
When the installation was finished, he installed the fglrx drivers for the on board ati automattically after the first boot. 

I then switched the VGA controller to AUTO in the bios, attached my screen to the ati radeon x1300 and it worked fine.
don't know if this was necessary but when I installed earlier versions, ubuntu couldn't cope with those two video controllers at all.

---

### Post by zgoda on 2008-04-29
OK, I finally updated my 320. It took 3 hours of pain. I had to start installer with ```
hpet=disable
``` but then LILO did not get this option into its config. I had to boot with livecd, chroot into newly installed system to update /etc/lilo.conf and update lilo installation. But it was worth trying.

---

