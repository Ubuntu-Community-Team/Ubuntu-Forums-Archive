---
title: "Quadruple Boot, Grub problem"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by MrBucket101 on 2008-09-27
I have Two versions of windows XP, Windows Vista, and Hardy Heron installed

this is the order in which i installed the OS' after partitioning

Installed Tiny XP to partion 3
Installed Tiny Vista to partiton 2
Then i ghosted back my school's installation of Windows XP
Then i finally installed Ubuntu onto an extended partiton containing a 2GB swap disk

I can access all of the Operating systems however, to boot into Tiny XP, I first have to select the Vista loader option in GRUB, and then it looks like another bootloader comes up, with the choice of earlier version of windows or Vista, if i choose Vista, it boots vista and if i choose earlier version of windows it boots Tiny XP.

I can directly boot my schools version of Windows XP through GRUB.

I would like to be able to get rid of the vista loader and simply boot each OS through GRUB.

i tried manually editing my menu.lst file and inserting a Tiny XP entry, basically all i did was copy the entry auto added for Vista and change (hd0,1) to be (hd0,2)

after i added the Tiny XP entry and i tried to boot into Tiny XP from grub i get this error "bootmgr is missing, press ctrl+alt+delete to restart"


here is the output of fdisk -l
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5489    41496808+   7  HPFS/NTFS
/dev/sda2            5490        6878    10490445    7  HPFS/NTFS
/dev/sda3   *        6878        8265    10482412+   7  HPFS/NTFS
/dev/sda4            8265       12922    35206447+   5  Extended
/dev/sda5            8265       12644    33109902   83  Linux
/dev/sda6           12644       12922     2096451   82  Linux swap / Solaris

```

here is my menu.lst file
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d807e71-d9c8-43a9-abde-41691143c30e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d807e71-d9c8-43a9-abde-41691143c30e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,4)
#kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Tiny Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

#user added entry
title		Tiny XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```

---

### Post by MrBucket101 on 2008-09-28
bump

---

### Post by meierfra. on 2008-09-28
Try this:

Copy the files "ntldr", "ntdetect.com" and "boot.ini" from the Tiny Vista partition  to Tiny  XP partition. 

Boot from an XP CD and press "r" to go to the Repair console.
Type 

```
map
```

 to figure out the drive Letter of your Tiny XP partition. Then type

```
fixboot X:
```

where X is the drive letter of the Tiny XP partition. Finally type"exit" to reboot. Choose "Tiny XP" at the grub menu and hope for the best.

---

### Post by Mark Phelps on 2008-09-29
If my multi-boot system is any indication, here's your problem ...

When Vista is installed after XP (to the same hard drive), it insists on writing its new bootloader files (NOT NTLDR) to the XP partition, and creating a loader menu containing both XP and Vista, with Vista being the default.

After that, any attempt to boot into either Windows OS brings up the Vista-created loader menu.

If tiny Vista is really Vista, you won't find any NTLDR files in it's partition because Vista uses an entirely new loader system.

Also, if you remove or wipe the XP partition, Vista won't boot anymore -- because you've effectively removed Vista's boot files.

Not saying there isn't one, but I've not been able to find a way around loading the new Vista loader menu to get into XP or Vista -- and I'm using GRUB to boot into several different Ubuntu installations as well.

---

### Post by MrBucket101 on 2008-09-29
> **meierfra. said:**
> Try this:

Copy the files "ntldr", "ntdetect.com" and "boot.ini" from the Tiny Vista partition  to Tiny  XP partition. 

Boot from an XP CD and press "r" to go to the Repair console.
Type 

```
map
```

 to figure out the drive Letter of your Tiny XP partition. Then type

```
fixboot X:
```

where X is the drive letter of the Tiny XP partition. Finally type"exit" to reboot. Choose "Tiny XP" at the grub menu and hope for the best.

will this overwrite grub in the MBR?

---

### Post by meierfra. on 2008-09-29
> When Vista is installed after XP (to the same hard drive), it insists on writing its new bootloader files (NOT NTLDR) to the XP partition, and creating a loader menu containing both XP and Vista, with Vista being the default.

You are right. All the Vista and XP boot files files should be on the XP partition. 

I got confused since the OP said  he can boot from the Tiny Vista partition but not from the Tiny XP partition. It should be the other way around. 

MrBucket101,  are you sure that "title Tiny Vista" gives you the Vista Boot Menu and that "Tiny Vista" is on (hd0,1)"?


So instead of moving "ntldr, ntdetect and boot.ini" from the Vista partition to the Tiny XP partition, you  need to move "bootmgr" and the folder "boot" from the  Tiny XP partition to the Vista partition.

 > Not saying there isn't one, but I've not been able to find a way around loading the new Vista loader menu to get into XP or Vista
I'm booting both Vista and XP directly from my Grub menu.



Also instead of moving boot files to add "XP" and "Vista" to the Grub menu, one can use  "EasyBCD" (see my signature) to add Ubuntu to Vistas Boot Menu.

---

### Post by meierfra. on 2008-09-29
> will this overwrite grub in the MBR?

No. It will only  change  the boot sector of the XP partition. (To overwrite the MBR you need to use "fixmbr")

---

### Post by Mark Phelps on 2008-09-29
meirfra:

"His" problems are similar to mine in that the only way I could select the Windows OS was to boot into the Vista-provided menu and select either Vista or the "earlier version of Windows( i.e., XP).

I also messed around with tweaking the GRUB entries but without success. I was convinced that my GRUB entries for the two different Windows OS's were correct -- they just didn't work as I had hoped.

I'm monitoring this thread to see what's different about the solution to "his" problem (not being able to boot directly to individual Windows versions using GRUB) that might fix my problem as well.

---

### Post by lemming465 on 2008-09-29
I'm not real clear on why the nested boot menu's is such a big issue.  Personally, I just live with them (grub on MBR; multiple windows installs use XP or Vista menu).

I tend to believe Mark Phelps' diagnosis.  What I think you'd need to do to fix it is run OS-specific boot repairs with just the partition you are repairing set as active.

I'd start by unsetting the boot flag on sda3, setting it on sda2, and running a Vista boot repair.  If that worked, I'd unset the boot flag on sda2, turn it back on sda3, and run an XP boot repair.  After that, there is a fair chance your grub menu's will work as intended.  There will still be XP or Vista boot menu's, but you could set the timeouts to zero to avoid seeing them.

```
sudo parted /dev/sda set 2 boot on
```

should change the active partition from 3 to 2, for example.

---

### Post by MrBucket101 on 2008-09-29
> **meierfra. said:**
> Try this:

Copy the files "ntldr", "ntdetect.com" and "boot.ini" from the Tiny Vista partition  to Tiny  XP partition. 

Boot from an XP CD and press "r" to go to the Repair console.
Type 

```
map
```

 to figure out the drive Letter of your Tiny XP partition. Then type

```
fixboot X:
```

where X is the drive letter of the Tiny XP partition. Finally type"exit" to reboot. Choose "Tiny XP" at the grub menu and hope for the best.

You are amazing, this fixed my problem, THANKS!:D


> **Mark Phelps said:**
> meirfra:

"His" problems are similar to mine in that the only way I could select the Windows OS was to boot into the Vista-provided menu and select either Vista or the "earlier version of Windows( i.e., XP).

I also messed around with tweaking the GRUB entries but without success. I was convinced that my GRUB entries for the two different Windows OS's were correct -- they just didn't work as I had hoped.

I'm monitoring this thread to see what's different about the solution to "his" problem (not being able to boot directly to individual Windows versions using GRUB) that might fix my problem as well.

see my above quote

> **lemming465 said:**
> I'm not real clear on why the nested boot menu's is such a big issue.  Personally, I just live with them (grub on MBR; multiple windows installs use XP or Vista menu).

I tend to believe Mark Phelps' diagnosis.  What I think you'd need to do to fix it is run OS-specific boot repairs with just the partition you are repairing set as active.

I'd start by unsetting the boot flag on sda3, setting it on sda2, and running a Vista boot repair.  If that worked, I'd unset the boot flag on sda2, turn it back on sda3, and run an XP boot repair.  After that, there is a fair chance your grub menu's will work as intended.  There will still be XP or Vista boot menu's, but you could set the timeouts to zero to avoid seeing them.

```
sudo parted /dev/sda set 2 boot on
```

should change the active partition from 3 to 2, for example.

the nested boot menu to me was an annoyance, and the only way i could access Tiny XP was through a nested boot menu, that is fixed now

Now that i have solved that issue, i am going to see if i can run a fix boot on the vista partition with a vista disc, to see if that will get rid of the nested menu, therefore eliminating the pesky bastids

Thanks for the advice

---

### Post by meierfra. on 2008-09-29
> i can run a fix boot on the vista partition with a vista disc, to see if that will get rid of the nested menu,

Fixboot won't help.  I suggest to use EasyBCD to edit your Vista Boot menu. 

But if you want, I can show you how to do it from the Vista command line.

---

### Post by MrBucket101 on 2008-09-30
> **lemming465 said:**
> I'm not real clear on why the nested boot menu's is such a big issue.  Personally, I just live with them (grub on MBR; multiple windows installs use XP or Vista menu).

I tend to believe Mark Phelps' diagnosis.  What I think you'd need to do to fix it is run OS-specific boot repairs with just the partition you are repairing set as active.

I'd start by unsetting the boot flag on sda3, setting it on sda2, and running a Vista boot repair.  If that worked, I'd unset the boot flag on sda2, turn it back on sda3, and run an XP boot repair.  After that, there is a fair chance your grub menu's will work as intended.  There will still be XP or Vista boot menu's, but you could set the timeouts to zero to avoid seeing them.

```
sudo parted /dev/sda set 2 boot on
```

should change the active partition from 3 to 2, for example.



looks like i need help eliminating the vista loader

i tried booting into a vista DVD and going to repair but it told me that there was a problem in the way my computer booted and that it needed to be fixed to access the repair console...I'm afraid this will affect grub, what do you guys think i should do

---

### Post by meierfra. on 2008-10-01
Boot into Vista and open a command line as administrator:
Click on Start, type "cmd" and press "Ctr+Shift+Enter" 
or  if you prefer:  
Start->All Programs->Accessories and right-click on Command Prompt and select Run as administrator. 

To delete Windows from the Vista Boot Menu type:

```
bcdedit /delete {ntldr} /f
```

If this did not solve your problem, post the  output of

```
bcdedit 
```

Also  post the drive letters of the Vista and XP partition.

Did you ever verify that Tiny Vista is on /dev/sda2 and Tiny XP on /dev/sda3?
(It could be that the Vista boot files now are on  the XP partition, and the XP boot files on the  Vista partition. That shouldn't really cause a problem, but  it  might  have confused the "Vista DVD" and it might also confuse "bcdedit")

---

### Post by MrBucket101 on 2008-10-02
> **meierfra. said:**
> Boot into Vista and open a command line as administrator:
Click on Start, type "cmd" and press "Ctr+Shift+Enter" 
or  if you prefer:  
Start->All Programs->Accessories and right-click on Command Prompt and select Run as administrator. 

To delete Windows from the Vista Boot Menu type:

```
bcdedit /delete {ntldr} /f
```

If this did not solve your problem, post the  output of

```
bcdedit 
```

Also  post the drive letters of the Vista and XP partition.

Did you ever verify that Tiny Vista is on /dev/sda2 and Tiny XP on /dev/sda3?
(It could be that the Vista boot files now are on  the XP partition, and the XP boot files on the  Vista partition. That shouldn't really cause a problem, but  it  might  have confused the "Vista DVD" and it might also confuse "bcdedit")

It fixed it for the most part, after i ran the command and rebooted and selected Tiny Vista from grub, grub loaded vistas bootloader (weird text scrolled across the screen) and then vista loaded

its not the route i was hoping for (i'm too picky i've been told) but this works for me

once again, thanks for the great help :D:D

---

### Post by meierfra. on 2008-10-02
You might try

```
bcdedit /timeout 0
```

in the Vista command line and  see whether it makes a difference.

---

