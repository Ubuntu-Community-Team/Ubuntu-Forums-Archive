---
title: "upgrade from 2.6.24.17 to 2.6.24.18 --&gt; kernel panic."
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by lynnevan on 2008-06-19
Fortunately 2.6.24-17-generic still works.

The error message is the usual - searched the forums, but all of the errors I found involved upgrading from 7.04 to 7.10 or 7.10 to 8.04.  That's not my case.  Hardy has been running fine.  Just caught the latest upgrade to the next kernel.  The error message is > [   27.293340] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

  In /boot, "18" duplicates "17".  Nothing missing.
Checked menu.lst looked OK, but re-wrote it to use shortcuts in / (i.e.: vimlinuz, vmlinuz.old, etc).  Same result w/ vmlinuz.  vmlinuz.old works fine.  Did a "sudo locate "2.6.24-17-generic" & "2.6.24-18-generic" and compared the two.  The only difference I found in almost 8200 lines of files was in the "18" kernel:
> /lib/modules/2.6.24-18-generic/volatile_bcmwl
/lib/modules/2.6.24-18-generic/volatile_bcmwl/wl.ko
These don't exist in the 2.6.24.17 kernel.
By running "locate" I verified that "18" is in all the right places.

So, here I am, begging for some hint of what might be wrong.

Please, any ideas, thoughts, or whatever would be welcome!!!

Thanks in advance,

lynnevan

---

