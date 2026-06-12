---
title: "Install on HP Dv6 Laptop"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by daniel.p on 2011-10-03
I tried installing from the 11.04 LiveCD but can't figure out how to install with the option to install alongside an existing OS. On my other HP laptop with Win7 I didn't have the issue. I was able to select the option and go through the install no problem. On this one though, I can't seem to do that. I'm assuming it has to do with the partitions.

For some reason there's 3. The first is the main Win7 partition, the other is labeled as Win Vista which I assume is recovery, and the last one is HP tools/apps (forgot the exact wording). It's an HP Pavilion dv6 from Wal Mart. This is [link]("http://www.walmart.com/ip/HP-dv6-1149wm/16662285") to the laptop I'm trying to install on.

If anyone else has done it, what steps did you take?

---

### Post by Quackers on 2011-10-04
Are you sure there isn't a 200MB system partition as well? Most recent HP laptops use all 4 available primary partitions by default.
This means that in order to install any other operating system you will need to delete a partition (probably the HP TOOLS one) and shrink the C: drive (as Windows calls it).
An extended partition can then be created in the new space. This extended partition can hold as many logical partitions as you wish.

---

### Post by SeijiSensei on 2011-10-04
[How to dual-boot Ubuntu on dv6tse]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5")

---

### Post by daniel.p on 2011-10-05
> **Quackers said:**
> Are you sure there isn't a 200MB system partition as well? Most recent HP laptops use all 4 available primary partitions by default.
This means that in order to install any other operating system you will need to delete a partition (probably the HP TOOLS one) and shrink the C: drive (as Windows calls it).
An extended partition can then be created in the new space. This extended partition can hold as many logical partitions as you wish.

I only recall there being 3 partitions, but I'll double check to make sure. I figured I could delete the HP Tools partition but wasn't 100% sure, so I figured I should ask here to make sure before making a mistake.

---

### Post by Mark Phelps on 2011-10-06
Deleting the HP Tools partion, while solve the "4 partitions" problem, leaves you with a new problem -- shrinking the existing partitions to create enough room to install Ubuntu.

So, if you're going to dual-boot, then you need to do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by punkybouy on 2012-01-16
Also remember you can have only ONE boot loader so if you are already running Windows then you are using the Windows boot loader.  There is a file off the root of C: that you can edit to offer up the choice of a second OS to load when the laptop is booted OR you can install GRUB which is the Ubuntu boot loader (I think) but you are going to have to modify that to indicate you also have another bootable OS (Windows) otherwise GRUB will install with only one option, to boot Ubuntu, and then you won't be able to boot Windows.  Perhaps during install Ubuntu will see the other OS and do this automatically, I don't know.  Typically I only run one OS preferring to run the second as a virtual machine under VirtualBox.

---

### Post by SeijiSensei on 2012-01-16
> **punkybouy said:**
> Perhaps during install Ubuntu will see the other OS and do this automatically, I don't know.

Yes, it does.  In fact it's much easier to install Linux over Windows because of this fact.  People trying to install Windows on an existing Ubuntu system encounter the problem that the Windows installer will take over the boot record and ignore the existing Linux installation entirely.

Virtualization is a fine option unless you have software that needs to talk directly to the hardware. Video is an important example of this.  Playing games and movies in a VM may not work well because the software can't communicate directly with the video hardware.

---

