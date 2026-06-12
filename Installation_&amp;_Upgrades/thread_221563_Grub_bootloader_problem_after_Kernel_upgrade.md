---
title: "Grub bootloader problem after Kernel upgrade"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by thort on 2006-07-23
Hi !

I'm running the new Dapper release. Today, I realized in the System Tray there was some upgrades available. I opened up Synaptic and did the upgrades.

The Kernel was upgraded. But, what a surprise! When restarting the computer the grub bootloader was updated, and the computer started up in Recovery Mode. After some time the boot halted at a prompt. I couldn't get further. I had no knowledge of which command to give.

So I had to force a restart of the computer in order to start up Linux in normal mode, tapping the arrow key in the bootloader. Then I had to edit the **menu.lst** file in order to make the bootloader start the way I want.

My question is: Was this a normal upgrade of the Kernel? Shouldn't the bootloader start whith the same startup option after the update as before? Otherwise there would be big problems for all Linux newbees.

---

### Post by ahallubuntu on 2006-07-23
Good question.  I had the same problem yesterday with my new Dapper Drake installation.  But, my install got hung up (not sure why) at the end doing the grub-install command and I had to re-boot the live CD and do that command by hand then hand-create a menu.lst file.  Is some other app that I didn't install supposed to auto-generate the menu.lst file?

If you didn't have the menu.lst file, I think Grub boots the /vmlinuz kernel, which is symlinked to the latest in boot/.  I'm surprised that isn't the default in the menu.lst file actually - that would make the most sense.  I copied my menu.lst file from somewhere else because I didn't have one and I needed to dual boot with Windows...

---

### Post by thort on 2006-07-24
Thanks ahallubuntu fo your reply!

It's interesting to hear thoughts about this topic. I have no problem now with my installation, but if someone have some more thoughts about the Kernel upgrade it would be welcome.

---

### Post by tarlos25 on 2006-08-03
I just received a kernel upgrade, and my grub was altered as well.  Both the menu.lst and menu.lst~ files have lost the location of my Windows partition.

---

### Post by avtolle on 2006-08-03
[http://www.ubuntuforums.org/showthread.php?t=199489&highlight=GRUB+boot+order](http://www.ubuntuforums.org/showthread.php?t=199489&highlight=GRUB+boot+order)
could be helpful. Please note the later posts, which discuss the fact that after updates to kernel, there is a change to GRUB. There is another thread I cannot currently locate that discusses this phenomonon in some detail. HTH.

---

### Post by tarlos25 on 2006-08-03
> **avtolle said:**
> [http://www.ubuntuforums.org/showthread.php?t=199489&highlight=GRUB+boot+order](http://www.ubuntuforums.org/showthread.php?t=199489&highlight=GRUB+boot+order)
could be helpful. Please note the later posts, which discuss the fact that after updates to kernel, there is a change to GRUB. There is another thread I cannot currently locate that discusses this phenomonon in some detail. HTH.

Good to know, but still extremely frustrating.  If something like menu.lst is going to be altered, at least alter it in such a way as to keep the existing information, or make a backup, rather than just overwriting the file AND the backup.  Either way, I'm making a backup somewhere completely out of that directory, and hopefully that one will be left alone.

---

### Post by Herman on 2006-08-03
You fellows should read the following thread. 

[What I Wish I'd Known -- Dual-Boot and the Ubuntu Potential User]("http://www.ubuntuforums.org/showthread.php?t=227300&highlight=herman")

I think it's great that you are using GRUB bootloader. :D 

You can make Windows boot by default by editing your menu.lst files, there are several methods, but avoid placing your Windows entry in the automagic kernels list. 

All the best, Regards, Herman :D

---

