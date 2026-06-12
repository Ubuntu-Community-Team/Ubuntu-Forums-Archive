---
title: "GRUB2 issue"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Joselladro on 2010-01-24
Hi all, I'm a new Ubuntu 9.10 user and I have a GRUB2 issue.

I had a Windows installed on a partition and this week I tried to install Ubuntu in other partition. The problem is that I can't access now to Windows for do some tasks. I tried to add a new line to the menu of the GRUB2 in grub.cfg (not directly), but I found another big problem, when I start the computer I cant see the grub2 menu.

- Press Esc during boot doesn't work (the screen turns black).
- I've tried to install startup-manager and turn on the "show boot splash" option.
- I've tried to do this tutorial [http://www.ubuntu-es.org/?q=node/97710](http://www.ubuntu-es.org/?q=node/97710) but grub2 menu still don't work.

I think the problem is how are the partitions structured on my pc, but I can't assure it.

some info:
[http://img192.yfrog.com/i/screenshot1cx.png/](http://img192.yfrog.com/i/screenshot1cx.png/)
[http://paste.ubuntu.com/360919/](http://paste.ubuntu.com/360919/)

Thank you for your help!

---

### Post by tachuela on 2010-01-24
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by darkod on 2010-01-24
In Gparted you notice the triangle mark next to /dev/sda1? I guess that is your windows partition and that mark means some problem was detected.
It seems the windows is not recognized at all and that is why grub menu is not showing at all, thinking ubuntu is the only OS. Grub menu doesn't show in that case.
You can try repairing the windows bootloader with instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot windows few times and let it do disk checks if needed. After that reinstall grub2 to the MBR using the instructions for grub2 and 9.10 on the same link.

---

### Post by mettaman on 2010-01-24
hello...

1) [http://grub.enbug.org/ChainLoadWindows](http://grub.enbug.org/ChainLoadWindows)

"
**Sometimes  "aptitude install grub2" seems to miss out your windows partition, at  least that happened to me.**

  
**This is how  to fix it:"**


-

2) [http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

"[FONT=Arial]This web-page is part of a larger site  giving examples of how to install Windows+Ubuntu Linux operating systems 'dual boot' in a computer.  [/FONT][Illustrated Dual  Boot HomePage]("http://members.iinet.net/%7Eherman546/index.html")"

-

wish you well :-)

---

### Post by mettaman on 2010-01-24
& i agree w darko

> **darkod said:**
> ...
You can try repairing the windows bootloader with instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot windows few times and let it do disk checks if needed. After that reinstall grub2 to the MBR using the instructions for grub2 and 9.10 on the same link.

---

### Post by Joselladro on 2010-01-24
> **darkod said:**
> In Gparted you notice the triangle mark next to /dev/sda1? I guess that is your windows partition and that mark means some problem was detected.
It seems the windows is not recognized at all and that is why grub menu is not showing at all, thinking ubuntu is the only OS. Grub menu doesn't show in that case.
You can try repairing the windows bootloader with instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot windows few times and let it do disk checks if needed. After that reinstall grub2 to the MBR using the instructions for grub2 and 9.10 on the same link.

Yes, I noticed that triangle but I dont know its meaning. The windows partition is /dev/sda5, I created sda1 during Ubuntu instalation. I'm going to try your link. Thank you! ;D

---

### Post by darkod on 2010-01-24
> **Joselladro said:**
> Yes, I noticed that triangle but I dont know its meaning. The windows partition is /dev/sda5, I created sda1 during Ubuntu instalation. I'm going to try your link. Thank you! ;D

Windows is on /dev/sda5? Which vesion? /dev/sda5 is logical partition inside extended. Windows usually doesn't like being on logical partitions, only on primary. Especially WinXP. This might be your problem and why grub is not detecting it.

---

### Post by Joselladro on 2010-01-24
> **darkod said:**
> Windows is on /dev/sda5? Which vesion? /dev/sda5 is logical partition inside extended. Windows usually doesn't like being on logical partitions, only on primary. Especially WinXP. This might be your problem and why grub is not detecting it.

sda5 is Windows XP Professional. Then what can I do? reinstall window after ubuntu?

---

### Post by darkod on 2010-01-24
> **Joselladro said:**
> sda5 is Windows XP Professional. Then what can I do? reinstall window after ubuntu?

I can't be 100% sure that this is the problem but if it is, the only thing is to reinstall. Copy your data from /dev/sda1 on external hdd and install XP there. That's a primary partition. But that would mean you have to reinstall all windows software too.
After that when you make sure XP is booting and working fine, you will just have to reinstall grub2 to the MBR using the above link. you DO NOT have to reinstall ubuntu completely.

PS. Are you sure XP is on /dev/sda5? Why does /dev/sda1 have boot flag? Look on the Gparted picture you attached. The boot flag would be on the windows system partition.

---

### Post by Joselladro on 2010-01-24
> **darkod said:**
> I can't be 100% sure that this is the problem but if it is, the only thing is to reinstall. Copy your data from /dev/sda1 on external hdd and install XP there. That's a primary partition. But that would mean you have to reinstall all windows software too.
After that when you make sure XP is booting and working fine, you will just have to reinstall grub2 to the MBR using the above link. you DO NOT have to reinstall ubuntu completely.

PS. Are you sure XP is on /dev/sda5? Why does /dev/sda1 have boot flag? Look on the Gparted picture you attached. The boot flag would be on the windows system partition.

Yesterday, doing some tutorials for restore the windows, I format sda1 and now i can mount sda5 and get all windows filesystem.
Furthermore, I've tried setting sda5 as boot in gparted, and nothing changes on boot.

Ok, I think the best solution is to reinstall.
Thanks for all! ;D

---

