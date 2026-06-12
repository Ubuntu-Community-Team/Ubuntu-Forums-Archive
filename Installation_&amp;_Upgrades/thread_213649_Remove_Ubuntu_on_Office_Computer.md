---
title: "Remove Ubuntu on Office Computer"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by murph2481 on 2006-07-11
I need to turn in my laptop for work and need to uninstall Ubuntu Dapper.  Can I just delete the partition and call it good?  What happens with GRUB?  Basically I want to remove all traces of Ubuntu

Thanks,
Dan

---

### Post by aysiu on 2006-07-11
[http://support.microsoft.com/default.aspx?scid=kb;en-us;314458](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)

---

### Post by murph2481 on 2006-07-11
> **aysiu said:**
> [http://support.microsoft.com/default.aspx?scid=kb;en-us;314458](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)

Alright thats assuming i reinstall windows to that machine.  What happens if I dont reinstall windows and just wipe out the partition with Linux?

---

### Post by aysiu on 2006-07-11
> **murph2481 said:**
> Alright thats assuming i reinstall windows to that machine.  What happens if I dont reinstall windows and just wipe out the partition with Linux?
The instructions I linked to tell you how to remove Ubuntu.

---

### Post by murph2481 on 2006-07-11
> **aysiu said:**
> The instructions I linked to tell you how to remove Ubuntu.

What if I am not reinstalling windows?

---

### Post by aysiu on 2006-07-11
1. Delete the Ubuntu partition
2. Use the *fixmbr* utility
3. Reformat the Ubuntu partition as FAT32 or NTFS

---

### Post by T700 on 2006-07-11
I think if you follow the instructions to 1. e. and then stop, you'll accomplish your goal.

Paul

---

### Post by Mike_N on 2006-07-11
Deriks Boot & Nuke(D-BAN) is what i use to wipe all traces of anything off hard drives. It take a while but never fails...

---

