---
title: "install from scratch, package ok, but grub failed."
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by Crishna on 2010-08-20
[FONT=Tahoma][SIZE=3]Hi dears Ubuntu Users.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]I am relativly new to Linux, 2 weeks ago, i tried my first linux installation with Fedora distro. using the live 64 usb boot version, everyhing looked fine. BUT i had issues with WINE so by recommendation, i went with Ubuntu and flushed Fedora.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]So, technicaly, the install works fine, during the process of installing from the live usb 64 bit 10.4 ubuntu. BUT at the end, when installing GRUB, it just simply failed! thats's a shame for me![/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]what i can tell you is the following. (thats what i think is my problem, but i need some expert help tho!)[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]my motherboard is a ASUS, im using 3 HDD 500GB sata2 drive, configured as a RAID in the bios, strip 0. so it presents to the OS one partition of 1.5 TB. Fedora detected it correctly, and was able to install grub on that.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]now, during the Ubuntu install, i can chose to pick up a partition that was not used on my 1.5 TB ( i reduced my partition to 1TB and allowed 500GB to linux). Windows 7 reside on the first partition. on this disk, partition 1 is a 100MB windows bootmanager. partition 2 is windows 7 itself 1TB. [/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]during the install of ubunto, i tell him to create a / partition, using 480GB as the third partition, and i created a 4th partition as a swap for linux.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]the install process the information, install the DATA on the third partition... BUT grub, can't !!! it failed... it keep looking for a /dev/sda disk... when installing GRUB, i can chose the drop down, for the 1.5TB disk, and when i press OK, he just simply try again to access /dev/sda disk... which is full of course and within a BIOS raid.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]so i just bypassed the grub install... and the anaconda completed the install process. at the end, he just warned me to install a boot solution. [/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]so i rebooted the computer... and sudenly, i got into GRUB command prompt... i managed to understand how to boot from there, my windows 7... but still, i can't or don't know how to create a menu.lst... anyways... after some more reading about grub, i was able to get my vmlinuz shown on the prompt, using some command and settings my root, [/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]grub > root (HD0,2)/     <pressing tab, shows me my availlable files, i can see the linux structure.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]grub > root (hd0,2)/    <by pressing enter, it tells me my partition mode, etc..[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]then i do :[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]grub > kernel (hd0,2)/vmlinuz[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]grub > boot[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]but this failed, i know im missing an operand, which is root=/dev/ whatever drive im using.. without doing root=/some dev device it tries to start on /dev/sda but that failed.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]someone can tell me, what is the /dev/device file that i mimight be able to use ? or maybe there is manual option i can use at the start of the ubunto install boot process ? or some comannd line within anaconda i could use ?[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]anyways, yesterday, i did went back into windows 7, and deleted the last 2 partition created for ubuntu, and only kept the first 2 partition for windows, and using windows 7 repair, i removed grub and kept only the bootmgr of windows.[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]i would appreciate some thoughts on this, and im availlable to test whaetver people are telling me... i can try back and fourth as im pleased![/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]best regards, [/SIZE][/FONT]
[FONT=Tahoma][SIZE=3][/SIZE][/FONT] 
[FONT=Tahoma][SIZE=3]Francois Desfosses, Alias Crishna the bald Vorise[/SIZE][/FONT]

---

### Post by Crishna on 2010-08-20
later, i will post detailed messages, since i will have to redo the procedure from start!

---

