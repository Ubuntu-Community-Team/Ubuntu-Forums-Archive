---
title: "How to make os_finder work on encrypted drive?"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by Isgar on 2012-07-27
Hello, this is what I did:
 -install Windows 7
-get rid of the 100mb boot partition and install boot-data on main win-partition (a terrible idea in hindsight)
-install ubuntu encrypted (/boot unencrypted)
-install grub2 into /boot 
-encrypt win7 with truecrypt and install tc-bootloader into MBR  

Until here, everything works fine. On startup tc-bootloader chains into grub, where i can choose to boot win7 or ubuntu. I got a bit annoyed that the win7 boot option was so far down in the grub menu, so I changed the order in /etc/grub.d 

The win7 boot option vanished completely from grub.  I wasnt aware how update-grub worked, it obviously cant find win7 with os_prober when the partition is encrypted. Sadly I didnt backup grub.cfg either.

 So how can I make os_prober work?
 Or alternatively, can I write/copy the script for win7 myself?

---

### Post by darkod on 2012-07-27
I was under the impression you need to leave the win7 boot files outside the encrypted partition too, same as with unencrypted /boot.

I think even TC won't be able to boot win7 directly with the boot files on encrypted partition. Can you boot win7 without going into grub2?

I suggest you try a new layout on the disk, with the win7 boot files outside the encrypted partition.

---

### Post by Isgar on 2012-07-27
> I think even TC won't be able to boot win7 directly with the boot files on encrypted partition.Why not? The tc-bootloader in the MBR decrypts the drive, so boot-data can be read.

> Can you boot win7 without going into grub2?How? I didnt find a way to ignore or skip grub while booting, but i rather do that before deinstalling grub just to test it...

---

### Post by darkod on 2012-07-27
> **Isgar said:**
> Why not? The tc-bootloader in the MBR decrypts the drive, so boot-data can be read.

How? I didnt find a way to ignore or skip grub while booting, but i rather do that before deinstalling grub just to test it...

With the mentioned TC bootloader. I don't work with encryption, but if it's called bootloader it should boot at least some OS, like windows, right? The point is, can it boot win7 with the boot files encrypted. Lets imagine it's single boot and you have no grub2. Can TC boot win7 as it is?

I read in one thread today that the person said for encrypted windows you need the boot files outside. I don't know more about that, except what i read. And I don't know if TC can decrypt them early enough so that the boot files can be found. Are you sure about that?

---

### Post by Isgar on 2012-07-27
I found a solution, i.e. i wrote a custom entry in grub.d/ that works:

```
 menuentry "Windows 7" {
    insmod ntfs
    set root=(hd0,msdos1)
    ntldr /bootmgr
}

```> Lets imagine it's single boot and you have no grub2. Can TC boot win7 as it is?Yes, the extra boot partition is a new feature in Windows 7, but you could encrypt system partitions with previous versions. I dont know if it would still be possible with the multiboot option selected (during encrypting).

---

### Post by darkod on 2012-07-27
So it was just that os-prober couldn't detect it and you needed to make a manual entry. Good job. :)

---

