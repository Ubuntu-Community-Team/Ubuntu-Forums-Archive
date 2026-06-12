---
title: "Grub error 22"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by Cotan on 2005-11-06
Hi,

The ubuntu installation goes well, but when I boot, I get the Grub error 22.
What is wrong, and what should I do to get ubuntu to work?
I have a raid controller integrated to my motherboard (HPT374), can it cause
the problem? And I dont know ho to switch the hard drive to LBA mode.
I searched bios for virus definitions, but only thing I founded was 
Virus warning and it was disabled.

So what can I do?

---

### Post by patsi on 2006-01-11
Hi!
I have the same problem on my abit kt7 max2 motherbord wich have the hpt374 sata where my harddrive is plugged in. I have also tried debian but that shit just blacks out and reboot! I'm cluelees to what may cause this problem would appricate any help I can get.

Cheers ;)

---

### Post by Sef on 2006-01-11
Here's a couple of suggestions to fix your problem:

> Message 5 in thread

Subject: Re: grub is gone
From: Jeffrey Laramie <jalaramie@xxxxxxxxxxxxxxxxxxx>
Date: Fri, 2 Jul 2004 14:29:13 -0400
To: qt-interest@xxxxxxxxxxxxx


On Friday 02 July 2004 12:24, Timothy Rupe wrote:
> Read the grub manpage.  When you run the grub program, you can use the
> "setup" command to write your boot sector. It would look something
> like this:
>
> grub> root (hd0,0)           (Specify where your /boot partition resides)
> grub> setup (hd0)           (Install GRUB in the MBR)
> grub> quit                  (Exit the GRUB shell)
>
> (Be sure to remember that grub numbers the drives and partitions a bit
> different than usual.  The first disk is 0, and the first partition is
> 0.)
>
> Reinstalling grub would probably not do this for you.
> - Tim
>

Ahh, this is good to know. Note to self: Read the grub man page _before_ you 
hose your system. :-)

Jeff

Message 6 in thread

Subject: [OT] Re: grub is gone
From: Kuba Ober <kuba@xxxxxxxxxxxxxxx>
Date: Fri, 2 Jul 2004 15:43:34 -0400
To: qt-interest@xxxxxxxxxxxxx


On piÄ&#8230;tek 02 lipiec 2004 12:06 pm, Jeffrey Laramie wrote:
> On Friday 02 July 2004 07:31, Hans MÃ¼ller wrote:
> > Hello i have a problem my grub is gone. I have try to install Winsows and
> > this has killed grub. So now the only way to run linx is booting via PXE.
> > I have try to run groub-install /dev/sda1 but i will not work. When i try
> > to boot then via the hdd, i get the error  22 from grub. What can i do?
> > The FC2 installation is on /dev/sdd2.
>
> Not sure why you cross posted this to the Qt list but I'll try to help. The
> Windows installation program overwrites the primary hard drive boot sector
> (even if the installation is aborted!) so your grub info is gone.
>
> IIRC you can use a recovery disk to boot into linux. Then uninstall the
> grub rpm and re-install it. This should re-install grub to the boot sector.
> The only other alternative I know of is to re-install linux. I've learned
> the hard way that on dual boot systems you always install Windows first.

There's no need for any recovery disks or whatever. Just make a grub floppy 
first, see: info grub, info:/grub.

Boot from grub floppy and *ONLY THEN*, while you're in grub's command line, 
install grub on your hard drive. That's the only sure way. From under unices 
it sometimes works sometimes doesn't as grub has to guess how the BIOS views 
the disks available under unix.

This method has never failed me and IIRC it's the method recommended in the 
info page.

Cheers, Kuba Ober

Link:  [http://lists.trolltech.com/qt-interest/2004-07/thread00053-0.html]("http://lists.trolltech.com/qt-interest/2004-07/thread00053-0.html")

---

### Post by Kipper on 2006-01-11
The last point about using GRUB on a floppy drive to install on a hard drive may or may not be true. But there is a catch-22 here, if you cannot boot your system and did not make a floppy boot disk during the install, that's it, you are stuck with your error 22.

The point is error 22 is explained  as a "cannot find the partition" type error.

I would ask just what drives where attached to your system during the install, and one what drive did you put GRUB and in what partition? Did you use "expert" or standard install. Expert gives you a choice of bootloader, GRUB or lilo, and the chance to make a boot floppy.

And I thought HPT374 was an IDE controller, where does SATA come into it?

An install on a Abit KT7 shouldn't be a problem. But it could well be a case of getting the BIOS settings correct for the RAID controller, which is not a real hardware RAID controller.

Mostly I have used Mandrake, and a variety of LiveCDs. I have installed Ubunutu 5.04 on an NF7-s on a PATA drive and it successfully recognised the second drive attached to the SATA drive. I used a separate /boot partition. Created a boot floppy and installed GRUB on the boot partition as well during the install. I used an existing GRUB installed in the MBR of the PATA drive to boot this Ubuntu install by editing the "menu.lst" file of the prevoius Linux install. In other words bits on one Linux install are used to boot another separate Linux install on the same disk (or in fact the SATA disk).

I'm not saying you have to do all this, but I have not had an error 22, or error 18 which seems to be cropping up a lot here. So it has got me puzzled as to why so many people are getting this problem. Where's the bug? In the procedure followed, or the software used? Or, is it in the hardware set-up?

---

### Post by thieves.honor on 2006-02-10
was having the same problem.  i had to pull my hd off of the raid controller and put it on the normal ide controller.  after that no more grub error.

---

