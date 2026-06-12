---
title: "boot windows from grub problem"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by morphodone on 2005-02-13
i recently bought a new hard drive and basically messed up my boot 
configuration after i installed it...that's making a long story short

i was able to repair the entries for ubuntu in the grub menu from 
the unoffical starter guide for 4.10, but i have not been able fix the
ability to boot back into windows

currently i have three disks installed with this order listed in bios
1) 80gb ide (ubuntu and fat partition)
2) 80gb sata (windows)
3) 200gb ide (for storage)

what entries do i need to make in the grub menu list to
be able to boot a separate drive as above?  it seems like
i have tried everything possible...

thanks for any help

---

### Post by Cyhatch on 2005-02-13
Try [this](http://www.ubuntuforums.org/showpost.php?p=66608&postcount=2), if it's not the thing, maybe post the entries section of your menu.lst file? Somebody might help you out.  :-)

---

### Post by morphodone on 2005-02-14
yeah, i saw that in the guide but it didn't work

it's no big deal because i can boot into windows
by choosing to boot that disk in the bios

thanks

---

### Post by Cyhatch on 2005-02-14
Hrem. Is your Windows HD connected as the second one? Then you put *hd1,0* in menu.lst and it still doesn't work?

C'mon, post the menu.lst anyway! :-)

---

### Post by morphodone on 2005-02-16
here you go...the windows drive is the third drive on my system

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
makeactive
chainloader	+1

---

### Post by Cyhatch on 2005-02-16
[Try](http://www.webmasterworld.com/forum40/359.htm) this one, and the links they give.

If it still doesn't help, it would be useful if you told us (ahem) how *exactly* you boot into Ubuntu/Windows.

---

### Post by GilGalad on 2005-02-16
Does your /boot/grub/device.map file contain a line with:

(hd2)   /dev/sda

---

### Post by morphodone on 2005-02-16
yes...

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda


when i try to boot windows it says something about filesystem unknown
i'll get the exact error...

---

### Post by morphodone on 2005-02-16
here's the error - i had to write it down on paper and type it in
so it may not be exact 

 Booting 'Windows  NT/2000/XP'

root (hd2,0)
 Filesystem type unknown, partition type 0x7
Savedefault
makeacitve
chainloader +1

---

### Post by GilGalad on 2005-02-16
[QUOTE=morphodone]
title Windows NT/2000/XP
root (hd2,0)
savedefault
makeactive
chainloader +1[/QUOTE]

Can you modify this entry so that it reads:

```
title Windows NT/2000/XP
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1
```

I think grub needs "rootnoverify" in order to boot "unsupported OS".

Cheers.

---

### Post by GilGalad on 2005-02-16
[QUOTE=morphodone]here's the error - i had to write it down on paper and type it in
so it may not be exact 

 Booting 'Windows  NT/2000/XP'

root (hd2,0)
 Filesystem type unknown, partition type 0x7
Savedefault
makeacitve
chainloader +1[/QUOTE]
 Yes, use "rootnoverify" as I posted. The partition 0x7 is NTFS.

---

### Post by wallijonn on 2005-02-18
[QUOTE=morphodone]
 Booting 'Windows  NT/2000/XP'

root (hd2,0)
 Filesystem type unknown, partition type 0x7
Savedefault
makeacitve
chainloader +1[/QUOTE]

If you can access another W2KP machine you can:

1] Login as Administrator
2] Set folder Options -> unhide system files, unhide known file types
3] [COLOR=Red]Copy NTDETECT.COM, ntldr -> a:[/COLOR]
4] open a CMD window (Start -> Run -> cmd)
5] [COLOR=Red]attrib a:*.* -h -s [/COLOR]

Walk the floppy over to your PC

6] Boot with W2KP CD, Repair, Command Console
7] [COLOR=Red]Copy a:\*.* C:\*.*[/COLOR] (copy to C: root. It should be different for WXPP & WXPH).
8] exit (which will cause an automatic reboot)
9] Remove floppy & CD

Grub should now boot into W2KP.

10] Login into Administrator Account
11] Strat -> Run -> cmd
12] [COLOR=Red]attrib DETECT.COM +s[/COLOR]
13] [COLOR=Red]attrib ntldr +s[/COLOR]
14] Right click those two files, properties, set hidden

While I have not tested this trick on WXP, it did work for me on W2KP.

Maybe we should start suggesting that people copy NTDETECT.COM & ntldr to floppy (using the above method)...

If you do not have access to another W2KP machine you will have to format a floppy and use Ubuntu to copy the files from the W2KP install CD to the floppy. 

.

---

### Post by morphodone on 2005-02-18
[QUOTE=GilGalad]Yes, use "rootnoverify" as I posted. The partition 0x7 is NTFS.[/QUOTE]

ahh, yes thanks
with your suggestion and a little reading i got xp to boot
i also had to add "map"

here's my config - i think i'll save it for safe keeping for next time    :-) 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader	+1

---

### Post by wallijonn on 2005-02-18
Were the files NTDETECT.COM & ntldr in C:/windows? 

Please post your fix as there will be others doing a search for the same problem.

---

### Post by morphodone on 2005-02-18
[QUOTE=wallijonn]Were the files NTDETECT.COM & ntldr in C:/windows? 

Please post your fix as there will be others doing a search for the same problem.[/QUOTE]

There was a not a problem with the windows bootloader itself.  I could boot
into windows by making the primary drive in the bios my windows drive.  

However, I read that windows doesn't like to be a slave drive and prefers to be the master so you have to 'trick' windows by using the *map* option in grub menu.lst as well as 'rootnoverify' as GilGalad suggested.  

I'm sure your fix will work though if the bootloader gets trashed for windows itself...that's happened to me many times as well.  :-)

---

### Post by Kreiger on 2005-02-19
[QUOTE=morphodone]ahh, yes thanks
with your suggestion and a little reading i got xp to boot
i also had to add "map"

here's my config - i think i'll save it for safe keeping for next time    :-) 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader	+1[/QUOTE]


Hey,i had the same error 0x7, etc. But i only have one drive. i tried rootnoverify, and  it froze again.. how does map work? (will be googling for it after posting, figured i will try here anyway)

---

