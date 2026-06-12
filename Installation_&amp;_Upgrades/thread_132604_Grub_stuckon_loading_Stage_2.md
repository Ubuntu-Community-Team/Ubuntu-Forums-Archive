---
title: "Grub stuckon loading Stage 2"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by kseise on 2006-02-18
After the recent kernel installation, my GRUM/menu.lst was rewritten incorrectly.
I have spent all last night and most of today trying to get back into my windows partition to get some of my work files.

My setup is as follows:
Windows XP on HDA1
Ubuntu on HDB1

The Windows portion my GRUB Menu.lst is as follows:
> 

title		Windows XP
	rootnoverify		(hd0,0)
	makeactive
	chainloader	+1
ALSO TRIED AS
root   (hd0,0)
makeactive
chainloader +1


On boot, GRUB loads stage one, and then can't seem to find Stage 2 and hangs.  When I launch find from the GRUB promp, it just hangs.

Anybody know how I can get this back operational?

---

### Post by kseise on 2006-02-18
Anybody?  I have a huge collection of shiny coasters now including:
Unlimate Bood CD
BartsPE
WinXP Boot disk
Win98 Boot disk

Nothing seems to work, I can't boot from the XP installation disk anymore either.

---

### Post by bearwood on 2006-02-19
I'm feeling for you brother. I too have been messing around for 2 days trying to get Ubuntu to dual boot with windows and it doesn't want to play nice. Thank god for knoppix at least that works.
The Ubuntu Grub installer sucks, it installs all nice but won't load to OS that IT wrote to the .lst file.
Looking at the forums it seems to be a major bug bear which is a pity cause Ubuntu is real nice system to use when it works. (I'm no programmer or hacker justa simple desktop user)

---

### Post by kseise on 2006-02-19
OK, lets try another approach, does anyone have a working grub/menu.lst for a setup like this:

Windows XP on HD0,0
Ubuntu on HD1,0
Swap on HD1,1

Or if I install Lilo is there a way to point it to my Windows installation?

---

### Post by de_doughboy on 2006-02-19
I'd use a DOS program called osl2000.exe boot manager. You can get it from [www.downloads.com](www.downloads.com) boot in dos then install osl2000 by running dosinstall.exe 
reboot your pc then select the partion you want to boot from. No need to change partion-active bits on the primary boot disk. There are others but this one is easy to use.

---

### Post by NoJock on 2006-02-19
I had a problem like this with mepis and found that my windows partition was hidden. Had partitioned with partition magic so it was easy with the recovery disks to unhide the partition.

Grub set for windows

title windows xp
rootnoverify (hd0,0)
chainloader +1 

this is all i have for windows as the first partition and it just works

here is my grub menu file

timeout 15
color cyan/blue white/blue
foreground ffffff
background 2f5178
gfxmenu /boot/grub/message

title MEPIS at hda3, kernel 2.6
kernel (hd0,2)/boot/vmlinuz-2.6.10 root=/dev/hda3 nomce psmouse.proto=imps splash=verbose vga=791 
initrd (hd0,2)/boot/initrd.splash 

title MEPIS at hda3, kernel 2.4
kernel (hd0,2)/boot/vmlinuz-2.4.29 root=/dev/hda3 nomce quiet splash=verbose vga=791 hdb=ide-scsi 
initrd (hd0,2)/boot/initrd.splash 

title windows xp
rootnoverify (hd0,0)
chainloader +1 

title Run MEMTEST to test system memory
kernel /boot/memtest86.bin

---

### Post by kseise on 2006-02-20
[QUOTE=de_doughboy]I'd use a DOS program called osl2000.exe boot manager. You can get it from [www.downloads.com](www.downloads.com) boot in dos then install osl2000 by running dosinstall.exe 
reboot your pc then select the partion you want to boot from. No need to change partion-active bits on the primary boot disk. There are others but this one is easy to use.[/QUOTE]
I like it.  I setup the bootloader on my other machine accidently.  I was only able to find the self extracting zip.  I couldn't fidn the dos version.  

Also, I don't have a floppy drive.  I will have to boot from a win98 setup disk.  My XP setup disk hangs at detecting hardware, then black screen of death.

---

