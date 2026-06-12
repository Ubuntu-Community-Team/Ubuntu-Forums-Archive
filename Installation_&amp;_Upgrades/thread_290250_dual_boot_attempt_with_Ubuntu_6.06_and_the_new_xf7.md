---
title: "dual boot attempt with Ubuntu 6.06 and the new xf7d"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-11-01
Hey folks!
I just downloaded the newly released [xfld iso]("http://distrowatch.com/table.php?distribution=xfld") from [distrowatch.com]("http://distrowatch.com/").
It's BEAUTIFUL! BUT.,After installing it onto hdb1, I had to reinstall GRUB to the MBR in order to boot to hda1!

Let me explain...
I have been running Ubuntu 6.06 (Dapper Drake) on my Ide hda1, and have been using Ide hdb1 as a storage drive.
I decided to erase hdb1 and install xfld, expecting to get a dual-boot option when rebooting.  Didn't happen!
I'm almost possitive that after installing xfld, Grub was rewritten to hdb1.

I now have two working OS's but I can only boot to one!  Can anyone understand what I'm getting at?
Here is my [B]fdisk -l
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2377    19093221   83  Linux
/dev/hdb2            2378        2482      843412+   5  Extended
/dev/hdb5            2378        2482      843381   82  Linux swap / Solaris

Disk /dev/md0: 1537 MB, 1537998848 bytes
2 heads, 4 sectors/track, 375488 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 1537 MB, 1537998848 bytes
2 heads, 4 sectors/track, 375488 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table[/QUOTE]
Can someone assist me with getting my dual-boot?
Thanks!

---

### Post by confused57 on 2006-11-01
Maybe you can use the live cd, or you might be able to boot into Dapper, to mount hdb1:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

What you could do once hdb1 is mounted is to open /boot/grub/menu.lst and note the entries to boot xfld...add an identical entry to your Dapper /boot/grub/menu.lst to boot xfld from your Dapper grub menu.

You could also get the xfld grub entry, if you can set bios to boot first to hdb.

---

### Post by randell6564 on 2006-11-01
> **confused57 said:**
> Maybe you can use the live cd, or you might be able to boot into Dapper, to mount hdb1:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

What you could do once hdb1 is mounted is to open /boot/grub/menu.lst and note the entries to boot xfld...add an identical entry to your Dapper /boot/grub/menu.lst to boot xfld from your Dapper grub menu.

You could also get the xfld grub entry, if you can set bios to boot first to hdb.
Thanks My friend!  I am going to give that a shot! just for the hell of it.,in case you spot something, here is my /boot/grub/device.map and following will be my /boot/grub/menu.lst which has no reference to hdb1.
> (hd0)	/dev/hda
(hd1)	/dev/hdb
> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by randell6564 on 2006-11-01
Hi confused57!
Well.,I THINK that I did what you suggested but to no avail!
I'm missing something; I know that it is not this difficult! lol!
I edited my Dapper (hda1) menu.lst after mounting hdb1 (xfld). It now is this:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

I added everything after "**END DEBIAN AUTOMAGIC KERNELS LIST**"
Next is my menu.lst from xfld (hdb1) of which I did not edit at all.
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-27-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
Still no dual-boot!  I can only boot to hda1.
Thanks!

---

### Post by randell6564 on 2006-11-01
"bump"

---

### Post by confused57 on 2006-11-01
What you can try is at the grub menu, scroll down to the xf7d entry, press "e" for edit, and change the root from (hd0,0) to root (hd1,0)...then I think you have to press "b" for boot.

If this works, you'll need to go into /boot/grub/menu.lst & change the entries:

title Ubuntu, kernel 2.6.17-10-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-386 
quiet
savedefault
boot

What you added looks correct, just need root (hd1,0).  I'm not familiar with the grub entry for xf7d...I'm not sure if "quiet"
should be on a separate line, or added to the line above, e.g.
initrd /boot/initrd.img-2.6.17-10-386 quiet

---

### Post by randell6564 on 2006-11-01
This is fricken CRAZY!  I went into my BIOS and all I had to do was change the Boot order from CDrom,Hd0,Hd1 etc...to CDrom,Hd1,Hd0!

I rebooted and NOW I have my dual-boot menu!  I Knew that it could not be that difficult! lol!  But I'm still a bit confused as to why I had to do this in the first place!  Never had to with all the past dual-boot installations!

Hd0 was always the original OS (with the boot order being hd0 THEN hd1) and hd1 came later.  When hd1 would be installed, it would automatically write GRUB to the MBR and I would have my dual-boot!
But this time I had to change the boot order; Weird!

Anyway, Thanks alot My Friend! And BTW, I recommend trying xfld. For me it is awsome!  I have always liked that translucent window effect that you get from 'Compiz', but could never get it installed properly on Dapper Drake using my ATI readon 9200 graphics card.  It works flawlessly on xfld!

---

### Post by confused57 on 2006-11-01
Good job figuring it out...sounds like it's working great.
I may have to download xfld & give it a go.

---

### Post by randell6564 on 2006-11-01
> **confused57 said:**
> Maybe you can use the live cd, or you might be able to boot into Dapper, to mount hdb1:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

What you could do once hdb1 is mounted is to open /boot/grub/menu.lst and note the entries to boot xfld...add an identical entry to your Dapper /boot/grub/menu.lst to boot xfld from your Dapper grub menu.

You could also get the xfld grub entry, if you can set bios to boot first to hdb.
Actually.,I believe that YOU figured it out for me in this post! eg.."if you can set bios to boot first to hdb".
So "Good job" to YOU My Friend! Thanks!

---

