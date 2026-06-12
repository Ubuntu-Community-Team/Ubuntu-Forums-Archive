---
title: "[NOOB HELP] Dual-Boot XP and Ubuntu on one drive"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by Justin125 on 2007-06-22
I am wishing to dual-boot with XP already installed and Ubuntu going on. I have read Guided One is the best option to go for a newbie dual-booting. I click and this comes up:

"Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.

GO BACK | CONTINUE"

On all the guides I have read this has not been mentioned... I'm unsure what to do?

EDIT: I have also done research on the forums here too, again, nothing mentioned on this.

---

### Post by logos34 on 2007-06-22
> "Before you can select a new partition size, any previous changes have to be written to disk.

You cannot undo this operation.


Personally I haven't done the guided install (always use manual mode) but I think it's teling you that the changes made to the windows partition (resizing/shrinking) must be written to disk before you can proceed to setting up your linux partitions on the remaining disk space.  Nothing to worry about.

---

### Post by Justin125 on 2007-06-22
> **logos34 said:**
> Personally I haven't done the guided install (always use manual mode) but I think it's teling you that the changes made to the windows partition (resizing/shrinking) must be written to disk before you can proceed to setting up your linux partitions on the remaining disk space.  Nothing to worry about.

I pressed continue and I got an error of:

"An error occurred while writing the changes to storage devices.

The resize operation is aborted. "

I press okay and get a weird window that appears to be a partition list and editor or something... There's one thing in the list:

/dev/sda |

/dev/sda1 | ntfs | /media/sda1 | *un-checked box* | 60019MB | 0 MB

Could someone tell me what to do? I have one hard drive with about 55-60GB space.

Help would be nice, as I said I'm a noob when it comes to this stuff: This is my first linux or ubuntu install.

---

### Post by logos34 on 2007-06-22
gparted is having trouble shrinking the ~60GB windows partition (sda1).  You might to abor the install and reboot into windows to run defrag several times and see if there are any 'unmovable' files listed at the end of the disk (which would block any resizing operation).  Temporaily disable hibernation file (control panel>power options) and virtual memory (ctrl panl>system>advanced tab).  Then try install again.

---

### Post by Justin125 on 2007-06-22
> **logos34 said:**
> gparted is having trouble shrinking the ~60GB windows partition (sda1).  You might to abor the install and reboot into windows to run defrag several times and see if there are any 'unmovable' files listed at the end of the disk (which would block any resizing operation).  Temporaily disable hibernation file (control panel>power options) and virtual memory (ctrl panl>system>advanced tab).  Then try install again.

Okay. Will report back when done.

---

### Post by fumduck on 2007-06-22
This guide helped me .. maybe it can help you too..


Also I don't kow if it helps, but I used gparted to partition my hard drive ahead of time, and then just manually  pointed ubuntu to the partition

---

### Post by Justin125 on 2007-06-22
> **logos34 said:**
> gparted is having trouble shrinking the ~60GB windows partition (sda1).  You might to abor the install and reboot into windows to run defrag several times and see if there are any 'unmovable' files listed at the end of the disk (which would block any resizing operation).  Temporaily disable hibernation file (control panel>power options) and virtual memory (ctrl panl>system>advanced tab).  Then try install again.

Okay I did so and then tryed to install Ubuntu again, the error I had before did not come up and that partition window did not come up, I went through everything and it is installing as of now.

Thanks for the help.

---

