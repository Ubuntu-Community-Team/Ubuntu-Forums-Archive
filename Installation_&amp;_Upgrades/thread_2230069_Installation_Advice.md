---
title: "Installation Advice"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by RishabhKumar on 2014-06-17
I am pre-Ubuntu user, but never used it as my primary OS. I have always used it on USB drive! Now I'm thinking to permanently switch to Ubuntu from Windows 8.1 (the reason because : 1) I love Linux 2)Windows 8.1 sucks real hard!). 
I have tried installing Ubuntu previously but every time it ends up messing my PC (total disaster)! So I thought this time I should ask pro-users how to install it perfectly without any mess.

The problem is that my Desktop isn't that cafe computers with only single OS with simple partitions! So please see my requirements and tell me how should I proceed.

My Desktop is dual boot with Windows 8.1 and Windows Server 2008R2 with 5 partitions : 200Gb X3 (No OS installed on these drives) and 200GB X2 (with Windows 8.1 and server)! PS: There's only one drive(1TB)!
Now what I want to achieve is that when I switch on my PC it should ask between Ubuntu and Server. I've tried earlier but it directly boots in Windows Server.

One more thing is that I don't want any harm to server or any other drives because they are used by my dad.

---

### Post by Bucky Ball on 2014-06-17
Welcome. Let us get it straight. You have Windows 8 and Win server installed, both of which you want to keep. This leaves you with three 200Gb partitions. Correct so far? Then it appears you want to erase Win8 because you say, " what I want to achieve is that when I switch on my PC it should ask between Ubuntu and Server." No mention of Win8. You do not have Ubuntu installed currently?

Before doing anything, backup any valuable data. Your best bet is going to be to partition manually (the 'Something Else' option when you get there) and avoid touching the two existing Windows partitions. You'll see them there quite clearly. 

Win8 uses UEFI so that might be the only complication. Are you going for 14.04?

PS: Can you boot fine from a LiveDVD/USB and get to a desktop?

---

### Post by sudodus on 2014-06-17
Welcome to the Ubuntu Forums :-)

0. I would recommend that you agree with your father to get an external drive and ***backup the whole drive*** (for example an image with Clonezilla). To play safely you should also get a second internal drive of at least the same size (not even one byte smaller), and try to restore the system to that drive. When it works, you know that the backup is really good, and can do things with the original internal drive and still have peace of mind.

1. Assuming Windows 8.1 is installed with UEFI, things are a bit complicated. If you want to switch between Ubuntu and Windows without changing in the UEFI/BIOS menu, you must install Ubuntu in UEFI mode too. This is possible in most but not all computers. You can start by reading these links,

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bucky Ball on 2014-06-17
Post a link to Boot Repair's bootinfoscript output here if you create one, not on the Boot Repair thread. Thanks.

---

