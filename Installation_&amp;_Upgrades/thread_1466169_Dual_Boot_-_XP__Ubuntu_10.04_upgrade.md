---
title: "Dual Boot - XP / Ubuntu 10.04 upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by NJC on 2010-04-30
Hi all - I installed Ubuntu 10.04 as an upgrade from 9.10 on a dual-boot (2 separate disks) machine and it decimated my Win bootloader. I did fix and here's my solution:

1/ Run Win XP installation disk
2/ Type R for Repair
3/ Choose XP installation
4/ Run FIXMBR and FIXBOOT

Note when I ran FIXMBR only, it did not fix my problem. But running both FIXMBR and FIXBOOT did solve the problem. I offer for information only, as your situation may require a different solution.

---

### Post by W.Elfo on 2010-05-01
This did not work for me. Now I can get into XP but not Ubuntu. Any suggestions as to how to undo this solution?

---

### Post by ieee488 on 2010-05-01
> **W.Elfo said:**
> This did not work for me. Now I can get into XP but not Ubuntu. Any suggestions as to how to undo this solution?

See if [http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11) is useful

I use Grub as my boot manager. I installed 10.04 onto the hard drive, and I am able to boot into either Windows XP, Ubuntu 9.10, or Ubuntun 10.04

---

### Post by W.Elfo on 2010-05-02
Thanks for the reply. I have followed the link you suggested & eventually arrived at 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
There I found & downloaded "Auto for Windows" I ran it, (it does not install as a program), & re booted. After a little tweaking & several reboots I can now access either partition. Thanks for the help. 
For anyone else who may follow this line of action note that when the boot loader offers the choices the Windows  choice is last, after what seems like 20 Linux choices. To reach it you must scroll down, off the page, (It is hidden initially) to what seems to be the end of a second page. After selecting it, after the memory test, XP can be accessed. 

Hope this helps someone.

---

