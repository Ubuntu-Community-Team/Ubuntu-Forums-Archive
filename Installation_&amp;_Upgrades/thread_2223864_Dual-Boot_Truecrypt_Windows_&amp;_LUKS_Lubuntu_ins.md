---
title: "Dual-Boot Truecrypt Windows &amp; LUKS Lubuntu install"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Remten on 2014-05-13
I am making a dual-boot installation of Lubuntu 14.04 (encrypted with dm-crypt LUKS) and Windows 7 (encrypted with Truecrypt) on a laptop that has a single hard drive (an SSD).
I am basically following the procedure described in this thread:
[http://ubuntuforums.org/showthread.php?t=1229541&page=3&p=10113708#post10113708](http://ubuntuforums.org/showthread.php?t=1229541&page=3&p=10113708#post10113708)

/dev/sda1 - Windows' boot info (system reserved), the partition is flagged as bootable.
/dev/sda2 - Windows' encrypted files.
/dev/sda3 - Lubuntu's /boot info (along with memdisk and Truecrypt's rescue disk iso), unencrypted.
/dev/sda4 - Lubuntu's /root, encrypted.

I installed Lubuntu using the alternative installer, and at the end I had the installer put the grub boot loader on /dev/sda. I then put copies of memdisk and Truecrypt's rescue disk iso on /dev/sda3, and updated grub with a grub.d/custom entry pointing to /dev/sda3 for booting Windows.

So now from the grub screen, I'm able to boot into Lubuntu fine.
But when I try to boot into Windows instead, I get an error that is caused by Truecrypt data that still needs to be removed from the MBR. This is an expected problem:
[http://ubuntuforums.org/showthread.php?t=1229541&page=4&p=11359228#post11359228](http://ubuntuforums.org/showthread.php?t=1229541&page=4&p=11359228#post11359228)
The suggested way to fix it is with
```
echo 'grub<3tc' | dd of=$yourhd count=8 bs=1 seek=6
```

I was able to do that successfully on the same laptop with Win 7/Truecrypt and Lubuntu **13.10**/LUKS. (Although I don't remember exactly which other steps I may have taken back then.)

But when I now try to issue the command with Lubuntu **14.04**, I get an error message
```
echo 'grub<3tc' | dd of=/dev/sda count=8 bs=1 seek=6
    dd: failed to open '/dev/sda' : Permission denied
```

I tried to do this using live CDs for lubuntu and xubuntu, as well as from booting directly into the already-installed lubuntu.

I am new to linux, so maybe the answer is very simple and obvious, but I am stumped.

---

### Post by Remten on 2014-05-13
Not sure if it is relevant, but it is non-UEFI. (Truecrypt can't handle UEFI, so I turned off UEFI in BIOS, or tried to anyway.)

---

### Post by matt_symes on 2014-05-13
Hi

```
echo 'grub<3tc' | dd of=/dev/sda count=8 bs=1 seek=6
```

I can i no way comment on  the above command as i have no idea whether it will fix your problem.

Commands like the command above have a habit of scaring me unless i know  exactly, not only what they do, but why they should fix issues in the  first place.

Can i make a suggestion: Image you hard drive before running the command in case it trashes your drive and makes it unbootable.

I guess what i am asking is are you 100% sure the above command will fix the issue ?

However, you say you have done this before so to get the command working you need to type.

```
echo 'grub<3tc' | **sudo **dd of=/dev/sda count=8 bs=1 seek=6
```

Use at your own risk.

Kind regards

---

### Post by Remten on 2014-05-13
> **matt_symes said:**
> Hi

```
echo 'grub<3tc' | dd of=/dev/sda count=8 bs=1 seek=6
```

I can i no way comment on  the above command as i have no idea whether it will fix your problem.

Commands like the command above have a habit of scaring me unless i know  exactly, not only what they do, but why they should fix issues in the  first place.

Can i make a suggestion: Image you hard drive before running the command in case it trashes your drive and makes it unbootable.

I guess what i am asking is are you 100% sure the above command will fix the issue ?

However, you say you have done this before so to get the command working you need to type.

```
echo 'grub<3tc' | **sudo **dd of=/dev/sda count=8 bs=1 seek=6
```

Use at your own risk.

Kind regards
 
That was it! Thanks. The dual-boot works now.

---

