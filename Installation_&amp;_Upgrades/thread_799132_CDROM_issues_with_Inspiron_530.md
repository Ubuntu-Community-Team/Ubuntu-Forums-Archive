---
title: "CDROM issues with Inspiron 530"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by rosenrosen on 2008-05-18
I am a Linux newbie attempting to install Ubuntu 8.04 onto a Dell inspiron 530.  I choose Ubuntu because Dell can ship this system with it so I assume its compatible.  I tried the Live and Alternate CD with similar results.  I boot from CD, select my language and then "Install Ubuntu".  The screen goes black for maybe 10 minutes with just a cursor and then starts scrolling system information.  It spits this message out over and over:

[#.#] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[#.#] ata2.00: cmd a0/00:00:00:24:00/00/a0 tag 0 pio 36 in
[#.#] ata2.00: status {DRDY]

(The right hand side may be getting cut off.)
If I hit Enter I get an (initramfs) prompt and I can enter Linux commands, but the error message keeps coming.

Sometimes I get to a spot where it tells me it can't find my CDROM and I have the option to load drivers from a floppy (but I don't have a floppy drive).  My CDROM is a SATA device as are the 2 internal hard drives.  The CDROM is a "PBDS DVD+-RW DH-16W1S" and Windows is currently working fine on this system.  Any advice?  Thanks.

---

### Post by Pumalite on 2008-05-18
Try the Alternate CD

---

### Post by rosenrosen on 2008-05-18
With the Alternate CD I choose "install" and after a loooooong time I get to another Choose Language menu, then Choose Keyboard Layout and then Detect and mount CD-ROM which has an error saying "No common CD-ROM drive detected" with other text and then I'm asked if I want to load drivers from a floppy.  I can choose no and manually install where my only choice is "cdrom" and then I accept "/dev/cdrom" but no luck.  Thanks.

---

### Post by galileon on 2008-05-19
hey, are u using an external cdrom? i had this problem with one before...

i solved mine by putting it inside m desktop when installing then...

the desktop install shud work tho, try a media check before installing, possibl a badly burnt cd,

also try to use the lowest possible burn speed when burning install cds...

good luck

---

### Post by charles woodward on 2008-05-19
I am having exactly the same problem.  The funny thing is that I actually had vista and ubuntu loaded onto PC, then decided to re-install - at which point the CD stopped loading Ubuntu.  The CD loads, but when you select any of the options (run live, install, check memory, check disk) all options fail.  It does drop down to the inbuilt shell (ash) but then reboots after a short time.

---

### Post by rosenrosen on 2008-05-20
I am not using an external CDROM but I do have room for a second internal.  MMaybe I'll look for a cheap one.  

Are there general solutions, troubleshooting techniques or places to look for info if neither of the 2 Ubuntu install CDs can see my CDROM?  Not surprisingly I have the same issue with Debian and Knoppix.  Thanks.

---

### Post by galileon on 2008-05-20
according to this,

[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg11248.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg11248.html)

the ata error could be something linked with the smp version of the kernel...afaik, ubuntu only ships smp enabled kernels now right? can anyone confirm that?


edit: also, according to this
[http://ubuntuforums.org/showthread.php?t=472056](http://ubuntuforums.org/showthread.php?t=472056)

and the previous, it can be a sign of hardware about to go south...

also, try to make sure the ide/sata cables are wll shoved in their places, because a loose connection could be the cause...

---

### Post by butterman on 2008-05-23
I have the same problem trying to install Hardy 8.04 Server on an Inspiron 530 that I just took out of the box.

I came across [this]("http://ubuntuforums.org/archive/index.php/t-4447.html"), but the bios tweaks are not available in the Dell BIOS.

Has anybody made any progress?

---

### Post by Brian96 on 2008-05-23
I am having the same problem with an Inspiron 530 that I also just took out of the box. I started off trying to boot into the live CD to repartition the hard drive. I have gotten EXACTLY the same error under these conditions:

1. Using 8.4 64 bit booting into the Live desktop.
2. Using 8.4 i386 booting into the Live desktop.
3. Booting into a 64 bit Wubi install.

Same event, same error message each time.

---

### Post by Pumalite on 2008-05-23
Are you running Vista?

---

### Post by butterman on 2008-05-23
> **Pumalite said:**
> Are you running Vista?

I'm trying to overwrite whatever is on the disk...windows pro, I think.  I'm not trying to dual boot.

---

### Post by Pumalite on 2008-05-23
DBan the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD to format your drive ext3:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Then try again.

---

### Post by Brian96 on 2008-05-24
> **Pumalite said:**
> Are you running Vista?

I am running Vista, so changing the BIOS settings was not an option for me.

I found elsewhere that if you add "all_generic_ide" to the end of the boot instructions (by hitting F6 and then adding it to the end of the boot options to boot the live CD or install, then add that to the GRUB boot options as well when the GRUB boot menu loads) that it solves the problem. This worked for me.

Does anyone know what the "all_generic_ide" argument actually does? Is there a potential performance loss with this option? My machine has a SATA HDD and a SATA DVD drive.

---

### Post by rosenrosen on 2008-05-27
My problem was solved by adding "irqpoll" to the boot options (using F6).  This was suggested by the first message that the installer spit out but it took 5-10 minutes to do so and I never stared at the blank screen long enough to see it before other messages had it scroll away.  This time I got lucky.  Would there have been a way for me to see the message after I missed it?  Anyway I am now well on my way to installing.  Thanks for all the replies.

---

