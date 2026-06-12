---
title: "Waiting for root filesystem..."
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by albatross83 on 2006-07-01
I installed from the "alternate" installation disk.  When asked to partition, I selected the option to formate the target drive, and it automatically created hdd1 as "/" and hdd5 as the swap partition.  The installation completed successfully, and I removed the CD and rebooted.

After booting up, I get the UBUNTU spash with the typical messages below that.. but it only gets to the "*Mounting root filesystem...*" message, or words to that effect, followed by:

*Waiting for root filesystem...*

After a couple of minutes it times out (?) and drops to a shell with the error:

*ALERT!  /dev/hdd1 does not exist.  Dropping to a shell!*

I'm at a loss here.. anyone know why this might be happening?  I didn't change anything between installation and rebooting aside from removing the CD.

---

### Post by albatross83 on 2006-07-01
Bump

---

### Post by scxtt on 2006-07-01
how is your disk currently partitioned? (any other OSes on it?)

---

### Post by albatross83 on 2006-07-01
Partition 1 - ext3 ~39G
Partition 5 - Logical, swap ~1G (whatever the ubuntu installer creates by default)

I think I've found the problem, but I'm not sure how to fix it.  When it drops to the shell, I checked /dev/evms, and it lists the (only) drive as hdc.  When installing, the drive was hdd.  As I mentioned, I didn't change anything between installing and rebooting.

So I assume there's some configuration I need to change, but I'm not sure what, or where.

---

### Post by scxtt on 2006-07-01
how many drives are in your computer, including optical ones? -- how many hd*'s &/or sd* exist in your system?  i'm finding it a little odd that you've got a "logical" swap partition, out on *d*5 ...

---

### Post by rcarring on 2006-07-02
If hdd is not found and hdc is, then it means the hard disk is not being discovered at boot time.

---

### Post by albatross83 on 2006-07-02
There's 2 drives in the system, both on IDE-2.  
Master - DVD Drive
Slave - 40GB HD.

The installer automatically created a logical partition for the swap, so I didn't argue.

AFAIK, any logical partition will automatically be numbered >4, since the first 4 are reserved for primary partitions I believe.  This is in fdisk -- I'm not sure how the OS is referring to them, as far as hdd*... probably hdx1 and hdx2.

---

### Post by albatross83 on 2006-07-02
[QUOTE=rcarring]If hdd is not found and hdc is, then it means the hard disk is not being discovered at boot time.[/QUOTE]

So it's not discovering the drive as HDC instead of HDD?  I only have 1 HD in the system though...

---

### Post by aggierandy on 2007-03-04
I think I was having a similar problem with an old Pentium III I was trying to load. It would give me that message followed by a drop to some interface. I am a complete newbie so as I ran here to my laptop to check the forums....it loaded! This took upward of 20 minutes! But it is up and running right now. I guess just turn it on and go to bed and check it in the morning!

Thats my newbie advice!

---

