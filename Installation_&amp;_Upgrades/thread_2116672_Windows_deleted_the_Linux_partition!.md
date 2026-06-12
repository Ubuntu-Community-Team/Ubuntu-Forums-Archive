---
title: "Windows deleted the Linux partition!"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by AmigaMind on 2013-02-16
Hello everyone, I was trying to reinstall Windows 7 on a dual-boot PC, I am not sure which Ubuntu version was installed (no experience with Linux...). I deleted the **Win** partition in Setup and this action seemes to also have deleted the **Linux** one (it appears as 'free space'). I didn't proceed with the Windows install and left it as is. The pc will not boot and give the 'grub rescue' prompt. Is there a way to recover the Linux partition, since all important data is there? I don't want to recover Windows 7, just a safe way to reinstall it. Thanks for the support...

---

### Post by darkod on 2013-02-16
First, for future reference, you don't need to delete the windows partition especially if you want to use the same partition again for windows. Simply tell the installer to install there and to format it. That will make sure old system files are deleted.

To try recover a deleted partition, try testdisk from live mode. If you are confused by the Deeper Search scan results, post a screenshot before you do anything. Testdisk is very powerfull and can recover partitions, but it can also mess things up even more.
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by snowpine on 2013-02-16
I will assume you [followed the official instructions]("https://help.ubuntu.com/community/WindowsDualBoot") for dual booting Ubuntu and Windows? Since the first step is "back up your data" you should be OK with simply reinstalling both OS's and then restoring your files from backup. Since you "have no experience with Linux" backups are super-extra-important---one typo on the command line is all it takes to lose everything sometimes.

If you did not make backups then I agree with darkod's suggestion to use testdisk. If this is over your head then spend a few bucks (or whatever is your local currency) to take it to a pro data recovery specialist, if the non-backed-up files are of great value to you.

---

### Post by AmigaMind on 2013-02-16
No backups, sadly... Thank you both for the immediate replies. I will boot from an Ubuntu 12.10 live USB to see if I can get a testdisk screenshot. The official instructions link has interesting suggestions but I'm not trying anything yet, I'll post back asap.

---

### Post by AmigaMind on 2013-02-16
Had a hard time running it from Linux so I used Hiren's Boot Cd and a camera for the screenshot... The jpg is about 4MB so I hope it's ok I uploaded it [here]("http://www.mediafire.com/?en50c70ael54oz3"), along with a log. Testdisk seemed to report the partition fine, I'm not sure what the errors in the log are about.

---

### Post by darkod on 2013-02-16
Is that the Quick scan or the Deeper scan screen?

It looks good, all partitions recognized, the start/end points and sizes look fine. I assume writing a partition table with these values should be fine.

What problems did you have running it from live mode? The only issue might be the path where the program is. You need to be in the correct folder or use the correct path ot run it.

---

### Post by AmigaMind on 2013-02-16
Sorry, that's a Quick Scan. I've started the deep and will upload it when it's done. I extracted the "testdisk-6.14-WIP.linux26.tar" contents and tried to run 'testdisk.8' and testdisc_static' from the USB but got error messages and I gave up... couldn't find it inside Ubuntu - not experienced at all in Linux.
How do I write partition tables? Using Testdisk? Thanks for helping out...

---

### Post by darkod on 2013-02-16
On second thought you might not even need the deep scan since the partitions seem recognizable with the quick scan too.

Refer to the step by step of testdisk, but in general if the partition list shown on screen is correct, you will hit Enter to continue to the next step, where you will have option to write the table with 'w' if I remember it correctly. You then use 'q' few times to close testdisk and that should be it.

Even with the partitions recovered you might need to reinstall grub2 to the MBR from live mode since it was probably blown away by windows when deleting the partition. But that is easy to do once you get there.

---

### Post by snowpine on 2013-02-16
^ Good advice above. The only thing I'd add is, once you've restored the partitions, your **immediate** next step should be to boot from a Live CD and back up the data you have worked so hard to restore. Then you can proceed to restoring GRUB and setting up the dual boot following the official guide I linked to in post #3. Good luck! :)

---

### Post by AmigaMind on 2013-02-16
Thanks for your invaluable support. It won't boot yet but I got the partition back and currently backing up files. I'll try repairing grub2 using Ubuntu secured remix. Do you think I should install Windows first and then deal with grub2 or viceversa? I'm kind of scared the Windows setup will mess it up again when it'll create the deleted partition. Should I also worry about possibly different Linux versions on the pc and the Live CD?

---

### Post by snowpine on 2013-02-16
The link I posted in #3 explains how to either install Ubuntu and then Windows, or Windows then Ubuntu. Most users find it slightly easier to install Windows first and Ubuntu second because GRUB should automatically detect the existing Windows, no further action necessary.

---

### Post by darkod on 2013-02-16
If the live cd is not the same ubuntu version, it's better to install grub2 by chroot. That's easy too, it only needs few more commands.

If you recovered all partitions as on your posted image, the "old" win7 partition will be recovered too. If you want to install win7 it's better to do it before installing grub2. It will delete it anyway.

Don't worry win7 messing up the table this time. Select the Advanced method in the win7 installer (or what ever it was exactly called), when is asks where to install also select Advanced option to show you more options for partitioning. Select the 170GB windows partition and click the Format option. That will format it deleting all files on it. Then with that partition selected as destination, continue the win7 install. That's it.

After win7 is done installing and rebooting few times and working, restore grub2 to the MBR. You will probably need to run update-grub first time you boot ubuntu to detect the new UUID of the win7 partition.

---

### Post by AmigaMind on 2013-02-17
Can't thank you enough, everything seems fine now. I didn't have the time so I went on and used secure remix 12.10 (12.04 LTS is installed). I just seem to get an extra Windows entry in the boot screen but they both seem to do the same - problem solved, thanks to your immediate support.

---

