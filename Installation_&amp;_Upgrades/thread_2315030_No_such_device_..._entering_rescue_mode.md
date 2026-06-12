---
title: "No such device ... entering rescue mode"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by duccnnd on 2016-02-25
I have a PC with Windows 8.1 pro installed on an SDD. It is running in BIOS/legacy mode.
I tried to install Ubuntu 15.10 on the HDD. I used boot-repair to make grub the default boot manager but when booting I got message: 

"error: no such device: [COLOR=#000000][FONT=Courier New]b504eba3-68d1-40a6-b1c2-97bde0cf9b92.
[/FONT][/COLOR]Entering rescue mode..."

So it seems grub is now my default boot manager, but the problem is that it could not find the device (which is sda3).
At the moment, I suspect Ubuntu cannot be booted from GPT drive (since my HDD has size of 3TB) in BIOS mode.
Link to boot-info: [http://pastebin.com/JG3f0T4y](http://pastebin.com/JG3f0T4y)

Please help me solve this problem.
Thanks

---

### Post by duccnnd on 2016-02-26
Ok, as I read here ([http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)), Grub2 should work fine with GPT partition so what I suspect is probably not the case. 
I followed this link ([http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204](http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204)) to re-install Grub but still got the same error.
Any idea how can I solve this? Please.

---

### Post by duccnnd on 2016-02-26
In the grub rescue, I tried "ls" and here's what I got:
*(hd0) (hd1) (hd1,gpt5) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1)*
It indicates that grub still found my sda3 (hd1,gpt3), doesn't it?
But when I tried **ls (hd1,gpt3) **I got "unknown filesystem".
I think this means my grub just could not work with GPT (contradicting with what I read as mentioned in my previous reply). 
I am really lost by now. Anyone know what should I do?

---

### Post by grahammechanical on 2016-02-26
What is the motherboard booting from? The SSD or the 3TB drive?

It should not make a difference as boot repair has installed Grub on to both drives. I see nothing much wrong with your Grub configuration file. It is pointing to the correct drive to load Windows 8 and the correct drive & partition to load Ubuntu.

GPT is part of the UEFI specification but it is backwards compatible with BIOS boot systems. With a UEFI motherboard & GPT partitioning we need a efi boot partition for both Windows & Linux to use (if installed in EFI mode). If installed in BIOS/Legacy mode there would be a bios boot partition.

With a BIOS motherboard & GPT partitioning we need a bios boot partition. Those are the vital differences.

You have installed Windows 8 on an SDD in BIOS/Legacy Mode. And you have installed Ubuntu on a 3TB drive also in BIOS/Legacy mode. Furthermore, the 3TB drive does have the necessary bios boot partition that goes with GPT partitioning for BIOS mode.

I see nothing wrong. Does Windows load? You should be getting a Grub boot menu with the option to load either Ubuntu or Windows. When you select Ubuntu you get a "no such device" error message. But what happens when you load Windows?

Grub uses hd = hard drive without distinguishing between IDE & SATA drives. (hd0) = first drive = SSD  = Windows 8. (hd1) = second drive = 3TB drive. (hd1,gpt3) = second drive, third partition = Ubuntu.

All that is as it should be. It has got me beat. Sorry.

Regards.

---

### Post by duccnnd on 2016-02-26
Thanks for your answer grahammechanical.

When I boot my PC, it goes directly to the "no such device ..." error and there is no boot menu to choose the OS. As a result, I could not boot to Windows neither. 
Also as you pointed out about the hd0 and hd1. As I see in my boot-info, root is always set to [COLOR=#333333][FONT=Consolas]root='hd0,gpt3'. 
[/FONT][/COLOR]However shouldn't it be 'hd1,gpt3' since I installed Ubuntu on the second drive? If so, how can I fix it?

---

