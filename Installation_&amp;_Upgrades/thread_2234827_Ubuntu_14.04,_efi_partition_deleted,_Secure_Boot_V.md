---
title: "Ubuntu 14.04, efi partition deleted, Secure Boot Violation"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by kevpatts2 on 2014-07-17
Hey all,

Have a new Dell 15R and I was dumping the pre-installed Win8 and going for Ubuntu 14.04. During installation I deleted all partitions (including EFI) and recreated as needed: efi, swap and root. Now when I boot I get a "Secure Boot Violation: Invalid signature detected. Check Secure Boot Policy." It does still boot though once I skip this error.

At the grub2 prompt if I type help I get:
error: Secure boot forbids loading of module from (hd0,gtp3)/boot/grub/x86_64-efi/help.mod.

I know this is because I deleted the EFI partition like an idiot! How do I fix this?

By the way, before doing this I successfully had Win8 and Ubuntu 14.04 dual booting to confirm hardware support. When it was like that I didn't get any Secure Boot warnings.

---

### Post by ajgreeny on 2014-07-17
I think Boot-Repair (see my signature) will be able to fix this for you by adding a new EFI partition, or putting the files needed back into the existing EFI partition.

---

### Post by kevpatts2 on 2014-07-17
I went in, click advanced options, enabled "Use the standard EFI file" and applied, went through all the procedures and rebooted, but same error is shown.

---

### Post by yancek on 2014-07-17
I don't use Secure Boot but from what you said, I wonder if disabling Secure Boot in the BIOS would eliminate this problem.  You don't indicate whether you have done that?

---

### Post by kevpatts2 on 2014-07-18
Disabling Secure Boot does make it work properly, but I'd like Secure Boot to be enabled.

I'm going to try to:
1. Delete all partitions while booted from a livecd.
2. restore the entire machine from the Win8 backup disk I made before I installed Ubuntu. Hopefully this will recreate the efi partition.
3. reinstall without deleting the efi partition this time.

---

### Post by oldfred on 2014-07-18
Secure boot is more about marketing than safety currently. 

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

Microsoft has had major issues with virus and other security issues. So they implement "Secure Boot" which solves an issue that has barely existed. But most do not know difference so now they think Windows is safer.  The only major Boot virus was actually Sony's implementation of it to prevent users from using/misusing? Sony software.

Later secure boot may be important, but currently is it not.

---

