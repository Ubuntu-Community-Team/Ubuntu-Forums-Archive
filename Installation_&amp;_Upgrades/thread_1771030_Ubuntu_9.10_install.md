---
title: "Ubuntu 9.10 install"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Synoc on 2011-05-29
ok I had an old copy of Ubuntu on hand, 9.10. friend's PC was a bit on the lean side so it sounded like a good plan anyway. the story ends with me trying a wubi install on his windows 7 PC. the wubi tanked and we jsut got  sh:grub. the research I could do on the problem basically said, they couldn't fix it.. so... we uninstalled ubuntu. but it still pops up with the boot options. even though ubuntu isn't on there. can someone help?

---

### Post by garvinrick4 on 2011-05-30
> **Synoc said:**
> ok I had an old copy of Ubuntu on hand, 9.10. friend's PC was a bit on the lean side so it sounded like a good plan anyway. the story ends with me trying a wubi install on his windows 7 PC. the wubi tanked and we jsut got  sh:grub. the research I could do on the problem basically said, they couldn't fix it.. so... we uninstalled ubuntu. but it still pops up with the boot options. even though ubuntu isn't on there. can someone help? go to command line in Windows 7 right click and with administrative:
bcdedit
Now find the entry that says wubildr in it and delete it;
bcdedit delete {indentifier number}

If any problems google to delete an entry in Windows 7 and sure you will get results.

##Did you remove wubi through ADD and Remove programs in Windows? There is also
a UBUNTU entry in C: Drive right next to Users and has an uninstall there also that is a
bit better I do believe at getting the attachment to Windows grub out of there at uninstall.

---

