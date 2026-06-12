---
title: "Dual boot Install help"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Kirk_McMillan on 2014-05-13
I'm stuck in the middle of my ubuntu dual boot install - unsure what to do next !

I have an SSD and a Slave.  The SSD has Windows C: and the slave has 2 partitions. I want to install 
unbuntu to Partition 2 on the slave.  At the moment this shows (in ubuntu install dialog) as free space.

I think next step is

1) Drive to install to.   Do I select free space ?  If so, do I need to format it first ?

2) Device for bot loader installation.  Is this the SSD ?

Help much appreciated !!!
Thanks, Kirk

---

### Post by mastablasta on 2014-05-13
> **Kirk_McMillan said:**
> 
1) Drive to install to. Do I select free space ? If so, do I need to format it first ?


yes and formating is done during install.

if oyu are in manual mode ("something else" options) you need to create root (/) partition (formated as you like suggest you stay wiht default ext4 for now)and /swap (formated as swap)
> 

2) Device for bot loader installation. Is this the SSD ?



yes. first sector. so if ssd is called sda and windows is on sda1 (first partition) then GRUB is on /dev/sda


by the way what windows? MBR or UEFI install? is partitioning GPT? it all might make a difference.

---

### Post by Bucky Ball on 2014-05-13
*Thread moved to **Installation & Upgrades**.*

You might have more luck here.

> **mastablasta said:**
> ... by the way what windows? MBR or UEFI install? is partitioning GPT? it all might make a difference.

This, apart from the other relevant points mastablasta makes.

(PS: mastablasta, today is Stevie Wonder's birthday, but you probably know that already!)

---

### Post by Kirk_McMillan on 2014-05-13
MBR, I'm pretty sure.

After waiting about 6 hours then seeing masterblasters affirmatives I hit the button!  If it buggers up WIN7 I'll re-install it

But didn't get far.

No root file system is defined.
Please correct this from the partitioning menu.

Damn !

Could you give some step by step instructions to do this please?

---

### Post by oldfred on 2014-05-13
I prefer to keep grub2's boot loader on the same drive as Ubuntu and Windows boot loader on same drive as Windows if system can boot from both drives. You mention slave and some old systems could not boot from a slave drive, but most newer systems can.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

I am reusing partitions with older installs, so partition does exist, but is just reformatted. If you have to add a partition you click on + instead of change. Install of 14.04 is to my SSD which uses gpt partitioning so it does show extra partitions for that. And combo box at bottom of screen still shows drive that is sda.

---

### Post by Kirk_McMillan on 2014-05-13
Hi Fred,

I'm not at the understanding stage yet - never heard of grub until today!   Those links are a bit too complex for total beginners.
If possible it would be cool if you could give me specific instructions (step by step) to move on from where I am.

I'm looking at this dialog box that says 'Please correct this from the partitioning menu." and offers OK only.

What does one do from here ?

---

### Post by oldfred on 2014-05-13
Did you click on plus and add a / (root) partition as shown in my attached screen shot? Best to also add swap, but size depends on amount of RAM you have.

If you have 4GB of RAM or more, a swap of 2GB is all you need unless you want to hibernate. And if dual booting hibernation is not recommended.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Kirk_McMillan on 2014-05-13
Thanks for help...  but I'm going to flag it!   Too complicated.

---

### Post by mastablasta on 2014-05-14
a very easy solution is to unplug your windows disk, then you can select to install to largest free empty disk space. once done. reconnect the windows disk and use boto repair tool to add windows to grub menu (boot loader that open on start). finally you need to let BIOS know to start the boot from the linux disk.

by the way what is the complicated part? even in windows you need to say where your root will be. root in windows is called c:\ in linux it's /

swap is the only thing different in this case. as windows (atumaticly) creates a file for it (i think it's called pagefile.sys). while in linux swap is a partition. swap partition is automaticly created if you use whole disk or install to largest free disk space option.

you can try installing it in virtualbox to see how the whole disk install looks like. it's just a couple of next clicks...: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

