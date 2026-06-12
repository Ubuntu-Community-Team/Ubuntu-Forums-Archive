---
title: "&quot;linux dd&quot; not working...."
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by thirunavukkarasu on 2008-06-25
Hi Guys,

When entering a 'linux dd' at boot prompt for asking a driver disk during the installation. It don't prompt for driver disk

Does anybody help to know how to insert a SATA/RAID driver in Ubuntu installation? 

In classic we go for 'linux dd' with Redhat or Fedora

Thanks in advance........

With Regards,
Thiru.S

---

### Post by dstew on 2008-06-25
What problem are you having? SATA drivers are included in the regular installation. If you need support for a RAID-enabled disk controller, you need to install and use the **dmraid** program. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

---

