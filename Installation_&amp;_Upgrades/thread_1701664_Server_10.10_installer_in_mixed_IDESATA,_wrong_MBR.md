---
title: "Server 10.10 installer in mixed IDE/SATA, wrong MBR"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2011-03-06
I am having trouble setting up a dual-boot Ubuntu (on IDE, unfortunately called /dev/sdb by Ubuntu) and Windows Vista (on SATA, called /dev/sda by Ubuntu) machine - the problem is related to where the Ubuntu 10.10 installer puts the Grub MBR - on /dev/sda - even though all of Ubuntu is being installed on /dev/sdb, my IDE drive.

The Grub install process is at the very end of the installation procedure.... is there a way to tell it to put the MBR on /dev/sdb (the IDE drive)?

(more detail if needed):

My machine has one IDE and one SATA hard drive; IDE is designated for Ubuntu, the SATA drive (which is removable, so it is not always in the machine) has Windows Vista. When I run the Ubuntu 10.10 server installer, the IDE drive is intended by me to go on /dev/sdb (the device Ubuntu calls the IDE drive), and the SATA drive is designated /dev/sda. This ordering of drives is not the way I would have preferred, but that's how the OS and the motherboard are interacting on this particular machine; it seems the ordering is inconsistent among various machines - calling IDE drives /dev/hdx would avoid this problem, but that's not how Ubuntu is built nowadays, so I am working through it.

On this machine, I can choose which of the two drives is enabled for boot as a BIOS set-up option. During the install of Ubuntu, I have set the IDE drive as bootable (important - this doesn't seem to influence the logic in the Ubuntu installer which chose the SATA drive - /dev/sda - as the place for MBR.) Basically, I want GRUB to offer the two options (Ubuntu or Vista), but if the Vista drive is absent on a given boot, of course I don't expect anything sensible to happen.

The problem is that Ubuntu 10.10 server installer wants to put the grub MBR on /dev/sda (which happens to be the Vista SATA drive) even though the Ubuntu partitions are being put on /dev/sdb (the IDE drive). This is not usable because when the Vista drive is absent (it is a removable SATA drive), I want the remaining IDE drive to operate stand-alone; it would be /dev/sda itself at that point.

---

### Post by YesWeCan on 2011-03-06
Unplug the Windows drive.
Install Ubuntu.
Plug Windows drive back in.
Boot Ubuntu.
Run 'sudo update-grub'


Don't let the Ubuntu installer waste any more of your time.

---

### Post by wb0gaz on 2011-03-06
Thank you... Good suggestion, if a bit of a kluge of necessity.

I have since my first post tried moving the SATA drive to a higher port number (choices 1..6, I moved it from port 2 to port 3 on the motherboard); this caused GRUB to identify the IDE drive as /dev/sda and the SATA drive as /dev/sdb, which allowed installation to proceed, however....

However....

When Ubuntu server starts, it now detects the SATA drive as /dev/sda, and the IDE drive as /dev/sdb.

This is really, really (really) disappointing - that the algorithm/code to map drive numbers is DIFFERENT between Grub and the OS Kernel?????

What will happen when I add another SATA drive? Will the mapping get mangled again?

Is there a definition of what is supposed to happen in terms of drive /dev/sd_ ordering?

What do I make of this?

---

### Post by NumPy on 2011-03-06
Honestly a removable drive is OS level naturally. The BIOS however might give different drive mappings based on whether its receives a response via the interface and so on. In that/this case GRUB/Kernel will always take what the BIOS gives as fact.

---

### Post by YesWeCan on 2011-03-07
> **wb0gaz said:**
> Thank you... Good suggestion, if a bit of a kluge of necessity.

I have since my first post tried moving the SATA drive to a higher port number (choices 1..6, I moved it from port 2 to port 3 on the motherboard); this caused GRUB to identify the IDE drive as /dev/sda and the SATA drive as /dev/sdb, which allowed installation to proceed, however....

However....

When Ubuntu server starts, it now detects the SATA drive as /dev/sda, and the IDE drive as /dev/sdb.

This is really, really (really) disappointing - that the algorithm/code to map drive numbers is DIFFERENT between Grub and the OS Kernel?????

What will happen when I add another SATA drive? Will the mapping get mangled again?

Is there a definition of what is supposed to happen in terms of drive /dev/sd_ ordering?

What do I make of this?
Well now you are asking for proper documentation...don't be rediculous! :P
My suspicion is that the bios is the culprit. It probably calls the booted hard drive sda so when you change the boot order the letters change. When you boot off CD or USB it is not clear what the letters for the hard drives will be. And with some bioses the letters of the non-boot drives can change between boots and mess up raid arrays.

This lettering musical chairs does strike me as idiotic.

The answer is to label each drive with a unique UUID and tell grub and the OS to use these. And this is what Grub2 and the Ubuntu installer does, and what mdadm doesn't do automatically (it labels but doesn't automatically configure to use them!).

---

### Post by wb0gaz on 2011-03-07
I would believe the root source of drive numbering chaos is in the BIOS, as I'm using the same OS (ubuntu server 10.10) on several machines; drive numbering is not consistent, although related to which SATA port is used for which drive (the IDE drive lives on the primary master in each machine).

Today, when (under Ubuntu) I used fdisk (on /dev/sdb - the IDE drive described at the beginning of this thread) to add a partition (it wasn't full), and I then rebooted so I could begin using the new partition on the IDE drive, ---> I discovered that the IDE drive was now on /dev/sda <---, and the SATA drive was on /dev/sdb; this is what I wanted in the first place, but I really don't know exactly (or inexactly, for that matter) how this happened. This kind of unexpected change isn't helpful at all.

All I can say is that the Ubuntu 10.10 386 server and alternate installer (both have this misbehavior; I've not tried the live install at all), the associated GRUB2 boot control program, and Ubuntu 10.10 OS, all collectively don't play by a consistent or documented (I'd rather have both, I'd settle for either) set of rules on drive numbering, and that is really irritating to put it mildly.

Thank you for the advice/discussion - every bit helpful and much gratitude to all that have taken the time to read/reply.

---

