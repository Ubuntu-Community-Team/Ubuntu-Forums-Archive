---
title: "Broken boot - Wubi"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Virgofenix on 2008-05-14
Here's what I did:

1] Installed WinXP SP2 on an NTFS partition( E: )
2] Created another NTFS partition( F: )
3] Installed Ubuntu using Wubi on F:
4] Deleted an existing FreeDOS FAT partition( C: )
5] Attempted to install Ubuntu, this time without Wubi, to the free space that was created from deleting C:
6] Installation fails (ERRNO5 - Input/Output error)

Now I can't boot into either WinXP or the Wubi installed Ubuntu. The BIOS tells me there aren't any disks present. I'll take care of the ERRNO5 issue some other time; right now, priority is booting into Ubuntu or Windows.

How can I boot into either Windows or Ubuntu? I used grub on Live-CD whenever I broke the boot of my non-Wubi Ubuntu install on my desktop. Afaik, Wubi-installs are bootable images. Can Live-CD touch data inside Wubi installs?

Here's the machine with the problem: [http://h10010.www1.hp.com/wwpc/hk/en/ho/WF06a/1090709-1116637-1123071-1123071-1123071-80598788.html](http://h10010.www1.hp.com/wwpc/hk/en/ho/WF06a/1090709-1116637-1123071-1123071-1123071-80598788.html)

---

### Post by Virgofenix on 2008-05-15
Day after bump.

---

### Post by johnbl on 2008-05-15
Seems like deletion of C: is the MS root drive and with that gone ...

---

### Post by Virgofenix on 2008-05-15
E: is the MS root drive. I'm trying to get Windows running today using the Windows disk. Should be easy enough with fixmbr. Problem is the Wubi install. I don't know that much about grub; and I used to just follow how-to's when fixing it. I haven't found any how-to's for fixing Wubi installs nor any scenarios similar to the one I'm having.

Edit: fixmbr isn't working; and the Repair console reads the Windows partition E: as C:. Looking over fixmbr info some more. If I can't get Windows to work that way then I'm guessing grub is my only hope.

---

### Post by GamerZFX on 2008-11-27
> **Virgofenix said:**
> E: is the MS root drive. I'm trying to get Windows running today using the Windows disk. Should be easy enough with fixmbr. Problem is the Wubi install. I don't know that much about grub; and I used to just follow how-to's when fixing it. I haven't found any how-to's for fixing Wubi installs nor any scenarios similar to the one I'm having.

Edit: fixmbr isn't working; and the Repair console reads the Windows partition E: as C:. Looking over fixmbr info some more. If I can't get Windows to work that way then I'm guessing grub is my only hope.

Something I've learned with several installations of winblowz, no matter what drive you put windows on (lets say H:) the ntldr, boot.ini, ntdetect.com, as well as other core system files will ALWAYS be on C: NO MATTER WHAT... Hopefully this helps (need a reinstall)

---

