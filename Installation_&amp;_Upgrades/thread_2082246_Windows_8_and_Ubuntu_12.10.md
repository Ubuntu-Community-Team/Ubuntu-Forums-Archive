---
title: "Windows 8 and Ubuntu 12.10"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by Avilade on 2012-11-08
Hello all

I try to install ubuntu "12.10" on a laptop with windows 8. The problem is that now can not get into windows (in ubuntu no problem), when I try to get the following error:

error: invalid EFI file path.


I read in the forum about "boot-repair", but generates the message GPT detected. Someone who can help me please.


[http://paste.ubuntu.com/1343875/]("http://paste.ubuntu.com/1343875/")

---

### Post by oldfred on 2012-11-08
Welcome to the forums.

gpt is the partitioning system used with UEFI, it replaces the 30 or 40 year old MBR partitioning system. 

It looks like Ubuntu installed ok and Windows is still there.

Grub2's os-prober has a bug where is still creates a BIOS type Windows boot, not the new efi boot. So that is why you get an invalid efi path.
Boot-Repair can fix it by adding correct efi Windows chain entry, but you will still have the old entries unless you clean them up. Easiest way is with Grub customizer.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

---

### Post by Avilade on 2012-11-08
Thanks oldfred. 

I installed "grub customizer" but now I do not know how to do "adding correct efi Windows chain entry".

Which are  Windows chain entry?

Thanks

---

### Post by oldfred on 2012-11-08
You need to use Boot-Repair to add the correct UEFI entry or manually added it.

But then you can use Grub customizer to remove the incorrect entries.

Correct chain entry is to the efi boot entry not to the Windows partition. This type of entry would be in 40_custom if you want it at the end or something like 25_custom if you want it before the incorrect entries created by the 30_os-prober. The scripts are run in number order, so that is where each script adds to the grub menu.

```
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

---

