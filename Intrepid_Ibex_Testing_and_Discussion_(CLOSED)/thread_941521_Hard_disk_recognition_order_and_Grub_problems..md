---
title: "Hard disk recognition order and Grub problems."
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SledgeHammer_999 on 2008-10-08
I am using 8.10 amd64 Beta.

There are two problems which affect each other.
I have 3 hard disks. 1 IDE and 2 SATA. I installed Ubuntu on the IDE one. One of the SATA one has Windows XP and the other SATA is for data storage.
The ubuntu livecd and the ubuntu install after some reboots they change the order in which they recognise my disks. I used **"sudo fdisk -l"**.
The order will be 1:
/dev/sda <---Ubuntu
/dev/sdb <---WinXP
/dev/sdc <---storage

2:
/dev/sda <---WinXP
/dev/sdb <---storage
/dev/sdc <---Ubuntu

I often see number 2 and rarely number 1(after 5-7 reboots). When I installed Ubuntu from the livecd the order was number 2.

That's the first problem. Now I have the second problem. Grub was installed on the ubuntu drive but the menu.list pointed to (hd0,0) which was correct at the point of the install. But as I have figured out grub recognises my drives in a totally different(and stable) order. The grub order is the order 1(which rarely ubuntu uses). But now, regardless of the order new kernel updates always change menu.lst to (hd2,0) instead of (hd0,0).

Any idea what should I check and maybe report?

Ps. I am almost certain that Feisty/Gutsy/Hardy had the order 1.

---

### Post by petteriIII on 2008-10-08
Isn't /boot/grub/device.map for that reason ? HD0, HD1, HD3 ... is BIOS order, /dev/sda, dev/sdb ... is Ubuntu order; so to say it forces Ubuntu to follow BIOS order ? You are in the rare opportunity to check, please report.

---

### Post by dabl on 2008-10-08
> **SledgeHammer_999 said:**
> I am using 8.10 amd64 Beta.

I have 3 hard disks. 1 IDE and 2 SATA. 

Yes, this is the scenario where you have some tricky issues.  I have 1 IDE and 4 SATA disks -- same problem.  Here's what I have learned from observation:

1. BIOS settings matter more to Linux than to Grub.  Grub insists that my IDE drive is hd(0), regardless of what the BIOS boot sequence is.  The *buntu installer accepts the BIOS sequence as being true.

2. On installation, the installer writes the boot menu as directed, but Grub always starts counting from the IDE drive.  So, when I install *buntu on /dev/sda1 (a SATA hdd that is set to #1 position in BIOS), it writes a boot menu that says the kernel is on (hd,0), but Grub considers that the IDE drive is (hd,0) so it puts up Error 15.  I manually increment the hdx number by +1 on the boot menu (and also fix it on the groot line in /boot/grub/menu.lst) and all is happy and works correctly.

This "IDE bus priority" issue seems to be somewhat BIOS/motherboard specific, and I assume it is a result of adding the SATA bus to legacy motherboard circuit designs where there was only the IDE bus present.

So, to understand your system, you need to observe the interaction of BIOS hdd boot sequence, installer results, Grub behavior, and the Linux device listing in /dev.  Here's a lot of great guidance on how to work with Grub:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Hope this helps.  :)

---

### Post by SledgeHammer_999 on 2008-10-08
the device.map
> 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


@dabl
Ok but why does this happen now? The earlier ubuntu version were ok. Anywayz, if I undersood you correctly, my system should recognise the drives in the same order everytime but this does not happen.

I have an Asus motherboard with a nvidia cphiset(I'll found out later).

---

### Post by dabl on 2008-10-08
"Why" is a tough one -- changes in kernels' device detection capabilities, and changes in the installer have happened in the 2+ years that I've been running *buntu, so prolly you can't write a permanent rule about the way it is.  A BIOS upgrade might also change things.

Note that the device.map is a Linux structure.  Remember that Grub is not Linux, and has its own view of the buses and attached drives.  :)

---

### Post by caljohnsmith on 2008-10-08
> **SledgeHammer_999 said:**
> 
That's the first problem. Now I have the second problem. Grub was installed on the ubuntu drive but the menu.list pointed to (hd0,0) which was correct at the point of the install. But as I have figured out grub recognises my drives in a totally different(and stable) order. The grub order is the order 1(which rarely ubuntu uses). But now, regardless of the order new kernel updates always change menu.lst to (hd2,0) instead of (hd0,0).

When you start up your computer, Grub sees the order of HDDs the same as the BIOS boot order, not as the drives are ordered in Ubuntu's /dev directory (all though they can be the same if you set up your boot order that way); that is why booting Ubuntu from Grub is not affected by problems with /dev order changing. If you want a temporary workaround for your menu.lst problems, you could change the "groot" line in your menu.lst back to:
```
#groot=(hd0,0)
```
And then your new kernel updates should use (hd0,0) instead of (hd2,0), assuming there are no other bugs.

---

### Post by SledgeHammer_999 on 2008-10-08
If I understand you correctly it should work like this: Grub gets the order from BIOS and tells Ubuntu how to associate the /dev/* devices with the ones it got form the BIOS. Then that means that the order of the device recognition should be the same in every boot. But this is NOT happening. I haven't touched anything, I just rebooted. 

So is this a bug? in the kernel? in grub? somewhere else?


My motherboard is an Asus A8N-SLI(nForce4, 939).

---

### Post by caljohnsmith on 2008-10-08
> **SledgeHammer_999 said:**
> If I understand you correctly it should work like this: Grub gets the order from BIOS and tells Ubuntu how to associate the /dev/* devices with the ones it got form the BIOS. Then that means that the order of the device recognition should be the same in every boot. But this is NOT happening. I haven't touched anything, I just rebooted. 

So is this a bug? in the kernel? in grub? somewhere else?


My motherboard is an Asus A8N-SLI(nForce4, 939).
I don't think it quite works that way; Ubuntu orders its devices in /dev by the type of device, so the order of drives in /dev would likely be IDE, SATA, then USB or something along those lines. The device order in /dev shouldn't change if you merely change the boot order of your drives. Only adding/removing drives should change the order of drives in /dev. But as I alluded to above, Grub on start up has to use BIOS to access any drives, so Grub at that point sees the order of drives as the same as the BIOS boot order, not necessarily the same as the order in /dev (although they could be the same). So if you don't add/remove any drives and the drives change order in /dev, that sounds like a bug to me.

---

### Post by SledgeHammer_999 on 2008-10-08
Ok should I file a bug report? Should I target a specific package?(kernel,grub)

---

### Post by caljohnsmith on 2008-10-08
> **SledgeHammer_999 said:**
> Ok should I file a bug report? Should I target a specific package?(kernel,grub)
Yes, I would file a bug report, and I guess if you have to target a specific package, your particular kernel might be at fault; it would be interesting to see if Hardy has the same behavior with the same kernel you are using, and I'm guessing it wouldn't. And if that were the case, that would suggest there is more to the problem than a simple bug in the kernel. So bottom line is I would target the kernel in your bug report, and let the bug testers figure it out from there. :)

---

### Post by dabl on 2008-10-08
Did you run (at your user prompt) ```
sudo grub
``` and do any of the following at the grub prompt? :

grub>  cat  hd (<Press the Tab key>      #info about drives with Tab completion
grub>  find  /boot/grub/menu.lst     # tells you where a menu.lst is
grub>  find  /boot/grub/stage1     # tells you where GRUB files are
grub> find  /vmlinuz          # tells you where a Linux kernel is

You might discover some differences between the Linux /dev/sdx device list and the grub "view" of them.  :)

---

