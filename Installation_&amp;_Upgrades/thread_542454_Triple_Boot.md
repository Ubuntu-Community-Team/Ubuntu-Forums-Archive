---
title: "Triple Boot"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by rapsball4 on 2007-09-04
Hi,

I'm looking to set up a triple boot between Windows Vista Home Premium (64), Mandriva Spring 2007 Free, and Ubuntu Feisty, with Windows by itself on the primary drive and the two Linuxes together on the secondary.  I can always set up one or the other Linux and have it work, with GRUB having no problem running both.  I installed Vista first, then Ubuntu, then Mandriva, so it is currently using its boot loader.  As far as I can tell, Ubuntu is still installed on the one half of the disc, but even when I try to add things to the boot loader, I don't really get anywhere.  There is no hdb1 option - believe its the /swap for Mandriva.  hdb2 was just Mandriva again because I had forgotten which I had put in which half of the drive.  hdb3 and hdb4 both stopped trying to boot due to different error messages, but looked like they were also trying to boot Mandriva.  Is it possible to have two Linuxes on the same disk?  How do I go about setting this up so that all three OS's are there and are accessible through GRUB?

Thanks in advance.

---

### Post by logos34 on 2007-09-04
From what I hear Mandriva has a bad habit of not detecting other OS installations .  So you have to manually edit your config files afterward to add them.  But it should be able to coexist with ubuntu on the same physical disk just fine.  

Post your Mandriva /boot/grub/menu.lst.

Also, the output for fdisk:
[B]
# fdisk -[/B]l (lowercase L)


For instance, if ubuntu root partition were hdb3 and Mandriva root the second partition, then you might edit your Mandriva menu.lst to look something like this:

> 
timeout 5
gfxmenu (hd1,1)/boot/gfxmenu
default 0

title Mandriva
kernel (hd1,1)/boot/vmlinuz-2.6.17-14mdv BOOT_IMAGE=Mandriva root=/dev/hdb2 resume=/dev/hdb1 splash=verbose vga=788
initrd (hd1,1)/boot/initrd-2.6.17-14mdv.img

title		Ubuntu 7.04 Feisty Fawn
kernel	     (hd1,2)/boot/vmlinuz-2.6.20-15-generic root=/dev/hdb3 ro splash quiet
initrd	      (hd1,2)/boot/initrd.img-2.6.20-15-generic

title Windows Vista
root (hd0,0)
chainloader +1

---

### Post by rapsball4 on 2007-09-04
I fidgeted around some more and just some more problems even getting them installed and partitioned properly, so I hope that that part is actually taken care of again.  

This is what my  fdisk gives:

> 
Device            Start         End          Blocks             ID     System
/dev/hdb1          1       31389      252132111        83    Linux
/dev/hdb2       31390  60801      236251890         5     Extended
/dev/hdb5       31390  31898      4088511            82    Linux swap/Solaris
/dev/hdb6       60051  60801      6032376            82    Linux swap/Solaris
/dev/hdb7       31889  60050      226130908+     83    Linux


And the menu.lst file:

> 
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1, 6))/boot/gfxmenu
default 0

title Mandriva Spring 2007
kernel (hd1,6)/boot/vmlinuz
BOOT_IMAGE=Mandriva_Spring_2007 root=/dev/hdb7
resume=/dev/hdb6 splash=silent vga=788
initrd (hd1,6)/boot/initrd.img

title Windows Vista Home Premium
root (hd0,0)
makeactive
chainloader +1


So what do I change in the menu.lst file?

---

### Post by logos34 on 2007-09-04
> **rapsball4 said:**
> So what do I change in the menu.lst file?

So Ubuntu root looks to be hdb1, and Mandriva is last.  Paste this entry right after Mandriva:

> title Ubuntu 7.04 Feisty Fawn
kernel (hd1,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/hdb1 ro splash quiet
initrd (hd1,0)/boot/initrd.img-2.6.20-15-generic


Or use the 'configfile' format:
> title        Ubuntu 7.04 Feisty Fawn
configfile   (hd1,0)/boot/grub/menu.lst

I would use the latter if possbile because you won't have to edit the Mandriva menu.lst again after the Ubuntu 2.6.20-16 kernel upate.  You'll go through two menu screens, however, to boot ubuntu.

You don't need two swaps.  Delete one and then point the other's fstab to the remaining swap. (Mandriva's is hdb6)

---

### Post by rapsball4 on 2007-09-04
Alright, I don't have any idea what's going on now.  I'm changing things as you directed (both ways) and they are not even showing up on the menu.  When I try to go through the System Configuration tool for it, it won't even add anything, and then its wiped out any changes I've made to the file.  I think I've messed with it a lot, so I will probably wipe them both out and try all over again.

---

### Post by logos34 on 2007-09-04
Not sure what the problem is.  Are you trying to edit the files as root?  You need administrative priviledges to save changes to configuration files.

---

### Post by rapsball4 on 2007-09-05
Yeah, the files were saved after changing (opened in Kate through root user, and changed permissions on the file to allow writing).  If I closed it and opened it again, it was still there - it only disappeared from the file if I tried to use the GUI version in the Configuration Panel afterwards.  It just wasn't showing up on the menu when I restarted anyway.

---

### Post by logos34 on 2007-09-05
> **rapsball4 said:**
> Yeah, the files were saved after changing (opened in Kate through root user, and c**hanged permissions on the file to allow writing**).  If I closed it and opened it again, it was still there - it only disappeared from the file if I tried to use the GUI version in the Configuration Panel afterwards.  It just wasn't showing up on the menu when I restarted anyway.

Actually, that's not very good idea.  You shouldn't mess with the permissions of system files.  The recommended way is to login as root temporarily, just long enough to make necessary changes.  Use 'su' or 'kdesu'

---

### Post by rapsball4 on 2007-09-05
Alright, I just finished going through reinstalling both and getting it all setup again, and I'm given the error message below when I try to load into Ubuntu:

> Error 17: Cannot mount selected partition

---

### Post by logos34 on 2007-09-05
I'd download the [SuperGrub CD]("http://supergrub.forjamari.linex.org/").  See if you can boot ubuntu with that.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by rapsball4 on 2007-09-05
Alright, I used Super GRUB to try to boot Ubuntu (now hdb5) and it came out with:

> Error 13: Invalid or unsupported executable format

---

### Post by rapsball4 on 2007-09-05
Alright, I've basically given up, just so ya know - three days almost straight of trying to set this up is too much for me.  I'll probably have to go Ubuntu-less.

---

### Post by maybeway36 on 2007-09-05
Can't you install Ubuntu after Mandriva?

---

### Post by rapsball4 on 2007-09-05
I tried to do it before by partitioning it and putting Mandriva on one, but then Ubuntu refused to install on the other (an error message that you can't have the beginning before end), but I just realized when you wrote that that I didn't try to put Mandriva on the whole thing and then resize it down to half using Ubuntu.  That may possibly work.

---

