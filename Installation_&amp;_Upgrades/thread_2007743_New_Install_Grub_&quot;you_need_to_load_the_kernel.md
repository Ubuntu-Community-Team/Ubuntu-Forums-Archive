---
title: "New Install: Grub &quot;you need to load the kernel first&quot;"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by FreeRangeChicken on 2012-06-21
I classified this post as 'all variants' because I don't believe it is specifically related to the Xubuntu flavor.


I recently installed Xubuntu 12.04 on my machine.  I wanted to preserve the Win Vista and Kubuntu 10.04 installs that already existed on the machine and add a Win7 install.  

Here are the steps I took:
1) remove original hard drive from SATA slot0
2) install new hard drive on SATA slot0
3) install win7 on first partition of new HD
4) install the old HD in SATA slot2 (SATA slot1 has DVD)
5) install Xubuntu 12.04 on second partition of new HD

During Xubuntu install, all of the OS's were detected (Xubuntu 12.04 + Win7 on SATA slot0, and Kubuntu 10.04 + Vista on SATA slot2).  

When I boot, there are grub menu entries for all four OS's, but only Win7 and Xubuntu (both on the new HD in SATA slot0) are bootable.

If I select either OS (Vista or Kubuntu 10.04) on the original HD (now in SATA slot2) I get the message "you need to load the kernel first" and I eventually get returned to the grub menu.

Any thoughts on how to boot the OS's on the original HD would be greatly appreciated.  I've seen the utility Boot-Repair, but it isn't clear to me that it will fix the problem.  I'd like to understand what is happening and why.

Thanks, 

Dave L.

---

### Post by dino99 on 2012-06-21
your issue is due to the devices switches: every time you unplug/plug a device it has a new uuid, but then the grub still have the old uuid.

so you need to know on which partition is installed your OS
 (boot on a livecd and run gparted and note the partitions (/dev/sda .... /dev/sdb ...) 

then open a terminal to install grub on the ubuntu hdd:

sudo grub-install /dev/sdx 
(replace sdx by the good one

sudo update-grub

exit and boot from hdd

---

### Post by drs305 on 2012-06-21
The UUID shouldn't change - that is why UUIDs are used in Grub rather than device names such as sda, sdb, etc.

Your best option is to boot the LiveCD, install and run Boot Repair. Click the 'Recommended Repair' button and it should fix your boot issue. 

There is a link to Boot Repair in my signature line.

---

### Post by FreeRangeChicken on 2012-06-21
Thanks for the reply dino99.

I suspected UUID may have changed when I moved the drive.  However, when I installed Xubuntu 12.04 on the new drive (sda) and grub was installed, the old drive (now sdb) had already been moved, so the UUID should not have changed since Xubuntu 12.04 was installed.

So are you saying that the bootloader on sda will not boot the OS's on sdb and there needs also to be a bootloader on sdb?  When I boot the computer, I'm guesing the bootloader on sda (sata slot0) will load.  How do I get to the OS's on the other disk?

---

### Post by FreeRangeChicken on 2012-06-21
drs305, 

Thanks, I've been looking at boot-repair.  I just get a little nauseous at the thought of diddling with MBRs and bootloaders (mainly because I'm ignorant of all that stuff).  

Any thoughts as to the nature of the problem?  I'm trying to educate myself as I go here.

---

### Post by drs305 on 2012-06-21
Is your current (working) Ubuntu OS listed as the first menuentry? That would ensure you are using its GRUB files for booting. If the entry isn't the first one it's possible you are using the GRUB files from the other installation.

You can make sure you are using your current GRUB files by running the following. X should be the drive your BIOS is currently booting first (sda, sdb, etc), or if it isn't the Ubuntu drive, change it to the Ubuntu drive and make sure that is the one BIOS boots first. Youi don't have to boot the Ubuntu drive first, but if the other drive contains the Windows bootloader this option will prevent it being overwritten by GRUB. The second command will make sure the Grub menu is updated.
```
sudo grub-install /dev/sd[COLOR="Red"]X[/COLOR]
sudo update-grub
```

If that doesn't solve things, run the boot info script (either manually or from Boot Repair) and post the results or a link. (BIS or Boot Repair in my signature line).

---

### Post by FreeRangeChicken on 2012-06-21
Yes, the new working Xubuntu 12.04 is the first grub menu entry.  I believe Win7 (also working) is next.  

Vista and Kubuntu on sdb (non-working) are at the bottom of the list.

I'll run the boot info script this evening when I get home.

Thanks for your time.

---

### Post by dino99 on 2012-06-21
also check the bios hdd boot order

---

### Post by FreeRangeChicken on 2012-06-21
Okay, so I ran boot-repair (output link below) doing the recommended repairs and now I get device not found and partition not found when trying to boot both of the non-working OS's.  The original working OS's (before repair) still work.

[http://paste.ubuntu.com/1053651/](http://paste.ubuntu.com/1053651/)

---

### Post by drs305 on 2012-06-22
The Grub menu entries look normal, other than your 10.04 installation still uses Grub legacy. 

At the Grub menu, try to manually boot 10.04 and let us know where it fails.


Press 'c' to get to the grub prompt
```
ls (hd1,5)/  # Does it find 'vmlinuz' and 'initrd.img'
linux (hd1,5)/vmlinuz root=/dev/sdb5 ro
initrd (hd1,5)/initrd.img
boot
```


If that doesn't work try these for the kernel and image lines:
```
linux (hd1,5)/boot/vmlinuz-2.6.32-41-generic root=/dev/sdb5 ro
initrd (hd1,5)/boot/initrd.img-2.6.32-41-generic
```
Added: These commands really don't do anything differently than the menuentry as far as loading the kernel and initrd image. It does eliminate some of the other commands built into the menuentry. I'm not confident it will work but it's worth trying and perhaps any error messages will shed more light on what's going wrong.

If you can boot into 10.04, I'd recommend purging 'grub' (Grub) and installing 'grub-pc' (Grub 2). The instructions can be found by going to the Grub2 Ubuntu community doc: 
_[https://help.ubuntu.com/community/Grub2/Installing#Purging_.26_Reinstalling_GRUB_2]("https://help.ubuntu.com/community/Grub2/Installing#Purging_.26_Reinstalling_GRUB_2")_

---

### Post by FreeRangeChicken on 2012-06-22
Thanks, I'll give it a try this evening.

---

### Post by FreeRangeChicken on 2012-06-22
This is interesting.  If I hit 'c' on the grub menu and type in the 'ls (hd1,5)/' command, I get 'no such partition'.

I then type 'exit' to get back to the menu and hit 'c' again and repeat 'ls (hd1,5)/' and it works.  There is a vmlinuz and an initrd.img.  If I continue with the rest of the commands in your first block of commands, the screen eventually goes blank and seems to hang.


I can mount and inspect these partitions from within the Xubuntu 12.04 OS.

---

### Post by YannBuntu on 2012-06-27
Hello
Following your PM,

I see no error in the Boot-Repair log. It successfully installed the GRUB of your Xubuntu (sda5) into the MBRs of sda and sdb.

As you now can boot into the systems located on sda (Xubuntu&Seven) but not the ones located on sdb (Vista&Kubuntu), I suppose that this is due to a bug of GRUB (which generated wrong entries, or cannot read on sdb...), so you should first create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
and see what GRUB devs will say.

As a workaround, we can try to install the GRUB of Kubuntu into the MBR of sdb, so that you can boot Vista&Kubuntu by making your BIOS boot on sdb. (and if you are lucky, this GRUB menu will also allow you to boot Xubuntu&Seven).
To do this:
1) run Boot-Repair, click "Advanced options", go to the "GRUB location" tab, select "*OS to boot by default: Ubuntu 10.04.4 LTS (sdb5)*" and "*Place GRUB into: sdb*", apply. **Indicate the new URL** that will appear.
2) Setup your BIOS so that your 320GB disk is first in the boot order.
3) Reboot and tell us what you observe (**do you see a GRUB menu? if yes, which entries work? which is the first entry?**)

---

### Post by FreeRangeChicken on 2012-06-27
Yann, 

I've submitted a bug report at Launchpad([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1018419](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1018419)).

I'll attempt your workaround this evening.

Thanks!

---

