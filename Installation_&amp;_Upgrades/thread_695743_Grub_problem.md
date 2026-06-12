---
title: "Grub problem"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ismakun on 2008-02-13
When I installed Ubuntu 7.10 on my desktop the first time I booted Windows with Grub it work flawless, but I restarted the computer to see if Ubuntu was working too but to my surprise for some reason the grub was replaced and my computer went directly to Windows.
I decided to installed the grub manually with the live cd but when I execute
-> find /boot/grub/stage1  it points to (hd1,1) and ubuntu is on (hd0,1).
I tried to root(hd0,1) but it wont let me. So I mounted (hd1,1) and the grub appeared again at startup but it wont boot any operating system. I tried changing manually the .list file and point it to (hd0,1) for ubuntu and (hd0,0) for windows but still it wont work. It load ubuntu with minor issues and it wont load windows.
So I had to fix the MBR with the windows cd. I tried to installed Ubuntu again clean but the grub is missing in action and it directly boots to windows.

I dont know what to do. I need help. Thanks in advance for your response. I've tried to install Ubuntu countless times in my desktop and it wont work, sometimes the grub appears the first time but after rebooting the mbr changes back to windows.

---

### Post by mindcry on 2008-02-13
[http://ubuntuforums.org/showthread.php?t=694793](http://ubuntuforums.org/showthread.php?t=694793)

I think you have the same problem with the guy in this post..
If you have windows vista then you sould read it..

---

### Post by ismakun on 2008-02-14
I have XP. I already tried that approach before I posted here, still the grub wont work. Im running out of options.

---

### Post by ismakun on 2008-02-14
Having two SATA Harddrives connected at the installation of the grub or ubuntu affect the grub?? If I disconnect one hardrive would it have any difference and after installation just replug it?

---

