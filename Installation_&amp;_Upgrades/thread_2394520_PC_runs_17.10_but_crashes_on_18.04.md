---
title: "PC runs 17.10 but crashes on 18.04"
date: 2018-06-17
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-06-17
when 18.04 was finalized, I upgraded all my PC's from 16.04 to 18.04.  However, one of them would not upgrade.  All attempts to install 18.04 crashed with a kernel panic error (reported by myself and others).  PC in question is an hp-compaq dc5800.  Processor is an Intel E2180.  RAM is 4GB.  PC runs Win 10 64 Pro just fine (dual boot with Ubuntu just as is the case with all my other PCs).  So today, I upgraded first to 17.04.  As soon as 17.04 was installed, Ubuntu said to upgrade to 17.10.  Upgrade to 17.10 went fine, but then Ubuntu said to upgrade to 18.04.  When I rebooted after the upgrade was complete, the PC crashed with the kernel panic error.  I cut a USB with the 17.10 ISO.  Installed 17.10 rebooted and no problems.  I immediately set software updates not to do release upgrades.  I added some programs I needed such as evolution and nemo.  PC wanted some updates to 17.10 and those were installed without problems.

Main reason for the upgrade was to get a later version of evolution so PC could serve as a backup for my laptop which is on 18.04 with evolution 3-28.1-2.

Question: Why will the dc5800 run 17.10 and not 18.04?  Can the problem be fixed?

John

---

### Post by mörgæs on 2018-06-18
I'm writing from a somewhat similar [dc7700]("https://ubuntuforums.org/showthread.php?t=361236&page=86&p=12775075&viewfull=1#post12775075"). As can be seen in the link it needed a BIOS upgrade before it was possible to install Buntu. Have you checked if a newer BIOS is available?

---

### Post by ajgreeny on 2018-06-18
Have you tried running a live version of 18.04 to see if that runs OK?

Triple upgrading as you have done is, in my opinion, is also increasing the likelihood of problems.

---

### Post by cigtoxdoc on 2018-06-18
Thank you for your replies.  Live CD and USB of 18.04 crashed on the dc5800 with the kernel panic error, so I knew I had problems.  Yesterday, I had time to do some research to see if I could find out why.  So far that question is unanswered.  17.10 works, 18.04 doesn't.  Perhaps someone knows why.  john

---

### Post by mastablasta on 2018-06-20
Did you upgrade the BIOS as suggested?

Also 16.04 is supported until 2021, there is no need to "rush" with the upgrade.

---

