---
title: "Grub Error 12"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by ep3w on 2007-06-04
I have feisty installed on a partition on my harddrive and just had to reformat the partition with windows and reinstall it.  Windows worked fine.  I reinstalled Grub using the ubuntu live CD and i can now boot to feisty but when i try to boot to XP i get Grub error 12.  Any idea how to fix this?

---

### Post by domer on 2007-06-04
I had the similar problem. Here is the fix.... load your "original" windows cd (I was using XP Pro) and boot your computer. After the cd loads, go to Recovery Console and type** fixmbr** followed by **fixboot**. 

[COLOR="Red"]**IMPORTANT:**[/COLOR] This will only help you log on to your XP partition if you need to save any important files. The above commands re-writes the Master Boot Recorder and thus you may have to reinstall Ubuntu and hope you don't get the same error message.

---

### Post by merlinus on 2007-06-04
I do not think you will need to reinstall Ubuntu, but you will have to restore grub after fixing the windows mbr.

You can do a search -- there are many threads here on how to do it from the live cd.

Here is one:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck!

-merlin

---

### Post by ep3w on 2007-06-05
I have tried using fixmbr before.  It worked to let me get into windows but then i could no longer get into ubuntu.  Then i would install grub again using the live CD and i was back where i started with the same grub error 12 when i tried to boot windows.  so it is like i can either use windows or ubuntu....i need a way to get them to both work using grub.  only ubuntu works in grub.  windows gives me the error 12.

---

### Post by confused57 on 2007-06-05
> **ep3w said:**
> I have tried using fixmbr before.  It worked to let me get into windows but then i could no longer get into ubuntu.  Then i would install grub again using the live CD and i was back where i started with the same grub error 12 when i tried to boot windows.  so it is like i can either use windows or ubuntu....i need a way to get them to both work using grub.  only ubuntu works in grub.  windows gives me the error 12.

It might help to post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

Just in case something changed in your partition numbering when you reinstalled Windows.

---

### Post by ep3w on 2007-06-05
Here is the output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6586    52902013+   7  HPFS/NTFS
/dev/sda2            6587        9729    25246147+   5  Extended
/dev/sda5            6587        9522    23583388+  83  Linux
/dev/sda6            9523        9729     1662696   82  Linux swap / Solaris

To better explain this....installing grub using a live CD allows me access to ubuntu via grub.  but trying to boot to windows gives me error 12.  using the windows recover with fixmbr allows me access to windows but grub no longer shows up so i cant get at ubuntu. i can access the windows partition in ubuntu.


Edit: I did have everything working at one point in time.

---

### Post by confused57 on 2007-06-05
You might want to post your menu.lst:
```
gedit /boot/grub/menu.lst
```

---

### Post by ep3w on 2007-06-05
Here is the menu.lst

##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e7954c1-c233-4e38-8ec7-f2f3c7aa942c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by confused57 on 2007-06-05
I believe your root should be (hd0,0)...that should work.

Added: Just in case, here's how to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
make your change, then quit & save.

---

### Post by ep3w on 2007-06-05
thank you!!! works perfectly!! i love these forums! couldn't have made the switch without them! :D

---

### Post by confused57 on 2007-06-05
> **ep3w said:**
> thank you!!! works perfectly!! i love these forums! couldn't have made the switch without them! :D

Thanks for the update...thought it would work, had my fingers crossed.   This forum and other Linux forums are what it will take to get more people to try Linux...it's a lot of fun and also comforting to know you have an option other than the  "mainstream"  OSes, which you have to actually pay hard earned money to use(not really own).  See you around.

---

