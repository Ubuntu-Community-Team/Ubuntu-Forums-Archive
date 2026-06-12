---
title: "Dapper Hosed my MBR"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by hansonc on 2006-06-07
Background info:
2 HDDs 
Primary Boot Disk SATA drive mounts as /dev/sda holds both WinXP and Linux
Secondary Disk ATA Drive mounts as /dev/hda

Well I had a dual boot situation with Windows XP Home and a Knoppix install that worked but after playing with the Dapper live CD I decided maybe I'd take the time to get my wireless working under that instead (It just never wanted to work under the Knoppix install).

The install went fine until it rebooted.

Grub was miss configured so nothing booted.  I'm able to change the boot script to boot Ubuntu correctly (it has the wrong drive in the script) but nothing I do can get me booted into Windows.

Any ideas?

---

### Post by Herman on 2006-06-07
Firstly, for other people who may be reading this and are worried about their MBR, thye can back up and restore thier MBR if thye want to this way, with any live CD like Dapper or Knoppix, and a floppy disk or a USB disk or CD, just adapt the following to your needs.

*You may need to adapt some of these commands with the correct name for your hard drive if you have two, and one is sata. *> **Back Up MBR with Dapper ubuntu-6.06-desktop-i386.iso before installation begins.**

To USB disk:

1) Plug in USB disk cord or check to see that it is already plugged in.

2) Boot ubuntu-6.06-desktop-i386.iso

3) Choose Start or Install Ubuntu

4) After boot-up, USB disk icon(s) should appear on the desktop.

5) Open a terminal (Applications, Accessories, Terminal)

6) [code] sudo dd if=/dev/hda of=/home/ubuntu/WINMBR.img bs=446 count=1[code]

7) 1+0 records in
   1+0 records out
   446 bytes copied,  4.3e-05 seconds, 10.4 MB/s

8) Open /home/ubuntu directory, locate file named WINMBR.img

9) Open USB drive (FAT32 partition), drag and drop WINMBR.img there somewhere.

10) Carry on with Ubuntu Install.

11) **Restore command**: [code] sudo dd if=/home/ubuntu/WINMBR.img of=/dev/hda bs=446 count=1[code] The file must be copied to the /home username directory of course, before issuing the command, or modify the command.
 
Now, if you want to fix GRUB, try using GRUB from the command line interfaces to search for your Linux kernels. You should also be able to boot Windows from Grub's command Line quite easily. Record your information, then open /booy/grub/menu.lst. and edit that with the same commands that worked in CLI mode.  [Click here for more info]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

If you are in a hurry, or just want to do things the easy way for now, and postpone the real job until later, you can boot with GAG Boot Manager. More info on how to use GAG boot Manager, [click here]("http://users.bigpond.net.au/hermanzone/p12.htm")
GAG will certianly boot Windows for you without a problem. It would be a good idea to always make a GAG CD or floppy disk before performing any Linux install if they jave anything urgent in Windows.

I hope something here will help. :grin: Regards, Herman

edit: I see you have Ubuntu booting, but just want to boot Windows, if GRUB CLI doesn;t work, and GAG Boot Manager doesn't work, mount Windows in LiveCD and check Windows boot files are all there and okay. (As shown in fig3 on [this page here]("http://users.bigpond.net.au/hermanzone/p6.htm").)

---

### Post by hansonc on 2006-06-07
Thanks a ton Herman.  GAG did the job, now I can get to work at getting things working correctly. 

Thanks again!

hansonc

---

### Post by Herman on 2006-06-08
That's good, it makes me happy to read that something helped. If you need more help and/or more specific help be sure to post again.
:grin: Regards, Herman

---

