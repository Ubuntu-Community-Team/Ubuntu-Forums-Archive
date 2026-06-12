---
title: "Errors  updating with dmks driver"
date: 2021-04-14
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2021-04-14
I just updated my system and got:

```
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-71-generic

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j4 KERNELRELEASE=5.4.0-71-generic -C /lib/modules/5.4.0-71-generic/build M=/var/lib/dkms/aacraid/1.2.1.60001/build....
Signing module:
 - /var/lib/dkms/aacraid/1.2.1.60001/5.4.0-71-generic/x86_64/module/aacraid.ko
Secure Boot not enabled on this system.
cleaning build area...

DKMS: build completed.

aacraid.ko:
Running module version sanity check.
Error! Module version 1.2.1.60001 for aacraid.ko
is not newer than what is already found in kernel 5.4.0-71-generic (1.2.1[50877]-custom).
You may override by specifying --force.

depmod...

Warning: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.

DKMS: install completed.
   ...done.
```

I' m confused here because I would think that 1.2.1.60001 is more recent that 1.2.1[50877]???

Please can you tell me what I need to do command by command to resolve this?

TiA David

---

### Post by DuckHook on 2021-04-14
I'm no server expert and don't work with RAID, so my input can only be of the general sort. The question here is: what have you done to your system? Lubuntu does not default to RAID. Therefore, you had to have installed it manually. It also seems like you installed a custom driver.

As a general observation, it is not possible to help with incomplete or insufficient info. Even for those with more RAID expertise than I have (who will hopefully jump in here), it is necessary to understand:

[list=1]
[*]what else you've installed, 
[*]how you installed it, 
[*]what your system HW setup is, 
[*]what you are trying to achieve, 
[*]what the system is used for, etc.
[/list]

---

### Post by David_Partridge on 2021-04-15
Meh!  I just have an Adaptec Raid card ASR-8885 (which is supported by LUbuntu out of the box), but so resolve a problem with the driver that comes with the kernel I installed the latest driver from Adaptec's website:

<https://storage.microsemi.com/en-us/downloads/linux_source/linux_source_code/productid=asr-8885&dn=adaptec+raid+8885.php>

The driver I installed was the dmks one.

David

---

### Post by DuckHook on 2021-04-15
If you replace a kernel module by installing a driver from an external source, then an update will naturally refuse to update that kernel module. After all, you presumably chose to replace the module for your own good reasons, and it would be potentially highly disruptive if the update process were to second guess you. What would it even use to "update"? The update process is both straightforward and primitive. It has no insight into your thinking or motives and will only update modules/apps/services after it has checked the previous version to ensure that all conforms to expectations.

If you want the latest kernel module in the repos, then I suppose you must back out your custom driver and install the repo driver.

CAUTION:

I have already noted that I have no RAID expertise. I do not know what this will do to your install. If you want to proceed on this advice, then make sure you have all of your data backed up and are prepared to reinstall from scratch if necessary.

---

### Post by deadflowr on 2021-04-15
Note that the system probably sees one version as 1.6 and the other as 15,
so to the system 15 is bigger and newer than 1.6.
You might need to manually remove the old first and then installing the new one.

> I have already noted that I have no RAID expertise. I do not know what this will do to your install. If you want to proceed on this advice, then make sure you have all of your data backed up and are prepared to reinstall from scratch if necessary.
Me too.

---

### Post by David_Partridge on 2021-04-15
Let us be clear here, the raid driver I downloaded and installed from the Microsemi (Adaptec) website (after advice from Adaptec Tech Support) is the latest version and fixes a problem with drive spin down (array downgraded on spin-up).  The version supplied with the kernel is back level.

All I am  asking is how I can nicely ask the system to ignore the fact that it incorrectly believes the driver I manually installed to be down level (which it isn't) and to use that instead of the version built into the kernel.

Surely not a big ask.

---

