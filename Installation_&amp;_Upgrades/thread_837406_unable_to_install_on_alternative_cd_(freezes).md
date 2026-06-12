---
title: "unable to install on alternative cd (freezes)"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by mwillbanks on 2008-06-22
I have been attempting to install KUbuntu for the last week now.  I've always used linux in a server environment and only slightly as a desktop environment.

So far what is happening is either when the live cd boots or I attempt to install it freezes after a short amount of time.  The farthest I have made it through has been getting to step 3 clicking the forward button and it freezes (this was on the OEM install which has been my best bet so far).

I am running the following hardware:
AMD Althon 64 3200+ 
1 GB Cosair ECC registered memory ( 2 x 512MB)
PCI Express NVidia 512MB (forgot the exact version but doesn't seem to be the problem)

All of the hard drives are SATA hard drives.  There are 3 on the system.

Also to give the answers to the first few questions I would be asked:
1. Version: KUbuntu Hardy (8.04) x64 Alternative cd
2. Disk Check: I've done the disk check and that passed.
3. Memory Check: I've let this run for a long *** time and passed all.

Any flags you think I should be sending?  Any additional things you can think of?  The only error I see while doing the installation is that it cannot find my wireless card drivers (which is fine because I am not using it yet and will get them later).

When disabling the splash page, everything clears [OK].  So if someone could throw me a bone that would be great.

---

### Post by mwillbanks on 2008-06-22
Some further information... It almost seems like it is timed from boot up.  I was able to make it into the partition screen which was step 4, went into manual partition, then lost my USB mouse... then about 30 seconds later i lost the keyboard and the install locked up.

so, it is seeing my disks just fine, reading back the details just fine, just linux absolutely hates this computer for whatever reason.  it just dies every time.  last time i attempted install of fedora had same freezing problems but atleast made it through the install.  maybe it will always be a windows box :(

---

### Post by mwillbanks on 2008-06-22
Maybe some further information will peak something here and to bump this hoping for a response:

Mobo: Foxconn NF4K8AB (verified running latest BIOS and Drivers from their website)

Errors that I am seeing:

Buffer I/O error on device sr0.....
end_request; I/O error, dev sr0.

also seen:
driver 'sr' needs updating - please use bus_type

also seen:
Doesn't support DPO or FUA on hard drive output

I've attempted mixing and doing a ******** of different flags such as:
noapic, disableapic, mce=off, ide=nodma, etc etc.  

Is there a way to get to the text install?  Anything?

---

### Post by mwillbanks on 2008-06-22
I was finally able to install using the following parameters:
noapic nolapic acpi=off irqpoll pci=noacpi pnpbios=off

However, now after booting it freezes almost instantly... Do these parameters not carry over and how do I get the boot loader (GRUB) to take these into consideration?  I attempted adding all of these as different parameters and it just instantly rebooted the machine.

---

### Post by mwillbanks on 2008-06-22
nevermind... kernel line ;)

---

