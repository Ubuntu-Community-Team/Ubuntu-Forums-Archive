---
title: "Fail to Boot Windows 7 after installing OpeBSD 5.1, then Ubuntu 12.04 with Grub 1.9x"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by just_ken_here on 2012-10-06
Hi

I have new 500gb HD put on my new built system.

1. I installed Windows 7 Pro 64bit created 1 partition. Booted fine.
2. Installed OpenBSD 5.1 (try it out) -- gone thru all the manual sector partitioning, disklabeling all that. Windows is gone (from the boot -- not from the drive)
3. Installed (final) Ubuntu 12.04 64bit Desktop -- with the hope that Grub will take care of the MBR and ready to boot all 3 (Windows 7, OpenBSD, Ubuntu)

Turns out only the Ubuntu & Windows option show up on the Grub menu..
Grub version should be the default that came out with the Ubuntu 12.04 CD.

Here are the final partition table :
[IMG]http://i.imgur.com/lp3WT.png[/IMG]

Yes, I put the OpenBSD (SDA2) -- on that part manually & not by accident !
I had no swap ( my RAM is 8 gb ) -- had too also since.. I can't waste the rest of the last 208 GB.

And do you see the boot flag on the OpenBSD partition ? what is that ?

-------------------- This is after the Ubuntu 12.04 Desktop 64 bit install. Current state of HD.

But now, when booting on Grub and choosing the Windows 7 Loader option.
The Windows boot failed:
[IMG]http://i.imgur.com/2yzcm.jpg[/IMG]

that was status : 0xc000000e

Questions:
1. So what happened to the Windows bootloader ?
Did windows installed the it's loader on the MBR
Did the OpenBSD overwrote & ruined it.
Did the Ubuntu Grub did ?

Basically what happened ? I have done the same with W7 and Ubuntu 10.10 on another HD on my laptop... all seems works ok with Grub.
Any scripts to run to find out ?

2. How to Fix this ?
Should I use the Windows Loader instead of grub on MBR ?
like this article suggested : [http://www.linuxbsdos.com/2011/09/21/tips-for-dual-booting-windows-and-linux/](http://www.linuxbsdos.com/2011/09/21/tips-for-dual-booting-windows-and-linux/)
But I don't really see the point / benefit --- since I have reinstalled Grub b4 using liveCD, which I dont think this will fix this prob ?

Also useless for now : [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

3. How to add the OpenBSD boot option to the Grub also ?


Thanks

---

### Post by just_ken_here on 2012-10-06
[http://ubuntuforums.org/showthread.php?t=2027848](http://ubuntuforums.org/showthread.php?t=2027848)

will this solve fix it ??

---

### Post by darkod on 2012-10-06
I think the OpenBSD installation messed it up. Especially since you say there was no option for win7 in its bootloader.

No, you don't need to use win7 bootloader, grub2 on the MBR is just fine. The problem is if OpenBSD really messed up win7 boot, it's not the fault of the ubuntu grub2 that can't boot it now. In fact, it is trying to, that error message is from win7, not grub2.

The boot flag should stay on the windows partition, I am assuming OpenBSD did that too since it's on its partition.

If you plan to run any repair with the win7 dvd, first use Gparted and activate the boot flag on sda1, deactivate it on sda2. The repair process should sort out win7 depending what the issue is. First try if only moving the boot flag can help.

Also, I am not sure what filesystem you used for OpenBSD but ubuntu says it's unknown, which means it will never detect it and add it to grub2. I have no idea why it doesn't recognize the filesystem.

---

### Post by just_ken_here on 2012-10-07
Darkod:[INDENT]I followed your advice on moving the boot flag to Win7.
Doesnt fix it. So the windows bootloader ( I assume on sda1 ) -- is messed up by the OpenBSD install..

A bit about boot partition :
[www.pcreview.co.uk/forums/does-active-partition-mean-t1489512.html]("http://www.pcreview.co.uk/forums/does-active-partition-mean-t1489512.html") 

---------
this is the bootscript run : [http://paste.ubuntu.com/1265083/](http://paste.ubuntu.com/1265083/)
after the boot flag was moved from sda2 -> sda1 using GParted

I will try the Win7 repair from the DVD tomorrow..

And it seems like I have to read also :
[http://www.openbsd.org/faq/faq4.html#Multibooting](http://www.openbsd.org/faq/faq4.html#Multibooting)  --- on Win7 part

----------
I am just trying to figure out what exactly happened... so I 'll keep posted if any.

Thx
[/INDENT]

---

### Post by just_ken_here on 2012-10-09
The Windows Loader on Boot Partition at SDA1 is fixed using the Windows install DVD.

------1st
tried : [http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

 >bootrec /fixboot
did not fix anything.
------2nd
just follow the automatic repair suggestion. Fixed it.


*************** But how I am still working on putting the OpenBSD bootinfo in either 1 of the bootloader: Grub or Windows Loader.

[http://www.openbsd.org/faq/faq4.html#Multibooting](http://www.openbsd.org/faq/faq4.html#Multibooting) for Windows7
yet to try that.
But thats just for Windows loader...


Anyone know how to put it in grub?

---

### Post by darkod on 2012-10-09
Now that you have windows booting, put grub2 from ubuntu on the MBR. I wouldn't even bother making windows bootloader load linux. Why when you have grub2?

The first time you boot, grub2 might not have a correct entry for win7 because you did a repair of the boot files. Once you boot ubuntu run the sudo update-grub which should detect win7 OK.

Whether it detects OpenBSD or not it depends if all is well with the installation and the boot files.

When you have ubuntu booted, post the output of:
sudo parted -l (small L)

---

### Post by oldfred on 2012-10-09
I have some examples from FreeBSD, not sure if yours would be similar or not:

[http://forums.freebsd.org/showthread.php?t=5918](http://forums.freebsd.org/showthread.php?t=5918)
menuentry "freebsd 8.0" {
    set root=(hd0,2,a)
    chainloader +1
}

[http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html](http://lists.freebsd.org/pipermail/freebsd-doc/2009-November/016465.html)
    menuentry "FreeBSD 7.2-RELEASE i386" {
            set root=(hd0,3)
            chainloader +1
    }

Grub shows mod files for ufs1 and ufs2. Not sure of differences but you may need to add those like we often have to add for NTFS.    insmod ntfs

So you may need this before the set root command:

insmod ufs1

---

### Post by just_ken_here on 2012-11-03
The OpenBSD install somehow mess that up. Maybe, I messed it up while setting the active boot partion.
I don't the Ubuntu install did screw the Windows.
How exactly and what really happened, I am still not sure..
I set the active partition to SDA2 - OpenBSD from SDA1 - Windows during the BSD install.
The BSD install should wrote the MBR or wrote Windows boot part?

How did or even did BSD change Windows boot code on SDA1 is ??

But who cares right.. ;)
---------------------------- The fix for me :
The Windows boot partition is fixed by Windows 7 DVD - Repair.
Automatically does it.

The fix for the OpenBSD entry : google - adding openbsd to Grub
[http://www.kariliq.nl/openbsd/grub2.html](http://www.kariliq.nl/openbsd/grub2.html)

solved.

---

