---
title: "How do I make a partition active?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by popophobia on 2007-12-15
Hi,
I've recently installed another copy of Ubuntu on the same drive (different partition though) and after the set up, it installed GRUB onto my drive. The configure for Grub now lies in the new partition along with the new linux install.

Now I want to reactive the old partition (i.e.: using grub settings from the old system) and delete the new one (experimental install). How do I go about doing that?

---

### Post by Herman on 2007-12-15
You just need to re-install GRUB from your old system to MBR instead of the GRUB from your new system.
Here's a thread where that's already explained, [HOW-TO install boot loader from Ubuntu]("http://ubuntuforums.org/showthread.php?t=609548")
If you aren't sure after looking at that thread, don't be shy to ask a few questions and I or someone here will help you.

Regards, Herman :)

---

### Post by popophobia on 2007-12-15
Thanks for the help. I tried working with GRUB as you suggested. But I get this error
```

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```

And GRUB still boot from the first partition (hd0,0), I want to activate (hd0,2) though.

---

### Post by Herman on 2007-12-15
>          You just need to re-install GRUB from your old system to MBR instead of the GRUB from your new system.You did a good job installing GRUB to the boot sector of your Ubuntu partition, and the 'error' you got was normal for installing GRUB to a partition, only because the stage1_5 isn't installed when installing to a partition.

Try replacing 'setup (hd0,2)' with 'setup (hd0), that will install GRUB to your MBR in your first hard disk, that's what you need to do.

Regards, Herman :)

---

### Post by popophobia on 2007-12-17
Thank you so much. I got everything working now.

Just one more question on GRUB: can I get GRUB to recognize a USB CD-ROM and boot from there (ie. LiveCD)? My BIOS doesn't allow direct boot from USB ports, and my internal CD-ROM is broken. I used to install Ubuntu through the net, but it'd be nicer to get GRUB to boot from USB.

Thanks for all the help.

Best regards,
popophobia

---

### Post by Herman on 2007-12-17
> Just one more question on GRUB: can I get GRUB to recognize a USB CD-ROM and boot from there (ie. LiveCD)? My BIOS doesn't allow direct boot from USB ports, and my internal CD-ROM is broken. I used to install Ubuntu through the net, but it'd be nicer to get GRUB to boot from USB. I don't know, it all depends on your particular computer and how the motherboard was made and what BIOS you have. 

I discovered I could boot my Acer 3003WLMi Notebook with GRUB in the MBR and then use a GRUB 'chainloader' command to boot another copy of GRUB or Syslinux in a partition in my USB drive. I was surprised that worked when I tried it, because before that I didn't know that computer could boot anything in a USB device.
I have also read that you can often tell if a computer has the ability to boot a USB device if you can press either the F8 or F12 keys during boot-up and get a menu of bootable devices to choose from. That didn't seem to be the case with my notebook, so I didn't expect it to be able to boot a USB device at all.
Then one day I was poking around in the BIOS, looking for some other settings and exploring in there when I discovered that the option for an F8 boot menu was there alright, I just hadn't enabled it. 
In one of my other computers it was enabled by default. So it is worth trying hard and having a really good look to see if your computer really can boot a USB or not, and it's worth trying GRUB anyway, even if you don't think it will work.

Now that you have GRUB in the MBR of your first hard disk, you can plug in your USB device and boot your computer to the GRUB menu.
When you get to your GRUB menu, press your 'C' key for a GRUB Command Line Interface. If you want to go back to your GRUB menu at any time, either press 'Esc' to go back, or else press 'Ctrl'+'Alt'+'Del' to reboot.
At the command Line Interface, you can experiment with GRUB commands. In most computers GRUB is 'interactive'. In other words, GRUB will type answers back to you (give you feedback).
So you can ask GRUB what hard disks GRUB can 'see', by typing 'root (hd' and pressing 'TAB' once or twice. GRUB will tell you something like (hd0) (hd1). That means GRUB can 'see' two hard disks, and one of them might be your USB device.
I have already explained quite a bit about how to get started using GRUB's Command Line Interface in my website's GRUB Page. If you try some of the tricks explained in there you'll soon get the idea and you should be able to boot almost anything with GRUB. Here's the link:  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

The problem you are facing though, is you are not only trying to boot a USB device, but it's a CD-ROM drive. I don't know if it's possible to boot a CD-ROM drive from a hard drive, even though it is common practice to boot a hard drive from a CD-ROM. You can try it though.

What I do know for sure is, we can copy the files from a Ubuntu CD to a partition in a USB flash memory stick and boot that and run it as a Live CD and install from it. 
Here is a link from the Official Ubuntu Wiki about how that, [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Regards, Herman :)

---

