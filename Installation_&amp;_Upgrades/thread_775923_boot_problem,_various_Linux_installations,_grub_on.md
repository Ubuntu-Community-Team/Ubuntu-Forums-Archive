---
title: "boot problem, various Linux installations, grub on wrong partition!?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by wotanunddasoh on 2008-04-30
Hi everybody!
First sorry, I am nearly sure that there is already a thread to this topic although it is a bit particular and so I didn't find what I am looking for. However, here the problem:
I've installed two times Ubuntu and one time Fedora on my computer. 
After I intalled the second Ubuntu I have the following problem:
When I start my computer I get a message:

No bootable device -- instert boot disk

I have enabled booting from harddisk in bios. So its not a bios problem. However, there is a strang workaround: If I instert the Ubuntu Live CD and choose "boot from Hard Disk" it works!!! How strange! 

I have the feeling that somehow the grub bootloader is not where it should be...
Has anybody an idea what might be the problem??? 

Thank you very much 

Kalle

---

### Post by lswest on 2008-04-30
try to restore the GRUB bootloader using the how-to i wrote a while back (third line of my sig has a link to it)  Seems like the GRUB install went awry.

---

### Post by wotanunddasoh on 2008-04-30
Hello Iswest!
Thanks for the very fast reply. Unfortunately, I already did what you suppose in that thread. 
stage1 was found in (hd0,0), hd(0,5) and hd(0,7)
well, this are my 3 Linux installations.
I set "root" to hd(0,0) and setup to hd0 (I just have that HD)

And as I said the bootloader is kind of working. It just doesn't start itself - I have to put the Live CD and choose "boot from first Hard Disk". Then it finds the bootloader root on (hd0,0) and displays me the boot menu. From this point everythings is fine. Its just that I won't boot directly without Live CD :(

Any idea?

Kalle

---

### Post by lswest on 2008-04-30
first off, my name is actually "L"swest, which is a put together of my first name's first letter, my middle name's first letter, and the first 4 letters of my last name ;) (if you look at my avatar you'll notice the "L" ;))

Secondly, are you sure the "hd0,0" is the root partition? can you post the output of ```
sudo fdisk -l
``` it seems the GRUB entry in the MBR is looking in the wrong place for the actual GRUB files.

> 18 : "Invalid or unsupported executable format"

This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD). according to [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)
so, try mounting your linux partition ```
sudo mkdir /media/linux\ drive/
sudo mount /dev/sda1 [i assume that to be your root filesystem] /media/linux\ drive/
``` and then run this command ```
cat /media/linux\ drive/boot/grub/menu.lst
``` and post the results here (if you don't feel like posting all that info, just post the relevant section that lists all the options of your boot menu towards the end of the file).

---

### Post by wotanunddasoh on 2008-04-30
Hello Lswest
Sorry for the 'L' confusion :) 
Of course I could post you the output. here it comes!
fdisk:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648       38913   283274145    5  Extended
/dev/sda5            3648        7294    29294496   83  Linux
/dev/sda6            7295        7780     3903763+  82  Linux swap / Solaris
/dev/sda7           32835       38913    48829536   83  Linux
/dev/sda8   *        7781       32084   195221848+  83  Linux
/dev/sda9           32085       32834     6024343+  82  Linux swap / Solaris

```

menu.lst:
```

...
default=1
timeout=10
...
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d76affb6-6daf-48b0-a75f-a95ca01b6072 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d76affb6-6daf-48b0-a75f-a95ca01b6072 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=628c72e3-cd72-4637-9a95-a15046ce4980 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=628c72e3-cd72-4637-9a95-a15046ce4980 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Fedora (2.6.23.15-137.fc8) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.23.15-137.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.23.15-137.fc8.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Fedora (2.6.23.1-42.fc8) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/1 rhgb quiet 
initrd		/boot/initrd-2.6.23.1-42.fc8.img
savedefault
boot

```

I hope it brings some light to this issue...

Thanks

kalle

---

### Post by Herman on 2008-05-01
Hello wotanunddasoh,
Your /boot/grub/menu.lst looks okay to me.

Can you remember replacing any drives in your machine lately? Do you have a PATA (IDE), or a SATA hard drive?

Have you checked to make sure your floppy disk drive bay is empty? (Maybe it's silly, but just an idea).

For a disc to be bootable, it needs to have a 55aa bootable disc signature in the MBR.
You can use the following command to take a look at your MBR in hexadecimal code to see if it has the 55aa signature,
```
sudo dd if=/dev/sda count=1 | hexdump -C
```

Have you checked that your hard disk is properly detected and set up in your BIOS?

Regards, Herman :)

---

### Post by isharra on 2008-05-01
> **wotanunddasoh said:**
> 
Of course I could post you the output. here it comes!
fdisk:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648       38913   283274145    5  Extended
/dev/sda5            3648        7294    29294496   83  Linux
/dev/sda6            7295        7780     3903763+  82  Linux swap / Solaris
/dev/sda7           32835       38913    48829536   83  Linux
/dev/sda8   *        7781       32084   195221848+  83  Linux
/dev/sda9           32085       32834     6024343+  82  Linux swap / Solaris
```

Sorry, doing a quick scan of the forum so I may be missing something obvious but you have /dev/sda8 marked as the boot partition NOT /dev/sda1 which i presume is (hd0,0). 

Unless you have grub installed to the master boot record (hd0) or to /dev/sda8 (hd0,5) I don't believe you can boot from the current disk layout.

The simplest solution would be to use fdisk and mark /dev/sda1 as the boot partition if that is where you installed grub.

Apologies for interrupting if this is in error.

---

### Post by wotanunddasoh on 2008-05-02
hello isharra,
no apologizing, please. Actually it was your hint that helped me. I had noticed before that sda8 was marked as the bootable section of the HD, but somehow I thought that by the boot flag grub would be able to identify it and load from there. However, the practice proofed me wrong and setting the boot flag to sda1 resolved the problem.

But I stay with the question why the second ubuntu installation changed that flag though? It found well the other installations what is proofed by the correct menu.lst file! Might that be a bug or is there is reasonable explanation?

But thanks a lot anyway!

Kalle

---

### Post by Herman on 2008-05-02
:confused: Hmmm.... Very interesting.

At first I didn't see any sense in this at all.
Now I am thinking about it a little deeper and I notice that the boot flag was set in a logical partition.
I am surprised that GRUB can set the boot flag in a logical partition.
Last weekend when I was experimenting to learn how to boot Windows in a logical partition GRUB could not set the boot flag in a logical partition, but a partition editor (GParted) could do it. 
My GRUB gets error 12 after the makeactive' command when it tries to set the boot flag in a logical partition.
I also didn't think that Linux even needs the boot flag when we boot with GRUB.
In tests, my Linuxes will boot just fine with no boot flag in the partition table at all, but I do know that we are supposed to have one boot flag in the partition table to make the partition table valid, (usually it can remain set on a Windows partition) if there is one.

... So, I fired up an old test computer and used Hardy Heron's Partition Editor, GParted, to delete the boot flag from a Windows installation's partition and set it in a Linux operating system in a logical partition.
The second hard disk in this machine has a data partition and a Linux installation in a logical partition.
The result was that both of my Linuxes in the first hard disk booted with no problem at all despite the fact that the boot flag was set in a logical partition and there was no boot flag in the primary partitions at all.
The operating system in the second hard disk booted just fine without any boot flag in the partition table of that hard disk at all. 
Of course, it is unlikely that Windows would boot without a boot flag, but I didn't bother trying to boot Windows.

For a second series of tests, removed the boot flag from the first hard disk too, and I booted both of my Linux (Ubuntu) installations in my first hard disk again. No problems were encountered. The Ubuntu installation in my second hard disk also booted without any boot flag at all in this machine, (on either hard disk). :confused:

This is not the first time that I have been unable to reproduce the same problems in a test computer that other people report in their machines. All computers are different, it seems.

SO I am still in the dark as to the rhyme or reason as to why it mattered that wotanunddasoh's boot flag being set in /dev/sda8 made the hard disk unbootable?
Anyway, I'm glad you got it fixed, isharra, you are a genius for picking that out.
Someday I might learn the reason why. 


Regards, Herman :)

---

### Post by meierfra. on 2008-05-02
> SO I am still in the dark as to the rhyme or reason as to why it mattered that wotanunddasoh's boot flag being set in /dev/sda8 made the hard disk unbootable?

I believe  there are some bios which refuse to boot  a  hard drive without a boot flag (and for the bios a boot flag on a logical partition probably does not count)


> Of course, it is unlikely that Windows would boot without a boot flag 

I don't think this  is true. As long as one boots Windows with grub, the boot flag should not matter.

---

### Post by Herman on 2008-05-03
:) Hello meierfra.
> I believe there are some bios which refuse to boot a hard drive without a boot flag (and for the bios a boot flag on a logical partition probably does not count)
 Oh, I see, yes, that makes sense. I think that would probably be right.
>  [quote]Of course, it is unlikely that Windows would boot without a boot flagI don't think this  is true. As long as one boots Windows with grub, the boot flag should not matter.[/quote]I'm not so sure about that, I don't think Windows will boot without a boot flag at all. 
 Of course, when we boot Windows with GRUB, then GRUB's makeactive' command will place the boot flag on the Windows partitionif there is one somewhere in the partition table already. If no boot flag exists, GRUB will make a boot flag for Windows.
The boot flag wouldn't need to have been there beforehand, so in that respect we needn't worry about having a boot flag on a Windows partition beforehand when we're booting with GRUB.
I don't think Windows will boot from GRUB without a boot flag without using GRUB's 'makeactive' command to make one though. :)

:oops: Oops! You are right again, meierfra, I tried it in my current test computer and Windows did boot without any boot flag at all set in either partition table.
Well, I'll be...!

---

### Post by isharra on 2008-05-04
The bios needs to know where to find the boot code. This is usually determined by the boot flag (unless the boot code is installed in the MBR.) On older operating systems the boot partition had to be one of the 4 primary partitions. These days grub can boot from logical partitions (as long as the bios also supports this.) 

Last I heard Windows needs to be launched from a primary partition but it's been years since I looked at the windows boot loader and I am uncertain if this is still the case with the Vista loader. If you are booting Windows by using grub then the windows partition does not need a boot flag, if you are booting windows by using the windows loader then it does need a boot flag.

For some unknown reason,  grub was installed to sda1 and the boot flag was set to sda8. The fact that these did not match caused the error (the bios could not find the boot code in sda8 where it was told to look.) There are good odds that you could have fixed the problem by using grub to install it's files to sda8 (using the grub setup command).

Grub does NOT set the boot partition flag for the disk, whichever partition manager used by the installation did that.

Hopefully this makes things a little clearer.

---

### Post by meierfra. on 2008-05-04
> Last I heard Windows needs to be launched from a primary partition

Even Windows can be booted from a logical partition theses days. 

> There are good odds that you could have fixed the problem by using grub to install it's files to sda8 (using the grub setup command).


I disagree.  Ubuntu had installed Grub's stage 1 files to the MBR and the stage 2 files to  /dev/sda8.  The bios refused to start the booting process since where was no boot flag on a primary  primary partition.  This happened before the bios even started looking at  any boot files.  Altering /dev/sda8  would not have changed that. I'm pretty sure that the problem could have been solved by setting  the boot flag on any of the four primary partitions.

---

