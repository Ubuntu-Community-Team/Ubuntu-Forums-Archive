---
title: "Ubuntu is gone with the wind !! Help !"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by a_ahmy on 2007-11-11
[CENTER]well a month ago i had dual booted ubuntu & XP after that i did format my C:/ drive which is where XP is installed after finishing i can no longer access D:/ drive where Ubuntu is being installed !!?!?! 

so basically its like this 

C:/ Windows :mad:

D:/ Ubuntu is no longer accessible also when booting up i`n not seeing the Boot menu !!?! it just loads straight up to XP leavin` me no choices :-?



any ideas on how to solve this problem !!![/CENTER]

---

### Post by ajgreeny on 2007-11-11
You probably installed grub in place of the windows MBR and now having replaced windows, grub has also gone.
**DON'T PANIC - **

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

PS  If you don't have a copy of ubuntu liveCD use any other live CD, eg DSL, Puppy etc etc. but do the same commands (you may not need the sudo part of the command, however.)

---

### Post by a_ahmy on 2007-11-11
Roger that ! LiveCD is about to load  ima goin` to try what you have mentioned out ! will keep ya updated 

thanks i really appreciate your help ,



:guitar:

---

### Post by a_ahmy on 2007-11-11
sh!t ! now i`m having trouble with ma Philips DVD +rw Sdvd8820 :( it won`t read Disks !! , guess i`ll have to replace it :cry:,

---

### Post by a_ahmy on 2007-11-17
aight ~ i`m gettin` this Error now ""Error 17: Cannot Mount Selected Partition"" :( 

I'd appreciate any help

---

### Post by Dragos Largu on 2007-11-17
I'm havin kinda the same problem, I've had Ubuntu and Vista, but now I've installed XP on an empty partition, and the funny thing is I can'd acces any thing else than XP. So, if Vista was on C:\ this corresponds to HD1? My XP is on HD8 and ubuntu on HD6. Can anyone run me through the process of getting GRUB to recognise all 3?

Ty in advance

---

### Post by Laserbeast on 2007-11-17
A good thing for every new Linux user wanting to dual-boot Windows and Linux is to either install Windows first, followed by the Linux distro.. or know how to reinstall GRUB if you really need to put Windows on the HD **after** you've installed Linux.

Windows likes to take control and redo the MBR :(

---

### Post by a_ahmy on 2007-11-17
> **Dragos Largu said:**
> I'm havin kinda the same problem, I've had Ubuntu and Vista, but now I've installed XP on an empty partition, and the funny thing is I can'd acces any thing else than XP. So, if Vista was on C:\ this corresponds to HD1? My XP is on HD8 and ubuntu on HD6. Can anyone run me through the process of getting GRUB to recognise all 3?

Ty in advance


check this post it might help , actually i`m readin` it now ~ goin` in action soon ~ :) [http://users.bigpond.net.au/hermanzone/p15.htm#17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

---

### Post by Dragos Largu on 2007-11-17
> **a_ahmy said:**
> check this post it might help , actually i`m readin` it now ~ goin` in action soon ~ :) [http://users.bigpond.net.au/hermanzone/p15.htm#17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

Big page :popcorn: ty, I'l post feedback.

---

### Post by pcostanza on 2007-11-17
When I had a similar problem months back, the Super Grub Disk worked great for me.  You should give that a try.

---

### Post by ElmFt7eZ Is Here on 2007-11-18
u have prb ok come i will explan 


:guitar:










































&#1578;&#1610; &#1575;&#1605;&#1606;&#1593; &#1610;&#1575; &#1582;&#1575;&#1605;&#1585; &#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607; &#1583;&#1610;&#1585;&#1578; &#1575;&#1604;&#1593;&#1575;&#1585;   &#1581;&#1578;&#1609; &#1601;&#1610; &#1605;&#1606;&#1578;&#1583;&#1610;&#1575;&#1578; &#1575;&#1604;&#1575;&#1581;&#1606;&#1576;&#1610;&#1577; &#1578;&#1578;&#1589;&#1585;&#1589;&#1585; &#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607; &#1588;&#1606;&#1608;  &#1605;&#1578;&#1601;&#1591;&#1581;&#1586; &#1601;&#1610; &#1605;&#1606;&#1578;&#1583;&#1609; &#1607;&#1584;&#1575; &#1588;&#1606;&#1608; &#1575;&#1604;&#1602;&#1610;&#1578; &#1581;&#1605;&#1575;&#1605; &#1608;&#1605;&#1581;&#1576;&#1587; &#1602;&#1606;&#1610;&#1606; &#1578;&#1578;&#1601;&#1591;&#1581;&#1586; &#1601;&#1610;&#1607; 

:lolflag:





&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;&#1607;

---

### Post by Alpha1Dash1 on 2007-11-18
Not sure I get the above post. 

Anyhow, moving on, I had similar problem about 1 year ago (including a dodgey dvd writer!). As has been suggested, super grub sorted it for me, because luckily it comes in 3 formats - iso, floppy & pen-drive. If you can't boot from a live cd, but still have a floppy dd, this should work for you too. I downloaded it from here: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by a_ahmy on 2007-11-18
> **Alpha1Dash1 said:**
> Not sure I get the above post. 

Anyhow, moving on, I had similar problem about 1 year ago (including a dodgey dvd writer!). As has been suggested, super grub sorted it for me, because luckily it comes in 3 formats - iso, floppy & pen-drive. If you can't boot from a live cd, but still have a floppy dd, this should work for you too. I downloaded it from here: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

well guess what ! i`v downloaded what u call ""super grub"" and it didn`t work for me ! i tried almost every Tool in there , the thing is that the Grub menu is there when i boot but after selecting XX.XX.XXX Generic i get this Error message !"" Error 17 Cannot Mount Selected Partition"" :(

Super Grub is a great Tool indeed  :guitar:

Guys we need Feedbacks !

---

### Post by a_ahmy on 2007-11-18
just got back from google ! the Error explains that the partition exists but the filesystem type cannot be recognized by GRUB ! ! ! 

now this`s really somethin` any Clues so far !!! ](*,)

---

