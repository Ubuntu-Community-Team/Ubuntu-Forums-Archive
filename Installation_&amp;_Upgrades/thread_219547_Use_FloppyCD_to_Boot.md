---
title: "Use Floppy/CD to Boot?"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by 67comet on 2006-07-20
Hello all,

I've got Linux on all my boxes here at the house. However my wife is fed up with dual booting. So I thought, could I leave the MBR alone, and boot with a floppy inside?

Anyone know if this'll work? Maybe boot from a cd to the hard drive? I hate to remove linux from her computer when they are all playing so nice together otherwise.

Thanks for any ideas ahead of time,
Justin

---

### Post by Herman on 2006-07-20
Hello, 67comet,

You can 'hide' the grub menu during bootup, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu") to see how. She won't see the grub menu, but you can catch it by pressing 'Esc' at the right time. This way is the quickest and easiest.

You can make a GRUB CD, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD") for that.

If you have the 'Alternate' install disk, it's easy to make a GRUB floppy disk, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") to how to install GRUB anywhere with the 'Alternate' Install CD. Type (fd0) on the line when you get to the step illustrated as step 11.

Choose whichever of those suits you best, All the best, Regards, Herman :D

---

### Post by 67comet on 2006-08-09
Those both look pretty good. My plan is to install Ubuntu to the hd on my computer, then turn around and put that harddrive in the other computer. Use the CD rom to boot into the harddrive.

Think it'll work?

*** Edit ***
I followed the steps here and all went well, except for the mkisofs part. [http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD](http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD) . This is what it tells me:
```

justin@JustinsUbuntuBox:~/iso$ mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \ -boot-load-size 4 -boot-info-table -o grub.iso iso
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node -  -boot-load-size

```

I tried to cd into the ~/iso directory so boot was the next visiable directory, and it's the same storie.

My biggest concern is not to touch the MBR of the new box. (Guess I could install to fd0, then fire up the XP disc and let it correct the MBR for me.

Justin

---

### Post by Herman on 2006-08-09
67comet, Thanks for letting me know that. It isn't anything you are doing wrong, I just tested that and I am getting the same error message too. I will try to find out  more about that when I get time. I have removed that how-to from the page for now. It seems as though maybe it's due to changes made in our software, possibly. It used to work last time I tried it. I'll see if I can find a new command for it or else I'll have to leave that item out. Sorry for the inconvenience of not having it work.
For the moment, here's a good how-to on [GrubHowto/BootFloppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28CategoryDocumentation%29")

Actually, I just regard the MBR as just another sector on my hard disk, which I overwrite or erase as many times as I please. Some days I overwrite mine several times. It hasn't hurt mine yet. Everyone can use their own computer the way they like though, do whatever makes you happy, and what you feel comfortable with. :D
Regards, Herman :D

Edit, about swapping the drive from one PC to another, you'll need to be sure the drive number will still be the same, eg (hd0). 
Otherwise GAG Boot Manager would be better for your purpose, GAG is a graphical boot manager that can run for a floppy disk, CD-ROM, or install to a hard disk,                     GAG Boot Manager Page..................................................................................[GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")
I think you'll have better results if you give GAG Boot Manager a try. Being graphical, it's a lot quicker and easier to reconfigure GAG when you change things around.
All the best. Herman :D

---

### Post by Herman on 2006-08-26
>  *** Edit ***
I followed the steps here and all went well, except for the mkisofs part. [http://users.bigpond.net.au/hermanzo...MAKE_A_GRUB_CD]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD") . This is what it tells me:
     Code:
     [LEFT]justin@JustinsUbuntuBox:~/iso$ mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \ -boot-load-size 4 -boot-info-table -o grub.iso iso
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node -  -boot-load-size[/LEFT]
 
 Okay, 67comet, If you are still there, or if anyone else wants to make their own Grub CD, it's fixed now.
It seems that the command to make the CD needs to be on two lines, like so, ```
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \ 
 -boot-load-size 4 -boot-info-table -o grub.iso iso         
``` If it's all in on one line it won't work, that was the problem. It was my fault, sorry, I probably changed it one time when I was tidying up the page, not realizing it would have a detrimental effect. It's fixed now, and I simplified the rest of the how-to as well.   :D
Regards, Herman

---

