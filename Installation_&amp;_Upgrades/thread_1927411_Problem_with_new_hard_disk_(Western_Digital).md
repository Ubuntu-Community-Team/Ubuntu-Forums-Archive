---
title: "Problem with new hard disk (Western Digital)"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by mgt2000 on 2012-02-17
Hi all,
I bought a hard disk yesterday (WD Scorpio Blue - WD10TPVT 1TB - more information is in [here]("http://wdc.com/en/products/products.aspx?id=140"))  and I replaced it with my previous hard disk. Now I only can install windows (XP and 7) but I can not install Ubuntu again (of course no other Linux based CD works!!!). What Can I do now? Can some one help me to solve the problem? 
I don't want to install windows and I only want to have Ubuntu.

Thanks a lot

---

### Post by stn21 on 2012-02-18
> **mgt2000 said:**
> ... Now I only can install windows (XP and 7) but I can not install Ubuntu again (of course no other Linux based CD can be boot and start!!!)...

What exactly happtens when you try to install ubuntu?

---

### Post by mgt2000 on 2012-02-18
> **stn21 said:**
> What exactly happtens when you try to install ubuntu?
Thanks for your reply.
The screen goes black and then the hard disk starts making a strange noise and that all, there is no error or any thing else on the screen and the system becomes locked!! but when I use Wubi, after restarting the system, it says "(hd0,0) prefix is not set"

---

### Post by darkod on 2012-02-18
You said in your first post that no linux cd can be booted and started? Is that right?

If you can't even boot the ubuntu cd it has nothing to do with the hdd. One option is video problem, but you only changed your hdd, the video card is the same. Did you have any video problems when installing ubuntu earlier on this computer?

---

### Post by mgt2000 on 2012-02-18
> **darkod said:**
> You said in your first post that no linux cd can be booted and started? Is that right?
If you can't even boot the ubuntu cd it has nothing to do with the hdd. One option is video problem, but you only changed your hdd, the video card is the same. Did you have any video problems when installing ubuntu earlier on this computer?

I can boot the Ubuntu CD (and its USB version) but none of Linux-based CDs can read/write the hard disk. No I have never had problem with video card (on-board- Mobile Intel® 945GM Express Chipset Family) and I can see the screen but non of these CDs (OpenSUSE, Redo backup and even Acronis true image which has a Linux-based version) can't recognize the hard disk and they just luck the system and the hard disk starts making a strange noise!

---

### Post by darkod on 2012-02-18
So, if you boot ubuntu in live mode and execute in terminal:
sudo fdisk -l (small L)

will it show the hdd? Post the results here.

If it literary locks the hdd it might be a hardware problem.

---

### Post by mgt2000 on 2012-02-18
> **darkod said:**
> So, if you boot ubuntu in live mode and execute in terminal:
sudo fdisk -l (small L)

will it show the hdd? Post the results here.

If it literary locks the hdd it might be a hardware problem.

Thanks for your quick reply. 
By boot, I mean I can start my computer from USB and I don't have a problem with that but after booting from USB (or CD) the system stop working in few seconds and I can not inter to the live mode or install it directly and all I have is just that strange noise. here is the information of my newer hard disk and it seems it doesn't have a special problem with linux: [here ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136545")
And of course, my previous hard disk was also from this manufacture but it was only 80 GB.
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136545")

---

### Post by stn21 on 2012-02-18
> **mgt2000 said:**
> ... I can start my computer from USB and I don't have a problem with that but after booting from USB (or CD) the system stop working in few seconds ...

Try to unplug the harddisk. Can you boot then? 

Like darkod has already suggested it sounds like you have a broken harddisk.

---

### Post by mgt2000 on 2012-02-18
> **stn21 said:**
> Try to unplug the harddisk. Can you boot then? 

Like darkod has already suggested it sounds like you have a broken harddisk.

I unplugged it but several times but still I have the same problem. Of course it doesn't work normally with windows XP and 7 (for example I can not format it or change partitions and it is completely impossible to format it as EXT4!) butI am not sure if it is because of the hard disk or it is because of its incompatibility with my laptop!
How can I be sure what is exactly the problem? (the hard disk or incompatibility issue, I mean?)

---

### Post by stn21 on 2012-02-21
> **mgt2000 said:**
> I unplugged it but several times ...

Not quite. I meant unplug it, do _not_ plug it in and boot live-linux. Sounds trivial but that way you can be sure that your boot-medium is OK and your computer has not developed some hardware-issue like a defect in a memory-module. If your computer boots OK without the harddisk then you can be pretty sure that the harddisk is broken.

I assume your harddisk is SATA. In that case unplug it, boot live-ubuntu and then plug it in again. If it is OK it should then auto-mount, if you have valid partitions with a filesystem. Otherwise it should at least show up in gparted and in the harddisk-maintenance-program from the system-menu (sorry, don't know the exact english menu-item, my ubuntu is german)

---

### Post by mgt2000 on 2012-02-22
> **stn21 said:**
> Not quite. I meant unplug it, 

Thanks a lot. As I said, with my old hard-drive I don't have a problem and Ubuntu works perfect. I gave the hard disk back to the store and they also couldn't format it there and it was broken! Now I use my own old hard disk :(

---

### Post by LinuxFan999 on 2012-02-22
Since the problem has been solved, please mark the thread as solved using the "Thread tools" menu.

---

