---
title: "Install Ubuntu without CD"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by ubuntu27 on 2006-04-06
Hello all Ubunteros (Ubuntu users) :) 

I have some “few” questions.

I just got a “new” [Acutally old] computer with NO OS that my mother has bought at the Thrift store.
And it didn't had any paper or anything that shows what it's inside them.

I gathered the following data from the Bios. 

CPU Clock: 450 Mhz
Cache Memory: 512K

Diskette Drive A: 1.44 Mb, 3.5 in
Primary Master Disk: LBA, UDMA 2, 8455 MB
Sec Master Disk: CDROM, VOMA 2
Display Type: EGA/VGA


When I turn on the Computer it shows the following:

Award Modular Bio V 4.51, An EnergyStar Ally.

Intel 440BX/ZX AGP BIOS for GBXC V2.9

Pentium III-MMX at 450 Mhz

ATAPI 44X CDROM.


Ok, the store or the people who provided the computer to the t. store has erased everything that's on the HD. That's what it says on the sticky note.

Now, I want to install our beautiful Ubuntu Linux or other distribution [Maybe this computer needs Xubuntu].  
But I cannot install any distro since the CD-Drive won't open. ] (*,) This is a Hardware issue that I don't know how to fix it. If anyone of you know how can I fix it I will appreciate it :)  

Now, since I cannot install from CD, I guess I will have to do a Internet/server install [is that how it is called?]  I remember seen it somewhere how to install Ubuntu directly from the internet... cannot find it. I did a search and the only thing that I found was how to install Ubuntu using Windows...  no this cannot help me :(

Summary:

How do I install ubuntu without using the CD?

Also: I guess I'll have to update the BIOS. How do i do that? [Is it necesary?]

Thank you guys!! :)

---

### Post by dermotti on 2006-04-06
Does the CDROM's LED blink? 

You could always use a paperclip and stick it in the little hole on from of the cdrom to open the tray. Its possible the cdrom drive is fine, just the drawer mechanism is broken.

I wouldnt update the bios unless there is a reason to do so. You coud accidently mess it up....

---

### Post by erniewinner on 2006-04-06
:rolleyes: i'd love an answer to this question! i want to try the same thing on an old world mac if i can't use the cd version...

---

### Post by ubuntu27 on 2006-04-06
[QUOTE=dermotti]Does the CDROM's LED blink? 
[/QUOTE]


yeah, the CD-ROM's LED does blink, but whatever I dosn't respond to the "Open" Botton. I mean, when I push/punch the open button, it falsh or blink the LED. But it dosn't open the tray.

[QUOTE=dermotti]
You could always use a paperclip and stick it in the little hole on from of the cdrom to open the tray. Its possible the cdrom drive is fine, just the drawer mechanism is broken.

I wouldnt update the bios unless there is a reason to do so. You coud accidently mess it up....[/QUOTE]

use the papaerclip to open the tray? I wonder if that works... let me see...

No it dosn't work.  This CD-ROM  seems open in a way that I've never seen before [Old fashioned way?] There is some kind of "door" like HP's and Compaq's Tower. I cannot describe well, but it is not a typical CD-ROM Drive :(

[QUOTE=dermotti]
I wouldnt update the bios unless there is a reason to do so. You coud accidently mess it up....[/QUOTE]

Yeah, you're right. Messing with the BIOS is a risky thing ><;
But, Would I benefict in anything if I update it?


Thank you !! :)

---

### Post by bray on 2006-04-06
to open ur CD drive, (this is a pain in the *** lol)
get a paper clip (or somethin that has the same thickness as the wire, open it out, and push it into the small hole (the drive release) that is on the front of the CD drive (its usually located near the eject button)

---

### Post by Bartender on 2006-04-06
ub27 -
When you say it has a door like HP's, do you mean the bezel (that's the name for the plastic face piece that snaps onto the front of the computer) has a door hiding the CD drive?  
Sounds like the machine was built somewhere around 1999 to maybe early 2000.  During that time the big manufacturers were making their first attempts to get away from the square "beige box" syndrome by installing swoopy-looking bezels.  These bezels often had false doors which hid from view plain old CD drives.

If it were me I'd remove the left side, top, and right side case covers, then figure out how to *carefully* pop the bezel off.  There will be a handful of wires from the "on" button, HDD LED's, etc. leading to a tiny little bus on your motherboard.  You don't want to jerk those wires loose from the motherboard by mistake.  Grab a fine felt pen and draw yourself a map on the back side of the left case cover, showing exactly where those llittle wires go.

Then if you want you can pop those wires off and set the bezel aside.  Or just leave the wires attached and place the bezel where it won't put tension on them.  At this point you'll see a typical CD drive screwed into the case with four screws.  Look carefully and you'll see the little hole for the paper clip.  If you make no progress with the existing drive, turn off the PC and swap it out for anything you can scrounge up.  CD drives are automatically detected during startup.  That part's easy.  What can be confusing the first coupla times is getting the "slave" & "master" thing correct.  

If you can borrow a CD burner that'll work fine as a reader.  It won't burn CD's without software but it'll still read them.

---

### Post by Bartender on 2006-04-06
The general rule of thumb with BIOS'es is if they're not broke don't fix 'em.  If you have your heart set on it, visit the manufacturer's website (or the motherboard manufacturer's website if you find that it's a name-brand board) and hunt around for BIOS revisions.  If your version is obsoleted by several revisions it might be worthwhile to flash.
If you have version 4.51 and they quit making newer revisions at 4.53, I wouldn't worry about it.
Unless someone added RAM during the PC's lifetime, you're likely to find the poor old thing has only 64 to maybe 128 MB of memory.  That would be a good place to start making improvements.

---

### Post by ubuntu27 on 2006-04-07
ok, I did what bray said. It opened the tray, and well, I inserted the Ubuntu Dapper D. Flight6 LIVE CD.

And WoW! It took 1 1/2 hour to load Gnome!!


Anyway, the sticky note says that this comp's has **7 GB** of HD. :-# 
Do you think it will be able to run Ubuntu in a stable condition?
Or should I use Damm Small Linux, Xubuntu, or other small distro?

What do you guys think?

Thank you in advance :)

---

### Post by Bartender on 2006-04-07
The Ubuntu install in my sig PC is taking up about 4.5 GB with Automatix installed.
The bigger question is how much RAM?

---

### Post by dermotti on 2006-04-07
I did Xubuntu server install, only takes 2.5 gigs. From there you can download any other packages you need.

---

### Post by ubuntu27 on 2006-04-07
[QUOTE=Bartender]The Ubuntu install in my sig PC is taking up about 4.5 GB with Automatix installed.
The bigger question is how much RAM?[/QUOTE]

I cannot find any info about RAM:(

[QUOTE=dermotti]I did Xubuntu server install, only takes 2.5 gigs. From there you can download any other packages you need.[/QUOTE]

Maybe I should just first Install Ubuntu and if things are not going well, then I overwrite it with Xubuntu, and then D. Small Linux :D :D

I am curretnyl downloading UBuntu's iso and Xubuntu's iso with Bittorrent...

Ubuntu has more seeders, thus allowing me to download faster :D  8)  Right now it is 70% [214 KB/s]
On the other hand, Xubuntu is 9.9% [24 KB/s]  :rolleyes: 


Thank you guys~  

I really apreciate your help. :)

---

### Post by erniewinner on 2006-04-07
enable the bios to count up the ram for you. i can't remember what that option is. i doubt it has 32mb or less... thats would'nt be that useable to anyone...  especially having a p3 450. unless of course it was sold by the owner? ubuntu requirement's can be low although 128mb is recommended. you would make that up for a couple of quid off ebay. and a p3 450 is good for most net stuff on ubuntu despite what anybody else might assume. i use a few boxes a p3 450 amoung them. i just upgraded it from 350mhz... probably a waste of time but thats as far as that motherboard can go!!!

---

### Post by Bartender on 2006-04-07
My sig PC works OK with standard Ubuntu install - when you get your PC going you'll find System Monitor.  My CPU often pegs out at 100% momentarily for basic tasks but that's OK.  It does the same in Windows 2000.  Whaddya expect for 450MHz?
I know there are several easy ways to check RAM once you've got Ubuntu installed, but can't remember right now.  As erniewinner mentions, RAM info oughta be available in BIOS.
You're reading up on how to check md5's right?  And you know about burning the download slowly, converting the .iso into an install CD instead of just burning as data, and using good quality CD's?

---

### Post by Panhead Bill on 2006-04-08
If you can access the BIOS during startup you should be able to see the ram size installed.  Usually you just hit the delete key just after the POST beep, (if you miss it hit reset and try again).

On some PC's the ram is tested (and counted) during startup, so it may be (for a second) displayed on screen before the IRQ listings.

---

