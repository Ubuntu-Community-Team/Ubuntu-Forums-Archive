---
title: "Can you spot the newbie error?"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by nilsderondeau on 2005-10-25
I apologize if you're expecting anything other than another LINUX newbie banging his head against the wall.   I'll tell you what I've been doing--what I need are suggestions for continuing...

My last 24 hours:
1. I'm trying to install ubuntu-5.10-install-i386.
2. I've burned the iso to a bootable disc.
3. After about a dozen tries to get through the entire installation, I burned another disc.
4. I repeated number 3 four times.
a. The verification program in the install routine rejected every CD I burned.
b. The CDs were burned at 4x using Iomega Hotburn Pro and Roxio (neither program has a 1x option)
c. I changed CD brands each time.
5. The install fails at various points because of copy problems from the CD.

Possible problems I forsee:
1. CD media--can ubuntu's install really be this picky?
2. CD burning software is crap
3. CD burner is crap (I've used two different ones)
4. CD drive in the machine to which I'm installing is crap

(I'm beginning to suspect number four)

I'd like to move forward somehow.  Should I:
A. Get new CD burning software?
B. Keep burning CDs while crossing my fingers?
C. Order a distribution CD and sit tight?
D. Simply try a different LINUX distribution?

My machine is an Acer Travelmate 514T.  Here are the specs.  (If anyone can anticipate any further hairpulls, I'd be greatly appreciative.)

Intel Celeron 466MHz

Core Logic Chipset:
ALi Aladdin IV  1531/1533
 
RAM 
64MB 

Video Subsystem
NeoMagic NM2200C  V.DH (NMG5)
2 MB

Hard Disk Drive	
4.1 GB
 
Floppy Disk Drive
1.44MB  3.5"

CD-ROM Drive	
24x CD     TEAC CD-224E-A26

Sound Subsystem
ESS Solo-1 E  (ES1946)
 
PCCard Support:
O2Micro OZ6833T Cardbus controller
1 Type III or 2 Type II / Type I

Pointing Device:
Touchpad

Peripheral Subsystem:
1 Parallel, 1 PS/2 (mouse/keyboard), 1 Serial,
1 VGA, 1 RJ-11, 1 USB,  3 Audio, 1 FIR

Modem: Lucent 56K

---

### Post by natstupid on 2005-10-25
Well, I am a newbie here myself. But anyway try the following suggestions. 

1. CD media--can ubuntu's install really be this picky?
    As far as I know it is not. I have tried it on quite a few different cd's and it worked. The only time it did not work, was when the RW I was using had a huge scratch. 

2. CD burning software is crap
    Have used roxio only once and Iomega never, so I cant really say. However I burnt my cds using [Burnatonce]("http://www.burnatonce.com"). Ensure that you use the default settings. It works well. 

3. CD burner is crap (I've used two different ones)
    Possible scenario. But it would take too much time to confirm this. Try 1,2,4

4. CD drive in the machine to which I'm installing is crap
    Most likely reason. If you are using windows try [Nero CD/DVD Speed]("http://www.cdspeed2000.com/") and use the disc quality test. If you cant, then I suggest you burn 650/700 MB to a CD and boot to a boot prompt, and copy the entire CD to the hard disk. If this goes without any errors then you should be good to go. 

Hope this helps.

---

### Post by K2712 on 2005-10-25
Did you check to see if the MD5SUM matched before you burnt the CD?

---

### Post by brk3 on 2005-10-25
hi, well done on the amount of info provided! But without a doubt your problem is a crappy cd, its happened me loads of times where i use an old blank cd thats being written to a good few times. just get yourself a box of new blank cds and try burning the iso again.

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=K2712]Did you check to see if the MD5SUM matched before you burnt the CD?[/QUOTE]

Erm, now see, you've caught me out.  I've come across the word MD5SUM a few times in other posts.  (You groaning yet?  Go ahead.)  I know what a checksum is, though.  I'll look through this site to see if I can't find the procedure...

---

### Post by cstudent on 2005-10-25
I would suspect a corrupted .iso file. I didn't see where you tried downloading the iso again.

Bill

---

### Post by earobinson on 2005-10-25
im pretty sure the recomend ram for ubuntu is 128

---

### Post by SilentCacophony on 2005-10-25
Hi. At this point, I'd suspect either a bad .iso, or #4 above.

I've personally had an unusually bad time installing Breezy because of an old cdrom drive. Added to that was that I was using cheaper non-branded cdr's. In my case, I installed another old cdrom drive, and it worked fine on that. ;)

Anyway, here's some info on md5sum:

[https://wiki.ubuntu.com/GettingUbuntu](https://wiki.ubuntu.com/GettingUbuntu)

Edit- note that the particular source of the md5sum would be different than on that wiwki page. it'll be listed on the download page, and the sytax would be similar.

---

### Post by az on 2005-10-25
[QUOTE=earobinson]im pretty sure the recomend ram for ubuntu is 128[/QUOTE]
Yes, but that should not affect the installation.  It will just run realy slow.

---

### Post by flower on 2005-10-25
here are few advices (based on my breezy installation which lasted about 5 days) :

1. Try downloading the ISO via BitTorrent, the BT client makes the MD5 check for every piece of the torrent itself :) (I personally had a bad download of the ISO via HTTP, and then re-downloaded it via BT)

2. I had an Acer Travelmate myself - I have to say it was hardly reading the half of the CDs I had ... so ... maybe is the CDROM after all ... 

3. Maybe it will be a nice shot to try to go to the shop and buy the most expensive blank CD they have ... some fancy Verbatim probably .. this worked for me on my Acer CD drive

4. Don't order a CD shipment of Ubuntu ... it will come in 2 months, so ... no point

5. Don't give up installing Ubuntu ... there's no Linux like it ;)

---

### Post by mikedtemple on 2005-10-25
I have a couple of Hoary CDs laying around.  If you're interested, and in the US, I'd be happy to Media Mail one to you.  

You can try to dist-upgrade to breezy from a base Hoary install.  It's not the best option, but if you want Ubuntu now, I'd be happy to oblige.

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=cstudent]I would suspect a corrupted .iso file. I didn't see where you tried downloading the iso again.

Bill[/QUOTE]


Hi Bill,

Um, I neglected to mention that I did indeed download the iso a second time.  For what it's worth, I downloaded it to a completely different hard drive.  Tonight I'll try a third iso download.

Cheers,
N.

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=mikedtemple]I have a couple of Hoary CDs laying around.  If you're interested, and in the US, I'd be happy to Media Mail one to you.  

You can try to dist-upgrade to breezy from a base Hoary install.  It's not the best option, but if you want Ubuntu now, I'd be happy to oblige.[/QUOTE]

That's very kind of you, however, I have to refuse your offer as I live in France.  The tactic ocurred to me, but I haven't yet investigated downloading the isos of previous versions.  Is this possible?

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=flower]
1. Try downloading the ISO via BitTorrent, the BT client makes the MD5 check for every piece of the torrent itself :) (I personally had a bad download of the ISO via HTTP, and then re-downloaded it via BT)
[/QUOTE]

Both ISOs I downloaded were via BT.

[QUOTE=flower]
2. I had an Acer Travelmate myself - I have to say it was hardly reading the half of the CDs I had ... so ... maybe is the CDROM after all ... 
[/QUOTE]

Yeah, I'm beginning to suspect this is the case.  Pity, as this machine is nigh useless as it is and I'm bothering with LINUX in hopes of recovering some of its utility.  Just not worth the money or bother to have a new CD drive installed.

[QUOTE=flower]
3. Maybe it will be a nice shot to try to go to the shop and buy the most expensive blank CD they have ... some fancy Verbatim probably .. this worked for me on my Acer CD drive
[/QUOTE]

I'll give it a shot.  Heretofore, I've been using some really sketchy CDs, but also Memorexes and Samsungs.

---

### Post by leezer3 on 2005-10-25
Hiya,
This almost certainly seems to be the CD drive- Different brands of media are going at different points, and BT means that it should be impossible for you to have a bust ISO. The fact that it is actually trying to install also rules out the problem of the burning software messing stuff up, as if this happens, then the CD won't even boot.
I take it you have a working network- Why not try the netinstall floppies:
[http://ubuntuforums.org/showthread.php?t=75372](http://ubuntuforums.org/showthread.php?t=75372)

Cheers

-Leezer-

---

### Post by joshuapurcell on 2005-10-25
I've had problems burning CDs from ISOs at times... it was the CD burning software configuration that caused the problems. If I remember correctly, **I turned off the option that told the burner to 'close the CD when completed'** or something like that. I was using Nero with an ancient HP burner running at something like 8X (which is as fast as that burner would go). No CD would install until I did this step.

---

### Post by Foaming Draught on 2005-10-25
Hi nilsderondeau, I'm with the earlier poster who said don't give up on ubuntu, there's no Linux like it (for a newbie like me, anyway).
Have you looked on eBay France for an enterprising chap who's burned 5.10 already and is now selling copies for, say, up to 10 euros or so incl postage? I burned my own Breezy Colony, but when I first started experimenting with GNU/Linux I didn't know what an .iso was, leave alone how to burn it to a CD. I didn't mind paying an Australian eBayer AUD20 for 5 Mandrake CDs and postage.
And while you're on eBay, look at the price of RAM for yr Travelmate. If the machine will take it, and it's cheap enough, you'll get another year or so of life from it by putting in at least 256MB and preferably 512MB.

---

### Post by Buffalo Soldier on 2005-10-25
[QUOTE=nilsderondeau]Erm, now see, you've caught me out.  I've come across the word MD5SUM a few times in other posts.  (You groaning yet?  Go ahead.)  I know what a checksum is, though.  I'll look through this site to see if I can't find the procedure...[/QUOTE]

For checking md5sum on Windows I'd suggest you download and install [winMd5Sum](http://www.nullriver.com/index/products/winmd5sum).

Let say for example the ISO that you want is [ubuntu-5.04-install-i386.iso](http://releases.ubuntu.com/hoary/ubuntu-5.04-install-i386.iso).[list]
[*] After you finish downloading that, download the [md5sums](http://releases.ubuntu.com/hoary/MD5SUMS) file.

[*] Open the md5sums file and look at the string of numbers and alphabets corresponding to the ISO you just downloaded. (**f6b3f164c99761234858a4d2c12d0840**  ubuntu-5.04-install-i386.iso)

[*] Run the winMd5Sum application that you have downloaded and installed earlier.

[*] Point it to the ISO file that you've downloaded. Hit **Calculate**. (It will take a few seconds or minute to do the calculation).

[*] Once it display the calculated checksum, go back to the MD5SUMS list and copy-paste the checksum and hit **Compare**.[/list]

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=natstupid]
4. CD drive in the machine to which I'm installing is crap
    Most likely reason. If you are using windows try [Nero CD/DVD Speed]("http://www.cdspeed2000.com/") and use the disc quality test. If you cant, then I suggest you burn 650/700 MB to a CD and boot to a boot prompt, and copy the entire CD to the hard disk. If this goes without any errors then you should be good to go. 
Hope this helps.[/QUOTE]

I'm going to try installing from the HD.  I've copied the contents of the disc, not the ISO file, to a directory of C:\ in Windows (of course).  So what do I have to do now?  Drop to the DOS prompt, change directories, and...?  Am sorry to sound so retarded.  Really, I'm a regular citizen, super-okay to sit next to on the bus.  Small animals and children like me, etc.

---

### Post by nilsderondeau on 2005-10-25
[QUOTE=Foaming Draught]Hi nilsderondeau, I'm with the earlier poster who said don't give up on ubuntu, there's no Linux like it (for a newbie like me, anyway).
Have you looked on eBay France for an enterprising chap who's burned 5.10 already and is now selling copies for, say, up to 10 euros or so incl postage? I burned my own Breezy Colony, but when I first started experimenting with GNU/Linux I didn't know what an .iso was, leave alone how to burn it to a CD. I didn't mind paying an Australian eBayer AUD20 for 5 Mandrake CDs and postage.
And while you're on eBay, look at the price of RAM for yr Travelmate. If the machine will take it, and it's cheap enough, you'll get another year or so of life from it by putting in at least 256MB and preferably 512MB.[/QUOTE]

Ah, but, but, all of these suggestions are so *practical.*  (Thanks.)

---

### Post by peebee on 2005-10-25
you may want to try the no=acpi switch and dont the "no detect pcmcia switch" 

when you run the install. It may not be the CD i had and issue that was similar to what people have been describing it was in 5.0.4 tho. until i disabled these two switches the system would not install, it would crash out with errors during the install.

---

### Post by taygan on 2005-10-25
[http://www.ubuntuforums.org/showpost.php?p=443608&postcount=12](http://www.ubuntuforums.org/showpost.php?p=443608&postcount=12)

Try enabling DMA on you cd-drive.  Lots of folks are having cd-reading problems because DMA isn't enabled.  sudo hdparm -d1 /dev/sda (or something similar for your drive (sda/hdb/hdc/etc.)

Check out the above link for a way to access it through the expert install, or just search for 'debootstrap' on the forums.

---

### Post by nilsderondeau on 2005-10-26
[QUOTE=taygan][http://www.ubuntuforums.org/showpost.php?p=443608&postcount=12](http://www.ubuntuforums.org/showpost.php?p=443608&postcount=12)
Try enabling DMA on you cd-drive.  Lots of folks are having cd-reading problems because DMA isn't enabled.  sudo hdparm -d1 /dev/sda (or something similar for your drive (sda/hdb/hdc/etc.)
[/QUOTE]

Thanks.  I had great hopes for the process described in the link you posted, mostly because it was New Information and because it allows me the opportunity to imagine I don't need to replace my CD drive to install Ubuntu.

1. The Expert install worked fine, including the tuning step.  
2. After the installer packaged started, I got as far as the partition step.  
3. The partitioner started and seemed to finish.  
4. The screen went black and then returned to blue, then put me back at the installer package options.  Partition Drives was selected.  So, accordingly, I...
5. Repeated the partition step.  The partitioner begins, but hangs at 52%.

So, Promising New Information seems to have led to a New Hairpull.  Is it good news that the partitioner's failure seems unrelated to the CD drive?  Maybe you all can tell me.

Edit:
Okay, so I gave the old college try, or as we knew it where I went to school, Brute Force Repetition.  I changed one asect, a hardware install option for IRDA (or whatever the infrared hardware abbreviation is).  Perhaps this was the hangup, perhaps the gods smiled.  Anyway, the partitioner ran.  At the moment I'm crossing my fingers and shooing away the cat while the kernel installs.

---

### Post by Irony on 2005-10-26
In Windows I use Deep Burner from;

[http://www.deepburner.com/?r=download](http://www.deepburner.com/?r=download)

Choose the free version. I've tried Nero and Pinnacle. Nero didn't work and Pinnacle was slow and buggy.

Deep Burner is fast and easy to use.

---

### Post by nilsderondeau on 2005-10-26
Just to report my final success!  The critical factor turned out (I think) to be turning on DMA as outlined in this thread: [Turn On DMA]("http://www.ubuntuforums.org/showpost.php?p=443608&postcount=12")

Other minor hairpulls:
Problem 1: The initial hardware recognition routine (amazing I don't remember it by name, as many times as I've seen it on the screen in the past forty-eight hours) would hang at 86%.
Solution 1: Enter "irqpoll" at the boot prompt

Problem 2: After turning on DMA as per the above thread, I selected IRDA (or whatever) option to install drivers for the IR port.  For some perhaps unrelated reason, the partitioner would not function correctly thereafter.
Solution 2: Don't monkey with adding extra modules.

Possible Problem 3: Burning discs.  Couldn't seem to get a single disc of the five I burned from 3 separate ISOs to check out.  I used Roxio, Iomega HotBurn with several different brands of discs.  
Possible Solutino 3: The winning combination turned out to be burning a disc with burnatonce (cited upthread) to a Samsung disc.

I really think, however, that turning on DMA was the critical factor.  Anyway, a hearty thanks to all of you who took the time to post.  I certainly do appreciate it!  For the record, I'll cite my system specs again should some other poor Travelmate bum tumble over the install.

Cheers,
N.


System: 
Core Logic Chipset:
ALi Aladdin IV 1531/1533

RAM
64MB

Video Subsystem
NeoMagic NM2200C V.DH (NMG5)
2 MB

Hard Disk Drive
4.1 GB

Floppy Disk Drive
1.44MB 3.5"

CD-ROM Drive
24x CD TEAC CD-224E-A26

---

### Post by Velox Letum on 2005-10-26
I have the same problem with my old rackmount server, though its during the copying of files. I've tried different types of CDs, pressed CDs, Windows disks, FreeBSD, new CD drives, etc., but I later found it was a problem with the IDE channels, and I had to move the cdrom to a different IDE channel. I had tried installers, copying over a compressed system by live cd, cloop filesystem off the live cd, and none worked...you might try a new IDE channel.

---

