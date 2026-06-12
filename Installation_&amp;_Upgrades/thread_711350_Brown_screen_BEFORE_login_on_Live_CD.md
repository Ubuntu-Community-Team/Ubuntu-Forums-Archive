---
title: "Brown screen BEFORE login on Live CD"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by grimdeath on 2008-02-29
Hello, I am a returning ubuntu user. I have tinkered with linux in the past but prefer to keep it to a second drive. I recently reformatted my computer and opened up my smaller secondary drive again and decided to go ahead and reinstall ubuntu on it and see what has happened in the last year or two since I last tried it.

I was still fairly familiar with the install process so I downloaded the latest x86 version, created a boot disk, booted into the disk and started the process of opening the live version. I am met with the orange progress bar and then finally after a good while I have a blank brown screen load with movable mouse cursor (cursor set as a "loading" type icon) but never reach the point of logging in or loading the desktop...whichever the live cd does.

After repeated searches on here and google I have found MANY people saying they receive this issue after the login screen, but I would assume that was not part the live cd process as ive not even had a chance to setup an account or anything like that. Just for fun I tried the disk on my laptop and sure enough it loaded right up the first time, no problem. Perhaps I should try to the alternate version and just install directly since that is my eventual goal after loading it...? Ive also heard someone say that recreating the boot disk at a 4x write speed may help, would that with this issue maybe?

My system has been upgraded since my last run so here's my system specs which I figure are part of the problem:
AMD X2 4200 socket 939
EVGA/Jetway SLI Edition motherboard
EVGA 7800gt
2 gb of ram (4 sticks of three mixed brands; has been stable in xp and vista for the last year or two)
Primary Drive: Seagate 300gb sata drive
Secondary Drive: WD 80gb caviar ide drive
Samsung 997df monitor (I remember having some minor issues with refresh rates in ubuntu last time with this monitor)

Any ideas what is going on?

---

### Post by louieb on 2008-02-29
Nice PC.   Don't think its hardware detection.  Just a guess.  Did you run the check media for defects option? Just a few twisted bits in the wrong place will give weird results. 
 It may be that it has to run code on the desktop that its not running when you booted to the desktop.

BTW: your right the live CD should not not ask you to login before displaying the desktop.

---

### Post by grimdeath on 2008-02-29
Iim currently at work and away from the PC but as soon as im home I will run it for sure. Im just doing some research on the issue in my free time here at work heh.

I was just referencing the "login" area mostly due to lack of a better way to describe were I am getting the issue and that it is not the same "brown screen" issue that seems to pop on on all my search results. I wish I could at least see a login screen :P If it is any help in diagnosing the error, I did notice that my loading icon cursor does not animate and the very top of the brown screen seems to have colorful bits of color, kind of like artifacts from a video issue....its like a 1-2 pixel tall strip that runs all the way from left to right at the top...may be nothing.

Any word if the alternate cd would be a better choice for what I am doing and possibly avoid this issue? I will try it anyways when I get home if all else fails.

---

### Post by papajon_s1 on 2008-02-29
Just thought I'd add that I am trying 7.10 on an ancient HP Brio and I am experiencing the same BSOD (Brown screen of Death).  I get a mouse icon that sometimes works but nothing else.  The CD drive just keeps accessing... going on 10 minutes now.  I'll keep playing around with it seeing what I can find out,  but any thoughts/help would be greatly appreciated.

papajon

---

### Post by papajon_s1 on 2008-02-29
Ok, scratch my last entry!  The machine was only seeing half of the 256 megs of RAM... nice... And I think my home vacuum cleaner bag was was cleanlier than the inside of that box!  New RAM (well, newer RAM) is now installed and I have a happy install icon staring at me now...  

papajon

---

### Post by grimdeath on 2008-02-29
yea, it is a repeatable problem that is for sure. ive ran into it all 3 times I tried it this morning. hopefully just switching to the alternate cd and skipping the live install will do the trick for me. papajon_s1  if you had some time please try this out, otherwise ill report if it works or not in the next hour or so after I get home, download and try it.

ive been looking at all these videos of things you can do in ubuntu now, seem MUCH less limited then a few years back. im soo jealous now haha

---

### Post by louieb on 2008-02-29
> **papajon_s1 said:**
> Just thought I'd add that I am trying 7.10 on an ancient HP Brio and I am experiencing the same BSOD...

How much ram on that old PC?  Problem is there are a few things that can cause that. In  grimdeath's case I'm guessing a bad burn thats causing problems with video detection. In your case, who knows. I think those HP machines came with 64MB memory not near enough to run the live  CD. You might try Puppy or DSL Linux. BTW: You would be better off staring your own thread. That way the forum members will be able to give you better help.

---

### Post by grimdeath on 2008-02-29
I just made it home, im about to create a new live disk as well as the alternate disk. I would like to have the live disk handy and working if possible as a helper tool incase things every went bad heh. I will try the other version if not and report back what's happened....if all goes well hopefully my next post will be made from ubuntu :)

---

### Post by louieb on 2008-02-29
> **grimdeath said:**
> ..I would like to have the live disk handy and working if possible as a helper tool incase things every went bad heh... :)

:KSBet the alternate CD works. The 2 CD's I keep laying around for fixing things I screw up are [Knoppix Linux]("http://www.knoppix.net/") and a [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

---

### Post by grimdeath on 2008-03-03
sorry to take so long to respond, I ended up having a HECK of a time on Friday. I went ahead and created a boot disk using the alternative disk and set about installing Ubuntu to my second drive. I went ahead and verified that both it and my live disk did not contain errors or what not (checked media). However, when I was installing using the alt. disk I was met with an error at the select and install section (i think that was the name) and after repeated tries was unable to get past that part of the installation. The error mentioned that I could skip that section and come back to it later if I wanted so I went ahead to try and install grub and the only other step listed was the finish installation...figuring I wouldnt be able to get past that section I finished and rebooted to see if my install was working as is.

The grub installation did not seem to recognize my windows install but I figured that could be configured later to work...after restarting I saw the grub screen with only Ubuntu options so I selected and loaded it and was met with a command line only setup asking for my login name and password..after some reading I discovered that my gui setup must of been one of those things that did not install properly and I was not able to get it to work at all...

A friend of mine stopped by and needed me to download a file for him in windows so I decided I would at least try to get windows to load with grub, but after a lot of time and headache figured out that I could not get it to recognize my window install properly. Im worried this may be due to the fact that both my hard drives are showing as master drives (one sata master and one IDE master), but unfortunatly I have lost my IDE pin to set it as a slave...any idea what I could do to get around this? I even went as far as to download knoppix and burn it at 4x speed to see if it could get the live version of that to load and work but with no luck...it did a very similar thing to the ubuntu live disk, load all the way till just before the desktop should appear and sit there at a mountain wallpaper screen and never do anything else...just sit there with a movable mouse. So it looks like im having a common issue between live cds between all my other problems :P 

I tried repair my windows master boot record with my vista install disk did not work either so fiinally after around 12 hours on and off tinkering with it decided to just reformat both drives and reinstalled windows on my primary drive again and got back to square one. I am a bit leery to start this again because windows is a serious pain in the rear to reinstall, update, and install all my backed up personal resources and applications again but I REALLY do want an windows/ubuntu dual boot.

Here's a breakdown of the issues I need help with:
1. Why the heck am I having so many issues with live cds (ubuntu and knoppix)? The ubuntu live cd works on my laptop and knoppix was burned at 4x (I need to test it on my laptop), so I dont really think it could be a bad burn.
2. Why was I getting an error during the alt. disk install?
3. What do I need to do to get grub to work properly with windows? If I can at least get this worked out I dont mind reinstalling ubuntu on my 2nd drive a million times if it takes it as long as I dont lose my windows setup again!

Sorry for the troubles but thanks for any help you guys can provide.

---

### Post by grimdeath on 2008-03-03
are bumps allowed on these forums? if not then I apologize

I sure hope to get some sort of a response on this issue, id love to hit these problems hard again tonight if I knew where to start with these issues. I'd love to be running ubuntu by the end of today :)

*edit*
if it helps, this is the step where my install received the error every time I tried to install it:
[http://x86virtualization.com/wp-content/uploads/2008/01/ubuntu-step-by-step-29.png](http://x86virtualization.com/wp-content/uploads/2008/01/ubuntu-step-by-step-29.png)

failed at approx. 85%

---

### Post by louieb on 2008-03-03
> 1. Why the heck am I having so many issues with live cds (ubuntu and knoppix)? The ubuntu live cd works on my laptop and knoppix was burned at 4x (I need to test it on my laptop), so I dont really think it could be a bad burn.

If the Ubuntu CD's pass the media check  they a probably good. The media check performs a series of md5sums of various important parts of the CD. 
That leads me to think a hardware detection problem. I've not had that problem with Knoppix. But it happens. Heres some cheat codes you can try
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

One other thing if you have any usb devices attached - unplug them - pin drive, bluetoooth, whatever. They sometimes confuse the installer. 
>  2. Why was I getting an error during the alt. disk install?
Are you getting an error message? Some step take a while with the alt CD theres a long one at about 85%  May just have to give it some more time. 
> 3. What do I need to do to get grub to work properly with windows? If I can at least get this worked out I dont mind reinstalling ubuntu on my 2nd drive a million times if it takes it as long as I dont lose my windows setup again!

Getting a mix of sata and ide drives to dual boot is sometimes a pain.  More problematic that two ide or two sata drives.  I don't have a mixed drive PC so I usually point problems to this thread.
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

If it were mine I would unplug the windows drive while trying to install Ubuntu. Then after Ubuntu is installed and working its just a matter of changing the GRUB configuration file to boot windows.  

>  		are bumps allowed on these forums? if not then I apologize
The unwritten rule of thumb is a bump a day is ok. 

:guitar:You seem to be doing everything right.  I'm running out of reasons and possible fixes for your installation problems.   Installing Linux and Ubuntu in paticular in not suppose to be this hard.

---

### Post by grimdeath on 2008-03-03
Ok I did everything I listed above and everything checked out, I even ran Memtest with no errors after and hour and 100% reached. I also burned my boot disks using CDBurner XP instead of PowerIso though ive never had a issue with either in the past. My live cd will still not load...one more detail about it is that if I dont touch anything at the brown screen my cursor stays as a pointer, as soon as I move it, it changes to a progress circle icon and "freezes" the animation on it though I can still move it.

none of those types of usb devices are plugged in, would a epson cx4400 all in one printer matter?

I did receive an error on the alt disk install, cannot remember the exact wording but it said it could not finish the "setup and install" step and sent me to a list of installation steps so I jump to (install base components, install grub, finish installation, etc..) I have not tested my new alt disk as all my troubles started last time I tried my first disk, though I know it's due to me installing grub on the windows drive :/

The suggestion of unplugging the sata primary drive during the ubuntu install is a GREAT idea, I will probably give that a try if you think my sata drive is interupting my IDE im trying to install ubuntu on. Any idea if that would effect getting the live cd to work?

I understand it's not suppose to be this hard, I did it before with much ease! I have checked the hardware support docs and it seems that all my major components are supported though I cannot find any details of my motherboard being supported...however it just so happens to be the same motherboard I had working last time I used ubuntu a couple years back so I would suppose that means its ok. EVGA(rebranded jetway) NF4 SLI edition motherboard. *pulls out hair* :P Im reading up on the links you sent, this thread looks like my exact hard drive setup so ill review it now though it seems they are able to use the live cd :/
[http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

*edit*
would it be of any help if i recorded a movie of the live cd boot process and what it's doing?

---

### Post by grimdeath on 2008-03-03
Well good news and bad news!!

Good news: I decided to give the alt disk another try, this was the 2nd one that I was really careful with. The install went great and very fast this time, it even finished! All I did differnt was unplug the sata drive during the installation. I was able to get into the ubuntu login screen and login!

Bad news: Thats as far as I got, I was then met with another brown screen, movable cursor but could not get past that, a grey bar appeared on the top and bottom of the screen but nothing was on them. The bottom one did have some weird artifacts on them though on the left end. Here's a picture:
[http://img525.imageshack.us/img525/6172/ubuntuxi1.jpg](http://img525.imageshack.us/img525/6172/ubuntuxi1.jpg)

I remembered some people saying to hit control + alt + F1 or F7 to see if a console terminal would open, it would not for me...nothing seemed to respond to mouse or keyboard clicks. The mouse was moveable though. Ill go ahead and start looking through the usual brown screen issues after login to see if there is a fix for those, please point me in the right direction from here! It's progress at least! :) oh and my grub is working properly, booted right into windows here after I reconnected the drive...I still need to test if ubuntu is working with this sata drive plugged in again though.

Nearly there!

*edit*
I can access the tty at the login menu, log in and run differnt things there. Would I need to update my nividia drivers maybe? I have ran sudo apt-get update && sudo apt-get dist-upgrade as I saw that in another thread...not sure if it will help. Control Alt F1, F7, backspace, delete are not working, neither is printscreen. Cursor still moves but no windows or anything pop up with those keys after im at the "desktop".

---

### Post by grimdeath on 2008-03-04
oh my goodness i got it! i saw a post saying reconfigure x, i did that and mostly just clicked enter on default values...when i restarted it said it was in low graphics mode, i tried logging in and it worked...but it was stuck at 800x600 max...i found a spot to install restricted drivers and nvidia was listed, installled, restarted and pow...12x10 is working for me now :D

yay for linux 15 minutes before the end of the day!

victory is mine!

*edit*
one quick question...i have black margins around the edge of my screen, will it mess with my windows install to edit my monitor or is there another way to get rid of those?

btw, hello from ubuntu! im soo excited :D

---

### Post by louieb on 2008-03-04
> **grimdeath said:**
> victory is mine!...*edit*
btw, hello from ubuntu! im soo excited :D

:popcorn:Cool. Don't know about your display. I have an Acer wide screen. I sometimes have to push the auto adjust after rebooting to the other OS.

---

### Post by grimdeath on 2008-03-04
It's not too big of an issue, im just glad it's working :) For anyone else that is having this issue I recommend reconfiguring x, I dunno what I did "wrong" but when I restarted it was in low graphics mode apon restarting...this let me finally login properly. Next I installed the nvidia restricted driver, restarted and then I was able to set a proper resolution higher then 800x600 or 640x480. Hope this can help someone else! Looks like the main culprit was ubuntu having issue with my samsung monitor (again!) or video card until I set a lower resolution.

BTW I was able to do in about 15 minutes what it took me a week to do last time I tried ubuntu a couple years back. This is amazing! So far I: installed nvidia drivers, changed my theme, installed flash in firefox, installed opera browser, and learned that I can litteraly click my windows hard drive and browse all the files on it! I browsed to my "pictures" file in windows and copy/pasted my wallpaper over into ubuntu's pictures folder...it shouldnt be this darn easy! :P All without touching the command line within ubuntu. So far it's been totally worth the trouble! I am looking foward to getting into more complicated matters but I think im gonna continue learning my fundamentals first...any recommendation where I should start next guys? Updates, install important new apps, etc?

---

