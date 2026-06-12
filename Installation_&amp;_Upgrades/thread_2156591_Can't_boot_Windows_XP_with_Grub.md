---
title: "Can't boot Windows XP with Grub"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by Cracky7 on 2013-06-22
When I select Windows XP entry on Grub, it just goes to a black screen, where I can't do anything. I have run sudo grub-install /dev/sda and sudo update-grub a couple of times, but the problem doesn't go away. All the files are there, though.

Help, please.

---

### Post by Mark Phelps on 2013-06-22
You might be able to fix it with Boot-repair:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by oldfred on 2013-06-22
All grub does is chain load to the Windows boot code in the XP NTFS partition. Then it is all Windows.

So if XP is not booting you may need to make Windows repairs. Often chkdsk is the first thing to try, but it may need other fixes also.

       To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

