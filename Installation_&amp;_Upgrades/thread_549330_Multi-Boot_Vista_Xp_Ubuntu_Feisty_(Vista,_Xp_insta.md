---
title: "Multi-Boot Vista Xp Ubuntu Feisty (Vista, Xp installed FIRST)"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by TCOzman on 2007-09-12
Ok so heres my problem as im sure you already know...I recently purchased a new 120 gb hard drive for my alienware laptop and i have installed Vista and XP first.  I have correctly edited Vista's bootloader to display both Vista and Xp respectively.  Now here comes the problem...in order to have ubuntu feisty to triboot ill need the grub loader but i dont want two bootloaders before i can get into vista/xp.  So can someone please direct me as to what to do.  

I also want to add i DO NOT WANT TO REFORMAT VISTA AND XP in order to have ubuntu.  There have been many tutorials that i have seen that require a certain order that isnt with vista and xp installed first so is there anything i can do to have my dear ubuntu to tri-boot with vista and XP??? Any suggestions will be appreciated! Thank you in advance

---

### Post by logos34 on 2007-09-12
No formatting of windows necessary (but highly recommended -- sorry, I need to vent my spleen against MS once a day).

Install Ubuntu using the **Alternate CD**, but make sure to write Grub to the bootsector of the root partition, **not the MBR**.  Use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") to add linux to vista boot manager.

If your need to shrink Vista it would probably be best to do so using the built-in tool, and to make an **extended partition** out of the freed up disk space.  Then put your linux /, /swap and maybe /home inside.

[http://apcmag.com/dualboot](http://apcmag.com/dualboot)
[http://www.techenclave.com/forums/printthread.php?t=95295](http://www.techenclave.com/forums/printthread.php?t=95295)
[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by TCOzman on 2007-09-12
Thank you for your quick reply and good instruction.  My only problem with the information that you gave me is the "alternate" disk.  Im not sure what you mean, but ill read up on all the links you gave me because i am not at all equipped with any linux knowledge. I usually just use the text editor and some other things.

Also keep in mind i have 12 gigs of space that i saved solely for ubuntu and also from the tutorials youve provided they all are dual boot not multi-boot.  And from my experience there is a difference because in order for me to have the bootloader read xp and vista together i had to edit it in vista.  In the past i originally had Vista and Ubuntu on the GRUB loader because it was just too easy but xp is the wild card... oh well ill just wait before i do anything and try to gather more information.  

One more thing...Xp and Vista make around 10000 times more sense to me than any kind of linux product out there and i hold windows near and dear to my heart because i grew up learning on windows o/s such as windows 3.11 and windows 95. 
(Sorry i really needed to vent too my networking class was a bummer today)

Ok three hours later i decided to bite the bullet and forget the fact that ill have two bootloaders instead of one (its just quicker this way)...so now im happily writing this from my newly installed ubuntu.  Thank you very much Logos34 for your help and if you have any suggestions about removing one of the bootloaders (doesnt matter to me) i would absolutely love it.  So im gonna go and make ubuntu look like Mac OSX all over again lol...

---

### Post by logos34 on 2007-09-13
> **TCOzman said:**
> Thank you for your quick reply and good instruction.  My only problem with the information that you gave me is the "alternate" disk.  Im not sure what you mean, but ill read up on all the links you gave me because i am not at all equipped with any linux knowledge. I usually just use the text editor and some other things.

I was referring to this:
> 
Download URL: [http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)
Ubuntu Edition: Ubuntu 7.04 alternate
Computer Platform: i386
Download Location: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

> Also keep in mind i have 12 gigs of space that i saved solely for ubuntu and also from the tutorials youve provided they all are dual boot not multi-boot.  And from my experience there is a difference because in order for me to have the bootloader read xp and vista together i had to edit it in vista.  In the past i originally had Vista and Ubuntu on the GRUB loader because it was just too easy but xp is the wild card... oh well ill just wait before i do anything and try to gather more information. 

Well, normally when you install vista after XP the former detects the latter and becomes the 'master' bootloader, chainloading it much as grub chainloads windows.  (On the other hand XP's ntdr can't load vista's boot manager).  So when you install linux on top of this, Grub in turn overwrites the Vista bootloader on the MBR, and adds an entry just for vista.  You choose this, which brings up the vista menu giving you the choice between vista or XP.  So it's a two-step process to boot windows. But sometimes XP refuses to boot, so you have to get in there and edit BCDedit manually.  Nor is Grub flawless, and sometimes there's a problem where it refuses to boot vista. So you have to resort to using vista bootloader instead to boot linux.

> One more thing...Xp and Vista make around 10000 times more sense to me than any kind of linux product out there and i hold windows near and dear to my heart because i grew up learning on windows o/s such as windows 3.11 and windows 95. 
(Sorry i really needed to vent too my networking class was a bummer today)

I guess we'll have to agree to disagree.  I too began with windows 3.x (and before that the early Macs, but most of my life experience with computers has been in the Microsoft world).  But it's not dear to my heart--quite the opposite.  If anything I resent it more and more that Microsoft has had a monopoly on the desktop environment all these years, and thus prevented the rise of alternatives like linux, which, after all has been around since 1992.   I'm no expert on this but it seems to me that windows makes sense only if you need universal out-of-the-box networking and hardware/peripheral support, and software support where no native linux version exists and WINE or Crossover Office just won't cut it (games, IE-based web development, MS Office, Photoshop, etc).  Otherwise linux alternatives can be found with only a little effort.  There's been a sea-change in hardware driver support in the last few years, Sun has just come out with an .ODF plugin so you can edit OpenOffice docs in windows, HP is set to ramp up their linux support, Dell has jumped on the Ubuntu bandwagon, google is writing apps for linux, local and regional governments the world over (developing and industrialised) are dumping M$ for FOSS alternatives...In fact, the MS deal with Novell (and the whole ensuing brouhaha over the secret 'patents covenant') should alert you to the fact that MS is seeking more interoperability with linux (on their terms of course) because they realize that linux is the future and the days of the monolithic closed-source OS are numbered.  It's just that they want to control its direction and 'synergize' it with their own interests--to simplify, the old 'if you can't beat 'em join 'em' strategy. That's the way it looks to me, at least.

> 
Ok three hours later i decided to bite the bullet and forget the fact that ill have two bootloaders instead of one (its just quicker this way)...so now im happily writing this from my newly installed ubuntu.  Thank you very much Logos34 for your help and if you have any suggestions about removing one of the bootloaders (doesnt matter to me) i would absolutely love it.  So im gonna go and make ubuntu look like Mac OSX all over again lol...

Glad everything works, even if you have to go through two menus.  Try the **EasyBCD** link I posted above if you want just one bootloader.

---

