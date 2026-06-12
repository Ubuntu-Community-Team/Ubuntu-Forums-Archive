---
title: "VirtualBox + Feisty, unable to format partitions"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by wwwcre8r on 2007-04-20
Install stops during partition phase... returns error
Whether I use the Guided or Manual method...

It says it is installing the system, "Detecting file systems..." and the progress bar gets to 15%

Then I get an error:
[B]Failed to create a swap space
The creation of swap space in partition #5 of IDE1 master (hda) failed.[/B]

I tried running sudo gparted -> manually formatting the partition, similar error.

From the terminal, after gparted loads, I see this error in the terminal:
**Unable to open /dev/hda - unrecognized disk label.**

Then in gparted I get an error when trying to create a new partition in unallocated space; first a pop-up asks me to set disklabel on /dev/hda... I click "Create" (leaving the default of msdos)... accept the consequences and then get this error:
**Error while setting new disklabel**

In the terminal, I see a new message:
[B]Input/output error during read on /dev/hda
Input/output error during write on /dev/hda[/B]

---

### Post by wwwcre8r on 2007-04-23
UPDATE: **I got it to work!!!**

Three things I changed in this new setup, not sure which of them were responsible.

[LIST=1]
[*]Took a snapshot of the install process while still running from the live CD.
[*]In Settings > General > Advanced > Extended Features... I enabled IO APIC
[*]Used an ISO as the source instead of the CD for installation
[/LIST]

---

### Post by ajun007 on 2007-05-03
Thanks wwwcre8r.  Just wanted to share that this worked for me also.  Details:

1. i had IO APIC enabled from the beginning
2. took snapshot after liveCD loaded to desktop.
3. changed to ISO as suggested

other details:
I'm installing xubuntu 7.04 on VirtualBox 1.3.8.
manually edited partition table 512MB swap, remainder is ext3 as /

now let's see how well this multicore support works for the new version of VirtualBox : )

---

