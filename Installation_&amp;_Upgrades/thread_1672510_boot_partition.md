---
title: "/boot partition"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2011-01-21
I have an old BIOS on my Dell Inspiron 8600. It reads only 137 GB in a 160 GB drive..(Cylinder 1024 limitation0 ..I have the latest BIOS for this model installed and it is not possible to upgrade further..So I have to necessarily circumvent this issue
 
I have a couple of distros installed..One solution which I read was to install the /boot partition within the first 1024 cylinders..
 
My simple doubt is suppose I have 2 or more Distros beyond the 137 GB , I may have to install /boot for these distros in one separate partition..
 
The nomenclature most distros use for these directories is only "/boot" ..
 
How do I distinguish which /boot dir is for which distro?!!
 
To illustrate I have say Kubuntu and Ubuntu beyond 137GB..The boot folders for both use the same name viz "/boot"...How to distinguish /boot of Kubuntu and /boot of Ubuntu?!

---

### Post by mikewhatever on 2011-01-21
I think what you want is not a boot partition, but a dedicated GRUB partition.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by srs5694 on 2011-01-21
No, a dedicated GRUB partition solves other problems -- although the two solutions could be combined.

The issue with the BIOS, as I understand it, isn't with the 1024-cylinder limit (that limit corresponds to a value a bit under 8 GiB), but to the use of 28-bit LBA addresses by some BIOSes -- 2^28 (sectors) * 512 (bytes/sector) = 128 GiB (or roughly 137 GB).

In any event, the solution is more-or-less as you suggested -- create a separate /boot partition that falls below the 128 GiB mark (not the 1024-cylinder mark, although that will certainly be safe) on the disk.

You can create multiple /boot partitions on one disk. Calling a partition "a /boot partition" is just a reference to where it's mounted in the Linux filesystem hierarchy. That information is *not* encoded in the filesystem or in the partition table in any standardized way; it's stored in the /etc/fstab file of the OS that uses it. Thus, you could have (say) /dev/sda1 be the /boot partition for Ubuntu and /dev/sda2 be the /boot partition for OpenSUSE. What's more, you can mount partitions in different places in different installations, or even temporarily on a single installation -- you could mount OpenSUSE's /boot as /opensuse/boot or even /somethingsilly under Ubuntu, for instance. The only tricky part is keeping which one is which straight. You can use filesystem names to help with this, or if you were to use the GUID Partition Table (GPT), you could use the partition name in the GPT, but basically it's just a matter of documenting it and keeping it straight in your own head. The /etc/fstab entries themselves will document it, but these aren't always the easiest files to reference, especially since most distributions today use UUIDs to refer to partitions. That's one reason I like GPT; with the right software (not all programs display GPT partition name) and setup, you can tell at a glance what a partition is for by using the partitioning software. GPT isn't compatible with booting Windows on a BIOS-based computer, though, so if you dual-boot Windows (or some other old OS) on this computer, using GPT is not a good idea.

The dedicated GRUB partition that mikewhatever mentioned can be useful because it de-couples the GRUB configuration from the OS. This can be handy if you frequently install and remove OSes -- conventionally, if you remove or replace whatever OS installed the GRUB configuration you use to boot, your boot process will be disrupted. With a dedicated GRUB partition, though, the GRUB installation is essentially separated from the OS, so replacing an OS will only affect that one OS's ability to boot.

---

### Post by oldfred on 2011-01-21
If you have all your data in a separate /data partition you only need 10 or 20GB for / (root) even including /home since data is in the partition at the end of the hard drive.

In the first 137GB you can fit a lot of system only partitions.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by vikrang on 2011-02-05
Thanks ...
 
I found another interesting link , wherein someone specifies deleting a particular line in GRUB2 which resolves the issue
 
I tried it but not working for me
 
<Quote>"I found that the second command: "if [ -n ${have_grubenv} ]; then save_env recordfail; fi" is the one that produces "error: out of disk". When I removed that from the default entry, my system booted fine.""<unquote>
 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477430)

---

