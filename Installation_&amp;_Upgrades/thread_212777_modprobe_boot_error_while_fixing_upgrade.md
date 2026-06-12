---
title: "modprobe boot error while fixing upgrade"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by jjaquinta on 2006-07-10
Hey Folks,
  My blocking problem is that upon boot, I get a whole bunch of Usage messages for /sbin/modprobe. It finishes saying "ALERT! /dev/hdc1 does not exist. Dropping to a shell!" and running the BusyBox Built-in shell. This does not list anything for /dev/hd* at all. But when I boot with a Knoppix Live CD I can see my hard disk just fine.
  History: I started upgrading 5.05->6.06. The baisics worked OK, so I left it for a bit. Then I read some forums to resolve the 400+ unupgraded packages and tried a few things. That broke X, but the system still functioned. After leaving it for another bit, I decided to tackle the X problem. I had lots of problems, but was making progress. The last problem I faced was being unable to put on python23. In the course of trying to resolve that I've got the stage I describe.
  So clearly something is screwed in my configuration. But since I can't boot into the system, I can't apply packages to resolve it. I can't re-install without erasing my hard disk. Has anyone seen this problem before? Or can you suggest an approach to take to fix it? I invested a lot in setting up this machine and I'd really rather not have to wipe it out and start over.
      Cheers,
          Jo

---

