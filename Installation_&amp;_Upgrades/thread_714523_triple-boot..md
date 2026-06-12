---
title: "triple-boot."
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2008-03-03
Hi there guys.

I have a dual-boot Virista/Ubuntu, but I want to test out other Linux distros as well.  I know I *could* run a live CD, but I find that these give very little idea of how easy a particular distro will be to set up drivers etc.  So, I was going to re-partition my HD by removing space from the NTFS shared data partition to create a new ext3 partition onto which I can install Mint, Debian, gOS etc and test them out.

Now, my question is:  Can I tell them to install the /home in the same pace as the /home is currently for K/Ubuntu, or will this screw up my K/Ubuntu settings, (meaning I'll need a dedicated /home partition for Mint/Debian, or do without and leave it as a directory within root?)  I don't wanna over-complicate by having 7 partitions!  Can I even set a separate /home partition in other distros?

Additionally, will these adjust grub or will I need to do it manually?

---

### Post by confused57 on 2008-03-03
> **lewisskinner said:**
> Hi there guys.

I have a dual-boot Virista/Ubuntu, but I want to test out other Linux distros as well.  I know I *could* run a live CD, but I find that these give very little idea of how easy a particular distro will be to set up drivers etc.  So, I was going to re-partition my HD by removing space from the NTFS shared data partition to create a new ext3 partition onto which I can install Mint, Debian, gOS etc and test them out.

Now, my question is:  Can I tell them to install the /home in the same pace as the /home is currently for K/Ubuntu, or will this screw up my K/Ubuntu settings, (meaning I'll need a dedicated /home partition for Mint/Debian, or do without and leave it as a directory within root?)  I don't wanna over-complicate by having 7 partitions!  Can I even set a separate /home partition in other distros?

Additionally, will these adjust grub or will I need to do it manually?
I would recommend not having a separate /home partition for the distros you install for testing...as mentioned in your other thread, it's not advisable to share home partitions among different distros.  Yes, you can set up separate /home partitions in the other distros, but for testing purposes you don't really need to and it would essentially be "wasted" HD space.

This explains how to boot different distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Even if the newly installed distro overwrites your Ubuntu grub's mbr, you can easily reinstall it to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then add a configfile entry to your Ubuntu grub's menu.lst to boot the new distro(see the previous link).

---

