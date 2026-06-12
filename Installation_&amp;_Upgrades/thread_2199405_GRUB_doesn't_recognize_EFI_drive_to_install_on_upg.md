---
title: "GRUB doesn't recognize EFI drive to install on upgrade"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by quequotion on 2014-01-13
Having the same problem as [this thread that was closed before the issue was ever solved for some reason]("http://ubuntuforums.org/showthread.php?t=2092516"), blocking upgrade to saucy.

[s]**The problem is definitely GRUB**[/s]. The drive is correctly formatted; I do have a UEFI system; I have installed grub to this drive before. GRUB is probably looking for something it shouldn't be, like an arbitrary file on the drive or a particular partition table format that isn't valid across different kinds of systems.

Unfortunately I have to say there's never been anything easy or straightforward about installing GRUB with EFI. Nearly every attempt has resulted in an unbootable system because of errors in how GRUB installs itself, misreads partition tables, etc. So, knowing that the problem is once again in GRUB, how can I convince GRUB that in fact my EFI partition is an EFI partition?

Alternatively, can I convince GRUB not to check if an EFI partition "looks" like whatever it believes an EFI partition should look like?

::EDIT::

The problem is definetly grub, unless the problem is a bug in all (ubuntu) linux kernels after 3.5.0 which is causing efibootmgr to crash and occasionally lock up the computer.

---

### Post by oldfred on 2014-01-13
That thread is now old, and UEFI has changed a lot. Best to see details of your system.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by quequotion on 2014-01-18
>>oldfred

Thanks for the advice.
In fact, I finally got the system booting and grub installed.

That thread may be old, but the failure of the grub installation process it describes has not changed.

The problem is that it is *unsafe* to use efibootmgr with any Ubuntu linux kernel after 3.5.0 (precise).
Any attempt to install grub-efi with an ubuntu linux kernel after this one will result in an incomplete or corrupt grub installation, possibly a lockup of the system, and certainly an unbootable computer (for me).

The only way I can safely install grub is to reboot with the kernel from precise or use a precise livecd.
I know everyone loves to point fingers at an unsupported setup: my entire system (efi partition, root partition, swap partition) is installed on a fakeRAID:0 (z68 chipset)
That said, the earlier, unresolved, thread also involved a fakeRAID setup and the user was experiencing trouble in 12.10 (quantal)

I think I see a pattern here: fakeRAID + grub-install to efi + kernel more recent than precise = critical failure

---

### Post by oldfred on 2014-01-19
There is a bug for RAID installs.

 grub doesn't boot with efi and md raid root
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229738)
RAID install with efi, need configfile and grub in efi partition.
[http://ubuntuforums.org/showthread.php?t=2190716](http://ubuntuforums.org/showthread.php?t=2190716)

---

### Post by quequotion on 2014-03-25
Issue resolved by giving up on the concept of using GRUB with UEFI.

*Users should be warned*: The problems are very serious; dm-raid is not being maintained and should be deprecated for mdadm, efibootmgr is broken, GRUB expects GPT partitions and BIOS, etc.

[gummiboot](http://freedesktop.org/wiki/Software/gummiboot/) (designed for UEFI), however, works very well and *does not suddenly or irreparably break during upgrades*.

---

