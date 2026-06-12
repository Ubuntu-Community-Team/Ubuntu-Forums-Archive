---
title: "Grub rescue"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by sami7 on 2015-06-29
I couldn't boot through grub and I'm stuck on grub rescue altought i tried running boot-repair but didn't work 

Here's the link of the log: [http://paste.ubuntu.com/11793144/](http://paste.ubuntu.com/11793144/)

Plz would anybody help me ? :/
thanks in advance

---

### Post by oldfred on 2015-06-29
Did you leave Windows hibernated?
Or is it Windows 8 which is always hibernated with its fast startup. You must turn that off if you want to dual boot.

And partition table shows an empty extended partition.

I would use your Windows repairCD or Flash drive and reinstall a Windows boot loader. Since Boot-Repair cannot mount the NTFS partition, it does not see your Windows install and offer to install a Windows type boot loader. You may be able to force that?

Then I might try testdisk to see if it shows your Linux partition(s)? Did you do a Windows install or reinstall? Windows does not know about Linux partitions, so it rewrites partition table leaving off the Linux partitions. Testdisk can usually restore them if that is the case.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by sami7 on 2015-06-29
Thanks for replying
and actually windows just stopped suddenly (windows 8.1) and showed me a blue error page and then it rebooted and didn't find grub :/

I'll try Testdisk in a few minutes

---

### Post by oldfred on 2015-06-29
Then you also may need chkdsk from Windows repairCD or flash drive. You cannot do that from Linux.

Any abnormal shutdown often corrupts data and chkdsk with Windows or fsck with Linux is the minimum required.
But it also then could be a hard drive issue. You may want to go into Disks, and in upper right corner icon is Smart Status. It can run tests, but all I know is passed is good.

---

