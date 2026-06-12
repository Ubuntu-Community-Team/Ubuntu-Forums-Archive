---
title: "dual boot ub14/win7 - was working, now: windows starts, goes black, and"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by jon93 on 2015-06-17
Hi.  dual boot was working fine for months.  I don't know what happened, now:  grub shows ubuntu and win7, when i choose win7 win starts, hangs at startup progress bar and goes black.  nothing.
 
 
 I tried boot repair.  Said it solved it. Boot-repair created another win7 load entry on other partition but neither of them works.

 
 
 Any ideas?  thanks.  If I can't fix the dual boot, I'd be happy to get win7 to load, that's my working os.


   
Here is the boot-repair link:  [http://paste.ubuntu.com/117261191](http://paste.ubuntu.com/117261191)

thank you

---

### Post by oldfred on 2015-06-17
Pastebin not valid. Please correct.

Boot-Repair typically copies the Windows boot files from the 100MB Windows Boot partition to the main install. Many user just did not know that Boot partition was essential and deleted it and had no boot files to repair it with. But then grub2's os-prober sees both sets of boot files and adds boot stanzas for both.

---

