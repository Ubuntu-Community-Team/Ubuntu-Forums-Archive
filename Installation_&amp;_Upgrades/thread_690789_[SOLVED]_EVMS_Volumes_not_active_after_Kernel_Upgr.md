---
title: "[SOLVED] EVMS Volumes not active after Kernel Upgrade"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2008-02-07
Hi,

I'm running Gutsy 64 bit and am using EVMS volumes. After a kernel upgrade this afternoon, all of the EVMS volumes are not active after rebooting. I can boot into Recovery Mode and run evmns (EVMS ncurses gui), go in and Activate each volume, exit the gui, run fsck on the devices and mount them. Then I exit and everything is fine.

The only message I see in dmesg is that the devices /dev/evms/lv* are not found.

Kernel is **Linux inferno 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux**

Prior to kernel upgrade, no problems with disks. Disks are SATA and are recognized during boot according to dmesg. Nothing in syslog to show you here. 

How do I get the volumes to mount up/activate on normal reboot?

TIA, Dante :confused:

---

### Post by DantePasquale on 2008-02-11
Well, since no one can help me out. I'm going to remove EVMS by first converting to compatability volumes. Then move to redhat where my questions actually get answered (and that's the corporate direction anyway).

---

### Post by DantePasquale on 2008-02-16
Here's what I did. booted in "Rescue" mode and ran the evmsn ncurses version. Activate all  the evms volumes that you want to work with. Save the work and re-enter evmsn. Then convert each volume to a compatible volume. This was very quick. Then Save your work. Edit the /etc/fstab to reflect the new devices in my case those were /dev/vg-misc/lv-home for /home. Oh, before doing that run fsck on each volume, just in case! Then reboot and if you didn't have any typos your volumes are now mounted on the correct mount points without using evms. Then I ran the Synaptic Package Manager, searched for evms and then uninstalled all the evms packages and patches that were installed. Then rebooted to see if there were any problems! Everything is cool now. Wish I had checked into the evms before using it with 6.06 LTS back when I went to Ubuntu from Redhat ;)

---

