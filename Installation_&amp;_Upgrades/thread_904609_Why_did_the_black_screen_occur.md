---
title: "Why did the black screen occur?"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by ahood on 2008-08-29
Hi All,

I have been using Ubuntu for quite a few years and promote its use to non-linux fold whenever as possible. 

I loaned a non-techy (i.e., Mac lover) co-worker an Ubuntu Hardy disk and told him to give the liveCD a try on his home HP machine (AMD XP 2.0 Ghz, 512 Mb RAM, NVIDIA FX 5200, 160 Gb).

After about a week, he informed me that he tried the Ubuntu liveCD. I asked him several questions about his experience and he remarked about having to deal with partitions. I thought this was odd, so I asked him some more questions. It turned out that he had installed Ubuntu Hardy onto his home PC system.

He doesn't want to give up WindowsXP, but is hugely annoyed with all the popups that occur with the Windows that came with machine a few years ago. 

I recommended that he might give VirtualBox a try and run WindowsXP on top of Ubuntu. My non-linux co-worker liked the idea. Because he is non-techy, I volunteered to take the system and install VirtualBox and WindowsXP (legitimate copy) onto his system.

I brought home the PC, verified that Ubuntu was indeed installed onto the hard drive along side WindowsXP (dual boot) and installed VirtualBox (VB), as well as a new copy of WindowsXP within VB.

I returned the PC to my co-worker and we tried it out, introduced the system to him. All was working fine.

My co-worker took the PC home. The next day, I saw my co-worker and he informed me that the machine would not boot up properly.

When the sytem is booted, he can see the HP BIOS splash screen, the Grub menu list of linux kernels and WindowsXP. He can also boot into native WindowsXP fine. 

However, when he attempts to boot into Ubuntu Hardy, a black screen appears and he shuts it down.

The only difference in hardware is the monitor, mouse and keyboard. My co-worker has assured me that the connection between the PC and monitor are secture. 

**Do you think the home monitor is likely causing the boot problem?**
The home monitor is an HP 17inch LCD. I used a 17 inch Samsung at home. I also successfully used his system with a generic LCD and a CRT monitor. 

**If Yes, why does this error occur?**

**If No or unlikely, what else could be causing the black screen?**

Any reply will be greatly appreciated.

Al

---

### Post by kellemes on 2008-08-29
/var/log/Xorg.0.log will likely show some info about this..
I *guess* you need to reconfigure xorg so it'll work with the new devices.

as root
```
dpkg-reconfigure xserver-xorg
```

or as user
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bmwman on 2008-08-29
Easier way for your non-linux friend to do this - when you get the menu with the kernels and XP, select the one that says kernel-version-bla-bla(recovery mode). Then you'll get a menu with few options and select Reconfigure Xorg - that will do it automatically. Then you can continue with normal boot. If that doesn't work, you can drop to the console from the same menu and use the commands in the  previous post.

Hope this helps.

---

### Post by kellemes on 2008-08-29
> **bmwman said:**
> Easier way for your non-linux friend to do this - when you get the menu with the kernels and XP, select the one that says kernel-version-bla-bla(recovery mode). Then you'll get a menu with few options and select Reconfigure Xorg - that will do it automatically. Then you can continue with normal boot. If that doesn't work, you can drop to the console from the same menu and use the commands in the  previous post.

Hope this helps.

Thanks for pointing that out..
Wouldn't have thought about it being on Debian. ;-)

---

### Post by ajgreeny on 2008-08-29
The actual option you get in recovery mode is **xfix** I think, which appears in a menu; just thought I'd say to avoid confusion.

---

### Post by ahood on 2008-08-29
Thanks for the quick posts!!! :)

I emailed the solution to my co-worker and I will report back when I hear what happens.

Al

---

### Post by ahood on 2008-09-03
Thank you bmwman and ajgreeny!

Booting into the latest kernel-recovery option in Grub and then selecting the fix sub-option fixed it!

Thanks so much!

Al

---

