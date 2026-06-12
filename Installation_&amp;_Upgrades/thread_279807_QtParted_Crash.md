---
title: "QtParted Crash"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by eskimokid on 2006-10-18
When I'm install my Kubuntu on my desktop, after i choose to edit my partition manually in step 5 out of 6, it pop-out an error and says that the qtparted is crashed
when i typed qtparted inside my terminal, it appear an error code like this

X Error: BadDevice, invalid or initialized input device 168

notes : I got a C drive and its installed with windows xp.

---

### Post by templar on 2006-10-30
I just had the same thing happen today. I tried running the partitioner manually.

ubuntu@ubuntu:~$ sudo qtparted
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode: 144
  Minor opcode: 3
  Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode: 144
  Minor opcode: 3
  Resource id: 0x0
Failed to open device


Im not sure what the fix is?

Thanks
Oliver

---

### Post by schmandr on 2006-10-30
Try the alternate install CD, it worked well for my system. Now I enjoy a beautiful new Kubuntu!

I had the same problem: There was already Windows installed on my computer and qtparted crashed during desktop install method of Kubuntu 6.10. But maybe it was because of my two SCSI drives?

Andreas

---

