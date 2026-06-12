---
title: "Buffer I/O error on device after RAID 0 install"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by kipling100 on 2008-01-15
Hi,
I installed Ubuntu 7.10 on my RAID 0 set, following a fakeraid tutorial.  Everything boots up fine and I've been using it for about a week now.

However, I get Buffer I/O errors from my dmesg output every time.  Can someone make sense of this?

```

[   18.602430] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.061245] Buffer I/O error on device sdb1, logical block 819201152
[   26.061250] Buffer I/O error on device sdb1, logical block 819201153
[   26.061254] Buffer I/O error on device sdb1, logical block 819201154
[   26.061257] Buffer I/O error on device sdb1, logical block 819201155
[   26.061261] Buffer I/O error on device sdb1, logical block 819201156
[   26.061264] Buffer I/O error on device sdb1, logical block 819201157
[   26.061268] Buffer I/O error on device sdb1, logical block 819201158
[   26.061272] Buffer I/O error on device sdb1, logical block 819201159
[   26.061276] Buffer I/O error on device sdb1, logical block 819201152
[   26.061280] Buffer I/O error on device sdb1, logical block 819201153
[   38.100199] Buffer I/O error on device sdb1, logical block 819201152
[   38.100569] Buffer I/O error on device sdb1, logical block 819201153

```

Thanks in advance,

Dennis

---

### Post by Partyboi2 on 2008-01-15
One solution is to try with  acpi=off added to boot options. Read more [here]("http://ubuntuforums.org/showthread.php?t=629707")
Another solution is to apply a patch. More [here]("http://gaugusch.at/kernel.shtml")
 [http://ubuntuforums.org/archive/index.php/t-426684.html](http://ubuntuforums.org/archive/index.php/t-426684.html)

---

### Post by kipling100 on 2008-01-15
Thanks for your response -- I'll try that out.
Do you think the buffer I/O errors are related to acpi?

---

