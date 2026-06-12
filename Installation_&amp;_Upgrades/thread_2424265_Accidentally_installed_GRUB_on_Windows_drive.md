---
title: "Accidentally installed GRUB on Windows drive"
date: 2019-08-06
forum: Installation &amp; Upgrades
---

### Post by ecec on 2019-08-06
When I reinstalled Ubuntu I accidentally installed GRUB onto the Windows Vista drive instead of the Ubuntu drive. When I boot into the Windows drive, GRUB works normally, but when I boot into the Ubuntu drive, it fails. How do I change it back so Ubuntu loads GRUB and Windows uses its normal boot loader?

---

### Post by guiverc on 2019-08-06
Boot into your Ubuntu and use the command `sudo grub-install /dev/sdx`  (where sdx is the drive you want to install grub onto).

For windows 8 (vista) it's the in effect the same, boot into windows 8, then open the windows shell and enter the commands
`bootrec /FixMbr`
`bootrec /FixBoot`
`bootrec /RebuildBcd`
though having never done this on windows 8, I'd would confirm those instructions, as I did find sites (elsewhere on answers.microsoft.com) that suggested doing it a different way  - I don't support windows so you can read [https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues) yourself...

---

### Post by ecec on 2019-08-06
> **guiverc said:**
> Boot into your Ubuntu and use the command `sudo grub-install /dev/sdx`  (where sdx is the drive you want to install grub onto).

For windows 8 (vista) it's the in effect the same, boot into windows 8, then open the windows shell and enter the commands
`bootrec /FixMbr`
`bootrec /FixBoot`
`bootrec /RebuildBcd`
though having never done this on windows 8, I'd would confirm those instructions, as I did find sites (elsewhere on answers.microsoft.com) that suggested doing it a different way  - I don't support windows so you can read [https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues) yourself...

I tried the grub-install command, and I got this error:
```
Installing for i386-pc platform.grub-install: warning: your embedding area is unusually small.  core.img won't fit in it..
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

The "i386-pc" platform is also unusual because my operating system is 64-bit.

---

### Post by oldfred on 2019-08-06
Please post exact command you ran.
You get that error if installing to a partition's boot sector PBR or install to a protective MBR on a gpt partitioned drive.
If drive is MBR(msdos) then you should be installing to sdb or whatever drive is, not to a partition like sdb1 or sdb2.

The i386-pc is just the BIOS version of grub2 or grub-pc as opposed to the UEFi version of grub2 or grub-efi-amd64 (for 64 bit PC).

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

---

### Post by ecec on 2019-08-06
Never mind, I solved the issue.

---

### Post by wildmanne39 on 2019-08-06
Please post your solution so the whole community can benefit from your answer.

Thanks

---

