---
title: "Install Ubuntu on Second Hard Drive, keeping Windows on others?"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by futurehusband93 on 2019-12-02
I originally installed Ubuntu about a week ago alongside Windows 7 on my largest hard drive, partitioning about 80gb of space to it. After a Windows update, I lost access to the installed partition, and could not find any way to fix it, even after a lot of searching, so I figured I'd just delete it, and use my second hard drive to install it separately and overwrite it.

I wanted to wipe one hard drive and fully install Ubuntu on it. 

Firstly, would that prevent any windows updates from affecting it?

Secondly, when I try to install, I get this:-
 [IMG]https://i.imgur.com/0EAcsVV.png[/IMG]

I don't know why it it's detecting Windows at all, but I want to make sure I don't mess up my other hard drives, as I transferred everything off my smallest so I could use it solely for Linux. Is it fine to do this on the whole hard drive, considering it thinks there is no OS at all on the computer?

Many thanks.

---

### Post by oldfred on 2019-12-02
UEFI or BIOS system?
UEFI or BIOS installs? Both need to be installed in same boot mode.

Windows in BIOS boot mode from MBR drives on major updates rewrites partition table and conveniently "forgets" to include any Linux logical partitions. Data is still there, and it just needs an entry in partition table.

Windows 10 needs to have fast start up off. That sets hibernation flag on all NTFS partitions which then prevents Linux NTFS driver from seeing them.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by futurehusband93 on 2019-12-02
Firstly, I already have deleted the Linux partition as I had pretty much no data on it at this point and merged the partition back in.

Secondly, I have Windows 7 on my PC, I forgot to mention. Also, I had changed boot modes to all UEFI, but originally one was in Legacy mode I think in the BIOS. Fast startup is disabled, I noticed a couple days back when looking through the BIOS.

---

### Post by oldfred on 2019-12-02
Windows requires MBR with BIOS boot and gpt with UEFI boot.
Most Windows 7 installs were BIOS, but update to ISO or some reconfiguration on a flash drive allowed UEFI installs of Windows 7.

Windows 10 on updates, turns fast start up back on.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

