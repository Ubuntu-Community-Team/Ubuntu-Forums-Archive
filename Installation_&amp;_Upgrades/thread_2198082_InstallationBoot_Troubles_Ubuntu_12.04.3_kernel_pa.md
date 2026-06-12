---
title: "Installation/Boot Troubles Ubuntu 12.04.3 kernel panic"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by chengarda on 2014-01-06
Apologies in if this has already been posted and solved elsewhere, I've tried every solution I've found searching for this problem, to no avail.

I'm attempting to install Ubuntu 12.04 (LTS) on an Advantech ARK 1388V machine, using a 16GB compact flash card.
I can boot from a LiveUSB created by the usb disk creator on another 12.04 machine.
When rebooting having removed the USB, GRUB starts, counts down before selecting the default OS (Ubuntu 12.04.3) (No others installed)
Then:

Couldn't Read File.
Press Any Key To continue...

[0.866308] kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

I've tried boot-repair, and received the following link [http://paste.ubuntu.com/6706943](http://paste.ubuntu.com/6706943) 

Appreciate any direction in this.

---

### Post by chengarda on 2014-01-07
Ok, update as of now:

Pressing e at the grub menu, showed the lis of boot commands, I changed the line set root=UUID='o8nwenrtgvwoerugt87' (or something like that) to say set root=/dev/sda1 (A moment of divine inspiration)

After giving the same "couldn't read file" error, and then blinking the screen a few times, Ubuntu started up.
I went into etc/default/grub and uncommented GRUB_DISABLE_LINUX_UUID=true and then update-grub to save it, because that seemed like a thing to do.

That made an extra few entries in the grub menu, some of which seem to work, but still give errors and general messiness before starting up proper.
I'm happy to leave it working as is for now, but if anyone knows of problems this is likely to cause, or a cleaner solution, please feel free to let me know.

If nothing bad happens the next few boots, I'll mark this solved tomorrow morning.

---

### Post by chengarda on 2014-01-08
If only.

Ran into further troubles, and thinking it was likely something I did, I reinstalled Ubuntu from scratch. Bad move, it seems, now I don't even reach the GRUB menu, I get 'out of disk' grub rescue.

Using ls, I can look through the drive, and all the files are there, except for /boot, which gives that same out of disk error.

Any help would be embarrassingly appreciated.

---

### Post by chengarda on 2014-01-08
Solved now, if anyone else runs into this problem, try booting from liveUSB/LiveCD, downloading and installing boot-repair, and select the options to reinstall grub, and disable UUIDs.

---

