---
title: "Install ubuntu on ufd"
date: 2021-12-28
forum: Installation &amp; Upgrades
---

### Post by baretta8989 on 2021-12-28
Hi All

I am new user in this os
First sorry if i write in wrong room

I have problem install ubuntu 21.10
I use acer aspire r11 and want install ubuntu in flash disk 64gb plug and play

I was make 3 partition
500 mb fat 32 for uefi partition with sdb1
4 gb swap sdb2
56 gb ext4 root partition sdb3
I select boot location on sdb part

I was diaable flag boot in windows hardisk efi partition

After i finish install
I am restart and unplug live usb iso 
And i press f12 select boot from my ubuntu ufd
Bit failed boot and my notebook restart with text appear in screen system restart

What the solution for this 

Thanks

---

### Post by TheFu on 2021-12-28
In general, end-users should stick with LTS releases only.  That would be 20.04 currently.
Newer releases aren't LTS (currently) and often have "technology demonstration" features that aren't ready for most users and still need some work.  This makes it hard for a new user to know whether something is actually broke or just behaving in the new way that hasn't been worked through yet.   A number of new technology features recently released have turned out badly. Most have been removed as defaults in the LTS release when that happened.

In short, 20.04 is the version almost everyone who isn't a developer should be running.  There are exceptions - like for extremely new hardware.  In general, Linux won't support really new hardware, so if you have that, expect to wait a year for solid support to be released in the non-LTS version.

When it comes to UEFI installations, beware that 1 partition on the hardware will have the UEFI stuff and it should be shared across all OSes. Creating a 2nd on a different disk is asking for problems and going to cause confusion.  This is an aspect of EFI booting.  If you google for "ubuntu UEFI", a help.ubuntu.com webpage will come up that is full of information.

I'm unfamiliar with the "ufd" term. Please explain.

---

### Post by QIII on 2021-12-28
This is a request for support, not a chat.  Moved to Installation & Upgrades.

---

### Post by baretta8989 on 2021-12-29
Thanks for your answer
I will ry install LTS 
I always fail install linux in ufd with uefi
Before  i install ubuntu i try install elementary os but the result same can not boot

But i try install chrome os it is success can boot

---

### Post by grahammechanical on 2021-12-29
An internet search reveals; ufd = USB Flash Drive. This is a removable drive. Yes? With the USB Flash Drive removed does Windows still boot? I think it does not because you removed the boot flag from the Windows efi partition.

When you installed Ubuntu to the USB Flash Drive was the Windows drive disconnected? If it was not then it is possible that the Ubuntu installer put the Ubuntu boot files into the Windows efi partition.

When you reinstall Ubuntu keep the Windows drive disconnected. This will force the installer to put the Ubuntu boot files into the efi partition on the USB Flash Drive. Then use the UEFI settings to select the boot order from Windows drive to USB Flash Drive whenever you plug the Ubuntu USB flash drive into the machine.

Regards.

---

### Post by tea for one on 2021-12-29
When you remove the USB Flash Drive, can you confirm that you can boot into Windows?

---

### Post by baretta8989 on 2021-12-29
Yes i want if i unplug usb flash disk it will be boot windows
And if i plug ufd it will run boot linux

Before i restart after finish install linux  i restore boot flag windows partition

I success install in chrome os
But always fail in any variant linux
I dont know why

I check, i mount efi partition linux
The boot file was already in boot partititon flash disk

---

### Post by TheFu on 2021-12-30
I've never known ChromeOS to be bootable with any other OS. Is this a new thing?  IME, I always had to wipe the firmware and physically remove a write-protect screw to get any Chromebook to use any OS other than ChromeOS. After those modifications, ChromeOS couldn't be used on the system again.  Are newer Chromebooks able to boot multiple OSes?  My chromebook experience is from 2011 - 2015.

---

### Post by tea for one on 2021-12-30
> **TheFu said:**
> I've never known ChromeOS to be bootable with any other OS. Is this a new thing? 

There is an organisation acquired by Google approx a year ago. [https://www.neverware.com/#intro](https://www.neverware.com/#intro)
You can download a free version for home use.

Perhaps the OP could offer clarification?

---

### Post by TheFu on 2021-12-30
I've followed Neverware for years.  Thought they were ChromiumOS, not ChromeOS.  Big difference when it comes to security. Huge.  Part of ChromeOS security (which makes it probably THE most secure OS we can get in the world today, is the use of TPM hardware, signed kernels, signed boot setups and 2 complete versions of the OS on the 11 GPT partitions.  5 for the "A" OS and 5 for the "B" OS, with the end- user having 1, encrypted, partition. Google pushes OS upgrades without asking and there is no way to stop it without using firewall blocking.

Neverware used to have VM images or even allow an installation into a VM, but that has been removed for some unknown reason. They took away the GPU drivers that VM systems use.

Neverware could be an ideal online banking distro, but making people dedicate an entire machine takes away from the usefulness.
 [https://krebsonsecurity.com/online-banking-best-practices-for-businesses/](https://krebsonsecurity.com/online-banking-best-practices-for-businesses/)

---

### Post by tea for one on 2021-12-30
> **TheFu said:**
> 
Neverware used to have VM images or even allow an installation into a VM, but that has been removed for some unknown reason. They took away the GPU drivers that VM systems use.

Is this useful?
[https://cloudreadykb.neverware.com/s/article/Download-CloudReady-Image-For-VMware](https://cloudreadykb.neverware.com/s/article/Download-CloudReady-Image-For-VMware)
I've not tried it (just supplying a bit of info)

---

### Post by TheFu on 2021-12-30
Not really. VMware stuff is DOA here after the things their management did in 2010-2011.  

[https://cloudreadykb.neverware.com/s/article/Can-I-get-an-ISO-file-to-install-CloudReady](https://cloudreadykb.neverware.com/s/article/Can-I-get-an-ISO-file-to-install-CloudReady) is closer.  They claim the installer is a raw QCOW2 image file.

But we don't know if the OP is using ChromiumOS.

---

