---
title: "Unsualy tripple boot issue"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by UBJim on 2010-04-15
Drive 0 - XP partition 1 Vistat64 Partition 2
Drive 1 data only
Drive 2 Partition 0 Win 7 partition 2 Ubuntu and SWAP partition on 3

I had 7 installed last and it would boot vista win7 and XP.

I installed grub, could only boot XP - however XP can not boot Vista or Win7

So I can boot Ubuntu and XP, but not Win 7.

I recovered with the CD and now I can boot win 7 which will boot to Vista and XP.What can I do now? I think that if I reinstall grub, I will go back to just booting Ubuntu and XP....

How can this be solved.... what am I missing?

Thanks Jim

---

### Post by Mark Phelps on 2010-04-15
Since you installed Win7 last, you most probably wrote the Win7 boot loader files into the XP partition -- it does that by default. This means that when you select the MS Windows option from GRUB, it hands off control to the Windows loader in the partition you select.  If this is the XP partition (which it SHOULD be), you will get an MS Windows menu that will list Win7 and XP.

IF you install GRUB2, I've found that it does an excellent job of finding other OS's by default.  Simply install that, and when you then boot into Ubuntu, in a terminal, enter "sudo update-grub" and you should be OK.

---

### Post by UBJim on 2010-04-15
Oh ya, it lists them all right,** but they don't work**. (they will only boot to XP ALL of them).

Nor does it seem can they be made to work. No matter how you change the parameters in grub.cfg, it will only go to the XP boot partition, and XP can not boot Win 7 - Win 7 has to boot XP.

Any way I can boot to Ubuntu from windows? 
On the install cd, how can I set the grub command line to boot from hd2,1 ?

At this point I can not longer boot Ubuntu (ran win 7 repair).

---

### Post by oldfred on 2010-04-15
Windows combines all its boots into one and moves some boot files from the second install to the one that boots.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

To reinstall grub (just be sure what version)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by UBJim on 2010-04-15
> **oldfred said:**
> Windows combines all its boots into one and moves some boot files from the second install to the one that boots.

Yes, but it seems in this case the picture is a bit different. It seems as though the first partition just has the XP boot on it, and when win7 sets thing up the MBR goes to some other partition, then if you pick XP it goes back to the first partitions loader to boot XP.

It also seems that Grub does not fully understand this, and just grabs this first boot loader. But all we can do is guess what happened, as there is no way to see what is really there for bootloaders (is there?).


> **oldfred said:**
> 
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) 

Very informative, I will study this. Thanks. Having work with embedded systems I was aware of this but did not know that particulars. Too bad there is not a utility out there that would just analysis this and report the set up. 
> **oldfred said:**
> 
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600) 

As I said grub SAW them and tried to but item in the boot menu, but did not do the right thing, so both the Vista and the Win 7 entries booted to XP. I think that when grub installed it killed off the Win7 bootloader.

> **oldfred said:**
> 
To reinstall grub (just be sure what version)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Well, I'll try again and report back, but since my install order was XP Vista WIn7 Ubuntu, I don't expect different results.

I really think that Grub just misreads the set up and does not do the right thing, but hey who knows. It's easy enough to get back to where I have it now....

Thanks...

---

### Post by oldfred on 2010-04-15
This will tell what boot loader is where and what files are where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

