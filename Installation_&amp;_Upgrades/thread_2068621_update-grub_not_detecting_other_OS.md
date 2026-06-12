---
title: "update-grub not detecting other OS"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by WanderingAlbatross on 2012-10-09
I recently did a major number of updates of my system.  One of the updates must have been to Grub, because after I restarted and grub came up, it wouldn't boot my other OS correctly, Archlinux.  Here is what it wrote into the Grub menuentry for Arch:
```
setparams 'arch (on /dev/sda4)'
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set=root 72b29576-5eb0-4b76-90c8-755c603e2515
linux /boot/vmlinuz-linux root=/dev/hda3 ro
initrd /boot/initramfs-linux.img
```

It would come up with a message saying it could not find /dev/hda3, waiting 10 seconds.  To fix it, I could knew what my configuration was, so I changed this line:

```
linux /boot/vmlinuz-linux root=/dev/sda4 ro
```

and it worked fine at boot up.  I had to make this a custom menuentry because update-grub keeps coming up with something that does not work.  This is workable for the time, I am just curious why Grub did this.

---

### Post by oldfred on 2012-10-09
Grub2's os-prober first looks for menu entries from other systems and copies those is grub2 or copies & edits it grub legacy type. I think it can just find kernels & create default entries also.

But your Arch must still use the older hda not sda type notation for drives. In Ubuntu it used to be hda for IDE and sda for SCSI drives. When SATA came out and became the standard Ubuntu used just the sda as the standard. I thought it was a combined driver and was now used by all Linux, but it must not be.

So grub is copying an entry that does not work in Ubuntu. Probably just should file a bug. 

Depending on how often Arch updates its kernel versus grub2 updates in Ubuntu you may want to copy your corrected entry into 40_custom and turn off os-prober. But you will have to manually update with every kernel update in Arch.

---

### Post by WanderingAlbatross on 2012-10-11
Hmmm...
This is an interesting thought, because ArchLinux likes the 'bleeding, cutting, edge'.  Also it was Ubuntu that suggested it to be 'hda3'.  Arch seems to like 'sda4'.  The two had been in harmony with each other for a few years.  Something has changed.  I will report the bug.

I would like to disable to OS-prober, but I didn't see any information on that one.  I thought it might be possible.  Perhaps I will just leave it and change the default boot OS.  It's good to have what the computer wants to do around so I can compare it.

---

### Post by oldfred on 2012-10-11
If you want to copy entries to 40_custom.

gedit /boot/grub/grub.cfg
gksudo gedit /etc/grub.d/40_custom
gksudo gedit /etc/default/grub
sudo update-grub

Two ways to turn off os-prober:
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

You can turn it back on by commenting out or changing to false or re-implement executable bit with +x in chmod command.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

