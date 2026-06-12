---
title: "Where to place grub?"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by hobbsie on 2007-04-29
Hey there,

I am currently running the live cd of the 64 bit feisty and i have this current setup

/dev/hdc - Windows Vista Home Premium
/dev/sda - Unpartitioned 80GB SATA
/dev/sdb1 thru 3 - NTFS Partitions

Now I was wanting to install fiesty to /dev/sda taking the entire drive in say 2 partitions, one for mount point / and one for swap.

I have attempted an install via the live cd and I must have put the incorrect location for grub to install (I clicked advanced and typed in /dev/sda0) needless to say it failed and couldnt recover.

So here's what I need to know, if I want to not have fiesty touch hdc and install itself into the boot record or first partition of sda what do i need to put in the advanced options area.

Also can i actually install grub into hdc with vista and be able to choose which os to boot (is fiesty vista aware bootloader wise)

Sorry for so many questions but any help would be appreciated

Cheers
hobbsie

---

### Post by mlind on 2007-04-29
You need to type in the **device** instead of partition, so use
```

/dev/sda

```

You can later on install grub (from terminal) by doing
```

sudo grub-install /dev/sda

```

And make sure /dev/sda is the first drive in the boot order (in bios). If you have more than one hdd, it's safest to put grub into drive where windows is not installed.
I'm not sure about vista, but with windows 2000 and XP, grub works fine from windows partition too.

---

### Post by mikewhatever on 2007-04-29
What do you mean by 'failed'? Did you see any error messages? It looks like /dev/sda0 was the right option, so I am not sure what went wrong. The surest way to prevent GRUB from getting installed to another drive's MBR is to disconnect that drive during the installation, and manually mount it later, if needed.

---

### Post by exactopposite on 2007-04-29
I'm having a similar problem. In my setup, sda is vista, and sdb is where i'm installing linux. (i also have sdc and sdd, but those are just storage drives). i used the alternate install disk, and i have tried installing grub to /dev/sdb. when i boot up the grub list comes up and no matter which os i select (ubuntu or vista) i get error 17. 

i set sdb as the drive to boot from in the bios before i installed. i've tried variations on /dev/sdb like sdb1, sdb5, hd1 and so on, but i can't get past the grub menu when i boot afterwards. it seems like i'm missing something simple here.  

i really wish they would change the way u select the location for gtub in the ubuntu installer.  in fedora for example i've never had any problems getting grub to install where i want it.  it's relaly the only thing i don't like about this distro.

anyway, any suggestions on what i should do to make this work? i have the alternate disk, but i can download a copy of the live disk if that will work better.

---

### Post by hobbsie on 2007-04-29
**@mikewhatever**
It basically crapped out and said it couldnt install grub to /dev/sda0

**@mlind**
I got past the failure to install grub by putting /dev/sda in the advanced options, however I am now suffering the same issue as **exactopposite** 
*Error 17: Cannot mount selected partition.*

I attempted to edit it to point to hd0,1 in case it got confused when i booted the first sda from bios but did not do anything.

As far as i can see (hd1,0) is the correct partition, and just for reference this is the menu.lst file in /boot/grub
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=550c706a-31f3-45bd-bb44-36847feb6630 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=550c706a-31f3-45bd-bb44-36847feb6630 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```

Hope someone can help me get it to boot properly

Cheers
hobbsie

---

### Post by louieb on 2007-04-29
> **hobbsie said:**
> ...(I clicked advanced and typed in /dev/sda0) ...
Your getting GRUB notation (starts w/0) mixed up with Linux notations (starts w/a for drives and w/1 for partitions).
There is no such place as /dev/sda0.
If you want to put GRUB in the MBR of /dev/sda  use /dev/sda 
> Also can i actually install grub into hdc with vista and be able to choose which os to boot (is fiesty vista aware bootloader wise)I would leave GRUB on sda and leave the VISTA drive alone. If its not done for you, its easy enough to add a VISA entry to  /boot/grub/menu.lst.  Post back if you  need. or the Dual Boot link in my signature has a how to.

---

### Post by louieb on 2007-04-29
I see you got past the sda stuff. 
Now it looks like Grub may be confused as to which drive is which.
Check file /boot/grub/device.map
Post it  here if you want more help.
[More on device.map]("http://www.gnu.org/software/grub/manual/html_node/Device-map.html")

---

### Post by hobbsie on 2007-04-29
**louieb**
Here's my device map

(hd0)	/dev/hdc
(hd1)	/dev/sda
(hd2)	/dev/sdb

What do you think, does it look correct?

Cheers
hobbsie

---

### Post by mlind on 2007-04-29
edit your /boot/grub/menu.lst and set 
```

# groot=(hd0,0)

```
then run
```

sudo update-grub

```

if this doesn't work, try (hd1,0),

---

### Post by louieb on 2007-04-29
Device.map looks ok. sda maps to hd1  like I would expect.
Don't see a good reason for it not to work.

```

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=550c706a-31f3-45bd-bb44-36847feb6630 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic

```
Can you boot to VISTA from the GRUB menu?
I'm out of ideas for now. But before you give up try [Herman on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by hobbsie on 2007-04-29
Well I finally got it sorted...

> **mlind said:**
> edit your /boot/grub/menu.lst and set 
```

# groot=(hd0,0)

```
then run
```

sudo update-grub

```

if this doesn't work, try (hd1,0),

I did as you suggested by editing menu.lst however the sudo update-grub didnt work, so I manually edited the rest of the menu.lst file so that it looks like this

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=550c706a-31f3-45bd-bb44-36847feb6630 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=550c706a-31f3-45bd-bb44-36847feb6630 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```

So its all working fine now, thankyou very much **mlind** and thanks to everyone who helped me...its great to be using my first ever 64bit OS :guitar: :D:D

Cheers
hobbsie

---

### Post by mlind on 2007-04-30
hiya hobbsie, nice to hear you got it sorted. The Ubuntu kernel entries are automatically generated from **# groot**  and **# kopt** parameters, so it's important you get it working by using those. Everytime you install a new kernel (or when update-grub is invoked), those automatically generated kernel entries are overwritten by using values from **groot** and **kopt**.

Your /boot/grub/menu.lst already contains an entry like this
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

```
Where does the groot currently point?

---

### Post by hobbsie on 2007-04-30
Hey mlind,

groot currently points to (hd0,0)

so based on what you are saying as long as groot point to correct place the other entries i changed wont be buggered up if update-grub or kernel update is invoked?

Cheers
hobbsie

---

### Post by mlind on 2007-05-01
> **hobbsie said:**
> Hey mlind,

groot currently points to (hd0,0)

so based on what you are saying as long as groot point to correct place the other entries i changed wont be buggered up if update-grub or kernel update is invoked?

Cheers
hobbsie

yeah, if you change groot to something else and invoke sudo update-grub, then every **root** definition in your (automagic) kernel list changes too.
The thing I was trying to say is that don't modify the kernel entries manually like that, use groot and kopt entries instead or you'll be surprised when next kernel update arrives.

---

