---
title: "Grub error 15"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by puner on 2008-04-27
Hey,

I was installing hardy and everything went fine. When I rebooted I got error 21. I used the "super grub disk" to restore the windows MBR and then it showed me "Error 15"

How can I fix this?

---

### Post by meanburrito920 on 2008-04-27
When did you get the error? when attempting to boot windows or Hardy? Error 15 means that the specified boot file was not found. Can you boot into the Hardy recovery mode?

---

### Post by Rallg on 2008-04-27
If the booloader was not found: Is it on the partition that you think it should be? For example, did you forget that the /dev/sda numbering is different from the (hdx,y) numbering when you installed?

Did you put Grub on a removable device (such as USB)? If so, does the removable device think it is the hard drive according to its own numbering?

If so, those things can be fixed.

---

