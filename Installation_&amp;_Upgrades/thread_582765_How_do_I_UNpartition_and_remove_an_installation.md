---
title: "How do I UNpartition and remove an installation"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mperedithe on 2007-10-20
I installed ubuntu a second time on my laptop because I can't get the sound working or printer working.  anyhow I set it up by partitioning the harddrive so that I wouldn't lose my previous installation in case I solved the problem.  How do I uninstall the second installation and configure my hard drive back to one solid unit.

---

### Post by Arenlor on 2007-10-20
I tried this, my short answer, you don't, my long answer, boot using an install CD then open a terminal and "sudo fdisk -l" if you see stuff like /dev/sda1 listed "umount /dev/sda" those (no number needed) I'm guessing you don't have a Windows or any other partition. Move your working partition (the one you want to keep) to the front (you just delete the rest, keep your swap though, do NOT delete your swap, remember, swap stays) then after you have deleted the partitions you do not want and have moved the one you want to the front (move/resize, just resize it to include all of the other ones old space) you tell it to apply changes, if you have any error while doing it try it again but along each step of the way (especially right after having launched gparted) run the umount again on the partitions.

---

### Post by mperedithe on 2007-10-20
Thank you for your reply.  Unfortunately I don't understand enough about ubuntu or linux for that matter to know how to perform your instructions.  So let me ask this ... is there a way to backup my settings and files so that I could just reload the OS and then restore my stuff or would the restoration reconfigure the partition?

---

### Post by Arenlor on 2007-10-20
If you backed them up to a disk or to something online then you could just format it. But no there seem to be a lot of complaints about it not letting you do this sort of thing simply.

---

### Post by ihcnet on 2007-10-20
You might want to back up the information saved on your windows partition before starting this process, just in case you run into any problems.You should be able to access the files on your Windows partition by mounting it in your Ubuntu partition and transferring the files off. If you don't know how to mount the partition, simply look here [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty). 

Grab a linux live CD, the Ubuntu one works fine and boot using it. After it boots up, use gparted to erase the partitions that are being used by Ubuntu. Then, resize the ntfs partition that windows is on to fill the entire hard disk. Now, you'll need to repair the mbr because grub won't work anymore with Ubuntu gone. Grab a Windows install CD, and use it to bring up the recovery console (should be as simple as booting the CD and then pressing 'R' when it prompts you to). Finally, run fixmbr at the prompt in the console and it should fix your mbr.

---

