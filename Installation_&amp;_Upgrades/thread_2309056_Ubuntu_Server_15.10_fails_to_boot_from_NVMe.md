---
title: "Ubuntu Server 15.10 fails to boot from NVMe"
date: 2016-01-07
forum: Installation &amp; Upgrades
---

### Post by seth-russell on 2016-01-07
I have successfully installed Ubuntu server 15.10 on an Intel NUC 5i5RYK with Samsung SM951 NVMe M.2 PCIe SSD but cannot boot to my new system. This is a new machine with no other OSes installed. Installation succeeds and grub installs successfully and starts correctly on restart. However, once the grub menu screen disappears and the rest of the system attempts to load, I get failures. 

Here's some of the errors I get:

error: failure reading sector 0x1dff40 from 'hd0'

After that message clears, a more detailed boot sequence occurs, but results in a kernel panic with messages such as:

... 
VFS: Cannot open root device
Please append a correct "root=" boot option
...
end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I've tried disabling UEFI boot and then reinstalling but that has no effect. I've also tried reinstalling with different partitioning schemes - both LVM and non-LVM, but that also appears to have no effect.

I am able to successfully install Ubuntu 14.04.3 on the same hardware. Is NVMe support missing from 15.10? Anyone know how to get grub to successfully boot from an NVMe device?

---

### Post by seth-russell on 2016-01-07
Here's an update on a few more things I've tried.

Ubuntu Server 14.04.3 (LTS) successfully installs and boots on this exact same hardware. Ubuntu Server 15.04 successfully installs and boots on the exact same hardware.

On 15.10 I also tried to use the boot-repair utility (results available at [http://paste.ubuntu.com/14432616/](http://paste.ubuntu.com/14432616/)), and it fails to fix the problem. Perhaps the problem is the NVMe drive isn't properly supported in 15.10 or the version of grub that comes with 15.10. I have applied updates at install time.

---

### Post by seth-russell on 2016-01-08
I was able to resolve my problem. Found two methods that fix broken Ubuntu 15.10 boot failure after initial install.

1) Boot Repair - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) The default or "Recommended Repair" doesn't work, but if I select the "Advanced Options" and uncheck "SecureBoot" but keep all other default options then follow the instructions, the system correctly boots to the newly installed OS. Results available at [FONT=arial]http://paste.ubuntu.com/14439023/[/FONT]
2) Install Ubuntu 15.04 first, then upgrade to 15.10. I found that if I install 15.04, run all updates:[INDENT]sudo apt-get update[/INDENT]
[INDENT]sudo apt-get upgrade[/INDENT]
then run [INDENT]sudo do-release-upgrade -d[/INDENT]

Ubuntu 15.10 works.

I'm still not sure of the source of the problem, but at least found a couple of work arounds for those that may have similar problems.

---

### Post by geekgee on 2016-01-22
Thanks for your efforts... the Boot-Repair method worked me.

I have an Intel NUC5i7RYH with a Samsung 256GB SM950 Pro PCIe NVMe M.2 SSD.  I had installed Ubuntu Mate 15.10 successfully but EFI wasn't able to boot off the SSD at all until I ran Boot-Repair as you instructed.

---

