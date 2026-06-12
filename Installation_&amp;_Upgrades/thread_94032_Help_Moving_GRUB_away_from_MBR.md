---
title: "Help: Moving GRUB away from MBR"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by thtan on 2005-11-23
I installed Ubuntu on one hard disk and kept my WinXP on a seperate hard disk. I was a newbie when i installed ubuntu (and still is!). Although i got GRUB to run fine and allows me to select which OS to boot each time, i found out that whenever i remove my hd with ubuntu installed, it gave me a grub error21 or error17.

Now, i'm not sure what's happening here. I just wanted my machine to allow me to boot into WinXP even if my ubuntu hd isn't plugged. And if i really need to run ubuntu, it will allow me with the options just like GRUB did. I Read some threads mentioning moving GRUB from the MBR into the linux partition (i guess i'm right here, correct me if i'm wrong), but didn't quite understand how they did it.

Anyone mind to help? In Dummies terms please... Thanks.

---

### Post by yesplease on 2005-11-23
In rescue mode you can put grub where you want [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode)


In your case I would put grub on floppy. 
In paragraph 8.6 you use /dev/fd0 (floppy) instead of /dev/hda. 

AFTER that you can remove your ubuntu disk and restore the windows mbr with the windows install CD.

---

### Post by dcstar on 2005-11-23
[QUOTE=yesplease]In rescue mode you can put grub where you want [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-rescuemode)


In your case I would put grub on floppy. 
In paragraph 8.6 you use /dev/fd0 (floppy) instead of /dev/hda. 

AFTER that you can remove your ubuntu disk and restore the windows mbr with the windows install CD.[/QUOTE]
Or install Grub fully on the Windows drive, then it won't matter if the Linux drive is plugged in or not.

---

### Post by thtan on 2005-11-24
yesplease, how do i restore the windows mbr using windows install disk?
Anyone?

---

### Post by kaamos on 2005-11-24
I have a vague idea that you use the cd to boot to windows rescue terminal (or something like that) and use the command "fixmbr".

But I bet google knows this better than I do. :P

---

### Post by dcstar on 2005-11-24
[QUOTE=kaamos]I have a vague idea that you use the cd to boot to windows rescue terminal (or something like that) and use the command "fixmbr".

But I bet google knows this better than I do. :P[/QUOTE]

IIRC it used to be "fdisk /mbr", but it could be different now........

---

### Post by manicka on 2005-11-24
[QUOTE=kaamos]I have a vague idea that you use the cd to boot to windows rescue terminal (or something like that) and use the command "fixmbr".

But I bet google knows this better than I do. :P[/QUOTE]

Yes that's correct, boot into the recovery console and run the fixmbr command

---

### Post by yesplease on 2005-11-24
With the windows XP install CD you can go into rescue mode. 

Commands that are applicable to this situation are fixmbr, fixboot and if your boot.ini is invalid you can use bootcfg (/list and /rebuild) in the windows repair mode.

However dont misuse this information, if you do not know what you are doing search for a windows FAQ first with these terms as keywords. (fdisk /mbr is for win98, but check this before using it)

No, it is not very hard :) Tell us if it worked or if you  need more info, good luck.

---

### Post by thtan on 2005-11-28
Hi, people, thanks for the reply.

Due to my foolishness, i installed a second windows onto my hd.
Here's what i did

1) set bios to boot cd-rom, place winxp install disc into cd-rom, boot
2) the installation disc ran setup (i wonder where can i choose rescue mode???)
3) installed winxp

When it was ready to run, i was suprised to find that i had two bootable windows on my hd. the folder names were [windows] and [windows.0], as expected. So glad that at least i can still boot into my "old winxp" and the settings were still fine. I just have to remove the [windows.0] folder and remove some lines on boot.ini. (Did i did sth wrong here??)

Now, ubuntu is left in the dark since i didn't reserve any method for it to boot yet. should i juz follow the method outline above? (section 8.6 of link given by yesplease)

---

### Post by bwog on 2005-11-28
With the method in the starterguide you can put grub where you want, /dev/hda, /dev/sdb or even /dev/fd0. When you write grub to the mbr of the disk, it will overwrite the windows mbr, this is normal.

Yesplease also said that you have to know what you are doing if you use the windows rescue disk (search for a windows tutorial first). When things do not work the first time with grub, they can almost always be repaired.

---

