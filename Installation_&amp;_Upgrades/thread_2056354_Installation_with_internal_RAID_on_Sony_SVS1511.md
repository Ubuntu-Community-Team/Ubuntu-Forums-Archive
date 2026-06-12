---
title: "Installation with internal RAID on Sony SVS1511"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by JJSkoli on 2012-09-11
I just bought a Sony SVS1511, on which I tried to install Ubuntu 12.04. I have had serious problems, which I only managed to circumvent, not solve. 

At the time of the installation I was unaware of the fact that the much touted 256GB SSD disk is actually a RAID 0 composite of two 128GB disks. So I tried to install through the usual iso for the 64bit version. Apparently grub recognized the presence of the RAID0 disk, and claimed to have completed the install. Power off, reboot, error message:
```

unable to locate operating system

```
After a few tries, I accessed the UEFI, deleted the RAID configuration, installed on the first disk. I now mount the other disk separately.

My questions are: 
1) I thought the ubuntu installer was supposed to detect RAID configurations automatically, without any need of manual intervention; so what's wrong?

2) Can I/should I restore the RAID configuration? In other words, is it worth the trouble performance-wise?

3) If it is worth the trouble, can someone please suggest the correct procedure to do this?


Thanks, cheers.

---

### Post by oldfred on 2012-09-11
I do not know RAID, but see little advantage to RAID on SSD drives. Also RAID 0 is not normally suggested.

Ubuntu's liveCD does not include RAID drivers, you have to use alternative or server versions to have the extra drivers that are more common with server installs. With RAID you have to install grub2's boot loader to the root of the RAID array not the MBR of the drive. Not sure with UEFI how that all works, but that adds another level of complexity.

Did you use 64bit and install in UEFI mode or in BIOS mode? How you boot liveCD determines which way you install.

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

To see details of your install:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by YannBuntu on 2012-09-12
Hi
Please first indicate your Boot-Info URL ([https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)), so that we know your exact config.

---

### Post by JJSkoli on 2012-09-13
Yes, thanks:

[http://paste.ubuntu.com/1201976/](http://paste.ubuntu.com/1201976/)

BTW, during my unsuccessful attempts to install 12.04 on the RAID0 configuration, I ran boot-repair. It stalled checking for my devices. I let it run for about 30 minutes (it protested it could take several minutes), then I figured it was taking too long, and cut it off. 

@oldfred:

I imstalled the 64bit version under UEFI, and used gpt for the disks. 

Once again, thanks for your help.

---

### Post by YannBuntu on 2012-09-13
> **JJSkoli said:**
> Yes, thanks:

[http://paste.ubuntu.com/1201976/](http://paste.ubuntu.com/1201976/)

Did you create this Boot-Info with RAID activated or deactivated ? (i suppose it was deactivated?)

My suggestion here would be to:
1) check the BIOS if there is an entry for sda1/efi/ubuntu/grubx64.efi . Create one if there isn't.
2) in case BIOS can't find the sda1 EFI partition: create a 2nd EFI partition on sdb, and use Boot-Repair to install grub in it.

---

### Post by JJSkoli on 2012-09-13
RAID is still de-activated.

There is no entry of the kind you suggest in the BIOS, so I'll create it. The file you mention is actually located in
```

/boot/efi/EFI/ubuntu/grubx64.efi

```
Should I point the BIOS to this path, or to the one you suggest,
```

sda1/EFI/ubuntu/grubx64.efi

``` 
?

---

### Post by darkod on 2012-09-13
The confusing thing is that the standard live cd does detect a fakeraid array (bios raid), and it can install on it, but very often it fails to install the bootloader. In my opinion, it should either be able to install all the way, or they should remove the module that is detecting the array so that it doesn't detect it at all (on the other hand some people might install on only one disk in this case and ruin their array).

For best raid support you need to use the Alternate Install CD. That should install the bootloader correctly.

I agree with oldfred that SSD raid makes little sense. Maybe for some testing, but not long term. It will provide some speed improvement, but on the other hand your data is at risk in RAID0 because if one disk goes, you lose all the data.

So, basically using the raid or not is your choice. You could use RAID1 maybe, but that will give you only 128GB usable space which is shame with SSDs. You lose half of it.

Also, are you trying to dual boot or not? If dual booting, the UEFI adds more complexity as oldfred said. If you plan to use only ubuntu, it should be much easier.

Also, if you decide to use raid, if dual booting you have to use the fakeraid. If using only ubuntu you can disable the raid in bios and use the linux software raid, regardless if we are talking about raid0 or raid1. You also need the alternate cd for that.

---

### Post by YannBuntu on 2012-09-13
**@JJSkoli:** the path "/boot/efi/EFI/ubuntu/grubx64.efi" is the one seen from Ubuntu. As /boot/efi is the mount point, I suppose that the BIOS sees another path, eg [UUIDofSDA1]/EFI/ubuntu/grubx64.efi or simply /EFI/ubuntu/grubx64.efi  . Please tell us if you find.

**@darkod:** for my information, why is RAID better supported by the Alternate? (because mdadm is preinstalled? because Ubiquity is buggy?)

---

### Post by darkod on 2012-09-13
> **YannBuntu said:**
> 
**@darkod:** for my information, why is RAID better supported by the Alternate? (because mdadm is preinstalled? because Ubiquity is buggy?)

I wrote that from the point of view that it does install the bootloader correctly on fakeraid, unlike the installation started from live cd.
With the alternate installer, you almost never need to add grub yourself.
With the live cd, almost always. And that confuses many people after the first reboot when there is no grub.

---

