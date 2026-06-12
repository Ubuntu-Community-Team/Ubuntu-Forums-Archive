---
title: "Need change module options on live cd  for installing..."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Jens7677 on 2008-05-01
Hello there,

I have a rather tricky problem, may be someone has an idea.

I want to setup my ubuntu on a dmraid partition. The partitions are created and setting up an earlier version of Ubuntu was no problem. But since several kernel versions a libata option (libata.ignore_hpa) got a new default and that results that I can't access my harddisks anymore. The solution is to change this option in /etc/modprobe.d somewhere. But now comes the tricky part. I want to setup I new installation from the live cd (upgrading screwed up my former installation, can't start from there either, so I want to start with a fresh install). But in order to get access to my harddisks I have to change that option before libata got loaded. I thought that I can just pass it as a kernel parameter on startup, but that won't work for because libata is compiled as module and not directly into the kernel. So obviously I have to set this option in /etc/modprobe.d. But since it is the live cd I will loose this change on restart and I can't reload the module because it is in use because of the cd-rom from where I have to start.

So, does any has any idea how to solve that? Like starting from usb, interfering the startup process to set that option before libata got loaded? Or anything else?

Regards,
Jens

---

### Post by Pumalite on 2008-05-01
This may help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by Jens7677 on 2008-05-01
Hi,

thank you for your fast answer. But unfortunately this topics won't help yet. I can't run dmraid -ay because my disk sector are recognised in a wrong way due to the fact that HPA is ignored.

I just need to change that option before libata got loaded.

Regards,
Jens

---

### Post by Jens7677 on 2008-05-02
Alright, I found a solution, the magic grub option 'break' did it. I just had to find a PS2 keyboard and now I'm able to do 
modprobe libata ignore_hpa=0
before other modules got loaded ('exit' to exit the busybox and continue with booting). Now I can finally discover my raid with dmraid --ay sucessfully.

It's time to get started with the installation ;)

---

### Post by Pumalite on 2008-05-02
Congrats.

---

### Post by morfyng on 2008-11-27
Hi,

can you help me, i don't understand what you mean with "*magic grub option 'break' did it*" is an option that i must to add at the kernel line in the grub or a special keyboard-combination ?!?
...I have 2 Sata HD in Raid 0 with WinXp and another Sata where I've installed Ubuntu.If I boot from Ubuntu HD and after reboot, my raid 0 disk is marked as failed and only after a cold reboot, the raid 0 return OK.
8.10beta does not contain this bug but now with the final the problem returned !!! I'm becoming crazy

---

