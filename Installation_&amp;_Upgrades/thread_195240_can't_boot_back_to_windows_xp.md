---
title: "can't boot back to windows xp"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by mrbob on 2006-06-12
I have a Dell Dimension L1000R computer with a 1.2ghz pentium 3 processor and  
256 mb of RAM.

I booted Ubuntu from a cd and didn't install it, but now I can't get back in to windows xp!

If I try to boot without the Ubuntu CD my computer says "Error Loading Operating System"

I can still boot to the Ubunutu disk, though.

Could someone help me out?

---

### Post by rado_london on 2006-06-12
Are you sure you didnt run any partitioner or installer?

---

### Post by mrbob on 2006-06-12
i ran the installer but didn't press install.  It still registers the same amount of space being taken up on my hard drive in ubuntu.

---

### Post by elbryan on 2006-06-12
Try to insert the Windows XP cdrom.. then you enter into the rescue console and write "fixmbr".

With this you'll rewrite mbr..

---

### Post by mrbob on 2006-06-12
will this wipe my hard drive?

---

### Post by rado_london on 2006-06-12
MBR isnt hard drive, it is Master boot record the begging of the HD which has a small program for booting up the OS.

---

### Post by elbryan on 2006-06-13
Right .. rado_london is right .. it won't wipe nothing .. no data will be touched..

---

### Post by mrbob on 2006-06-13
thank you!

---

