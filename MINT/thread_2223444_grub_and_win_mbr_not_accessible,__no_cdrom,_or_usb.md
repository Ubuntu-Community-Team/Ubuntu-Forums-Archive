---
title: "grub and win mbr not accessible,  no cdrom, or usb boot"
date: 2014-05-11
forum: MINT
---

### Post by equitube on 2014-05-11
HI im steven, IT pro for 20 urs, new to linux. I recently installed a dual boot xp and mint13. No, it never did dual boot. 

Its an old HP pavillion xh545 notebook,  975mhz athlon iv 512 ram. Cdrom is out, bios too old to boot from.

I had some luck with plop boot mgr. I was able to do a winxp reinstall from usb with it. I tried to install several linix distros using all the major usb tools. It never would install or even run live.

I tried mint 13 and voila it installed and ran live. I installed it to hd replacing an unbootable copyof ubuntu. It wouldnt run off hd though.

On the mint forum, I found and ran some terminal commands to check which part was which. The other was supposed to install grub, which apparantly wasnt installed.

after running and rebooting, all I can get is the grun 1.9 bash like com, and line. I tried to learn all I could about bashing,  I was finally able to see the parts which are all now msdos, I believe.

I cant use plop or access usb for booting or cd rom I have no money to repair,  and wouldn't for a machine of this year.

does anyone have a solution or ideas?  I worked so hard finally getting some results andI ccant trash it now

When I use the ls command from grub I get: (hd0) (hd0, msdos6) (hd0, msdos5) (hd0, msdos1) (fd0)

The floppy drive may or may not be functional,.and I've got to find a floppy . The other 5 computers here (3 are tabs), dont have fdd. Although I do have a couple old compaq 500 mhz somewhere w floppies I think.

---

### Post by jdeca57 on 2014-05-11
Did you try variants of Ubuntu that are suited for usage of less RAM, like Lubuntu? That might be a better way to get that hardware to work again, since 512 MB RAM isn't much and what you're trying - running an older version of Mint - will probably fail because Mint is a distribution that aims at comfort. So that is not meant for a less powerful machine.

---

### Post by equitube on 2014-05-11
I even tried puppy, but the fact that most of the install attempts hung at the same spot leads me to believe that it was a chink in an incredibly patched and convoluted system. Great exercises in learning linux "from the grub up"

---

### Post by grahammechanical on 2014-05-11
I am speaking only as regards Ubuntu. When we run a live session it uses an open source video driver. When we install and tick "Install third Party Software" a proprietary video driver is installed.

Sometimes, often in my opinion, the first reboot after installation, and of course subsequent boots, fail due to an incompatible proprietary video driver. The graphic adapter in that machine may not be supported by the latest proprietary video drivers. After a period of time support of obsolete graphic adapters is dropped. You may need a proprietary video driver more in keeping with the age of that machine. Or to use only the open source video drivers.

Another thing, the term msdos is used by the Grub developers to refer to partitions. Why they use that term I do not know. Perhaps it is because they needed their bootloader to be compatible with Microsoft terminology. So, msdos1 is the first partition; msdos2 is the second partition and so on. whereas hd0 is the first hard drive and hd1 is the second hard drive.

The Linux developers use hd for IDE drives and SD for Sata drives and the use letters of the alphabet to distinguish drives and partitions. So, sda = first hard drive and sdb = second hard drive. Whereas, sda1 would be the first partition on the first sata drive, then sdb6 would be the sixth partition on the second sata drive.

A third point that you may not be aware of, 512GB RAM seems just about adequate but does the graphic adapter have its own memory? Or is it using some of RAM? Does the OS really have 521 GB available or something less.

If you are getting a grub rescue prompt then grub is unable to load the Linux kernel for some reason. 

Regards

---

### Post by oldfred on 2014-05-11
If you get grub> or grub rescue that is just the grub command line with very limited commands and not bash with is the terminal in your install.

You may be able to manually boot.
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
OR if configfile does not work This example uses sda5:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

Or remove hard drive and plug into one of your systems with a working CD or USB port to install to hard drive.

---

### Post by equitube on 2014-05-11
I know there are three parts on the 20gb hd. 1, a winxp clean install that I did using plop 2 wks ago, 10gb. A 7.5 gb linux part, that had what looked like a good lubuntu 13 distro, and a 500mb linux swap part. That was what I chose in unetbootin for persistence I think. And a 1.5 gb part for mbr.

when I saw the parts in grub, they said not a recognized file system. But ill try the commands you've listed, thanks so much. Oh the machine has 512mb not gb memory, and it is maxed out.

Well, at least those commands did something. It tried to boot into mint 13, then I got the following:

After a number of lines starting with [    3.654627]  sda: sda1 sda2 <sda5 sda6> 

then a lot of [[120^^ gave up waiting for root device

ALERT! /dev/msdos6 does not exist dropping to a shell

then busybox v1.18.5 (ubuntu 1:1.18.5 lubuntu4) built in shell (ash) Enter help  for a list of built in commands.

I should note that when typing ls my listed drives were (hd0) then hd0, msdos 1 2 and 5

---

### Post by oldfred on 2014-05-12
If you have 1, 2 & 5, then 5 is probably swap. But then which is your install 1 or 2?

Try this with all three, sda5 shown. 
 Adjust drive, partition to your install:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

---

### Post by equitube on 2014-05-12
I found the linux part but for some reason (following some other forums directions) I think the files needed to boot got installed or moved under the media directory.  How do I see inside those subdirectories. I can see them listed, but don't know the proper commands.

does anyone know of a good command reference, I found a few online command lists, but without at least a little explanatory text, I don't know basic file manipulation in linux, although I used to be pretty proficient in DOS

---

### Post by oldfred on 2014-05-12
Years ago I downloaded from somewhere a simple cross ref from DOS to Linux for many basic commands.

This has somewhere all the info you need, but is way overkill. :)

 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

---

### Post by equitube on 2014-05-15
Under (hd0, msdos6) I can see all those, the kernel etc, ill try to boot from that lcation

> **oldfred said:**
> If you get grub> or grub rescue that is just the grub command line with very limited commands and not bash with is the terminal in your install.

You may be able to manually boot.
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
OR if configfile does not work This example uses sda5:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

Or remove hard drive and plug into one of your systems with a working CD or USB port to install to hard drive.

I tried that, got a kernel panic due to "cannot open root device or unknown block"

---

