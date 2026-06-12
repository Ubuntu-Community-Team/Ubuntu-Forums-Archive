---
title: "SATA Matrix Raid with dmraid destroys Raid Array"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Timeforce on 2008-02-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi

i switched over from gentoo to ubuntu/kubuntu. I am using a Gigabyte DS4 Board with onboard raid controller (ICH8) with the matrix raid technology (raid 1 & raid 0 on two drives). I got it working in gentoo and also with help of the fakeraid tutorial on the wiki in ubuntu.
But my problem is, that this only works until i switch off my pc the first time after install.
The problem is known here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435/comments/10]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141435/comments/10")
but i dont know how i can solve this.
i booted in the live cd, installed ubuntu but the hpa flag was already set when i started the live cd so my raid config wont work after a cold start. 

Any suggestions? Any help? Thanks!
Timeforce

---

### Post by Timeforce on 2008-02-06
does no one know a solution how i can turn of ignore hpa for the live cd to install it?

---

### Post by simons-photography on 2008-02-16
I think you will just get told to use linux software raid

---

### Post by Timeforce on 2008-02-18
I "solved" it by not using my harddisk at full level. So i left the last 10 mb of my hdd unused  and so ubuntu doesnt resize this partition -> no overwriting :)

---

