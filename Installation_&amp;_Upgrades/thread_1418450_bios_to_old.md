---
title: "bios to old?"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by Dn4mycrownj on 2010-02-28
Lets see, where will i start I have taken three towers that were free and have built one computer for about $25 american, that was the one stick of ram i needed.
 The computer has a supermicro P6SBA board. An external VGA card dont know what kind did not have to find drivers for it the board recognized it. If you guys need some more information just let me know and i can get just about anything for it. a

 The HD that i found to work out of the three had win 2000 on it. I got into it and i do not like windo at all, never have. I have 9.1 on two different laptops so i was going to install it on this desktop for the kids and then put msdos as the other os for old school games.

 Before i started anything i updated the bios, with a msdos boot disk, to the current one that supermicro offered for that board. That part had no problems. After that i switched the jumper and cleared the cmos again everything still cool. 

All of this is from live cds from ubuntu images i did not download any images from outside sources.
I started by installing msdos first well i had a corrputed disk on number 2 or something like that and the install failed halfway through. Just my luck for now. I have all them files backed up on cd just no new 3.5 to put the files on to them. Nobody used 3.5 any more lol. After that i went to put 9.1 on it. The error came up about the bios being 1999 and could not load. Then i went through all my cds and found a copy of 8.04 same thing with that. I have now tried to install the beta of 10.04. This install goes all the way through the loading line the burnt orange splash screen comes up and then it flashes a few times and goes black and the mouse spinning image comes on. This image stayed for about 30 min then i hit escape to try and quit the load of the cd and the spinning mouse icon stopped moving and frooze up. I had to do a hard shut down. 

After all of that here i am.

 Now for my question what version can i install and update to the current version or is there a patch that i can use to get this going? 

 I do not know if my 10.04 disk is good i have tried to do a clean install on the dell 1150 but the first try has not gone so i am trying it again. This is nothing new on that thing though. The 8.04 and the 9.10 are both good because i have used both of them for a clean install in the past. There is currently no OS on this desktop at this time because of the error while loading msdos. 

 I have access to a valid copy of win xp, if we need this to be able to change something else. I also have a msdos boot 3.5 disk with the cd driver for dos on it. "tested good" 

My main goal for this computer is to run msdos 6.22 with norton commander 5.51. and a second os of ubuntu some version for the the kids to be able to use the computer need that GUI for them. 
I am even down with a way of changing the bios upgrade date if you can do that. 

Crown

---

### Post by oldfred on 2010-02-28
Does the liveCD run on this system? What is one stick of RAM? If the computer is that old it may be 64 or 128MB well below what Ubuntu now requires as a minimum. 

I did get Ubuntu (2 years ago) to install on a 128MB portable but it must have taken 4-5 hours to install and another 4-5 hours to update over the internet. I think it was in effect running from swap. It was still slow. I then installed several lightweight linux versions until I found one that worked with my combination of hardware and was reasonably quick.

---

### Post by Dn4mycrownj on 2010-02-28
I cannot get the live cd to run on this computer. The ram stick is 256mb i only bought one cause i wasnt real sure the board was good.  Now i know the board is good and the ram is good.  The board has a date on it of 07/99.

---

### Post by Dn4mycrownj on 2010-02-28
Update:: my 10.04 disk is good. Just did a clean install on a dell 1150 only prob was to download the broadcom driver no wifi out of the box. lot easier wifi than my atheros card.

I have gotten 5.1 to install on the desktop, so far, i am now going to use it to try and update and upgrade to the newest version over the update manager.  
Before all of that i am going to get dos back on to some 3.5 i went and got some new ones.
Hopefully this will be easy to run both msdos and the newest ubuntu on this desktop. I might need more ram for ubuntu 10.04 to run worth a crap. 
Can someone give me the command to run update through terminal please.

---

### Post by efflandt on 2010-02-28
I installed Ubuntu on an old PIII 550 and the only thing it complained about for pre-1999 BIOS is that it would not automatically use acpi unless you included **acpi=force** as a kernel boot parameter.  I also had an issue that it would shutdown, but not power down, and **lapic** boot parameter resolved that.

I was experimenting with different installations and discovered that if you add boot parameters (that you know work) when booting the install CD, it automatically adds those as defaults for grub on the installed system.

---

### Post by oldfred on 2010-03-01
Also check out Herman's page on BIOS limits. You need to have your boot at the beginning of the hard disk:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

---

### Post by Mark Phelps on 2010-03-01
> **Dn4mycrownj said:**
> I cannot get the live cd to run on this computer. The ram stick is 256mb i only bought one cause i wasnt real sure the board was good.  Now i know the board is good and the ram is good.  The board has a date on it of 07/99.
I believe that you can install using the Alternate CD on that little memory.  Also, this board is upgradeable to a max of 768MB of memory -- more than enough to run Ubuntu.

My bigger concern is that the max CPU speed for this mobo is 400MHz.  My previous experience with processors at 600MHZ and 800MHZ was that Ubuntu was slow slow as to be all but useless.

---

### Post by dandnsmith on 2010-03-01
As regards speed in use, back in December I was playing with 2 mobos with 99 BIOSes. I loaded AntiX, DSL, and Puppy - one of those might have enough for what OP wants.

As regards max possible CPU speed, both mobo board manuals understated what the loaded BIOS could cope with and use - in one case it would take an 800MHZ PIII,in the other I've persuaded it to be happy with a 600MHZ PIII (but will have a try with an 800 MHZ to see if it will 'go').
It is well worth exploring the BIOS options for speed, as these exceeded the manual staement of limits in both my cases.

I have loaded U9.10 on one configuration - but cannot remember how much RAM I had at the time, having started with 190MB and then purchased more.

HTH

---

### Post by Dn4mycrownj on 2010-03-07
between work and everything else i have finally been able to get back to here. I went ahead i tried out the version of puppy 4.3.1. I installed msdos 6. and then the version of puppy 4.3.1.  This has worked very well for what i wanted. I have also installed that version of puppy on the old dell 1150 and that computer now runs much better.   That for you for the help. 

 I did not solve the problem of the bios, but i got what i wanted from the help of all.

---

