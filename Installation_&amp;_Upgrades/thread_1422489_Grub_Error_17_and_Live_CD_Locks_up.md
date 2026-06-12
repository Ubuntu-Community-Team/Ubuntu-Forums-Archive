---
title: "Grub Error 17 and Live CD Locks up"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by fireman71 on 2010-03-05
Hello everyone,

I am running into a couple of problems. I downloaded Ubuntu Desktop 9.10 (32bit) and booted into the live cd and after a couple of seconds it locks my computer up completely. I can install Ubuntu 9.10 Desktop from the CD fine though. This is the first problem.

The second problem is that after installing Ubuntu Desktop 9.10 and rebooting I get a Grub 1.5 Error 17. I searched and searched for a way to fix this with no avail on my own. I downloaded Ubuntu Server 9.10 (32bit) and installed it and am receiving the same error message. I believe that the problem might be that I need to mount my root partition on sdb and my home partition on sda. System information is as follows:

This is a zareason system that came with ubuntu 7.?? something on it so I know the hardare is linux compatibile. First harddrive is 500G sdb that I have as a single primary partition set to mount at /home formatted to ext4. Second harddrive is 120G sda that has 6G for swap at the beginning of the drive and the rest set to mount at / formatted to ext4.

I cannot for the life of me figure out a way to get in and look into the grub settings and haven't figured out grub2 enough to be sure that i even know where to look (no more menu.lst based on my readings on the internet). And I cannot get ubuntu livecd to stay running long enough to do anything other than click on the applications or system button before it locks up.

Anyone have any ideas? All help is greatly appreciated.

Thank you,
Ian K. Harrell

---

### Post by stlsaint on 2010-03-05
What hdd has grub installed to mbr and what hdd is set to boot first in bios? (master/primary hdd)

---

### Post by fireman71 on 2010-03-05
good questions. I am not certain but i believe that the drives were reversed before somehow. How can I check to confirm this to answer your question?

---

### Post by stlsaint on 2010-03-05
A quick test would be to switch the boot order of your harddrives in bios. If grub isnt properly on either of the two drives than thats your answer to your issue. You need to re-install grub if this is so. Please see my signature for links. Since you are on 9.10 karmic than select the grub2 link.

---

### Post by fireman71 on 2010-03-06
This fixed the booting problem so I can now boot up and get in. Thank you.

---

