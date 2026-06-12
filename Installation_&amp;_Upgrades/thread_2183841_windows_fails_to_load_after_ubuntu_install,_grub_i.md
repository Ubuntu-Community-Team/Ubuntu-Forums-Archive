---
title: "windows fails to load after ubuntu install, grub issue"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by izar on 2013-10-26
I recently install ubuntu 13.10 in dual boot with windows 7.
when i startup grub loads fine, and so does ubuntu.
but if i select windows from grub i get an error message, something like:

```
"windows failed to start. A recent hardware or software <bla bla bla..>"
error code: "0xc000000f" 
```

**my workaround:**
i reverted the mbr to a backup i created before installing ubuntu. now windows loads ok. (no grub or ubuntu available now of course...)
so this is obviously an issue with grub not loading windows properly, but i have no clue how to fix it. :(

**additional info:**
hp Folio 9470m
SDD hard-drive
windows seems to startup from a small partition (102MB) labelled "boot" on the beginning of the hard drive.

**note:**
i posted the question also here: [http://askubuntu.com/questions/366333/windows-fails-to-load-after-ubuntu-install-grub-issue](http://askubuntu.com/questions/366333/windows-fails-to-load-after-ubuntu-install-grub-issue)

---

### Post by oldfred on 2013-10-26
Do you have Windows 7 hibernated? That often causes issues?

---

### Post by Allavona on 2013-10-26
The issue isn't with Grub since your able to see and start the windows boot sequence. You have UEFI, and that small FAT32 partion contains the BCD which is corrupted as the error code states. Use the link in Oldfreds post for installing on UEFI.

---

### Post by izar on 2013-10-27
@oldfred:
no windows is fully shutdown.

@allvona:
my bios has a uefi option but it is set to 'legacy' instead. this is how it came per-installed with windows, and it still works now as i mentioned.
also, i can't see how the BCD can be corrupt if i can boot it using original MBR.
also, i think if i had UEFI then grub would not work at all unless installed properly.
BTW the small partition is ntfs, and i think it is used because the main partition is encrypted.

i think i will try the boot-repair tool, but i'll backup everything first because this tool seems vary dangerous.

---

### Post by izar on 2013-10-28
tried re-installing everything from scratch. tried also the boot-repair tool.
same results.:(

---

### Post by oldfred on 2013-10-28
Normally Windows boots from reading MBR and finding partition with boot flag and jumping to its PBR partition boot sector to boot. All grub does jump directly to the PBR which bypasses the Windows MBR code.

Perhaps with encryption the Windows MBR code does something more? So something is not intialized correctly?

On Vista but 7 is the same with just the separate boot partition.
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I might try chkdsk in Windows. I had an old XP that would boot, but could not be seen from anything in Linux. After a chkdsk then I could see it from Ubuntu and it booted a bit faster.

---

