---
title: "[SOLVED] Grub Error 21 - I can't get rid of this thing!"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Eagleguy125 on 2008-05-30
Alright, here goes. I recently installed Ubuntu 8.04 to my external hard drive, and I'm really enjoying it in a lot of ways, but that is beside the point for now. When I boot up my computer, if I do nothing, I get the now hauntingly familiar screen telling me that I've got GRUB Error 21.

If I turn on my computer (To get the external spinning.), then restart it, F12 my way into the boot menu on startup, boot from my hard disk, and then select either Ubuntu (External hard drive.) or XP Pro (Internal hard drive.), *THEN* I can start using my computer. However, that is a big hassle to go through, and I'd really rather not have to do all of that just to use my computer.

After about a week of researching the issue (Error 21, I quickly found out, is Grub's way of saying "I can't find your Ubuntu install!") and trying solutions (If you can find it on these or any other Linux forums, I've probably tried it.), I've got nothing to show for it. Everything from reinstalling Grub via Ubuntu to more drastic BIOS changes have yielded no fruits for my labor.

If you've got any kind of solution that even has a chance of working, please, show it to me. I'm about done with jumping through hoops every time that I boot. On a side note, if your solution involves a nice, easy-to-use menu from which I can select my chosen OS for that session as an end product, by all means post that as quickly as possible.

Other info: I'm running a Dell machine that was originally meant for business purposes with mostly standard-issue stuff. Oh, and Ubuntu is also doing this on another friend's computer, which somehow got this issue after I plugged my drive into it. That one is an HP somethingorother home desktop unit.

I thank you all in advance for your help. Have a great day!

---

### Post by Pumalite on 2008-05-30
This might apply to you (from another thread):

21 : Selected disk does not exist

In the Bios there is a facility to enable "USB lagacy support". I think your problem will disappears if you "enable" this function.

Your problem stems from having installed Grub, the Linux boot loader, into the MBR thereby overwriting XP's MBR.

Grub can't find the external hard disk because it needs "USB lagacy support enabled". You managed to install the Linux because it was the kernel who detected the USB device and found it. At boot time Grub has no access to a kernel and so it need "USB leagacy support enabled".

---

### Post by logos34 on 2008-05-30
> **Eagleguy125 said:**
> If I turn on my computer (To get the external spinning.), then restart it, F12 my way into the boot menu on startup, boot from my hard disk, and then select either Ubuntu (External hard drive.) or XP Pro (Internal hard drive.), *THEN* I can start using my computer. However, that is a big hassle to go through, and I'd really rather not have to do all of that just to use my computer.

Check if your Bios has a 'Pre-delay' setting (what it's called on Intel at least) to give the external drive time to spinup before POST.

Alternatively you can restore windows bootloader (xp disc>recovery console>**fixmbr**) and then install Grub to the MBR of the external usb drive and boot directly to that when you want linux (but you'll have to toggle the Bios boot drive each time).  Either that or make a separate /boot on the internal drive.

grub-->mbr of external disk:

**sudo grub-install /dev/sdb**

**gksudo gedit /boot/grub/menu.lst**

-change the **groot** and **root** lines to **(hd[COLOR="Blue"]0[/COLOR],?)**

---

### Post by meierfra. on 2008-05-30
> Alternatively you can restore windows bootloader (xp disc>recovery console>fixmbr) and then install Grub to the MBR of the external usb drive 


This needs to be done in the opposite order. First install grub to the MBR of the external drive, then restore  the windows boot loader. (Otherwise you won't be able to boot into ubuntu, after fixmbr. You could use a LiveCD to reinstall grub, but that is a hassle and "sudo grub-install /dev/sdb" won't work that easy.

---

### Post by Eagleguy125 on 2008-05-30
Thank you very much for your help. I'll attempt these solutions and report back with the results. It might be a while, though: My brother's high school graduation party is starting up in about twenty minutes.:)

---

### Post by logos34 on 2008-05-30
> **meierfra. said:**
> This needs to be done in the opposite order. First install grub to the MBR of the external drive, then restore  the windows boot loader. (Otherwise you won't be able to boot into ubuntu, after fixmbr.

yes, got the order reversed

> You could use a LiveCD to reinstall grub, but that is a hassle

yes (but not that much of a hassle)

> and "sudo grub-install /dev/sdb" won't work that easy.

It won't?  works for me every time

---

### Post by meierfra. on 2008-05-30
> It won't? works for me every time

Really?   I was only talking about the LiveCD situation.  From the LiveCD I need to use    the  "--root-directory" option.( or chroot)

---

### Post by logos34 on 2008-05-30
> **meierfra. said:**
> Really?   I was only talking about the LiveCD situation.

Ok, I see now. 

> From the LiveCD I need to use  the  "--root-directory" option.( or chroot)

Exactly. either that or chroot (see my post in other thread).  I  didn't know you could do this from the live cd until Herman showed me about a year ago. I had always just used the grub shell method.  Herman absolutely hates chroot (I don't know why though, because it's good for some things)

---

### Post by Eagleguy125 on 2008-06-02
Thank you, it is FIXED! I only had to change the root line in menu.lst from (hd0,1) to (hd1,0). Swapping two characters solved all of my problems. Aren't computers great? Anyway, I now need to mark this problem as solved. How do I do that? Edit: Never mind, I figured it out.

Also, does anybody know how I can resize the external drive's Ubuntu partition to 100GB instead of 300GB? I want to have 200GB of NTFS storage on it so I can actually use the drive. :)

Thanks again! :guitar:

---

### Post by meierfra. on 2008-06-02
> Also, does anybody know how I can resize the external drive's Ubuntu partition to 100GB instead of 300GB? I want to have 200GB of NTFS storage on it so I can actually use the drive.

Just use gparted (Ubuntu calls it Partition Editor)
But you won't be able to run it from Ubuntu (since you can only resize unmounted partition). You can run it from  the Ubuntu LiveCD, but I recommend getting  the  [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") or  [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php")

---

