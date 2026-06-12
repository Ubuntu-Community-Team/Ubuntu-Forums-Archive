---
title: "Moving wubi"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by vivakh on 2011-07-11
Hi guys, & girls too :)

I need some advice and help one something. As the title says, i need help to move a wubi install.
I have installed natty using wubi one my work computer. I now want to move this wubi install and make it a full install on my home computer. Main reason I installed it on my work computer was to get in all the updates and load the software that i need, for my connection speed at home is slow and it would take a while.

My home set up is:

1 160GB HD (sda); With Ubuntu 11.04; not partitioned (Boot loader installed to this drive, and this drive is first hard drive in BIOS)
1 160GB HD (sdb); Partitioned 60GB with Win7, 100GB for data

Now i want to move my wubi from my work computer to my home computer, onto sda. I don't care for the current install on sda, it can be deleted. I don't want anything happening to sdb though, as it has most of my data on there. The boot loader location and everything else should remain exactly the same as above, but instead of the current installiation on sda, i need the wubi install to go there. How can i go about doing this? My current wubi size is 11GB.

---

### Post by Mark Phelps on 2011-07-11
The instructions for "moving" a Wubi installation are documented in the linked Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by vivakh on 2011-07-11
Thanks for replying Mark. I checked the link you posted and the only thing close to my query on there was, [SIZE=1][COLOR=Black][https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)[/COLOR][/SIZE]

From there, i was pointed to here, [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

From what i gather from that information, wubi needs to be installed on the computer that you want to move onto. Wubi is installed on my work system and my home system does not have wubi on it.
Do you think i should install wubi on my home computer in sdb and replace the root.disk file, and then try the move?

---

### Post by vivakh on 2011-07-11
Anyone? I really would like to try it this afternoon when i get home.

---

### Post by Frogs Hair on 2011-07-11
If there are files you need from your work computer copy them on a removable device and add them to your home installation .

It reads like you want copy the entire Wubi configuration from your work computer , install it in Windows on your home computer and move it to its own partition . Correct me if I'm wrong . I think moving files to a different installation would be much easier .

---

### Post by vivakh on 2011-07-11
I would like the current wubi to be moved to my home computer, but not as wubi, as a full installation. I have all current updates and software i need on the wubi, so i want to transfer the entire thing to my home computer, replacing the current ubuntu 11.04 on the home HD with the wubi file from my work HD

---

### Post by Frogs Hair on 2011-07-11
> **vivakh said:**
> I would like the current wubi to be moved to my home computer, but not as wubi, as a full installation. I have all current updates and software i need on the wubi, so i want to transfer the entire thing to my home computer, replacing the current ubuntu 11.04 on the home HD with the wubi file from my work HD

Try a forum search because there are others who have wanted to do something similar and I think they were successful . I remember two threads for sure .
If you don't find an answer try posting on this thread. 

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by Frogs Hair on 2011-07-11
Take a look at this link .[http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)

---

### Post by vivakh on 2011-07-12
Thanks for replying. I got through with it though. What i did was copy the root.disk from my work pc onto my external HD. Then, when I got home, I installed wubi in my win7. Re-booted, completed the install, re-booted again, then in the grub menu, i pressed "e" on the first entry, and took note of the following:
"set root= sdb, msdos2" and there was another line with, "linux/boot/vmlinuz-blah blah blah root=UUID=A string of numbers and letters."

I took note of sdb, msdos2 and the UUID. Then i rebooted into windows, and copied my root.disk from my external HD into the disks folder of the ubuntu install folder. Then i rebooted, and went to boot into ubuntu. Grub took a little longer to show up, but it did eventually. Once there, i hit "e" on the first entry again, then i saw that the two things i noted before had changed. So i changed them back to the values they were before, including the UUID. And i also deleted the line that begun with "search --no floppy blah blah blah" then hit ctrl-x, and my wubi booted right up with the wubi from my work PC. When i was in, i went to the terminal, ran "sudo update-grub" and updated the boot loader. Now all that is done, i followed the auto migration instructions [here]("http://ubuntuforums.org/showthread.php?t=1519354") and everything went smoothly.

Thank you all for your help :D

---

