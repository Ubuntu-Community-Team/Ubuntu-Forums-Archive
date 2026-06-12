---
title: "Ubuntu 10.04 LTS grub/install problem"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Alex N on 2010-05-12
Hello,

I've got the following problem during installation.
I am installing Ubuntu on partition sda5 formatted as ext3.
I told installer to NOT modify MBR, because I fear it can destroy it. I am using Vista boot manager (EasyBCD) that works perfectly.
The installation process finished, and I created a record for booting Ubuntu. The boot failed, and the reason was simple: there was NOTHING in /boot/grub/ folder.

Moreover, there is apparently no GRUB on LiveCD, so I can not reinstall it.

The menu.lst I have on the main partition is

find --set-root --ignore-floppies /boot/grub/stage1
chainload +1

All is fine, but there is no /boot/grub/stage1

What to do ? Let Ubuntu trash my MBR, restore it and use EasyBCD again ?

---

### Post by dino99 on 2010-05-12
lucid work with grub2 (ie grub-pc + grub-common) and cant work with menu.lst

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-05-12
> **Alex N said:**
> 
I told installer to NOT modify MBR, because I fear it can destroy it. I am using Vista boot manager (EasyBCD) that works perfectly.

All is fine, but there is no /boot/grub/stage1

What to do ? Let Ubuntu trash my MBR, restore it and use EasyBCD again ?

1. Your fear from grub2 is too exaggerated. On the contrary, grub2 works perfectly because it can locate and boot most OSs you can think of. It's exactly that fear that is driving you into more problems, and more complicated solutions.

2. Having said that, you are free to use EasyBCD if you like. The step you missed was:

You don't tell grub2 NOT to install, you tell it to install to the root partition (in your case /dev/sda5). This is crucial because EasyBCD can't boot ubuntu directly, it just calls grub2 to continue. At this moment there is no grub2 to call.

My suggestion (not the same as my advice below):
Delete the EasyBCD entry you created. Haven't worked with it, but better to delete this "wrong" entry.
Boot with the 10.04 cd in live mode and install grub2 to /dev/sda5. You can do this in terminal with mounting root and also using the --force parameter because grub2 doesn't like being installed to a partition and has to be "forced":

sudo mount /dev/sda5 /mnt
sudo grub-install --force --root-directory=/mnt/ /dev/sda5

After grub2 is installed, restart, go in EasyBCD and create new entry. This time it should work. If it doesn't, you have only EasyBCD to blame, not grub2 or ubuntu. :)

[COLOR=Red]My advice[/COLOR]:
Get over your fear of grub2 and let it handle things. They work perfectly like that. In other words, don't do the above and install grub2 on the MBR. If you want the commands for that, just ask.

Cheers.

---

### Post by Alex N on 2010-05-12
Thank you for your detailed answer. 

> **darkod said:**
> 
You don't tell grub2 NOT to install, you tell it to install to the root partition (in your case /dev/sda5).


In fact this is exactly what I wanted to do. I thought that unchecking "Install the Grub boot loader to the master boot record" will do the task. 

> **darkod said:**
> 
[COLOR=Red]My advice[/COLOR]:
Get over your fear of grub2 and let it handle things. They work perfectly like that. In other words, don't do the above and install grub2 on the MBR. If you want the commands for that, just ask.
Cheers.

I think I can just reinstall Ubuntu. But maybe there is a better way ?

---

### Post by darkod on 2010-05-12
> **Alex N said:**
> Thank you for your detailed answer. 



In fact this is exactly what I wanted to do. I thought that unchecking "Install the Grub boot loader to the master boot record" will do the task. 



I think I can just reinstall Ubuntu. But maybe there is a better way ?

You're welcome.

I'm little confused which approach you decided to take. In both cases, no need to reinstall ubuntu at all.

1. If you still want to use EasyBCD you just need to add grub2 to the partition /dev/sda5. The commands for that are in my previous post. You have to boot with the ubuntu cd in live mode (Try Ubuntu) and in terminal execute those two commands.

2. If you decided to let grub2 take the MBR, I would first boot windows and remove easybcd. Let the vista boot process be the default, as if you never used easybcd. I'm not sure if additional steps are needed I think just removing easybcd is enough.

Then boot in ubuntu live mode and the commands are slightly different (the second one):

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 to the MBR of your disk /dev/sda. Reboot and you should see the grub2 boot menu where you can select ubuntu or vista. If vista is not there boot ubuntu and try in terminal:

sudo update-grub

---

### Post by Alex N on 2010-05-12
> **darkod said:**
> 
sudo mount /dev/sda5 /mnt
sudo grub-install --force --root-directory=/mnt/ /dev/sda5


Well, this did not help. GRUB is now installed into sda5, and I can invoke it using EasyBCD. It does not start boot process, however, but stays at the command line. I can type in
root (hd0,5)  // for some reason it is hd0,5 now
linux (hd0,5)/boot/vmlinuz.......
boot

which results in kernel panic "can not mount root fs"
I wonder why it does not start boot process.
So far there is no problem in EasyBCD.

---

### Post by dino99 on 2010-05-12
after installing grub, you need to run:

sudo grub-mkconfig
sudo upgrade-grub
sudo update-initramfs -u

---

### Post by Alex N on 2010-05-12
> **dino99 said:**
> after installing grub, you need to run:

sudo grub-mkconfig
sudo upgrade-grub
sudo update-initramfs -u

sudo grub-mkconfig says

error: cannot find a device for / (is /dev mounted?).

---

### Post by dino99 on 2010-05-12
look at the link posted into post # 2, i think that your formatting process is not complet or wrongly done.

---

### Post by darkod on 2010-05-12
> **Alex N said:**
> Well, this did not help. GRUB is now installed into sda5, and I can invoke it using EasyBCD. It does not start boot process, however, but stays at the command line. I can type in
root (hd0,5)  // for some reason it is hd0,5 now
linux (hd0,5)/boot/vmlinuz.......
boot

which results in kernel panic "can not mount root fs"
I wonder why it does not start boot process.
So far there is no problem in EasyBCD.

Sorry, my mistake. Because you originally didn't install grub2 none of the config files are there. This is rare situation and I completely forgot about it. That's why grub2 has nowhere to go.

Let me look around to find the commands to use.

---

### Post by darkod on 2010-05-12
You needed to mount few other stuff too. I think this should sort it out, you need to do it from the live mode again:

sudo mount /dev/sda5 /mnt
sudo grub-install --force --root-directory=/mnt/ /dev/sda5
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt update-grub
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

Restart. I think it should be good now. Sorry about that. :)

---

### Post by Alex N on 2010-05-13
Thank you, this works. GRUB already has been successfully updated to next version, so I think the system will live this way.

---

### Post by jao_madn on 2010-06-25
Mine is the same and forums instructions works..Thanks to Every one.

Hi,

We have the same problem,

Mine is an asus notebook with dual boot windows 7 Pro 64 Bit Oem preinstalled and Ubuntu 10.04 installed second, Dual boot with grub boot loader seems fine but at certain point i decide to change the loader and used Windows 7, i used the easyBCD 1.7.2 (note: Don't check the "GRUB INSN'T INSTALL TO THE BOOTSECTOR" when adding linux it will used the grub 0.4.3 i guess and wont boot to linux and put in grub cmd window althought i try to used it but i have no luck booting linux, If u do boot again to win7 and delete and add again and don't select that option:i try it many time and lucky it don't affect the loader) i stumble this furom and pretty usefull i tried the instruction told by DARKOD
I boot to linux live CD 10.04 mount the linux partition which mine is sda7
and used the command by DARKOD only and no other command:
sudo mount /dev/sda7 /mnt
sudo grub-install --force --root-directory=/mnt/ /dev/sda7

And with luck my Linux 10.04 Boot pretty Good althought it some kind of ODD its because EASYBCD si fine chossing between windows7 and linux and if you choose linux it will looad again the grub choosing linux and win7, you have 2 ways to choices how to  load win7..haha..

By the way why is that so?

---

