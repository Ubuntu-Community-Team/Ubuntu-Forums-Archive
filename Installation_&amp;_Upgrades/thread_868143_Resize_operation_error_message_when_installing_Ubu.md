---
title: "Resize operation error message when installing Ubuntu?"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Mr_Duck on 2008-07-23
Hi, I'm kind of new to Linux,  and I'm trying to install Ubuntu to my laptop as a dual boot. When I try to partition the drive using the partitioner on the Ubuntu disk, I get an error that says "Resize operation failure. An error occurred while writing the changes to the storage devices. The resize operation has been aborted." I went to the Ubuntu irc server, and they told me to defragment the drive in Windows. I did this, and I got the same error message. I tried using a different drive partitioner and it got an error message too. Does anyone know how I could fix this?

Thanks.

---

### Post by avtolle on 2008-07-23
If your Windows installation is Vista, use the Vista app to resize the Windows partition.

---

### Post by Mr_Duck on 2008-07-23
I'm running Windows XP service pack 2. I'm new to this, sorry for not including that information in the beginning. Also; what is wrong with what I'm doing/my hard drive partition that's causing this error?

---

### Post by mattredux on 2008-07-30
Hey, I was having exactly the same problem. I had already defragged the Hard Drive in windows xp however try running "chkdsk /f" command in the 'Run' command from the start menu. It'll ask you if you want to do it on restart as it's already being used. Type Y and hit enter. Then shut down your pc and boot it (remember windows not linux) up again.

For me this seems to have worked.

---

