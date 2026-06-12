---
title: "Unable to install ubuntu"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by stefaan.dutry on 2007-05-10
I'm currently running windows vista.

I want to install ubuntu on a second HD.  

What i've done so far:
[LIST]
[*]I've downloaded Ubuntu 7.04 i386
[*]I've checked the download by letting it compute the checksum(it was correct)
[*]I've burned the download to a CD
[*]I've inserted the CD
[*]I get to the point that i get the CD runs when i startup the PC
[*]No matter what i select on the screen i'm then getting a black screen and 2 lines on the bottom of it.
[*]I've waited 5-10 minutes without change.
[*]The CD drive and the processer don't seem to do any activity; they just stop. :( 
[/LIST]

I am hoping someone could help me.  Any kind of help would be greatly appreciated.

thanks in advance

---

### Post by kyphi on 2007-05-10
Is your machine a desktop or a laptop.

Please specify what motherboard you are using and what connection you have for your hard drives and your CD drive, i.e. SATA or IDE.

Then we can begin to sort things out for you.

---

### Post by stefaan.dutry on 2007-05-10
> **kyphi said:**
> Is your machine a desktop or a laptop.

Please specify what motherboard you are using and what connection you have for your hard drives and your CD drive, i.e. SATA or IDE.

Then we can begin to sort things out for you.

*my machine is a desktop
*connection for harddrives and CD drives is IDE
*motherboard:

Form factor µATX Form Factor 9.6 x 9.1 inches 
Processor brand Intel Pentium 4 
Processor socket type 478 
Processor family  Intel Pentium 4 HT processors 
Processor front side bus frequency 400/533 MHz 
Maximum approved processor Intel Pentium 4 HT processor up to 3.06 GHz
Intel Celeron processor up to 2.80 GHz 
Chipset name Intel 
Chipset "North Bridge" Intel 845GE 
Chipset "South Bridge" Intel CH4 
Memory type PC 2100 or PC 2700 DDR 
Memory sockets 2 DDR-DIMM 
Maximum Memory 1.0 GB (2 x 512 MB DDR-DIMMS) 
Graphics Intel Extreme Graphics 
Graphics configuration Down 
Graphics connector (AGP) AGP 4x 
Audio Integrated AC97 2.2 Audio 
AC'97 CODEC Device RealTek ALC658 six channel 
Audio Jacks ( Legend below )  2M (1F+1B), 2LI (1F+1B), LO, Headphone connector 
Ethernet 10/100 LAN supplier RealTek RTL8101L 
Ethernet configuration Integrated, Down 
IEEE 1394 Front/Back Options 1B VIA VT6307 1394 controller 
IDE UDMA modes 2 x UDMA 100/66/33 
Expansion slots (AGP/PCI/Exten) 1 AGP, 3PCI 
USB ports Front/Back 6 (2F + 4B) 
Serial, parallel, floppy, PS2 keyboard and mouse 1S,1P,1F,PS2 K+M 
Available manufacturing options ( Legend below )  GLE6

ps: that were the specs i could find according to the model on the manufacturers site, i'm not at home currently;  was a HP a640.be to start with (now with 2x512 MB ram atm); also has a different soundcard (a type of Hercules (PCI) ) and a ATI RADEON AGP graphics card.  i'll post them when i get home.

---

### Post by Topsiho on 2007-05-10
You write: "I've burned the download to a CD"
Did you do this writing as an image?

The downloaded file is an .iso file which you should not burn as an ordinary data CD but *as an image*. I do not know how this is called in your burn program, in K3B it is a menu option in the menu Tools.

Topsiho

---

### Post by stefaan.dutry on 2007-05-10
I've used the tool that was recomended by the site where i downloaded it :

I used **infra recorder**.  This program was suggested at [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")


I get to the first screen of that CD where there's a 30s cooldown time to allow you to make a choise.
In this menu i've choosen both the check disk option and the run and install option (not at the same time ofcourse) but either of those ended up in a black screen with 2 lines of text on the bottom of the screen.  And then nothing happens anymore.  The PC doesn't respond to any actions anymore (except reset button and power button that is).  I waited about 10 minutes before i decided to do this.

Version:  **UBUNTU-7.04-desktop-i386.iso**

Hope this helps in getting more responses.

I have now downloaded version **UBUNTU-7.04-alternate-i386** because i read that sometimes the normal version fails to work.  I'm going to try that out this evening.  Any further suggestions are still more than welcome.

---

### Post by mve-lamb on 2007-05-10
Hi i have exactly the same problem on several (3) PCs with different hardware ... UBUNTU 7.04, I have no this issue with 6.10, and 6.06 on the same machines.

When you boot Live CD, and try to install it from shortcut on desktop you went trought partitioning and after that instalation hangs (it hangs on 15 minutes) i wait a long time but the same, also started instalation several times from the beginig. I don't know why it happend? but i resolved this:

 Do partition on your HDD manualy, not automatic or recomended...just you need to do it manualy, create swap, root, and so on... 1.start from shortcut on desktop "install on hard drive", 2.when you reach partition manager choose:  manual partition (or something like this)

I hope this helps  :) excuse me for my medley english

---

### Post by Topsiho on 2007-05-10
Hi stefaan.dutry,

Seems my guess that you did not burn the .iso as an image was wrong. In that case it's indeed a good idea to use the alternate CD instead. There is something very seriously wrong with the Live CD (desktop) version, as very many people have trouble installing from it, or, after installing, booting Feisty. Just have a look around in this forum alone. The many advises you see only work for some people, while not for others.
The previous Ubuntu's did not have this nasty bug or Ubuntu would not have become this popular at all :( 

I had the same issue on one of my three computers, and with the alternate CD everything went fine enough.

The suggestion of mve-lamb  to partition your drive before installing is a good one. You can do that very nicely with the GParted live CD, which you can download as an .iso (and then burn it as an image) too. The GParted on this live CD is a much better one than that in the install program, which als uses GParted, but an older one or a clipped one, I do not know.

So good luck to you,

Topsiho

---

### Post by stefaan.dutry on 2007-05-10
I tried using the alternate CD and i have the very same problem as with the desktop CD

This time i've noted down the 2 lines at the bottom and here they are

[B]CNT 14: CR2 F8000000 err 00000000 EIP c020c384 c020c384 cs 00000060 flags 00010003
Stack: c00f7d20 c03f129b c0371d8c 00000002 c00f7d29 000f7d20 00000000 00000000[/B]


The lines are exactly the same with both CD's alternate or desktop.

Therefore my guess is that it has something to do with my hardware not being supported or something.

I accept all the help i can get :)

---

### Post by kyphi on 2007-05-11
This is all very puzzling.

I have checked the HP site for information on the HP Pavilion a640.be and found nothing of note.  Although I did not look for a BIOS update.

So, the questions in my mind are:

1.  Are your drives correctly set up as master and slave?
2.  Since you also have Vista, are all your drives recognised, including the CD burner?
3.  Do you have a RAID configuration for your hard drives?
4.  Were your ISO files burned correctly?

To check point 4, go to a newsagent and look for a computer magazine with a Knoppix disk (or Ubuntu or any other ready to run distro).

---

### Post by stefaan.dutry on 2007-05-11
> **kyphi said:**
> This is all very puzzling.

I have checked the HP site for information on the HP Pavilion a640.be and found nothing of note.  Although I did not look for a BIOS update.

So, the questions in my mind are:

1.  Are your drives correctly set up as master and slave?
2.  Since you also have Vista, are all your drives recognised, including the CD burner?
3.  Do you have a RAID configuration for your hard drives?
4.  Were your ISO files burned correctly?

To check point 4, go to a newsagent and look for a computer magazine with a Knoppix disk (or Ubuntu or any other ready to run distro).

The answers i can give according to me:

1)  My drives are set up correctly according to me;  the master is the harddisk with vista on it; the other one is set as slave;  I could browse in it before i formatted it.

2)  Every single piece of my hardware is recognised and working as it should under vista.

3)  There is a raid controller in my PC, but it's not being used at the moment;  there's no disk attached to it

4)  I've tried running the CD's from another PC; there they go further is i use them under microsoft virtual desktop.  So I assume it's not the CD's, but rather the combination of installation CD with my system.

I hope i get another reply to this :)

---

### Post by stefaan.dutry on 2007-05-11
> **mve-lamb said:**
> Hi i have exactly the same problem on several (3) PCs with different hardware ... UBUNTU 7.04, I have no this issue with 6.10, and 6.06 on the same machines.

When you boot Live CD, and try to install it from shortcut on desktop you went trought partitioning and after that instalation hangs (it hangs on 15 minutes) i wait a long time but the same, also started instalation several times from the beginig. I don't know why it happend? but i resolved this:

 Do partition on your HDD manualy, not automatic or recomended...just you need to do it manualy, create swap, root, and so on... 1.start from shortcut on desktop "install on hard drive", 2.when you reach partition manager choose:  manual partition (or something like this)

I hope this helps  :) excuse me for my medley english

It's not the same problem.  I do not get as far as actualy seeing the ubuntu desktop that should load [LIST]
[*]completely in RAM.  I only get to the initial screen where you can select to:
[*]start or install ubuntu
[*]start ubuntu in safe graphics mode
[*]check cd for defects
[*]memory test
[*]boot from first hard disk
[/LIST]
So you see i get nowhere near the desktop where you can click install:(

---

### Post by stefaan.dutry on 2007-05-11
I've downloaded the **Ubuntu-6.06.1-desktop-i386**  (the LTS version)

I'm going to try this this afternoon ( around 16:00 (GMT+1))

If i get the same error then it's got nothing to do with the 7.04 version

Can anyone tell me if it will recognize that vista is already installed on my pc?

PS: i'm getting tired of downloading and burning to CD :( 

I accept all help i can get :)

---

### Post by stefaan.dutry on 2007-05-11
> **kyphi said:**
> This is all very puzzling.

I have checked the HP site for information on the HP Pavilion a640.be and found nothing of note.  Although I did not look for a BIOS update.


[URL="http://h10032.www1.hp.com/ctg/Manual/c00220400.pdf"]
http://h10032.www1.hp.com/ctg/Manual/c00220400.pdf[/URL]

Hope this gives you some more information.

---

### Post by anarchitecton on 2007-05-11
I've been having the same exact problems as described in the first post. I've also [_posted_]("http://ubuntuforums.org/showthread.php?t=439466") here yesterday.


Any news in how to resolve this problem?

thx.

---

### Post by stefaan.dutry on 2007-05-11
> **stefaan.dutry said:**
> I've downloaded the **Ubuntu-6.06.1-desktop-i386**  (the LTS version)

I'm going to try this this afternoon ( around 16:00 (GMT+1))

If i get the same error then it's got nothing to do with the 7.04 version

Can anyone tell me if it will recognize that vista is already installed on my pc?

PS: i'm getting tired of downloading and burning to CD :( 

I accept all help i can get :)

Well i've tryed it, this time when i make my choise at the screen my pc starts to reboot thus taking me back to that screen after a while :-(

i'm all out of ideas here

---

### Post by mnederlanden on 2007-05-11
I have the same problem with 7.04. It hangs up several times. If I restart while it hangs up it can sometimes get past the place where it hangs. 

Sometimes it hangs at Loading hardware drivers -- when I get past it it gives me the error : 226.728419 bcm43xx_microcode5.fw not available or load failed.

Sometimes it hangs up at Configuring network interfaces.

Sometimes it loads GNOME but then gives me a blank screen.

As the earlier poster I am attempting linux for the first time.

I am downloading 6.06 now since many people on the forums state that earlier versions did not have this problem.

---

### Post by stefaan.dutry on 2007-05-11
> **mnederlanden said:**
> I have the same problem with 7.04. It hangs up several times. If I restart while it hangs up it can sometimes get past the place where it hangs. 

Sometimes it hangs at Loading hardware drivers -- when I get past it it gives me the error : 226.728419 bcm43xx_microcode5.fw not available or load failed.

Sometimes it hangs up at Configuring network interfaces.

Sometimes it loads GNOME but then gives me a blank screen.

As the earlier poster I am attempting linux for the first time.

I am downloading 6.06 now since many people on the forums state that earlier versions did not have this problem.

Well my last post just said I tried the 6.06 version; and as you can see it's not better.

---

### Post by Jazztux on 2007-05-11
Hi,
i got a question. When you chose start or install ubuntu, do you see a windows-like window saiyng it is loading the kernel?? ;)

---

### Post by stefaan.dutry on 2007-05-11
> **Jazztux said:**
> Hi,
i got a question. When you chose start or install ubuntu, do you see a windows-like window saiyng it is loading the kernel?? ;)

I see a windows like window ( a small one) with a loading bar.  It fully fills up.  I still have the original selection window as background then.  After it's filled up 3 rows of green letter appear(just like they are being typed at the moment) then screen goes black.

---

### Post by Jazztux on 2007-05-11
Ok, now another question: what graphics card do you use? Is it integrated or it's ang agp card?

---

### Post by BorgCymru on 2007-05-11
I'm also having problems installing onto the new box.

At first the Live CD wouldn't load, it would get to the buff coloured screen before the desktop showed and hang, I tried with safe GFX mode and after 5 attempts it did load, when I tried to install it hung at 36% for 30 mins so I turned it off.

Still can't get the 'live' to even load now.

Worked OK on my shuttle as a test but on this box nothing.

Both have the same HDD set up, GFX card and chip set board.

very odd, can I download an earlier version and then update. ?

---

### Post by Jazztux on 2007-05-12
Yes, you can, but if'll be not exactly the same as installing directly the new version. Otherwise, you'll be able to use all the new features in 7.04 ;)

---

### Post by stefaan.dutry on 2007-05-12
I got the 7.04 version installed now.

I just added the option **acpi=off** 

Then everything worked fine.

---

### Post by hanzj on 2007-05-14
Dear Stefaan,
I have the same problem. Where did you add that option of "acpi=off"?

Thanks.

---

### Post by stefaan.dutry on 2007-05-15
> **hanzj said:**
> Dear Stefaan,
I have the same problem. Where did you add that option of "acpi=off"?

Thanks.

When your pc boots, it goes to the initial screen from the CD.

If you look on the bottom of the screen you'll see there's some options there that can be accessed using the function keys. (F1;F2;F3;...)  The last one (F6 if i'm not mistaken) is the options  press that button that's shown there; then you'll see a line come up where you can add text; there type **acpi=off**.  

That's what i did and it worked fine.

in steps:
[LIST=1]
[*]boot with CD in PC
[*]you should see a screen where you need to make a selection
[*]press **F6**
[*]add **acpi=off**
[*]select the run/install option
[/LIST]

I hope this was of some use to you

---

### Post by hanzj on 2007-05-15
Stefaan, 
I did as you said, but it doesn't help me. I still have the same black screen.

---

### Post by stefaan.dutry on 2007-05-16
> **hanzj said:**
> Stefaan, 
I did as you said, but it doesn't help me. I still have the same black screen.

Then i won't be able to help you, sorry.:( 

I'm not an experienced user. This was my very first install of any linux version.

I hope you get your problem sorted out.

P.S. : i'll stop watching this thread now

---

### Post by cattaman on 2007-05-26
I am having the same sort of issue. When i tried installing i got the black screen of death LOL. i downloaded the alternative and was able to install however the first time i try to load from the boot manager i go back to the black screen of death. My system specs are as follows

AMD 3800+ dual core s939
2x512 MB OCZ ddr
K8N Neo4-F MSI motherboard
Saphire ati x800gto vid card pci express
2x 250GB seagate HD non raid

Also using an nec 90gx2 LCD  monitor

I have ubuntu sitting on my HD waiting to use if i can get it working please help us!

---

