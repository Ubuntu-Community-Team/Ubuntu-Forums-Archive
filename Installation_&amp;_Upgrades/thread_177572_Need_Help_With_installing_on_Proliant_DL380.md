---
title: "Need Help With installing on Proliant DL380"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by linuxgoojoo on 2006-05-16
I'm tryin to test out and use ubuntu. i have had experience with other distros(mandrake, slackware, Red Hat, Fedora), and i have heard alot of good things about ubuntu. I have a Compaq Proliant DL380 with an 18.2gig and 2 9.2gig Hard drives in the smartarray. I have the compaq smart start CD. I am using raid-0. I go through all the setup and get it ready for the OS to be installed. I  drop the cd in and boot it up. It loads everything, until it gets to searching for hard disks. It finds the new hard drives. Its shows:
....
cpqarray: Finding drives on ida0 (integrated array)
cqparrar isa/c0d0: blk=512 nr_blks=35520480
cqparrar isa/c0d1: blk=512 nr_blks=35553120
 /dev/ida/c0d0: _
....

I just hangs there. It doesnt do anything after that.


Anyone have any ideas? Any help is much appriciated. :mrgreen:

---

### Post by linuxgoojoo on 2006-05-17
Any ideas?

I guess it would probably be time to give this server away and go buy another one. I'm going to try to slap mandrake or slack on this server. I would still enjoy to try out this distro, but i'm going to go with one that works on this server, if mandrake or slack dont work, then someone going to get a nice christmas paper weight. ](*,)

---

### Post by linuxgoojoo on 2006-05-18
bump.


Anyone on this?

---

### Post by Drazyl on 2006-06-28
Try disabling ACPI (acpi=noirq on the kernel command line) - I have a DL380 with FC5, and this is needed to boot, otherwise the cd-rom seems to hang it.

---

### Post by KUKBAHLAM on 2007-08-07
I had trouble installing on a Proliant 1600. The machine would randomly lock. After reading the above message, I replaced the stock CD drive with another and the hang went away.

Thank you for the help. This is my first experience with Unix since Vax/VMS. Without great community support, this would have been much more frustrating!

---

### Post by dougynga on 2007-08-20
I am getting all the way thru the setup to the section where it detects the hard drive. Then it ask to partion disk: with a WARNING - Ignore to continue. 

Then it gives the option to do a guided partition or /dev/ida/c0d0 0B0 Compaq Smart Array - 

It goes to create new empty partition table on this device and then hangs on unable to detemine geometry of file/device. 

Any direction here? Or do I just give up?

---

### Post by dougynga on 2007-08-20
p.s. that is on Ubuntu 7.04 - Supported to 2008.

---

### Post by crouton on 2007-11-19
For anyone interested, there is another thread that has more information. [http://ubuntuforums.org/showthread.php?t=384319](http://ubuntuforums.org/showthread.php?t=384319)

---

### Post by citybird on 2008-01-16
I have been following those other threads closely and now I have come to the conclustion that the DL380 is a special case.

My current problem child is a G4 with a Smart Array 6i.
I can install, partition, and reboot with no problem but when it tries to boot from the hard drive it hangs.
no messages, nothing.

i have tried disabling modules, installing the cpqarray module, installing grub to my boot partition /dev/cciss/c0d0p1 with the expert installer.

I hope to beat this as I would like to use this server.

---

