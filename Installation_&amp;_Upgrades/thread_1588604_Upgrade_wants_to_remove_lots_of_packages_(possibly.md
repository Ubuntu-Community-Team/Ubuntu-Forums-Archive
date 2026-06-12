---
title: "Upgrade wants to remove lots of packages (possibly depending on plymouth)"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by Ubentoo on 2010-10-05
Dear ubuntu users,last week I encountered the following problem: The update manager suggests a distribution upgrade (strange enough since I already have 10.4 and 10.10 is not released yet). The even worse part is that 24 packages shall be removed from my system, including acpi, cryptsetup, network-manager, nvidia-current, plymouth-x11, samba and wine. About 5 weeks ago I experimented (without success) with disabling plymouth because I wanted textmode during booting. I found some warnings that one should not completly remove plymouth because lots of dependencies including cryptsetup (which is vital to my system). So I did not remove plymouth (a look in Synaptic confirms this), but I may have changed some settings concerning plymouth.I am not sure what this upgrade is about. Can anyone help me with this odd behavior of the update manager?Thanks a lot, Ubentoo

---

### Post by mikewhatever on 2010-10-05
Since your system is somewhat customized, I wouldn't recommend upgrading at all. 
Open System->Admin->Software Sources, Updates tab, and disable 'Release Upgrade' notification.

---

### Post by Ubentoo on 2010-10-05
Thank you, but this is not an option for me since I like to use current software versions. Still I don't understand why this is an 'upgrade' at all. Furthermore, why does it want to remove my packages?

---

### Post by Ubentoo on 2010-10-05
As it turns out, removing an entry in the sources list was the problem. Following this [http://ubuntuforums.org/showthread.php?t=1180456](http://ubuntuforums.org/showthread.php?t=1180456) I had installed clanbomber and the entry for dapper seems to have caused the problem. Since I do not need updates for clanbomber or any other dapper package, I removed this entry. Now everything seems to be fine.

---

