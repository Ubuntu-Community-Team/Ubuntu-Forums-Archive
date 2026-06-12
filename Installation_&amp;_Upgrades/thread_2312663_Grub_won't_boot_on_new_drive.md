---
title: "Grub won't boot on new drive"
date: 2016-02-06
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2016-02-06
I have a hard drive that is failing.  I have moved everything onto a new disk, installed GRUB on the new drive (currently called /dev/sdb1) and can chainload from the old grub loader to the new one successfully.  However, if I remove the old disk then the system fails to boot and I just get a blank screen with "GRUB " at the top.  If it is any relevance, I am using "legacy" grub - i.e. 0.97 for various reasons.

What have I done wrong?

---

### Post by ajgreeny on 2016-02-06
I have no idea if you've done anything wrong but I think Boot-Repair in my signature below may help you; as far as I'm aware it will still work on legacy grub, though it is a very long time since I've done anything using that version.

---

### Post by Colin@oxford on 2016-02-06
Solved! it appears that there was an old GRUB installed in the MBR.  I had installed in the partition so that worked on chainload but not on direct boot from the BIOS.  Re-installed GRUB to the MBR and all was OK.

How do I mark this thread "solved" ?

---

