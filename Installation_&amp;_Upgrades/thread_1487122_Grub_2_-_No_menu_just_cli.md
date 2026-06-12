---
title: "Grub 2 - No menu just cli"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by sin-tax on 2010-05-18
Hopefully someone can help point out to me what i'm doing wrong, i'll give a quick rundown of what I have configured. 
 
single hdd
 
/dev/sda1 = 100mb Windows7 boot part
/dev/sda2 = Windows7 part ( encrypted w/ Truecrypt) 
/dev/sda5 = /boot Ubuntu 10.04
/dev/sda6 = / Ubuntu 10.04
 
Truecrypt bootloader is in the MBR 
 
 
The Truecrypt bootloader will boot other loaders if esc is hit, I can choose to boot /dev/sda5 and grub loads, but no menu is displayed, all I get is a GRUB> cli. I've reinstalled Grub to /dev/sda5 using the chroot method outlined in the Grub2 info page on this site, but it always results in the same outcome of ending up in the Grub cli. 
 
I can chroot that install and attempt a update-grub, but all i get is "cannot find list of partitions!"
 
attached is the boot_info_script results. Any help would be killer. I really would love to have a encrypted dual boot system. 
 
Thanks!

---

### Post by darkod on 2010-05-18
Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 210237184 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

You did install grub2 to /dev/sda5 but somehow it doesn't continue to core.img correctly. Try again but because you have separate ubuntu /boot partition you need to mount both / and /boot. Also, it seems your grub.cfg is not correct so you might need to chroot and update it too.

From live mode, it would be:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo grub-install --force --root-partition=/mnt/ /dev/sda5
sudo chroot /mnt update-grub
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

Restart and hopefully it will work.

---

### Post by r_s on 2010-05-18
There is no menuentry listed in your grub.cfg file , so there will be nothing for grub to display. Why don't you manually add your ubuntu partition to the grub.cfg file.

---

### Post by darkod on 2010-05-18
> **r_s said:**
> There is no menuentry listed in your grub.cfg file , so there will be nothing for grub to display. Why don't you manually add your ubuntu partition to the grub.cfg file.

Only that wouldn't help. Grub2 is not finding core.img correctly.

---

### Post by r_s on 2010-05-18
> **darkod said:**
> only that wouldn't help. Grub2 is not finding core.img correctly.
+1

---

### Post by sin-tax on 2010-05-18
> **darkod said:**
> Boot sector info: Grub 2 is installed in the boot sector of sda5 and 
looks at sector 210237184 of the same hard drive for 
core.img, but core.img can not be found at this 
location.
 
You did install grub2 to /dev/sda5 but somehow it doesn't continue to core.img correctly. Try again but because you have separate ubuntu /boot partition you need to mount both / and /boot. Also, it seems your grub.cfg is not correct so you might need to chroot and update it too.
 
From live mode, it would be:
 
sudo mount /dev/sda6 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo grub-install --force --root-partition=/mnt/ /dev/sda5
sudo chroot /mnt update-grub
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
 
Restart and hopefully it will work.
 
I'm not sure I know anything about the --root-partition switch. I'm thinking you are meaning --root-directory, but how I understand that switch is it should be the actual location of the boot files (/boot) where as you specificed that it should be the linux install (/), which would work if I was not using a seperate boot partition.  
 
When I installed Grub last I used the following procedure... 
 
boot from live cd
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt/boot /dev/sda5 --force
 
Still just leaves me with the GNU Grub cli :confused:
 
I'm going to look into the specific issue of the core.img not being found. That one kinda baffles me a bit since its obviously there and it shows there in the script.

---

### Post by darkod on 2010-05-18
> **sin-tax said:**
> I'm not sure I know anything about the --root-partition switch. I'm thinking you are meaning --root-directory, but how I understand that is it should be the acutal /boot where as you specificed that it should be the linux / 
 
When I installed Grub last I used the following procedure... 
 
boot from live cd
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt/boot /dev/sda5 --force
 
Still just leaves me with the GNU Grub cli :confused:
 
I'm going to look into the specific issue of the core.img not being found. That one kinda baffles me a bit since its obviously there and it shows there in the script.

Yes, the switch is root-directory. Sorry about that. :(

When reinstalling grub2 in your situation, you definitely have to mount both / and /boot, and the --root-directory is / as the name says, definitely not /boot.

I guess this is why it can't find core.img. Yes, core.img is on /dev/sda5, more precisely in grub/core.img but you told grub2 that /dev/sda5 is root, so it tries to find a boot folder in it.

You can split it in two steps. First just reinstall grub2 with:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --force --root-directory=/mnt/ /dev/sda5

Then run again the script, you will see the message that it can't find core.img will be gone. Or course, it still won't work because as it has been pointed out, your grub.cfg has no linux entries.

So the second step would be to chroot and do the update-grub. No need to reinstall grub2 to /dev/sda5 again of course.

---

### Post by sin-tax on 2010-05-18
I seem to be in maybe a worse state now. Now the script does not even recognize the grub config at all, and Grub hangs on boot. I'm gonna RM sda5 and sda6 and try the install with just one partition as a POC.
 
I'm open to any more ideas though. I followed your steps though....
 
Updated Boot_Info_Script results file attached.

---

### Post by darkod on 2010-05-18
Hmmm... This doesn't make sense.
/grub/grub.cfg and grub/core.img are missing from /dev/sda5. Also the kernel files are missing.

The commands I wrote couldn't have deleted them. Was it all you executed, or you were trying something else too? Or maybe earlier?

You can create new grub2 config files by chroot into the / partition and using grub-mkconfig, but I'm not sure about adding the kernel. I have never deleted one.

PS. The kernels are missing even in the first results file. I missed that reading it the first time. That's why grub.cfg had no linux entries, there were no kernels at all.

---

### Post by sin-tax on 2010-05-19
Update: after deleting the /dev/sda5 and /dev/sda6, reinstalling with just one partition. Everything works as it "is supposed to". Hitting ESC at the Truecrypt boot loader, directs me to choose what partition to boot from, I choose the linux partition and it boots into Grub w/ proper menus. So i know it will work. 
 
I'll bang on this thing a few more times, and see what I can come up with. 
 
Thanks for the info about the kernel images being missing. I may have to go down that road.

---

