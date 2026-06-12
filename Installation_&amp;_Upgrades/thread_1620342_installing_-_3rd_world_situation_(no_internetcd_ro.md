---
title: "installing - 3rd world situation (no internet/cd rom)"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2010-11-12
I need to install ubuntu or edubuntu (preferably) on an older computer (256 ram) whose cd rom is shot, but the USB ports work! The family has 2 kids and the parents are very computer illiterate and know NO English. The kids' future is dependent on learning English. The grandfather is illiterate in his language!  They are not down and out people, but they could use some help, if you know what I mean! I do have an external DVDRW drive and 2 computers where Ubuntu Maverick and Lucid have been installed. I will be about 300 km from them to give support. I have 2 days Monday to Wednesday next week to install Ubuntu or edubuntu.

I read on the internet 3 solutions, one of them offering a USB fix, which I am not 100% clear on:

[LIST=1]
[*][http://fasterthanlight.wordpress.com/2009/01/05/packgs-without-internet/]("http://fasterthanlight.wordpress.com/2009/01/05/packgs-without-internet/")

[*][http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

[*][https://wiki.ubuntu.com/OfflineUpdateSpec]("https://wiki.ubuntu.com/OfflineUpdateSpec")[/LIST]

I do not know how to program and am far more comfortable around a GUI, even though I sometimes venture off using the terminal (albeit, copying and pasting codes that other provides and that often I only get half the meaning of :) ).

The USB stick option seems to be one of the best solution at this time because I have tested it in the past! The computer has suddenly crashed (I had installed Windows in a multiple user/password mode), but one of the kids (older) was using games from friends' usbs (maybe full of virii)! Maybe the crash is a hardware crash as surges are common in the area. (I will be able to check for that using some kind of software if I can boot the comp.) After installing Ubuntu succesfully on two more recent computers already, I think Ubuntu or edubuntu might be the best solution for this situation. I am also 300 KM from being able to help out these people!

I have a few questions at this time. 

If the option of basically using one computer's image (ubuntu Maverick) that I have installed with all the packages that come with it (solution 1) is a viable one, how am I going to deal with the difference in hardware between the two computers. DOn't they need "drivers" and packages related to these specific components? Could I use the external dvd drive? If so, how can I get the old computer to recognize it. Assuming I can make it work again, would I need to download (beforehand) the windows drivers/files needed? Install them which might help if I want to use it to install the ISO image. I am not thinking about a dual boot since space is an issue and windows is a bad option anyway (virii).

Perhaps you can advise me on which will work ...hopefully from experience! 

Thank you for all your help! This family (I am sure) will be very greatful once the computer is running again!

---

### Post by C.S.Cameron on 2010-11-13
You can move Ubuntu from one computer to another as long as proprietary drivers have not been installed.
If the CD drive is plug and play you should not require any windows drivers to make it work.
There should be a setting in BIOS to boot from USB optical drive if the computer is less than about 7 years old. If the computer is older than 5 years it will probably have a problem with booting from USB flash drive.
Good luck.

Edit:
My project for today is to install Ubuntu on a third world kid's computer.
I had it dual booting just fine last year but the little brat got the Windows partition totally infected with a multitude of virii and he wiped the Ubuntu partition reinstalling Windows, (kids like to play Windows games).
The Ubuntu install CD won't make it past the try/install screen and it won't boot USB flash. I am going to give wubi a try but figure I will eventually pull the HDD from it, hook it up to my laptop and install Ubuntu to it from there. (I have a gizmo for hooking up 3.5 HDD's to USB).

---

### Post by pierreu1 on 2010-11-13
Oh! Thanks! I am told (but cannot confirm until I can get into the bios ...if I can go into the bios ... :) ) that the computer might be older than 7 y. o. in which case usb boot might be impossible! Thanks for the reminder for the plug and play feature, in which case ... wow ... all should be fine! Let's hope that works! That would be the simplest and easiest way to do things. 

Ya! Virii in windows are a real pain for 3rd world countries. The older kid is going to be really pissed if I bring in Ubuntu! :) I better lock the comp. down with all kinds of passwords. :)

Is there a way to exclude my proprietary drivers and invoke them? You can tell I don't know what I am talking about ... :) , but how do I bring in/save those drivers that the old comp. will need? If I can get in Windows, it might be easy in the device manager/system manager. If I cannot access Windows, is there any way to get access to that info in another way?

Thanks!

---

### Post by C.S.Cameron on 2010-11-13
> Is there a way to exclude my proprietary drivers and invoke them? You can tell I don't know what I am talking about ... , but how do I bring in/save those drivers that the old comp. will need?

As long as you did not consciously install any proprietary drivers ie Nvidia, you should be ok.
Lots of people install Ubuntu to pendrives, these pendrives will boot almost any computer,(that will boot flash), regardless of the individual computer driver requirements.

I've discovered that the reason I am having a hard time reinstalling Ubuntu in this kid's computer is that an unscrupulous computer shop owner swiped a RAM stick from the computer when it was taken in for service. Now it only has 256 MB

---

### Post by pierreu1 on 2010-11-13
Ya! Definitely much harder to trust the work people do in countries were there are wide discrepancies in levels of wealth and perceived wealth (as shown via movies and shows, local or otherwise). The same goes for this old computer. One never will know what took place during the times it was "serviced". It is so easy to replace old parts that work, fix the part that needed replacement, and fabricate a story! For instance, grounding has not been done properly and I tried to see if I could do it, but my knowledge in electricity is definitely close to inexistent! All I know is that a copper wire needs to be fixed somewhere to the metal frame of the chassis, but I am not too sure where to look or if it was done. I looked into the power box once. Maybe I will do again! Maybe that is the cause of the crash, although the power surges and the virii are more likely sources for the breakdown! I will have a look!

Not sure what took place on the old computer of course in terms of drivers. On my computer, none that I am aware of. I guess it is best I take both computers with me, the dvd drive and test things out.

Thanks for the help!

---

### Post by pierreu1 on 2010-11-17
Follow-up: The Edubuntu and Ubuntu install did not work (one version is a proven version). 500 virii were found on the USB stick and I did not bother checking if there were in the comp. I decided to try installing Ubuntu, but no matter what I tried it did not go past a certain point. The DVDRW player was bootable, but the 256 DDR1 RAM  with 64 shared is likely the issue. The Window XP was booting no problem. Can someone rule out the virii, trojans, and worms for the non Ubuntu boot? My next step is to add memory. Will 512 DDR1 be okay? I will inform Ubuntu and Edubuntu that it would be nice if rates of progress (rather than the 4 dots blinking) can be added to the downloading because this could have saved me precious time. As a result I had to bring the computer with me, preventing the kids to get any English exposure. Not a huge deal, but still ...! On the other hand, the other kid bringing virii with games might think twice doing it next time (and by extension, think twice about disobeying instructions next time)! Maybe I am dreaming! Anyway, ... if someone could confirm a few things because, oddly, finding DDR1 sticks is not that easy, although one would think there would be tons of those around in the country I am in ... for a decent price (apparently they can be ordered for the same price than 512 DDR2 RAM as far as I have been able to find out. Anyway,... I await your help! Thank you!

---

### Post by C.S.Cameron on 2010-11-17
512 MB RAM should be enough, 256 was almost enough for the computer I am working on but Ubuntu installer claimed there was only 255 MB.
I agree with you about a progress bar, those 4 blinking dots can be a waste of time.

I have installed Avast on the kid's computer because I don't think I can prevent him from using Windows but he can't update it with no internet connection.

Today I will try to find and confront that computer vendor that pinched the kid's extra RAM.

---

### Post by pierreu1 on 2010-11-17
You are doing a dual-boot then! Good luck with the unscrupulous vendor! One would have to do a print out of the whole comp. system before showing those guys anything! BTW, the bios om my comp shows a DDR2 category, but none installed! How can I know if it can take DDR2 and how many RAMS? Maybe the guy who "fixed" the comp before was just as unscrupulous with this comp.? :)

---

### Post by C.S.Cameron on 2010-11-17
You should be able to find a manual for the motherboard online.

The motherboard I am working has two different kinds of slots for the RAM.

---

### Post by pierreu1 on 2010-11-19
Oh! Thanks! DId not think info on as boring topics as motherboards could be found on the web, but ... I guess --- why not!

Found out that that I can put as much as 2 GB of DDR333 on this, although I probably wont! What do you recommend I buy? Another 256? I think I have 2 512 in Canada from a computer I was going to throw away! I will probably use those next year and replace them, but I am not sure that they are the ddr333 type!

---

### Post by dino99 on 2010-11-19
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by pierreu1 on 2010-11-19
Oh! Thanks! What a great find! Very informative! And I found [this (1) ]("http://edubuntu.org/documentation/10.10/installation-guide")(piggybacking) for edubuntu 10.10. My 256 - 64 = 192 system went as far as the language section and then on and on and in fact never went past that,... but I found out but too late that the system had really just 192 RAM, which was by a long shot too little. I will see if I can get two 512 sticks! Thanks again!

(1) [http://edubuntu.org/documentation/10.10/installation-guide](http://edubuntu.org/documentation/10.10/installation-guide)

---

