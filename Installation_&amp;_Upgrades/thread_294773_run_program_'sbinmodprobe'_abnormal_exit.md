---
title: "run_program: '/sbin/modprobe' abnormal exit"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by gronbaek on 2006-11-07
I just upgraded my 6.06 system to 6.10 system and now I can't boot.
Attempts to do a complete new install from CD hangs with the following error:

> EIP: [<f8852682>] pdc_sata_scr_write+0x12/0x20 [sata_promise] SS:ESP 0068:dff11d98
udevd-event[1680]: run_program: '/sbin/modprobe' abnormal exit

If I wait around 5 to 10 minutes the system will eventually continue booting and 1 out of 10 tries it will actually boot all the way to the installation system. But then the SATA disk in my system isn't found. So I'm guessing this has something to do with the Promise SATA controller on my motherboard. The motherboard is a Soltek SL-K890Pro-939 with the VIA K8T890 + VT8237 chipsets.

Does anybody know a solution to the problem except from reverting to 6.06 of course..

---

### Post by ellion on 2006-11-21
I have the same problem, but my Promise Controller isn't onboard, it's PCI

---

### Post by NeoNecro on 2006-11-26
I also have this problem, with a pci promise sata controller.

It gives the following error:
udevd-event[1644]: run_program: '/sbin/modprobe' abnormal exit

But when I boot an older kernel version the system boots like it should.

---

### Post by jmeyerdo on 2006-12-03
Hi!

Same problem for me (Promisa SATA PCI). I noticed the same with Fedora Core 4, 5, 6 (yes - still using FC on some machines installed before knowing Ubuntu... :))

I would suggest it is a kernel-problem. Before kernel 2.6.17 everything was fine but with all newer kernels I run into this problems.

Any further news/ideas about this?

Kind regards,

       Jens

---

### Post by NeoNecro on 2007-01-08
Does somebody know if this problem still occurs with kernels newer then 2.6.17? Or is it still in there?

---

### Post by jmeyerdo on 2007-01-08
Hi!

I am using 2.6.18-1.2860 without problems now. But only on Fedora Core 6. Untested on Ubuntu.

Kind regards,

     Jens

---

### Post by NeoNecro on 2007-01-10
I've just compiled the 2.6.19 kernel and it seems to work now.

But, I forgot to put in ntfs support and my disc on the sata controller are formatted in ntfs, so it is of not mutch use. But it works.

---

### Post by drinklime on 2007-01-15
i still get this error with 2.6.19 :-k

---

### Post by keflavich on 2007-01-26
I'm getting this problem on 2.6.18.  It worked fine until today, when I tried installing JRE and ndiswrapper.  ndiswrapper functioned fine, but I have to assume it is in some way responsible since as far as I know it's the only thing I installed that used modprobe.  Is there any way to bypass modprobe on starting the computer so Ubuntu doesn't freeze?

---

### Post by DonovanM11 on 2007-11-04
I just upgraded my feisty fawn 7.04 to gusty gibbons 7.10 and i continue to get the message every time it boots.

---

### Post by harishjp on 2007-11-15
I just upgraded it on my desktop. It works perfectly when I boot using 2.6.20-16. Fails with similar message when using 2.6.22.14.

[112.913340] BUG: Unable to handle kernel NULL pointer deference at virtuall address 0000000
....
Modules linked in: ide_cd cdrom ide_disk ata_generic libata scsi_mod floppy via_rhine via82cxxx ide_core ehci_hcd uhci_hcd usbcore 8139cp 8139toomii thermal processor fan fuse apparmor commoncap
...
Call Trace:
ide_in_drive_list [ide_core]
idedisk_check_hpa [ide_disk]
__slab_alloc
release_console_sem
task_no_data_intr
ide_add_setting
ide_disk_probe
driver+probe_device
__driver_attach
bus_for_each_dev
driver_attach
__driver_attach
bus_add_driver
sys_init_module
prio_tree_insert
syscall_call

run_program: '/sbin/modprobe' abnormal exit:
...
ALERT: /dev/disk/by-uuid/<uuid> does not exist. Dropping to a shell.

It throws up initramfs prompt after some time. I did an "ls /dev/disk/by-uuid/", I found the uuid to be listed there. when I hit ^D it continues to boot and fails again informing that it could not mount other partitions and throws up a maintenance shell. Hit ^D again it proceeds to boot and the desktop comes up.

Any fixes?

---

### Post by harishjp on 2007-11-27
issue fixed:

discussion here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/154591)

---

