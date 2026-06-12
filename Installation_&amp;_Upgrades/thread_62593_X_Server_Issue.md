---
title: "X Server Issue"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by Oberkorn on 2005-09-05
Hello.

I've tried to do my own research using the search and have been at an impass for several hours now.  

I loaded Ubuntu Hoarty and had issues initially (network detection, trashed my windows xp partition (backed up what i wanted and i have my wife's laptop to use so no biggie there)) but pushed through those.  

Finally got Ubuntu to load but am having the same issues that many have had/are having regarding X server not loading and being dumped to the command line after seeing no screens found.

I've tried editing the xorg.conf file many times and that doesn't seem to work.  My knowledge with Linux is extremely limited (I am taking a class on it but am only in the beginning nor do I expect the class will even touch on this subject (we're using CentOS on the computers in class)).

My setup:
AMD 64 3000+
1GB Ram
SATA approx 75GB raptor *can't recall the exact size*
ATI Radeon X700 Pro (RV410) with 128MB ram
Sony CPD-200ES 30-70khz hori./50-120hz vert., max 1280x1024 reso.

I do believe the issue is with the card and not my monitor?  Or perhaps a combo of both.

Here is a list of forums/sites I have up just so you can see where I'm trying to look for help.  They may hold the answer but I'm not seeing it either because it's too indepth or because it's 4:31am heh.
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)
[http://ubuntuguide.org/#generalnotes](http://ubuntuguide.org/#generalnotes)
[http://www.ubuntuforums.org/search.php?searchid=1610807](http://www.ubuntuforums.org/search.php?searchid=1610807)
[http://wiki.x.org/wiki/FAQ](http://wiki.x.org/wiki/FAQ)

Any assistance will be greatly appreciated, either through direct answer to my question or direction as to where I can go to get some help.

I'm really wanting to learn more and use Linux more (not that I have a choice on my desktop having wiped out windows lol).  I'm certainly not giving up.  It's just the command line is pretty bleak and I like GUIs with eye-candy and the like.  Residuals from my years of windows I guess.

Thank you in advance!!

---

### Post by tktreload on 2005-09-05
hi

when you are on the console and try to start the X server what errors do you get back?

If you dont like the small resolution on the tty you can change it by adding vga=791 for 1024*768 or vga=794 for 1280*1024 to your grub menu.lst.

add it to the a line so that it looks something like:
kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda2 ro quiet splash vga=794

then at least you can look at nice hi res tty...until the problem is sorted  \\:D/

---

### Post by Oberkorn on 2005-09-05
Thanks for the reply!

From the console I type X and here is the reply:

(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Thanks for the assistance.

---

### Post by Oberkorn on 2005-09-05
Update:

I was reviewing my /var/log/Xorg.0.log file and noticed a couple of things:
1)  says "unknown chipset" in lines such as
(--) PCI:*(5:0:0) ATI TEchnologies Inc unknown chipset (0x5e4b) rev 0, Mem @ 0xd0000000/28, 0xe1000000/16, I/O @ 0xa000/8
(--) PCI: (5:0:1) ATI Technologies Inc unknown chipset (0x5e6b) rev 0, Mem @ 0xe1010000/16

2)  And yet it appears my vid card is showing up in the chip sets.  
(II) v41 driver for Video4Linux
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver ATI Rage 128 chipsets: (lists numerous Rage cards then it goes)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
then I scroll down and find my card:  ATI RADEON X700 PRO.  Now I do notice that some of the others like the X600 and the X800 have (RVxxx) where the X700 PRO entry does not.  Could that be a problem and the source of the "unknown chipset"?  Because I find it odd that it would say "unknown chipset" if the autodetect in the xserver-xorg reconfigure is able to notice (RV410).  That is ofcourse it knows it there but doesn't have the support yet.  Dunno.

And I was reading about going to places like Mesa or Gatos and the sites were out of control.  Very complicated stuff to get the drivers.  Which brings up a side question: I don't have my network configured yet.  So I either have to fix it from the command line (which I assume is possible) or get the driver and put it onto a floppy.  Not sure how to do either but I would think fixing the network would be the better solution.

Either way, hope this sheds some more light on my issue.

Thanks!

---

