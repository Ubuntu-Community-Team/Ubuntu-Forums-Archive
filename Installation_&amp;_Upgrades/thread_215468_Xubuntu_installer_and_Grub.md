---
title: "Xubuntu installer and Grub"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by piaggio on 2006-07-14
I just installed Xubuntu 6.06. It overwrote my MBR with Grub. Did I not see some option to do otherwise? Did I not see some warning that it would do this? Is this my mistake, or did it really just overwrite my MBR without any warning or option to do otherwise? If this is really the case, please, please change it before the next release. At least give us a warning. 
I found [instructions ]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-46088")from IBM that helped me configure Grub so I can use the Recovery partition (My system is dual boot, and I will need to reinstall XP sooner or later), but I'm not quite sure what the first part does. 

 title Original Preload

    hide (hdX,Y)
    rootnoverify (hdX,Z)
    chainloader+1

It sounds like it should hide the service partition so I don't accedentaly overwrite it, but I'm not sure what to put for Y, and Z. The service partition is hda2, and Windows is hda1. Linux is hda3. Can anybody help?

---

### Post by Herman on 2006-07-14
> I just installed Xubuntu 6.06. It overwrote my MBR with Grub. Did I not see some option to do otherwise? Did I not see some warning that it would do this? Is this my mistake, or did it really just overwrite my MBR without any warning or option to do otherwise? If this is really the case, please, please change it before the next release. I presume you used the new 'Desktop' Live/Install CD. That was developed to install Ubuntu fast and easy because so many people complained that the traditional installer, which has more informative messages and some confirmation screens and the full range of bootloader options was too complicated for most new users. 

The tradititional installer is still available, as the 'Alternate' install CD, and still features the old familiar text based partitioner which only needs half the amount of RAM. many people still prefer it. 

Anyway, to your present question:
>       title Original Preload[INDENT]       hide (hdX,Y)
       rootnoverify (hdX,Z)
       chainloader+1
     [/INDENT]title Maintenance Partition[INDENT]       unhide (hdX,Y)
       rootnoverify (hdX,Y)
       chainloader+1

     [/INDENT]It sounds like it should hide the service partition so I don't accedentaly overwrite it, but I'm not sure what to put for Y, and Z. The service partition is hda2, and Windows is hda1. Linux is hda3. Can anybody help? Well, to me it looks like they mean this will allow you to 'hide' the service partition because Windows might not boot if it can 'see' another Windows on the same disk. In GRUB numbering, we convert hda to hd0, because GRUB numbering always begins counting from zero instead of one, and uses numbers instead of letters for designating hard drives.
Partition numbers also count from zero with grub, so 'hda1', (your Windows partition),  becomes 'hd0,0' in GRUB's numbering scheme.
Your Service partition, 'hda2', will  be called 'hd0,1' as far as GRUB is concerned. Therefore I think this should be right,
```
title Windows Operating System
hide (hd0,1)
rootnoverify (hd0,0)
chainloader+1    
  
title Service Partition
unhide (hd0,1)
rootnoverify (hd0,1)
chainloader+1

``` I hope that works for you, I'm  not very experienced with the hide/unhide commands myself.  I always thought we were supposed to use the hide/unhide commands in pairs together in the same operating system entry, for example:
```
hide (hd0,0)
unhide(hd0,1)
rootnoverify (hd0,1)

hide (hd0,1)
unhide (hd0,0)
rootnoverify (hd0,0)
``` but probably I'm wrong and they're right, I learn something new every day. Maybe it has something to do with how it's combined with other commands like 'savedefault' , I don't see that here, so maybe that's why we only need one hide or unhide command at a time for this useage. I hope it works for you.
Good luck with it, Regards, Herman :D

---

### Post by piaggio on 2006-07-14
> I presume you used the new 'Desktop' Live/Install CD. That was developed to install Ubuntu fast and easy because so many people complained that the traditional installer, which has more informative messages and some confirmation screens and the full range of bootloader options was too complicated for most new users.

The tradititional installer is still available, as the 'Alternate' install CD, and still features the old familiar text based partitioner which only needs half the amount of RAM. many people still prefer it.

Oh. It's my mistake then. I see the note about using it to install Grub in places other than the MBR. ](*,) I wish I'd seen that. It would have been easier, too; the live cd takes roughly half an hour to boot on my computer. Well thank you; I'll remember that the next time I install.
> 
title Windows Operating System
hide (hd0,1)
rootnoverify (hd0,0)
chainloader+1    

Oh, so the first part is for the Windows partition? That makes sense.  I'll try this out. Thanks.

---

### Post by piaggio on 2006-07-14
That worked. Thank you.

---

### Post by Herman on 2006-07-14
piaggio, I am very happy that was succesful. congratulations! :KS

Now that you have GRUB, you will really like it, I think, it is a very capable bootloader. 
One of the biggest advantages of using GRUB is that your Linux (Ubuntu) kernels will be in GRUB's automagic kernel's list which is updated automagically when Ubuntu has an update and a new kernel is installed. Ubuntu will boot up as usual and you won't need to update the Ubuntu entry manually with the new kernel's details.  GRUB also is able to be customised a great deal to make it work the way you like, or just for fun and good looks too.

One thing you can easily change is the title for the operating system, you can replace that with anything you like on that line, for example as follows,
>                                title Windows Operating System
hide (hd0,1)
rootnoverify (hd0,0)
chainloader+1 >                                title Windows XP of piaggio
hide (hd0,1)
rootnoverify (hd0,0)
chainloader+1 Also it is possible to 
(a) change the default operating system that is booted if no-one is watching while the computer boots up
(b) Set the timer to a different number of seconds
 (c) Change the colors of the grub menu to pretty colors or add a nice picture for the background (called a 'splashimage')
(d)  hide the grub menu during boot-up
(e) use GRUB's Command Line Interface to find and boot any operating system that is bootable. That can help in all kinds of tricky situations.
(f) make a GRUB CD for your computer for an emergency.
  ... and quite a few other tricks and customisations as well. 
To find out more, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm").

Most people really like GRUB when they find out they can do a lot of things with it. Other bootloaders are extremely boring and useless by comparison.
Happy Ubuntuing as well! Regards, Herman :D

---

