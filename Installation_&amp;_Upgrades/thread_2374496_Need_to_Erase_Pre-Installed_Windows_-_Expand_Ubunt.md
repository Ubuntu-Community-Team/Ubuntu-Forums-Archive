---
title: "Need to Erase Pre-Installed Windows - Expand Ubuntu"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2017-10-16
The Short Version:

On a new (to me) computer that came with Windows 10 pre-installed, on which I have installed Ubuntu as well, how do I delete the Windows partition and expand the Ubuntu partition(s) to take it's place?

The Long Version:

I accidentally disabled UEFI boot mode before installing Ubuntu. I shrank the Windows partition down to 30gb and installed Ubuntu in the 204(?)gb remainder, leaving the original recovery partition alone. Windows would boot, but Linux wouldn't. I found my mistake and re-enabled UEFI boot mode and reinstalled Ubuntu. Now Linux will boot, but Windows no longer shows in the grub menu, which I have to call up with the left shift key. I really don't need or want Windows anyway, but I would like to keep the recovery partition, just in case. The disk image looks like this:

```
 
     System     |   Windows   |                             Extended Partition 4 204 GB                                | Recovery Image | Free Space
   Partition 1   |  Partition 2  |---------------------------------------------------------------------------|      Partition 3     |    1.2 MB
367 MB HTFS | 30 GB NTFS |  Filesystem Partition 201 GB Ext4  |  Swap Partition 6 3.4 GB Swap  |                 16 GB NTFS    |

```

I haven't installed anything other than Ubuntu proper, so if I have to start fresh I can do that too.

---

### Post by RobGoss on 2017-10-16
From reading your post it sounds like you no longer care to use Windows correct?

Why not just do a clean install of Ubuntu and save yourself a lot of time and trouble

---

### Post by rebeltaz on 2017-10-16
> **RobGoss said:**
> From reading your post it sounds like you no longer care to use Windows correct?

Why not just do a clean install of Ubuntu and save yourself a lot of time and trouble

lol.. yeah, I most likely will never use windows, but I'm the kind of person who likes backup options. Glutten for punishment, I suppose. I probably will just wipe the drive, but... unbeknownst to you, you solved my problem. The 'bootrepair' link in your signature did the trick. Thank you :)

---

### Post by RobGoss on 2017-10-16
Wanting to have something to fall back on is always a good idea, It took me sometime before I deleted my last installation of Windows but after I did I have no regrets

Glad you got it all sorted out

---

### Post by ian-weisser on 2017-10-16
With W10, you don't need to retain the recovery partition. You simply need to preserve (write down) the Product Key stored in UEFI.
If you ever wish to reinstall W10 on the same hardware, download the USB installer from MS and enter the Product Key when prompted.

---

### Post by rebeltaz on 2017-10-17
> **ian-weisser said:**
> With W10, you don't need to retain the recovery partition. You simply need to preserve (write down) the Product Key stored in UEFI.
If you ever wish to reinstall W10 on the same hardware, download the USB installer from MS and enter the Product Key when prompted.

Too late :) 

There is a product key on a sticker on the main unit. Would that be the same as the key stored in UEFI? I did not know that. I haven't installed windows since XP! lol

I appreciate that info. Thank you!

---

### Post by RobGoss on 2017-10-17
> **ian-weisser said:**
> With W10, you don't need to retain the recovery partition. You simply need to preserve (write down) the Product Key stored in UEFI.
If you ever wish to reinstall W10 on the same hardware, download the USB installer from MS and enter the Product Key when prompted.


Good tips  was not aware of this my self, I have removed a few OS's of Windows. I also believe the Product key is embedded on some motherboards

---

### Post by ian-weisser on 2017-10-17
> **rebeltaz said:**
> There is a product key on a sticker on the main unit. Would that be the same as the key stored in UEFI?

High likelihood they are identical.

---

