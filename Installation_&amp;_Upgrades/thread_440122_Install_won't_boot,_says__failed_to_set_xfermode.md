---
title: "Install won't boot, says:  failed to set xfermode"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by PiercedLip81 on 2007-05-11
Ok I searched but im not able to read thru all the posts at the moment, i did find this one I bookmarked [http://ubuntuforums.org/showthread.php?t=414002&highlight=failed+to+set+xfermode](http://ubuntuforums.org/showthread.php?t=414002&highlight=failed+to+set+xfermode). just looking for a simple answer...whats causing the errors, if its hardware I can swap it out. 

Quick rundown, installed ubuntu on a master drive, worked, put in another drive that was bigger to use. Now can't get the install to complete.

My goal is XP Pro on master HD, Ubuntu on Slave HD.

Its not the CD, because I tested it on my laptop and the cd boots fine...now on this pc it wont boot at all. it gives me these errors after i tell it to boot the cd/install.

/bin/sh: can't access tty; job control turned off
ata2.01: failed to set xfermode (err_mask=0x4)
ata2.01: failed to set xfermode (err_mask=0x4)
ata2.00: failed to set xfermode (err_mask=0x40)

I am installing on a Dell Dimension 8100 1.4ghz pentium 4, 512mb ram, Nvidia GeForce2 MX/MX 400 Graphics.

I have no clue what those errors are, nor any luck searching on how to resole the issue. I also tried installing w/ the text mode installer, but it just freezes up. Is this a cd drive issue/hd,etc?

My bios has a setting for hard drives named Primary drive 1, primary drive 2. 1 is set to on, 2 is set to off, but both drives show up in My Computer in XP just fine. Think this stays off, since drive 2 its not primary.

Any tips/advice?

pclinuxos also throws errors, so its something w/ the hardware on this pc, but what?

Thanks guy! I look forward to using linux if I ca ever get it installed again!

---

### Post by PiercedLip81 on 2007-05-11
i've been reading up and it looks to be a cd drive issue and its not detecting it. I am going to try and swap the drive and see if i have any luck w/ that. maybe since its an older drive its not reading it properly? Worth a shot?

---

### Post by RetepNamenots on 2007-05-12
I'm getting the exact same problem. I've read somewhere that adding **irqpoll** to the boot line could help; I'll try this next as I don't have any other drives to use...

---

### Post by PiercedLip81 on 2007-05-12
problem solved here. It was my dvd drive. I just unplugged it, and made my burner the master drive for boot and it worked. odd? Now it installed and I can't get into either os...I get a grub error 21. Im working on it now :-/

my partitions look like this (loaded from live cd)

device type mount point format size used

/dev/sda
/dev/sda1 ntfs /media/sda1 61843mb unknown
free space 8mb

/dev/sdb
/dev/sdb1 ext3 /media/sdb1 19140mb 2400mb
/dev/sdb5 swap 880mb 0mb


I can change the partitions manually in there it seems? Still no booting of either OS. This sucks :-/

---

### Post by MadScientistVX on 2007-05-18
> **PiercedLip81 said:**
> Ok I searched but im not able to read thru all the posts at the moment, i did find this one I bookmarked [http://ubuntuforums.org/showthread.php?t=414002&highlight=failed+to+set+xfermode](http://ubuntuforums.org/showthread.php?t=414002&highlight=failed+to+set+xfermode). just looking for a simple answer...whats causing the errors, if its hardware I can swap it out. 

/bin/sh: can't access tty; job control turned off
ata2.01: failed to set xfermode (err_mask=0x4)
ata2.01: failed to set xfermode (err_mask=0x4)
ata2.00: failed to set xfermode (err_mask=0x40)



Had the exact same problem (actually ata1.01 giving me a problem), added irqpoll to kernel boot options, as per  RepetNamenots, and it worked. Many thanks!!:)

---

### Post by nxt on 2007-05-28
added a new line to grub with "irqpoll" and it worked like charm....

.....i almost smashed the machine though - it's hard to google it out without being able to boot first  :D

---

### Post by KMWolf on 2007-06-08
Hmmm....
So I added irqpoll to the kernel line in /boot/grub/menu.lst, saved it, rebooted - and got the same error as before. Looked again in menu.lst and found, that irqpoll has gone. Seems as if the file was rewritten, after I changed it.
My menu.lst looks like this near the end:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
		find --set-root /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-16-generic
boot

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
		find --set-root /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
		find --set-root /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		find --set-root /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		find --set-root /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

I added irqpoll in both kernel lines after "splash".
Any help, please.

---

### Post by KMWolf on 2007-06-08
Got it:
I had to change the kernel line in the Windows-file c:\wubi\boot\grub\menu.lst, because /boot/grub/menu.lst in Ubuntu is obviously written from it. Now it works perfectly.
Thanks for listening :D
Knut

---

### Post by nxt on 2007-06-14
I had the same problem  - but them I added the irqpoll bit into "default kernel options" part of menu.lst.

If you add irqpoll directly to the generated line kernel option, it will be rewritten by update-grub :(

---

### Post by ImALittleTeaPot on 2007-12-24
Hey. I've been having ata5.0 failed to set xfermode (err_mask=0x40) error messages too. Tried the irqpoll thing and it worked, but i read that this causes a performance hit. Can anyone verify that? Or does anyone know anything about ata failed to set xfermode error messages?

---

### Post by rookie4evr on 2008-03-30
Hi everyone ...
some of u guys mentioned .. to add, "irqpoll" .. after kernal line ...
what is the "kernel line" :confused:
because ... when i click on the option to install ubuntu ..
I get this bar that goes from 0% to 100% .. and it says .."kernal something" .... after that ... ubuntu's loading bar show up loading...
and after that I get booted to this .. black screen giving me the error message u guys got ....
can some one please tell me step by step how to fix this problem .....thanks

---

### Post by wisekki on 2008-04-03
>  Hey. I've been having ata5.0 failed to set xfermode (err_mask=0x40) error messages too. Tried the irqpoll thing and it worked, but i read that this causes a performance hit. Can anyone verify that? Or does anyone know anything about ata failed to set xfermode error messages?

Yea I can verify this.. performance hit is very bad.. when unrarring or even loading
a big text-file I can't do anything else.. even the mouse lags badly.. and it's only
because of this irqpoll that I have to use :mad:

 - Andy

---

