---
title: "the disk drive for /tmp is not ready or present"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by Sapph1r3 on 2014-02-06
Hi there,
Apologies if this is posted in the incorrect section.
We recently upgraded from 11.10 -> 12.04.
Updates were run overnight (there were about 700 to do) and upon checking in the morning, a number had failed with the following error:
[PHP]gzip: stdout: No space left on deviceE: mkinitramfs failure cpio 141 gzip 1update-initramfs: failed for /boot/initrd.img-3.2.0-58-generic with 1.dpkg: error processing initramfs-tools (--unpack): subprocess installed post-installation script returned error exit status 1[/PHP]
One of the updates required a reboot, which was initiated.
Thereafter Ubuntu proceeded with a disk check.
As this machine is required to remain active, the check was cancelled after an hour which brings us to the error at hand:
[PHP]the disk drive for /tmp is not ready or present checking 1 of 3 press s to skip or m for manual recovery.[/PHP]
Could this have been caused by the previous error and would this happen again should another restart is initiated?
This machine is in a remote location so I am unable to see the screen when the reboot occurs.
Any advice would be greatly appreciated.

---

### Post by fdrake on 2014-02-06
i do not think that the 2 messages are related. Do you have the /boot in the same partion with the / or in a separate one? if so check that you have enough space in /boot or get rid of some of your older kernels. A disk check or a cleanup of the /tmp should help to fix the second error

---

### Post by Sapph1r3 on 2014-02-06
I didn't do the initial setup for this machine, I'm just starting to take over its maintenance which is done using webmin, so I don't know about the partition structure.
With Webmin I can see the following:
 /
|- .config
|- 0755
|- backups
|- bin
|- boot

backups is a separate drive not a partition
And /boot is at 99%

---

### Post by Bashing-om on 2014-02-06
Sapph1r3; Hi !

My 2 pounds worth: as fdrake advises -> clean up the /boot directory (partition (??) .
Let's see what there is to do, and then do it:
```

uname - r ## to know what kernel is booting, KEEP this one ! AND one other as a backup
dpkg -l | grep linux-image ##to see what is going to be removed
dpkg -l | grep linux-headers ## ditto, see what is going to be removed
sudo dpkg -P linux-image-3.2.0-{12,13,14,15,16,17}-generic-pae ##this is only an example to purge the image files
sudo dpkg -P linux-headers-3.2.0-{12,13,14,15,16,17}-generic-pae ## ditto, for the header files

```
Any doubts or hesitations, pause and ask !

Hopefully there is enough headroom at 99% usage for "dpkg" to operate.

Else is going to be drastic and a bit painful.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Sapph1r3 on 2014-02-07
Thanks for the replies guys.
I've logged a request to go out to the machine and give this a go.
Machine has been up since restart, which is good.
Will report back on what happened.

---

### Post by Sapph1r3 on 2014-02-07
And finally back from that trip.
There were quite a few old kernels to get rid of.
Process was time consuming but it got done.
The disk checking error is no longer present, but it still wants to do a disk check on reboot.
boot.log reports it hasn't been done for quite a number of days...but that's a different "problem"
Thanks for the help :)

---

### Post by Bashing-om on 2014-02-07
Sapph1r3; Good deal !

Glad you have overcome that little situation !

Please mark this thread solved -> 1st post -> thread tools.

Checking repairing the file system might be a challenge, as must be done while the file system is NOT mounted.
Usual method is from a liveDVD(USB) and invoke a ramification of the "fsck" tools. But certainly needs to be done.

[INDENT]it ain't nothing
[INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT]

---

