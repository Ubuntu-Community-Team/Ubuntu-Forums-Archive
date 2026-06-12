---
title: "PXEBoot with multiple drives prompts"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2010-04-30
I want to boot off pxeboot w/ multiple drives and just go through formatting the first drive.  My preseed.cfg works fine here with one drive in the machine:

[https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot#preseed.cfg](https://www.digisoftinc.org/wiki/index.php/Ubuntu_preseed.cfg_installs_off_PXE_Boot#preseed.cfg)

but when I have more than one drive it prompts me to write the changes to disk.  How can I by pass this?  

I also have tried this with no luck:

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

Any help would be greatly appreciated.  I'm using the new AMD64 LTS.

---

