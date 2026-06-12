---
title: "Moving an existing system disk to an ICH10R RAID1"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by DaleAmon on 2011-03-12
I've read many of the postings on ICH10R and grub but none seem to give me the info I need. Here's the situation: I've got an existing server on which I was running my RAID1 pair boot/root drive on an LSI based RAID chip; however there are system design issues I won't bore you with that mean I need to shift this RAID pair to the fakeraid (which happens to most reliably come up sda, etc). So far I've been able to configure the fakeraid pair as 'Adaptec' and build the RAID1 mirror with new drives; it shows up just fine in the BIOS where I want it. 

Using a pre-prepared 'rescue' disk with lots of space, I dd'd the partitions from the old RAID device; then I rewired things, rebooted, fired up dmraid -ay and got the /dev/mapper/ddf1_SYS device.

Using cfdisk, I set up three extended partitions to match the ones on the old RAID; mounted them; loopback mounted the images of the old partitions; then used rsync -aHAX to dup the system and home to the new RAID1 partitions.

I then edited the /etc/fstab to change the UUID's; likewise the grub/menu.list (This is an older system that does not have the horror that is grub2 installed) 

I've taken a look at the existing initrd and believe it is all set up to deal with dmraid at boot. So that leaves only the grub install. Paranoid that I am, I tried to deal with this:

 dmraid -ay
 mount /dev/mapper/ddf1_SYS5 /newsys
 cd /newsys
 pivot_root . /oldsys
 chroot . bash
 mount /proc
 mount /dev
 grub-install /dev/mapper/SYS

and I get messages about 'does not have any corresponding BIOS drive'.
I tried editing grub/device.conf, tried --recheck and any thing else I could think of, to no avail.

I have not tried dd'ing an mbr to sector 0 yet as I am not really sure whether that will kill info set up by the fakeraid in the BIOS.

I might also add that the two constituent drives show up as /dev/sda and /dev/sdb and trying to use either of those directly results in the same error messages from grub.

Obviously this sort of thing is in the category of 'kids don't try this at home', but I have more than once manually put a unix disk together one file at a time, so much of the magic is not new to me. It's just that in this case the magic is not working :-(

So, what next?

---

### Post by DaleAmon on 2011-03-15
I have made progress. I was able to install the boot block manually:

	apt-get install grub
	grub --device-map=/dev/null
	grub> device (hd0) /dev/mapper/ddf1_WBX0SYS
	grub> root (hd0,4)
	grub> setup (hd0)
	quit

Which let me boot successfully... sort of. My initrd did not recognize the dmraid device for whatever reason. I took a quick look at the code of the scripts in initread and I thought it would. Instead it booted off the RAID then in initrd mounted root on sda only.. and over night this corrupted things so I'm researching while I'm letting a BIOS verify run.

---

### Post by DaleAmon on 2011-04-02
Just in case someone else has to deal with this problematic Intel chip... I solved my problem with an initrd script of my own which I placed in the local-top directory. Note that I had to use a time delay because the disk discovery is still going on at the time when the initrd boot occurs, so I had to wait for it to settle before I could reliably start up the raid control:

#!/bin/sh

# DMA20110316
# local-top script for initing the Intel ICH10R dmraid.

PREREQS="udev all_generic_ide"
prereqs()
{
        echo $PREREQS
}

case $1 in
# get pre-requisites
prereqs)
        prereqs
        exit 0
        ;;
esac

. /scripts/functions

sleep 30
/sbin/dmraid -ay

if [ ! -e "/dev/mapper/ddf1_WBX0SYS" ]; then
        panic "Failed to enable ddf1_WBX0SYS"
else
        log_success_msg "Enabled /dev/mapper/ddf1_WBX0SYS"
fi

---

