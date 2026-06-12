---
title: "Ubuntu &amp; EVMS"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by pvanberlo on 2006-07-29
Hello,

I'm about to install Ubuntu, but I'm wondering how to properly use EVMS with it. I know you can setup LVM and RAID using the installer, but does that in fact use EVMS or the default LVM/software RAID? Is there a good HOWTO on setting up Ubuntu with EVMS? I tried searching the forum, the wiki and Google, but couldn't come up with detailed information.

Thank you.

Regards,

Paul

---

### Post by OptikKnight on 2006-08-01
I've been looking for documentation on it as well...not because I'm not familiar with it, but because I was hoping it might be available on the alternate installation disks, since I'm contemplating building a server using Ubuntu. 

I didn't look very hard, honestly, but after an hour or two of searching, I've found no significant documentation of EVMS on the Ubuntu installation disks. From my experience of EVMS, it's quite handy, so I'm a bit disappointed that EVMS isn't directly available for advanced configuration of storage volumes during installation.

Fortunately, EVMS has the capacity to adapt basic configurations of LVM and software RAID (MD). Though I haven't tried it yet (I will tomorrow), I'm fairly confident that you could set up something resembling your desired configuration using the LVM and RAID utilities built into the Ubuntu installer, and then install EVMS after you complete the base installation, and then use EVMS to further modify/configure your volumes. I do not know for sure, but I'm guessing the Ubuntu kernels already contain support for booting EVMS-configured volumes. If not, there's plenty of documentation available on it -- search google, "gentoo setup evms", should be the first entry, a HOWTO.

Anyway, good luck on this! I'll come back if anything notable occurs. If it works, write up some documentation! ;)

---

### Post by OptikKnight on 2006-08-01
UPDATE:

I may have been mistaken about EVMS not being available on Ubuntu at the initial installation stage. I just checked up on a fresh installation (on which I didn't intentionally install EVMS) and found it there, so it may be available after all!

I'll continue to update as necessary.

---

### Post by mlind on 2006-08-01
Ubuntu kernel has necessary stuff for evms to work, and bd-claim patch seems to be applied aswell. necessary evms packages are installed by default too.
EVMS homepage contains all the information for setting it all up uphttp://evms.sourceforge.net/

I've followed those instructions and evms layer is working nicely.

---

### Post by pvanberlo on 2006-08-02
Well, after messing around a bit I figured out how to install Ubuntu cleanly using debootstrap, including a full EVMS setup.

If anyone is interested in a howto, I'm sure I can write one.

---

### Post by OptikKnight on 2006-08-02
... Right, so yes, EVMS is installed in the default Ubuntu installation, but is not available during installation. 

Not sure who to talk to about this, but I'm of the opinion that the installation tools on the alternate installation disc should be rewritten to use EVMS as an intermediary layer when doing partitioning/raid/lvm setup, since advanced users may have need for some of its functionality over the standard raid/lvm features already in use. 


I, personally, don't have need of a howto on this matter, but I'm sure others might find it useful. I'd be willing to review any documentation written on implementing EVMS in Ubuntu for the sake of future users who may need it.

---

### Post by mlind on 2006-08-02
> **OptikKnight said:**
> ... Right, so yes, EVMS is installed in the default Ubuntu installation, but is not available during installation. 

Not sure who to talk to about this, but I'm of the opinion that the installation tools on the alternate installation disc should be rewritten to use EVMS as an intermediary layer when doing partitioning/raid/lvm setup, since advanced users may have need for some of its functionality over the standard raid/lvm features already in use. 


I, personally, don't have need of a howto on this matter, but I'm sure others might find it useful. I'd be willing to review any documentation written on implementing EVMS in Ubuntu for the sake of future users who may need it.

Dapper has evms features included on kernel and necessary userspace package are installed by default. You can adopt evms after you've already installed your distribution.
evms site contains very good install instructions (you can skip to step 6 on [http://evms.sourceforge.net/install/](http://evms.sourceforge.net/install/)).

Although Ubuntu specific wiki article would be good.

---

### Post by pvanberlo on 2006-08-04
> **mlind said:**
> Dapper has evms features included on kernel and necessary userspace package are installed by default. You can adopt evms after you've already installed your distribution.
evms site contains very good install instructions (you can skip to step 6 on [http://evms.sourceforge.net/install/](http://evms.sourceforge.net/install/)).

Although Ubuntu specific wiki article would be good.

Unfortunately, I do not see this working for 'native' EVMS volumes. If we start with LVM2+RAID and afterwards move to EVMS, you either end up with compatibility volumes or you have to manual convert to EVMS native volumes.

Also, when doing a manual debootstrap setup, after a reboot things do work, but get slightly messed up. Some of the md devices are duplicated (i.e. there is a md255 device all of a sudden). I have pin-pointed this to be an issue with the initrd image, and the startup of mdadm, mdadm-raid and lvm. Since EVMS takes over all of these functions, these should not start anymore, since this can lead to unexpected behaviour. Mind you, things will most likely still work, but probably not as some people expect it.

I removed mdadm, mdadm-raid and lvm from the startup sequence, and deleted their respective startup files from the initrd. After this, everything seems to work flawlessly, except for the wierd /dev/md255 device which has replaced /dev/md2 completely now.

Since EVMS can replace the above, why can't this be the default for Ubuntu? Configuring can be daunting, but I'm sure that the installer can do some magic to hide things and make it easier for the user. Or perhaps add a boot option 'enable_evms' which makes sure the rest isn't loaded, that way only the bootloader config file has to be modified to include this option.

In the end, I do believe EVMS will be replacing LVM sooner or later, but that's of course my personal opinion.

---

### Post by OptikKnight on 2006-08-10
I just converted one of my Gentoo servers from standard raid (md) and lvm to EVMS, and it went surprisingly smoothly. I used genkernel to build the kernel and initramfs to call 'evms_activate' early in the boot process, but that took a few tries because I kept forgetting to compile in certain drivers ;) 

Before that, I was attempting to build an Ubuntu backup server (on an entirely different machine), using the standard raid (md) and lvm at first, since they're available in the initial installation process. I'm not sure why, but this system experiences a kernel panic while rebuilding a RAID-5 array of 4x 120gb harddisks, and I've seen this behavior on both the Gentoo livecd and in my current Ubuntu installation. I'm beginning to wonder if one of my drives is bad or something.

In the process of attempting that Ubuntu server installation, I completed the basic installation and began attempting to modify the initramfs to call 'evms_activate' and disable raid (md) and lvm, so that the system would depend only on EVMS to manage the volumes, and boot correctly. Since I've never modified an existing initramfs before, this proved quite challenging, and I ultimately gave up after several tries... Perhaps this is an issue that deserves careful documentation, by someone more skilled than myself. Preferably (for users who don't feel up to the task) this documentation would not involve recompiling the kernel, since some users are wary of it.

(I did look it up via google and found some documentation on it, but all attempts failed when following existing documentation.)

Other than that, (based on my experience with my Gentoo server) converting from basic raid (md) and lvm to EVMS is really quite simple.

---

