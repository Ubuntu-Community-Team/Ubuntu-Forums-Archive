---
title: "Grub error 21 using /dev/hde on HPT372 controller"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by Raptor Ramjet on 2005-05-08
Hello,

I've just installed Ubuntu on a machine with an Abit KD7-RAID motherboard (which features a Highpoint 372 RAID controller)  In this machine I have a single 120Gb disk which is attached as primary master on the IDE3 controller.  Sadly though once the install had finished I rebooted the system and it fails to boot with Grub failing at "Stage 1.5" with "error 21".   

Now I know there's no problem with the hardware as about 40 minutes earlier it was happily running Slackware 10.1 and Lilo had no difficulties booting (The main reason I'm installing Ubuntu is I simply can't get monodevelop working on Slackware and Synaptic is just so damn good)

As I'm not using the RAID features of the board I would therefore expect Linux to "see" the drive as /dev/hde.  I've also just booted the machine using Knoppix and in case it's any use here's my /boot/grub/menu.lst file (n.b. I've removed all the commented out lines to reduce the size of my post):

<pre>
default		0
timeout		3
hiddenmenu

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hde1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

</pre>

So any advice will be most welcome.

Thankyou

---

### Post by Raptor Ramjet on 2005-05-10
Following my initial post I've now read up loads about Grub and have made a Grub boot disk.  Following this I've tried manually installing Grub which produces the following output:

<pre>
grub> find /boot/grub/stage1
	(hd0,0)

grub> find /boot/grub/stage2
	(hd0,0)

grub> root (hd0,0)
	Filesystem type is Reiserfs, partition type 0x83

grub> setup (hd0)
	Checking if "/boot/grub/stage1" exists...yes
	Checking if "/boot/grub/stage2" exists...yes
	Checking if "/boot/grub/resiserfs_stage1_5" exists...yes
	Checking if "/boot/grub/resiserfs_stage1_5" exists...yes
	Running "embed /boot/grub/resiserfs_stage1_5 (hd0)"... 18 sectors are embedded
	succeeded
	Running "install/boot/grub/stage1 (hd0) (hd0)+18 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
	Done.

</pre>

So a quick reboot later and I'm back to the familiar "Error 21" problem outlined above.

This being the case would anyone like to give me any pointers as to how I can get this bloody system to boot ?  Or should I give up on Grub and install good old Lilo (which has NEVER let me down...)

Yours rather dissapointedly.

---

### Post by Raptor Ramjet on 2005-05-11
Well after more playing around (sorry R&D) I got bored and installed LILO.  As expected this works a treat so I've now got a system which boots properly and I'm not best pleased with GRUB.

So my advice to anyone having problems booting from a disk attached to a motherboards onboard RAID controller is don't use Grub.  Use LILO. Or if I was a "l33t" teenage script kiddie I'd say to Grub "j0o fails it".

Ho hum.  And no replies in this forum to boot (apart frm my own)

---

### Post by shinde on 2005-06-23
explain to me how you came to solve this please?  how did u install LILO when u cant even boot up, because im having the same problem with GRUB.  i get the error 21 on boot and cant boot windows or ubuntu

---

### Post by Raptor Ramjet on 2005-09-14
Firstly apologies for not replying to you sooner (I've not been keeping up with the forum lately)

Anyway to get Lilo installed I actually did a full reinstall of Ubuntu and then chose to use Lilo instead of Grub (I forget the exact steps but it's one of the options when you do an install)  I always keep my home directory on a seperate partition to allow me to do this should the need arise :)

Athough since then I've done a spot more investigation and I do believe you can boot an installed kernel by first booting from a cdrom (the Ubuntu live disk should do the trick) and then issuing the following at the "boot:" prompt

boot: linux root=/dev/hde1 ro

Of course you'd substitute /dev/hde1 with the device name where your kernel is installed.

Hope this helps or maybe someone more knowledgable would care to point out a better way ?

---

