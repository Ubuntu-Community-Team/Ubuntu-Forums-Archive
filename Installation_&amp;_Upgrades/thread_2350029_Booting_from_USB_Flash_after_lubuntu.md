---
title: "Booting from USB Flash after lubuntu"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by FrancescJC on 2017-01-20
Hi,

Once installed lubuntu in a Netbook, I would like to boot from a USB Pendrive to install Windows XP again.
From the BIOS Boot Menu I select the PenDrive but it is going to GRUB menu instead of booting from USB.

How can I force to boot from USB?

Thanks..........

FJ

---

### Post by gupperino on 2017-01-20
If you are selecting the USB drive in your BIOS it should work.

Are you saving your changes?
Are you getting any messages?
Is the USB drive working/bootable? If the pc can't boot from the USB it may automatically boot up into grub.

---

### Post by ajgreeny on 2017-01-20
How did you create the bootable XP USB drive?

I don't think it is as simple a job as it is when creating a Linux distro bootable USB. 
I have not used Windows since XP so I may be wrong about that, but my searches suggest you need either rufus or some other USB creator specially made for XP.

---

### Post by C.S.Cameron on 2017-01-20
I have used the Ngine method for installing XP to USB:

[http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)

Not quite as easy as installing Ubuntu.

---

### Post by Bucky Ball on 2017-01-21
I STRONGLY advise you to install Windows first. Save yourself some time and grief. Trying to install Windows after Ubuntu can be a problematic waste of time (although it could be considered a learning curve). 

Easiest is Windows first, first partition and a primary one. Once you know that is up and running without issue, install Lubuntu or whatever Linux you're going for. Choose 'Something Else' when you get to partitioning (not 'Alongside') and leave the Windows partitions alone. 

When you reboot, it should pick up both OSs. If not, it shouldn't be too much trouble to get Windows onto the menu (running Lubuntu, open a terminal and try 'sudo update-grub').

Windows wants the first primary partition unless you massage it. Ubuntu doesn't care where it is. A logical drive inside an extended partition is fine. Doesn't need to be a primary partition.

Good luck.

---

### Post by FrancescJC on 2017-01-22
I've tried it without success with rufus and other tools.

Finally I used HirensBoot tools to delete and create new partitions.
I think the problem was in the partitions. I suppose the ubuntu installation modified them.

Thanks to all!

F

---

