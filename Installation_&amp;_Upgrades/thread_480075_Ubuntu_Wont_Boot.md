---
title: "Ubuntu Wont Boot"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by LordV on 2007-06-21
Ok, first off here is my system:

Intel Core2 Duo E6400
2gb ram
Asus P5N-E Sli
ATI X1650/GeForce 7600GT (whichever i feel like using)


Now i have 2 hard drives. First i have my big harddrive with Vista on it and i have a smaller harddrive that I installed Ubuntu x64 on. NOTE!: I unplugged my Vista harddrive before installing ubuntu so i wouldn't mess up vista.

So I plugged in my ubuntu hard drive and used the live CDs that i ordered. It installed everything fine and when it went to boot Ubuntu it just stopped at the loading bar. I was told before to press ESC when it shows the GRUB thing and remove the "silent" line and then boot. I did this, and nothign happed. 

I need some help! Thanks!

---

### Post by logos34 on 2007-06-21
more info, please

so you're getting the grub menu, you choose the ubuntu kernel 2.6.20-15 or whatever and it just freezes at the loading bar? is your ubuntu drive sata or ide?  did you plug your vista drive back in just before booting ubuntu? what's the 'silent' line?

---

### Post by LordV on 2007-06-21
> **logos34 said:**
> more info, please

so you're getting the grub menu, you choose the ubuntu kernel 2.6.20-15 or whatever and it just freezes at the loading bar? is your ubuntu drive sata or ide?  did you plug your vista drive back in just before booting ubuntu? what's the 'silent' line?

yes i get the menu, it auto choosees the newest ubuntu, and it freezes at the loading bar, the bar doesnt move.

drive is ide

vista drive doesnt matter

silent line i was told is in the grub menu for options when you boot, i was told to take it off and it would show me errors instead of hiding them.

---

### Post by wpshooter on 2007-06-21
I would do the same things you did except I would use the ALTERNATE (text based) CD installation instead of the live CD.

Good luck.

---

### Post by logos34 on 2007-06-21
> **LordV said:**
> yes i get the menu, it auto choosees the newest ubuntu, and it freezes at the loading bar, the bar doesnt move.

drive is ide

vista drive doesnt matter

silent line i was told is in the grub menu for options when you boot, i was told to take it off and it would show me errors instead of hiding them.

oh, 'quiet' option (end of kernel line) is what you mean.  

When you installed did you have to pass any special boot options (like 'acpi=off', noapic, etc) to get it to work on your machine?

When you did the 'e' edit thing in the grub menu what did your 'root' line say?  If your root partition is the first one on the disk then it should read **'root (hd0,0)**'.

You might also want to post your boot log files, especially the dmesg output from your kernel ring buffer.  Someone may be able to tell you exactly what's going wrong in the boot process.

Boot from the live cd.  You have to mount your root partition to get to your logs.  Go to the desktop, open a terminal and enter:

> [B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu   (*replace 'hda1' with your root partition)
cd /mnt/ubuntu[/B] 

[B]dmesg | tail -n 30
cat /var/log/syslog | tail[/B]

Copy and post to the forum if possible.

While you're in your files might as well check **/boot/grub/menu.lst**.  Maybe there's an error somewhere.

Post that too if you want.

---

