---
title: "Problems installing Ubuntu on 2nd HDD"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Knives412 on 2009-12-08
I am new to Linux and Ubuntu, and I'm having a lot of trouble. I'm trying to install Ubuntu 9.10 64 bit onto my second HDD. I got vista on my other and XP on my second with there recovery partitions. Fist i Partitioned 30 GB's off of the second HDD. 

I then created the CD from the iso. I had a few problems getting the disc to boot right, had to press F6 and select "noapic" and "nolapic". Finally got the installer to load then used the wizard to partition 2 GB's for swap area, 10 GB's for "/", and about 10 GB's for "/home". Finished the instillation then rebooted it booted to vista with no option to boot to Ubuntu. I then changed the Bios to boot off the second HDD. 

I can now get to the Grub boot loader but when i select Ubuntu it goes to a black screen with the cursor in the top left corner. I tried to re-install Grub but it seems I do not have "/boot/grub/stage1", "/boot/grub/stage2", and "/boot/grub/menu.lst". I have been searching all over for solutions but can"t find any. All Help much appreciated, and Thanks.

---

### Post by darkod on 2009-12-08
You have grub2 coming with 9.10 and those files don't exist in it. It could be because of driver or another problem.

If you had to use noapic and nolapic, first try instead of hitting enter at the ubuntu entry, I think you need to press 'e' to edit the line. Add both commands at the end, see if it boots fine. If it does, there is a way to add them permanently to the boot command.

Another option is to try the recovery mode entry. Will that work? But even if it does, it will open just command text prompt, not the GUI desktop. If the issue is video driver you can use this prompt and install a driver.

---

### Post by Knives412 on 2009-12-08
Alright, so I rebooted and tried to add "nopic" and "nolapic" after "initrd /boot/initrd.img-2.6.30-14-generic". Don't know if that was the line i was suppose to add it to, but it didnt help just went to the same screen with the cursor a little lower down the screen.

Also I am using an ATI Radeon HD 2400 XT gfx card, I heard that ATI has some problems with Ubuntu.

---

### Post by darkod on 2009-12-08
In case it's a driver issue (and I can't be sure), try this. Select the recovery mode entry. On the next menu select something like "root with networking" to have internet access. After it loads to the command prompt do:
sudo apt-get install envyng-core envyng-qt

Then run it in text mode with:
envyng -t

Install the ATI driver (no need to remove the current one). It knows where to download it from. Just follow the questions.

After it finishes, reboot and try the normal mode entry to see if it worked.

---

### Post by Knives412 on 2009-12-08
Ok so I tried using the recovery mode and through out the boot it keep saying "Buffer I/O error on device sdb, logical block 0" and it would range from block 0 to block 10. 

At the end it would say 

gave up waiting for root device. Common problems:
     -boot args (cat /proc/cmdline
         -check rootdelay= (did system wait long enough)
         -check root= (did system wait for the right device)
ALERT! /dev/disk/by-uuid/0f2273e6-f46d4fsa-b389-917423ba4fd8 does not exist. Dropping to a shell!

(initramfs)

That's where it stops and i cannot input anything.

---

