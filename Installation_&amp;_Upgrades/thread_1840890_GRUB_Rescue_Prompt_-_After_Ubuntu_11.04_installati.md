---
title: "GRUB Rescue Prompt - After Ubuntu 11.04 installation"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by neonitron on 2011-09-08
Hi guys,

I need some help. I installed Ubuntu 11.04 and after the installation completed I restarted my computer, and then grub now automatically goes into GRUB RESCUE prompt. 

Here is a summary of what I have done:

1 - Installed a fresh copy of Windows 7 using 50GB's on a Corsair SSD. Also, Windows 7 created a 100MB system reserved partition. I then left 10 GB's for Ubuntu 11.04.

2 - Booted from Ubuntu 11.04 disc. Used the manual partition manager and created 2 5GB logical partitions for Ubuntu (1 for Swap and 1 for root files EXT3). Chose /dev/sda/ for GRUB installation location. Then went through the Installion of Ubuntu 11.04 successfully. 

3 - Restarted the computer and now I receive the Rescue Prompt.

Cannot boot into Ubuntu or Windows because it looks like Grub is all wierded out and sending me to the rescue prompt.  


What are your recommendations or steps I should take to fix grub? I have not tried anything as of yet? Nor do I know any grub rescue commands that I can try?

Any suggestions are greatly appreciated!

Thanks,
Neil

---

### Post by masho95 on 2011-09-08
Just out of curiosity could you type "ls" at the rescue prompt and tell me what you get back? I'm having the exact same issue on my computer after upgrading from 10.10 -> 11.04

Also type "set" and see what comes back. Should tell you what the prefix and root settings are at.

---

### Post by neonitron on 2011-09-08
Hi masho95,

Just at work right now. Will definitely try tonight and post back.

Cheers,
Neil

---

### Post by YesWeCan on 2011-09-09
Grub rescue is not too bad...it means the grub boot program at the disk start is working fine but for some reason it cannot locate the rest of the grub files in /boot/grub in the Ubuntu root partition. There is a procedure here [https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting) for manually telling it and booting. :)

I notice you chose ext3. Any particular reason, ext4 is a more efficient fs. Also, 5GB is bare minmum for root because you'll probably only have 2GB for apps and user docs. Not a big deal if you are just experimenting. The swap doesnt have to be that big either....depends on your RAM size. Swap is overflow, virtual RAM.

---

### Post by neonitron on 2011-09-11
When I type ls I receive:

**(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (cd) (fd0) (fd1)**


When I type set I receive:

[B]prefix=(hd0,msdos5)/boot/grub
root=hd0,msdos5
[/B]

I'm going to try the recommended steps from YesWeCan now. 

Cheers, Neil

---

### Post by neonitron on 2011-09-11
Hey guys,

Just wanted to post back to say that I was able to resolve my grub problems by using this utility - Boot Repair.

1) Boot from LiveCD

2) Install the Boot Repair Utility (steps here - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )

3) Run the utility and perform the recommended repair.

4) Boots up fine again and I can select my Windows 7 or Linux OS.

Cheers, Neil

---

