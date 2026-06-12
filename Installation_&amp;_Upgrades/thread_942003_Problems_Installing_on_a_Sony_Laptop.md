---
title: "Problems Installing on a Sony Laptop"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by bigDs54 on 2008-10-08
hey all, new to the linux experience but i've been reading the archives to find a solution to my problem. i have a sony vaio vgn-nr430 laptop came with vista, backed it up on my external, i downloaded the live cd ubuntu-8.04.1-desktop-i386.iso, md5sum checks out, i made a 21 gig partition, i already tried burning at lowest speed even different programs, have used infra and cdburnerxp, but the all the cds stay stuck on the beginning screen anytime i try to press enter on any of the options, the one with the options to check cd, install...etc, tried the cd on an old desktop of mine and it worked like a charm, fell in love with it in the 5 minutes i was messing with it :), any ideas on what could be the prob? thanks in advance! p.s. not trying to sound like an *** on my first post but kinda on a time-crunch.. i deploy on tuesday :) :( >:|
- D

---

### Post by Pumalite on 2008-10-08
Have you tried the Alternate CD?

---

### Post by bigDs54 on 2008-10-08
> **Pumalite said:**
> Have you tried the Alternate CD?

thats the text version right?

---

### Post by Pumalite on 2008-10-08
Right:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Kuroyume on 2008-10-08
you may be suffering from [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137"). Try booting with the AC adapter unplugged from the computer. If you can boot that way, do a normal install and get the latest kernel upgrades on the installed system you should be able to boot normally.

---

### Post by bigDs54 on 2008-10-08
> **Pumalite said:**
> Right:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

thanks for the help but alternate fails cd check i get "./pool/restricted/d/drdsl/drdsl_1.2.0-1_i386.deb" then something about failing md5sum, but i checked iso before burning?

---

### Post by bigDs54 on 2008-10-08
> **Kuroyume said:**
> you may be suffering from [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137"). Try booting with the AC adapter unplugged from the computer. If you can boot that way, do a normal install and get the latest kernel upgrades on the installed system you should be able to boot normally.

thanks for the lead am checking now wont boot by just unpluging ac but their saying removing the 'quiet' option how do i do that?

---

### Post by Joe2Shoe on 2008-10-08
I had problems installing Ubuntu on my Vaio, also.
Insert the CD, reboot the laptop, at the first screen, hit F6 for 'Options', type "noapic" (without the quotes), then hit Enter.
Worked for me.
Good luck.
Joe.

---

### Post by Partyboi2 on 2008-10-08
> **bigDs54 said:**
> thanks for the lead am checking now wont boot by just unpluging ac but their saying removing the 'quiet' option how do i do that?
After you have booted the ubuntu cd and are at the main menu press F6 and remove the word "quiet" then press "enter to boot.

---

### Post by bigDs54 on 2008-10-08
> **Joe2Shoe said:**
> I had problems installing Ubuntu on my Vaio, also.
Insert the CD, reboot the laptop, at the first screen, hit F6 for 'Options', type "noapic" (without the quotes), then hit Enter.
Worked for me.
Good luck.
Joe.

did that and it just loaded vista instead :(
did you use live cd?
trying it normal just made everykey beep when pressed with frozen screen
and trying it it in safe grafix just loaded vista instead.
what vaio are you using?

---

### Post by bigDs54 on 2008-10-09
> **Partyboi2 said:**
> After you have booted the ubuntu cd and are at the main menu press F6 and remove the word "quiet" then press "enter to boot.

tried to no avail still just freezing up without anything on screen changing

---

### Post by Joe2Shoe on 2008-10-09
I use Active@ISO Burner to burn .iso files to CD/DVD.  Never have any problems.  It's free!  
[http://www.ntfs.com/iso-burning.htm](http://www.ntfs.com/iso-burning.htm)  

I installed 8.04.1 on my Vaio PCG-FX210 (7 years old).  It has an AMD Athlon (Palomino) 1.2GHz Mobile CPU, Crucial 512MB PC-100 SDRAM, WD Scorpio 40GB HDD, DVD-ROM, Floppy Drive, 14" LCD.  

If everything works for you in Vista, but not in Ubuntu, I'd say that it's a hardware issue, probably driver-related.  

You may want to try Xubuntu or Kubuntu instead, to determine the problem.  
[http://kubuntu.org](http://kubuntu.org)  based on the K Desktop Environment.
[http://xubuntu.org](http://xubuntu.org)  Xfce Desktop Environment.

Good luck.
Joe.

---

### Post by Kuroyume on 2008-10-09
it seems to me your CD is defective. what media are you burning to? try changing brands, or using a different burner.

---

### Post by bigDs54 on 2008-10-09
> **Kuroyume said:**
> it seems to me your CD is defective. what media are you burning to? try changing brands, or using a different burner.

if its the media wouldnt it not work on the desktop though?

---

### Post by Joe2Shoe on 2008-10-09
> **bigDs54 said:**
> if its the media wouldnt it not work on the desktop though?

That's why I suggested that you type "noapic" after pressing F6 for  Options at the boot-up screen.
Give it a shot.  What do you have to loose?
Good luck.
Joe.

---

### Post by Kuroyume on 2008-10-09
> **bigDs54 said:**
> if its the media wouldnt it not work on the desktop though?

good point... laptop readers can be a pain the *** sometimes though...

try the noapic thing

---

### Post by bigDs54 on 2008-10-09
noapic doesnt do anything , the time it did produce a different result was when i tried in safe grafix mode and it still froze but this time it just made any key i pressed beep, then i tried running fedora 9 live cd and it worked fine, havent installed it though cause i am really leaning toward ubuntu, alternate cd also hangs the same

---

### Post by Pumalite on 2008-10-10
Get ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Download and install
Go to Mode>ISO>Burn; select 1x as the speed of burn.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Clean the lens in your burner, do ms5sum on the iso, check CD integrity before install. Do not use CD-RW

---

