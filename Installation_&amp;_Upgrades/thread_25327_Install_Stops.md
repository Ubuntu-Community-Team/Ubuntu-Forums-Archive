---
title: "Install Stops"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Qwacko on 2005-04-09
Hey

I am installing hoary, and when it get to the Installing base system step, it progress until it gets to 17% and at the bottom it tells me that it is "extracting base-files" then it just stops, and refuses to proceed any further. I am installing it on a 14Gb partition with 800Mb of swap space, as a dual boot with windows. I have tried with different partition sizes, and formatted the parititon and tried again, i have used different disks (Kubuntu, and Ubuntu) and have done a md5 check on the disks which turned out correct. Any ideas what might be going wrong??

Thanks in advance
James

---

### Post by Qwacko on 2005-04-09
I ahve also tried leaving it to see if it would proceed, i left it for 2 and a half hours, and nothing happened

Thanks
James

---

### Post by SmallOak on 2005-04-10
I may have a similar problem.

"Detecting hardward to find CD-ROM drives"
"Loading module 'ide-cd' for 'Linux ATAPI CD-ROM"

It sits at 86% for quite a while and then it flickers, goes to a blue screen with a grey band at the bottom and just hangs there. Irony is of course that it is booting the installer from the CD fine. But it is probably something else which is causing the problem.

Maybe there are some switches I can use to get it to boot. We'll see.

Edit: After reading a bit more I find that others have a similar problem, read: [Link to post.](http://ubuntuforums.org/showthread.php?t=24775&page=1&pp=10)

[i]Edit 2: So after reading some of that I set it to be American Keyboard, American location. Seemd to stall at the same time. So I left it and went to dinner. Came back and now it seems stuck at:

"Scanning CD-ROM,0%"
"Scanning /cdrom/pool/main/a..."

I will leave it there and see what happens.[/i]

Edit 3: Chugging along now. Painfully slow. An hour later it is at 4%. I'll let it run over night and see what happens.

---

### Post by SmallOak on 2005-04-11
12 hours later, 72%.

It will be interesting to read the installation log file to see what is holding it up. Maybe something is timing out.

Edit: About 20 hours later it is still installing. Now it has installed / partition and is extracting Ubuntu core files. 

The machine is a 700 MHz Athlon with 256 Mb RAM, so resources should be enough. *shrug*

---

### Post by SmallOak on 2005-04-19
Replaced the CD drive with a new one and it installed like a charm.
Incompatible drive was: Pioneer LaserMemory Super 24x

---

