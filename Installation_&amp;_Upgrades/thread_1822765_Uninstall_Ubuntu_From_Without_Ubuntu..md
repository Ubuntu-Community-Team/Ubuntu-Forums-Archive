---
title: "Uninstall Ubuntu From Without Ubuntu."
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by Dansid on 2011-08-11
My Ubuntu 11.04 is broken.

Happened when I upgraded via update manager.

Now when I select Ubuntu instead of Windows from the boot scree, I get purple flashy, or a black screen with a purple line at top, so suffice it to say Ubuntu is unusable. 

Is there a way to uninstall it from outside of it?  I need to completely erase its existence, including restoring the partitioned Hard drive back to windows. 

Safe Mode does not work.

Can someone help me...anyone?

---

### Post by YannBuntu on 2011-08-11
Hello
There is a tool to uninstall Ubuntu: [OS-Uninstaller]("https://launchpad.net/os-uninstaller"). But before, let's try to repair it: 

> **Dansid said:**
> Happened when I upgraded via update manager.

Do you mean when upgrading from 10.10 to 11.04 ? If yes, I would recommand reinstalling Ubuntu 10.10 over 11.04 if you want a quick solution. But if you absolutely want to use 11.04 :

> **Dansid said:**
> Now when I select Ubuntu instead of Windows from the boot scree, I get purple flashy, or a black screen with a purple line at top

See [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) , and try the solutions via a Ubuntu 11.04 CD.
Once you have found the correct settings (kernel options, GRUB resolution...), these settings can be easily applyed to your current 11.04 install via the Advanced options of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by fhrhd on 2011-08-11
I want to uninstall it too!it still boot but ugly interface.
I installed macbuntu 10.10 on my 11.04

---

### Post by YannBuntu on 2011-08-11
@fhrhd : please open a new thread, with more details.

---

### Post by Mark Phelps on 2011-08-11
> **Dansid said:**
> Is there a way to uninstall it from outside of it?  I need to completely erase its existence, including restoring the partitioned Hard drive back to windows. 

The details depend on HOW you installed it -- which you failed to tell us.

If it was a Wubi-install, you simply boot into MS Windows and remove it like any other application.

If it was a separate partition install, presuming you're running Win7, boot into it and use the Disk Management utility to remove the partition. You may not be able to reclaim the free space since Disk Management is very limited in what it can do.  If that's the case, then Google for EASEUS Partition Master or Partition Wizard.  Both of those are free downloads and can be used to do partition changes on MS Windows filesystems.

---

