---
title: "I get an error message while trying to boot from the live cd"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Dan777 on 2006-11-15
I've got as far as opting to boot from the cd, my computer displays the ubuntu logo and some options. I choose "start or install..." and at the next screen I get an error message like this:


"[17179571.860000]PCI: cannot allocate resource region 0 of device 0000:03:00.0"


this line is repeated four times, identical except instead of 0 it says region 1, 2 etc

Then at the end of those messages it says:

"[17179571.860000]PCI: Error while updating region 0000:03:00.0/0 (0000c00 !=00000000)


[17179571.860000]PCI: Error while updating region 0000:03:00.0/2 (0000c00 !=00000000)"



Please help!!

---

### Post by Dan777 on 2006-11-16
I also tried with the 6.06 live CD, Thats gets as far as the Ubuntu logo with a loading bar, but then it cuts out to a screen saying "uncompressing linux, booting the Kernal, OK..." then it stops and nothing happens.

Are there any known issues with Core 2 Duo processors, is linux compatible with the architecture?

---

### Post by taurus on 2006-11-16
How fast did you burn those ISO images?  Make sure you burn them slow like 4x because fast burning CD can sometimes cause problems.

---

### Post by garbagefan2 on 2006-11-16
> **taurus said:**
> How fast did you burn those ISO images?  Make sure you burn them slow like 4x because fast burning CD can sometimes cause problems.

I had to burn them at 4x. When I tried 6 or 8x it didn't burn right.

---

### Post by Dan777 on 2006-11-17
It's not burn speed, I've tried two versions both burned at 4x
I tried 6.10 and then 6.06, when i tried 6.10 i got the error message during startup like i posted, and when i tried 6.06 it let me select an option from the boot menu, then when the ubuntu logo appears and there is a loading bar, the bar just freezes.

---

### Post by taurus on 2006-11-17
What's the spec of your machine then?  You can always try the alternate CD...

---

### Post by Grim Tuesday on 2006-11-17
hmm i have a problem somewhat like that... it's just the live cd hangs at the loading phase.

---

### Post by Dan777 on 2006-11-17
My specs are :
Core 2 Duo E6400 @ 2.13 GHz
2 GB DDR2 Ram
Nvidia GeForce 7900 GS 256MB Gfx card

I'll give the alternate cd a try too.

---

### Post by taurus on 2006-11-17
Maybe Dapper (the alternate CD) works better for you!!!

---

### Post by Dan777 on 2006-11-17
I tried with the alternate CD and it failed, citing inability to 'mount' my CD-ROM drive... it asks for drivers on a floppy, but I don't have any, I don't even have a floppy drive.

---

### Post by K.Mandla on 2006-11-18
I've had that happen before, where it couldn't mount the CD-ROM. Occasionally it worked for me to tell it to try again, and on the second attempt it found it.

Of course, that machine was a 120Mhz Pentium, and comparing it with yours, all I can say is ... no guarantees. :)

---

### Post by hulleye on 2006-11-18
Am having the exact same problem. I have a dual core 3GHz Pentium. It wouldn't boot up with the Edgy Live CD, dumping me into a busyboot(?) command line (covered elsewhere). I decided to try using Dapper 6.06.1 but after choosing the Startup from disk option, it reads "Uncompressing Linux Kernel, OK... booting" or something like that and gets stuck there.

I didn't want to install on this machine, since I wanted to test out hardware compatibility before making a more permanent move. That's why, I'd rather not try out the Alternate installer until I can get the Live CD to work.

Any help would be appreciated.

---

### Post by Dan777 on 2006-11-23
Ok, I've tried Ubuntu/Kubuntu/Xubuntu (all 6.10) and Ubunutu 6.06/Kubuntu6.06/Alternate Ubuntu.

None will install, I'm guessing that since someone else using a C2D is having problems means that there's an issue with intel's new core 2 duo processors. 

Giving up.

---

### Post by LxP on 2007-01-27
Yes, I'm also having the same problem with my newly installed Intel Core 2 Duo E6300.  Will post back if I find a solution; in the meantime please speak up if there's a known one.  :)

---

### Post by confused57 on 2007-01-27
> **LxP said:**
> Yes, I'm also having the same problem with my newly installed Intel Core 2 Duo E6300.  Will post back if I find a solution; in the meantime please speak up if there's a known one.  :)

You may have to wait on Feisty release or try the Feisty testing live cd...the newer kernel may have better support for the latest hardware...of course, that may have nothing to do with your problem.

---

### Post by Dan777 on 2007-01-30
OK, I just tried installing version 6.06 again, I didn't get the PCI error message, I got the ubuntu load screen, that seemed fine, then it went to a black screen with the text "uncompressing linux... OK, booting the kernel" same as b4...

then nothing happened... left it for about 10 mins, so I'm pretty sure it hung.

---

### Post by dbqp on 2007-02-01
I had this same exact error happening on my son's computer (go figure, the older dad is trying to convince the younger to switch to linux) so that all but one computer is running Linux Ubuntu.

Magically, everytime I had the install disk in the optical drive, I could choose to boot from hard drive at the initial menu and the OS would load without problem.  Take the CD out and the system would freeze at the splash screen after the PCI: error 0000000.0000 (blah blah blah).

The only logical explaination I can give is due to the EIDE and SATA mix of drives in his Acer Media Center PC. This is after the drive is wiped and repartioned. It seems with the EIDE/SATA mix, the BIOS wants to see the IDE drives as the initial Primary and SATA only as an after thought.  I did make sure the Hard Drive was the boot device and all the other BIOS variables, but could never get it to load the OS without the disk inserted in the drive.

At least when the CD is inserted, it forces the machine to rev up the hard drive...

Can anyone else try this that is having this error and confirm if this is just a "one off" for his particular machine or across the board?

Of course, we don't want to leave it like this and will still be hunting for answers!

---

### Post by Dan777 on 2007-02-01
Well all my HDDs are SATA, and my disc drive is on an ide cable.. so you could be right... but if thats the case its surprising you dont hear it more often.

what specs is the computer you had this problem with?

I've got a core 2 duo e6400, on a ECS P-965

---

### Post by dbqp on 2007-02-02
> **Dan777 said:**
> Well all my HDDs are SATA, and my disc drive is on an ide cable.. so you could be right... but if thats the case its surprising you dont hear it more often.

what specs is the computer you had this problem with?

I've got a core 2 duo e6400, on a ECS P-965

It's an Acer P4 3.0GHz (single core)
1GB RAM
2 Optical drives on IDE Channel as Master and Slave
1 200GB Seagate SATA Drive as Master
ATI Graphics with 256MB Shared Memory
Has all the bloated hardware for Media Center Edition (card readers, extra audio/video connections, etc...)

Maybe this is a problem not due to the Dual Core, but with the mix of opticals on IDE and HDD on SATA?

Hmmm...did you try this method out or have you solved the PCI: error problem?

---

### Post by Raptormn on 2007-02-02
i having the same problem same setup as well

Intel E6700
2GB Ram
2 Seagate SATA drives
Lite-on DVDRW IDE
8800GTX

---

### Post by Raptormn on 2007-02-02
well i am going to try Feisty herd 3. todays version and see if that works :-k

---

### Post by Dan777 on 2007-02-02
If its due to mixing sata and ide devices then I guess I'm stuck with windows... because I can't rightly use my PC without its hard drive or disc drive.

---

### Post by Raptormn on 2007-02-02
ok so i tried the live kubuntu feisty cd it load alot further but no luck so i am going to try the alt cd see if that works.

---

### Post by notquitehere188 on 2007-02-03
i am having the exact same problem

my hardware is:
C2D E6400
GA-965P-S3 MoBo
2GB corsair ram
ati X1900 graphics
320GB sata
40GB ide

I seem to also share the mixed sata ide, and C2D

i had managed to install in text mode, but it still did not work when i tried to boot it getting the same error as the live CD

i installed it on the ide 40 GB, on the same IDE channel as my DVD Drive

sadly, since it did not work, i formatted over it with vista

---

### Post by Dan777 on 2007-02-03
I think the only common hardware link is the P965 chipset, must be an anomaly with it's sata controller? I know people running linux who have Core 2 duos in laptops, so it can't be that. And almost everyone uses sata hard drives, and I know plenty using linux.

---

### Post by Dan777 on 2007-02-16
It is the 965 chipset thats causing the problems. Feisty was supposed to fix this, and it kind of did, since I can get in the live environment using the 7.04 CD, but when I try to install its not detecting my HDDs, so there may still be problems with the sata controller. I'll keep you posted with how I get on.

---

### Post by fingidor on 2007-03-11
Any news on the problem?

---

### Post by Dan777 on 2007-03-11
Well, I am basically waiting to try again once feisty is finished completely. I don't want to be wasting DVD-Rs on the daily alphas, so I'm biding my time :)

---

