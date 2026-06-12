---
title: "Ubuntu 10.10 No Root File System is Defined"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by FSCII on 2011-02-11
Ok I'm having a problem and it seems like partitions during the dual boot install.

Here's EXACTLY what I get...

Menu: Allocate drive space
    Erase and use entire disk
X  Specify partitions manually (advanced)   [X denotes I chose this option]




I have 3 partitions on my gateway laptop...

[graphical bar across the top]
sda1 NTFS - 10g - weird partition w/recovery software or something from Vista
sda2 NTFS - 140g - Windows Vista
47g FREE SPACE  [this is where I want ubuntu]

[Middle Window]
/dev/sda
  /dev/sda1    ntfs     10g    (built in recovery disc for Vista)
  /dev/sda2    ntfs     140g  (this is where Windows Vista is)
  free space                47g  (where I want Ubuntu)

So Now I highlight the 47g partition where I want ubuntu and double click it.
I get the "Create Partition" dialog box.

Type for new partition (I chose Logical -- should it be primary or logical and why?)

New Partition size (47g)

Location for the new partition:  Beginning

Use as: Ext4 Journaling System

Mount point:  (blank and I left it blank I have NO idea what these options mean!!!)

I click ok and it does "scanning disk".  Now it shows the top bar of "Allocate drive space menu" with blue color for 3rd partition as sda3 (ext4) 47gb

In middle it shows now

dev/sda5 (why not sda3???) ext4  47gb


Bottom of window:

Boot Loader
/dev/sda ATA (bunch of numbers)   --- I left this as default

[options i didn't choose for boot loader below]
dev/sda1 Windows Vista (loader) is this correct it should be the hidden recovery disk only 10gb here
dev/sda2 Windows Recovery Environment (loader) [WHAT? this is the 140gb partition!]
dev/sda5

I click "Install Now" and I get this error:

"No root file system is defined.  Please correct this from the partitioning menu."

HELP - it looks like all my bases are covered what am I missing?!

:confused:

---

### Post by FSCII on 2011-02-11
The only two options I'm leaving alone are

Mount point on the new partition (what should it be)
and the Boot loader (leaving its default /dev/sda/blablabla)

---

### Post by Quackers on 2011-02-11
As you selected logical for partition type (which is fine) the installer will have created an extended partition (probably /dev/sda3) - as a logical partition resides within an extended partition. /dev/sda5 will be the logical partition.
The mount point needs to be specified. In a normal installation the mount point for the root partition will be
 " / ", from the drop down menu.
When the mount point is not specified for the root partition, you get the error "no root file system is defined".

The bootloader should normally be left in the default setting.

---

### Post by FSCII on 2011-02-11
It was the mount point, I chose / and its proceding.  Thanks, I wasnt sure what it should be (nor the boot option).  Most appreciated!

---

### Post by Quackers on 2011-02-11
You're welcome  :-)

---

### Post by Arthur007 on 2012-06-19
Thanks, it works for me too ^^

---

