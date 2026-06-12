---
title: "installing on SSD that cannot boot"
date: 2018-10-30
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-10-30
i have a machine that has a 1TB spinning hard drive to which i have added a 120GB solid state drive.  the problem this machine has is that it's BIOS fails to recognize the SSD and will not boot from it, probably because it is not IDE or USB.  but Linux *can* see and access the SSD just fine once it is up and running (16.04 LTS).  the 1TB drive runs about 49.4MBps while the SSD runs about 524.8MBps when reading sequentially through about 64MB.  writing is about 85% of the speed on each.  i would like to install the system on the SSD but boot from the old 1TB drive.  can the normal Ubuntu installer for 16.04 set this up?  or should i not even do this?

---

### Post by Bashing-om on 2018-10-30
Skaperen; Hummm ...

Sure can be done to boot both/either. *IF* your bios supports AHCI and is so enabled.
When booting does the bios splash screen indicate the SSD drive? OR is it that the linux system picks up the drive after it is booted ?

Be aware I had to jump through some hoops to know AHCI for my old Phoenix bios.

for proof:
> 
sysop@x1804mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="x1604" UUID="d9c2a8e6-d014-42a6-846f-7e7892f4aef5" TYPE="ext4" PARTUUID="b6a9f0ca-01"
/dev/sda5: UUID="8d4743bc-8e47-4650-b5fd-1ea904d4ecda" TYPE="swap" PARTUUID="b6a9f0ca-05"
/dev/sda6: LABEL="x1810" UUID="49de038e-9807-469b-9009-540f2989f913" TYPE="ext4" PARTUUID="b6a9f0ca-06"
/dev/sdb1: LABEL="x1804root" UUID="1460de17-30e4-4566-b181-18c17b62887a" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sdb2: LABEL="x1804home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sdb3: LABEL="x1804var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sdb5: LABEL="u1804" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sdb6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sdb7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" TYPE="ext4" PARTUUID="c6c4079f-07"
sysop@x1804mini:~$

where I can boot any operating system from either drive.

[INDENT][INDENT]1st things first
[/INDENT][/INDENT]

---

### Post by Skaperen on 2018-11-01
there is no indication that the "drive" (it's a long card) exists until Linux is up and running.  so it must have a driver for that chipset that comes in by default, and apparently no BIOS extension on the card.  i see no ROM or ROM socket anywhere on the card.  maybe BIOS was in flash (there are about 27 like chips on it that i assume are flash) and something discarded.

i was wrong about the hard drive; it looks like SATA.  but apparently the SSD card isn't.  but it is fast and plugs straight into the bus.  it was hard to get in there because it was so long.  there was only one slot it would go in and a lot of stuff was in the way.

my idea is to have the boot partition (with grub and a few kernels) and /var and /home on the 1TB spinner and other filesystems on the SSD.  i have not yet decided about swap but the box has 16GB RAM so i may just do without.

---

### Post by Bashing-om on 2018-11-01
Skaperen; Hummm ....

Bummer that Bios does not see the card :(

But, yes  nothing to prevent one having boot - and all the files needed to get the kernel up and running - on the spinner and all other files on the SSD card. Might be a pain keeping up with the partition assignments and the required symbolic inks. And, a small swap partition - or now-a-days a swap file - is cheap insurance, as the system so expects "something" to be present.  A lot will depend on when the SSD is brought on-line. As to any performance boost in such an arrangement .. Just do not know.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
will be worth the read.

[INDENT]'Buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Skaperen on 2018-11-04
i'm thinking of having a copy of /usr on the SSD and have it mounted over the original /usr late in init, probably by /etc/rc.local. then all i need to do is install on the spinner as if it was going to be where everything is run from.  i would have a flag file to indicate not to use SSD which i would set and reboot when i need to install something.

---

