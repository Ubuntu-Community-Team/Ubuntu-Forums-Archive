---
title: "Ubuntu 10.04 won't fresh-install"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Copperline on 2010-04-30
Hi I'd really appreciate some help on this if possible!

I've used Ubuntu without a problem since 7.10 although my system currently has Karmic running perfectly on a dual boot with XP. I also run Windows 7 (I have to for work!) and everything is fine with that too...so I know my problem is unlikely to be my equipment.

Intending to install just to see how it runs on my equipment I have attempted to fresh install Lucid on a clean (tested and fully functional) drive but the install keeps failing at the start.

I have now downloaded the iso twice from different server locations and burnt it using two different programs (K3b and Nero) on two different brand new CD-ROMS...with two different DVD drives and at the slowest speeds (just to be sure) and still no luck. When I can get it to work I would rather clean install on my existing Ubuntu system instead of upgrading as I find it to be better and I like a clean start anyway.

The system boots from the live cd, loads the boot scripts, displays the purple screen with the two white icons at the bottom and then proceeds to load files without displaying anything for a few minutes. Then a box appears stating that the installer encountered a problem and that I will be given a desktop session to resolve the problem (which does happen). This has happened a few times now and I'm at a loss...the system runs quite well from the live cd and I can use everything quite happily - I just can't install it. I have tried an alternate install...which appears to have worked but I'm not confident.

Could anybody perhaps shed some light on what's happening here? This is the frist time I've had problems with any Ubuntu install.

Very Many Thanks.
Copperline

---

### Post by jrop on 2010-05-04
> **Copperline said:**
> Hi I'd really appreciate some help on this if possible!
This is the frist time I've had problems with any Ubuntu install.
Copperline

I'm a new ubuntu user, and really have loved Jaunty 9.04.  When 9.10 came out, I tried installing it on one of my other computers, and experienced the infamous Karmic "freeze".  When 10.04 came out, I was very excited to try it, but unfortunately am experiencing the same error as above and can't get 10.04 to install completely (I also get freezes when running the live CD and see a lot of SQASHFS errors when shutting down sometimes).  I realize that lately HAL has been deprecated, which seems like a major structural change to me (or perhaps I don't know what I'm talking about), and my experience with 9.10 and 10.04 so far have been very dissapointing.  That being said, I think I'm stuck on Jaunty until someone comes up with a solution to this.

I havn't tried the 64-bit version or alternate install yet.

---

### Post by isc62 on 2010-05-04
My desktop has been running 9.10 since it came out. I have had very few issues with it during this time. 10.04 on the other hand is quite a disappointment. 5 attempts from 2 separate downloads have failed. The first attempt on day 1 was an attempt to upgrade. During installation of grub the pc locked up. Attempt 2 was a complete install from the same source disk. This attempt ended with grub not installing. Attempt 3, 4, 5 were today. This disk was downloaded from the Ubuntu web site. the install process was super slow. all three ending when attempting to insert the password. the dialog box continued to fill upon the 6th key stroke. I have given up and have returned to 9.10.

---

### Post by gerkin on 2010-05-05
I've had the same problems and tried similar solutions including the alternate install.  

I previously had the Karmic freeze and decided to wait for this LTS release Lucid is looking like a disappointment to me

Each attempt has left me with a munted machine (on both my EeePc and desktop) which i have fixed by reinstalling Jaunty to repair.

I have also tried a USB install to get around the possibility of a disk write problem - that has failed as well

---

### Post by snash on 2010-05-05
Me too. Attempting to install 10.04 on an old PentiumIII with 256MB, just as an IM tool. It was running xubuntu 8.04 (I think) and I thought a fresh install would be quicker than upgrading....

First installation got to 93% and stayed there overnight.
Second attempt is at 89% and not moving.
I am over-writing the 40GB disk.
It has an old AGPx8 128MB graphics card.
If the machine is out of spec then I would like to be told that at the beginning of the process.

Next step is to run from the CD first.

I expect there is a way to see the text output of the installation process, but I do not know what that way is.
Steve

---

### Post by dino99 on 2010-05-05
> **snash said:**
> Me too. Attempting to install 10.04 on an old PentiumIII with 256MB, just as an IM tool. It was running xubuntu 8.04 (I think) and I thought a fresh install would be quicker than upgrading....

First installation got to 93% and stayed there overnight.
Second attempt is at 89% and not moving.
I am over-writing the 40GB disk.
It has an old AGPx8 128MB graphics card.
If the machine is out of spec then I would like to be told that at the beginning of the process.

Next step is to run from the CD first.

I expect there is a way to see the text output of the installation process, but I do not know what that way is.
Steve

on your system you should install something else than the heavy gnome or kde desktop and their so heavy firefox and ooo, maybe xfce or lxde.

---

### Post by shooter468 on 2010-05-05
try the LiveUSB thing and install from USB
its less prone to errors than CDs

---

### Post by jrop on 2010-05-05
> **shooter468 said:**
> try the LiveUSB thing and install from USB
its less prone to errors than CDs

That's broke when I try it as well.  I get to the purple screen that says "ubuntu" (with the dots underneath it) and it stays there forever.  MAN!  C'mon Ubuntu!  Everyone says 10.04 is so perfect and users like myself are missing out.  How about a release that makes everything already in place bullet-proof?

---

### Post by Rasa1111 on 2010-05-05
> **jrop said:**
> That's broke when I try it as well.  I get to the purple screen that says "ubuntu" (with the dots underneath it) and it stays there forever.  MAN!  C'mon Ubuntu!  Everyone says 10.04 is so perfect and users like myself are missing out.  How about a release that makes everything already in place bullet-proof?

can you get to the ubuntu menu? 
if not.. try hitting spacebar at the purple screen with 2 white logos at the bottom.
and if it works.. use the menu from there. 

I burned 4 discs before i got it to work.. [all the cd's were good]

but my graphics card had an issue or two [still unknown to me]
and after i was told to hit spacebar at that purple screen...
it got me to the ubuntu menu, ...
and the live cd session ran great...
so i attempted an install..
and it's working perfectly. 
beautifully actually. :KS

so, I got like five 10.04. discs here, all good... 
I just didnt know what to with my given issue. lol

I still dont know what my issue was exactly.. 
something graphics card related i believe..
but im kinda n00b.. so im not too good with that stuff yet. lol
have patience.. 
once you get it going... youll love it i think.

p.s.. beloved windows cant even do what your asking. 
"everything already in place and bullet proof" :lol:
not happening on any OS.

---

### Post by jrop on 2010-05-05
> **Rasa1111 said:**
> can you get to the ubuntu menu? 
if not.. try hitting spacebar at the purple screen with 2 white logos at the bottom.
and if it works.. use the menu from there. 

I burned 4 discs before i got it to work.. [all the cd's were good]

but my graphics card had an issue or two [still unknown to me]
and after i was told to hit spacebar at that purple screen...
it got me to the ubuntu menu, ...
and the live cd session ran great...
so i attempted an install..
and it's working perfectly. 
beautifully actually. :KS

so, I got like five 10.04. discs here, all good... 
I just didnt know what to with my given issue. lol

I still dont know what my issue was exactly.. 
something graphics card related.. 
but im kinda n00b.. so im not too good with that stuff yet. lol
have patience.. 
once you get it going... youll love it i think.

I've actually done that.  When the icon with the keyboard shows up, I press any key and then get the "traditional" menu present in previous versions.  I then select "Try without installing" and it load the GNOME desktop.  Once there, I try the installation process, but get errors when it tries to format the drive that it wants to install on.

---

### Post by Copperline on 2010-05-05
Wow...sounds like I'm not the only one with problems then - which I guess is a relief!

I've tried a few things since my first post and still not got things to work properly!

1. The CD is good...I tried booting the live CD on a friend's machine - worked fine.
2. I have tried a different CD drive that was known to be in full working order - fails.
3. I have reset my system BIOS to default settings - still fails.
4. I have flashed my BIOS with the latest update - still fails.
5. I have tried onboard graphics only and then tried an external graphics card - fails.
6. I have tried brand new (correct) system memory - still fails.
7. I have cleaned the computer inside carefully...as well as the RAM packets - fails.
8. I have tried a brand new hard drive - still fails.
9. I have tried loading the live CD environment without a HDD in the box at all - fails.
10. I have reset the BIOS using both the jumper and removing the battery - fails.

Short of going out and buying a brand new system I now have no idea what could possibly be wrong. Everything else works fine on the system...XP, Windows 7, Vista (even Vista...) and Ubuntu 9.10.

However...I have just noticed that a message flashes across the top of the screen for a second after I select to load the desktop session...

**(process:312):GLib-WARNING --: getpwuid_r(): failed due to unknown user id (0)**

if this makes any sense to anybody out there I think this may be the root of the problem! Could anybody explain it at all please?

Thankyou!

---

### Post by Copperline on 2010-05-05
> **Rasa1111 said:**
> can you get to the ubuntu menu? 
if not.. try hitting spacebar at the purple screen with 2 white logos at the bottom.
and if it works.. use the menu from there. 

I burned 4 discs before i got it to work.. [all the cd's were good]

but my graphics card had an issue or two [still unknown to me]
and after i was told to hit spacebar at that purple screen...
it got me to the ubuntu menu, ...
and the live cd session ran great...
so i attempted an install..
and it's working perfectly. 
beautifully actually. :KS

so, I got like five 10.04. discs here, all good... 
I just didnt know what to with my given issue. lol

I still dont know what my issue was exactly.. 
something graphics card related i believe..
but im kinda n00b.. so im not too good with that stuff yet. lol
have patience.. 
once you get it going... youll love it i think.

p.s.. beloved windows cant even do what your asking. 
"everything already in place and bullet proof" :lol:
not happening on any OS.


Thanks for the spacebar tip by the way...I imagine we were all supposed to guess that one because I didn't read it anywhere but maybe that's my fault. 
The spacebar option did indeed give me the usual Ubuntu menu (try Ubuntu...install etc.) and also includes the option to check the CD which was helpful.
However...CD check was fine with no errors found.
I did select try Ubuntu...but "gdu-notification-daemon" crashed and I couldn't report it.

I still can't install as I still get my friend the unrecoverable error box.

Copperline

---

### Post by simpleeddie on 2010-05-05
At the spacebar menu, press F6 to edit the boot options. Turn on what you want (I didnt turn on any, but its the only way i know how to bring up the text down the bottom) and then edit the text boot parameters - remove the words 'quiet' and 'splash'. this should stop any bootloader issue. I'm having a very similar issue (hanging at the purple screen) which I can not seem to get past, but I think it has something to do with the drives - do any of you with issues run a RAID config?

---

### Post by Copperline on 2010-05-05
Hi thanks for your reply...the F6 boot option isn't a help to me as I can boot into the installer fine (but may be useful to others!) 

My problem is after the initial loading...when I've selected to install, after the purple screen with 'ubuntu' and the five scrolling dots and I can see a softer coloured purple screen and a mouse pointer (just before the window that offers the options to install and run the live CD should pop up) that I'm having the issue.

I don't have any RAID config at all on this machine...I am just trying to install on a brand new HDD that everything else will work on fine.

Cheers!
Copperline

---

### Post by williejones on 2010-05-05
> **Copperline said:**
> Hi thanks for your reply...the F6 boot option isn't a help to me as I can boot into the installer fine (but may be useful to others!) 

My problem is after the initial loading...when I've selected to install, after the purple screen with 'ubuntu' and the five scrolling dots and I can see a softer coloured purple screen and a mouse pointer (just before the window that offers the options to install and run the live CD should pop up) that I'm having the issue.

I don't have any RAID config at all on this machine...I am just trying to install on a brand new HDD that everything else will work on fine.

Cheers!
Copperline



Sounds like graphics issue, either the kernel mode settings or your graphic card.
Try booting with **nomode** option and see what happens.

---

### Post by ciamele on 2010-05-05
I was having trouble installing Ubuntu 10.04 and finally found a way to do it. I tried mutliple CDs of the regular install, and one of the alternate install.

There are several solutions I can think of, they all require the following:
1. The use of a USB flash drive that you don't mind formatting
2. A PC that can boot from a USB port.
3. A second computer would help, but is not necessary for all potential solutions.


First, the way I succeeded:
1. I have a laptop already running Ubuntu 10.04.
2. I downloaded the installation iso on that laptop.
3. Plugged in my flash drive.
4. Clicked on System > Administration > Startup Disk Creator.
5. Selected my iso.
6. Selected my USB drive (and chose to erase).
7. Clicked Make Startup Disk
8. I plugged the USB drive into the PC I wanted to install Ubuntu 10.04
9. Turned it on and set the BIOS to boot from that drive.
10. Then I chose the install option. Victory!

So far (30 minutes), so good.


The other ways you can pull this off are variations of the above (ALL are UNTESTED).

Alternate 1: If you're able to boot into the LiveCD and test 10.04
1. Download the iso to your hard drive.
2. Boot up in the LiveCD
3. Mount your hard drive.
4. Continue from line 4 of my steps above.


Alternate 2: If you have a Windows box handy

1. Go here and follow the instructions to put Ubuntu on a flash drive (they have instructions for Kubuntu, Xubuntu, and NetBook; look at the links on the left): [http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")
2. Boot from USB.
3. Double click the install option on the desktop.


I hope this helps. Good luck!

---

### Post by jrop on 2010-05-07
> **Copperline said:**
> I did select try Ubuntu...but "gdu-notification-daemon" crashed...

Hmmmm...I get this too, even if I boot with nomodeset on a usb stick (yeah, I did get the live usb to work).  I was looking around and I guess gdu stands for gnome disk utility- seems pretty important/critical and it doesn't make me feel confident that it failed...

---

### Post by jrop on 2010-05-07
Well, I think I might be on to something now.  I downloaded the 64-bit version of the desktop live cd (this may or may not work for the 32-bit--I haven't tested it) and **unplugged all of my usb devices** (except for what I considered to be the essential ones).  I was then able to boot into 10.04 without any error messages (and yes, without even hitting the spacebar when the first screen comes up).

I have yet to actually try installing Ubuntu 10.04 since this is finals week, and I'm not sure yet if I want one more thing on my plate just incase it doesn't work. ;)

Anyway, I'm excited about the possibility of this working.

---

### Post by Copperline on 2010-05-07
> **williejones said:**
> Sounds like graphics issue, either the kernel mode settings or your graphic card.
Try booting with **nomode** option and see what happens.
Thanks...that sounds like a good suggestion. I've quite a lot on my plate at the moment but I'll give it a try in the next couple of days and hopefully...that will work!

Cheers!
Copperline

---

### Post by Copperline on 2010-05-07
> **ciamele said:**
> I was having trouble installing Ubuntu 10.04 and finally found a way to do it. I tried mutliple CDs of the regular install, and one of the alternate install.

There are several solutions I can think of, they all require the following:
1. The use of a USB flash drive that you don't mind formatting
2. A PC that can boot from a USB port.
3. A second computer would help, but is not necessary for all potential solutions.


First, the way I succeeded:
1. I have a laptop already running Ubuntu 10.04.
2. I downloaded the installation iso on that laptop.
3. Plugged in my flash drive.
4. Clicked on System > Administration > Startup Disk Creator.
5. Selected my iso.
6. Selected my USB drive (and chose to erase).
7. Clicked Make Startup Disk
8. I plugged the USB drive into the PC I wanted to install Ubuntu 10.04
9. Turned it on and set the BIOS to boot from that drive.
10. Then I chose the install option. Victory!

So far (30 minutes), so good.


The other ways you can pull this off are variations of the above (ALL are UNTESTED).

Alternate 1: If you're able to boot into the LiveCD and test 10.04
1. Download the iso to your hard drive.
2. Boot up in the LiveCD
3. Mount your hard drive.
4. Continue from line 4 of my steps above.


Alternate 2: If you have a Windows box handy

1. Go here and follow the instructions to put Ubuntu on a flash drive (they have instructions for Kubuntu, Xubuntu, and NetBook; look at the links on the left): [http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")
2. Boot from USB.
3. Double click the install option on the desktop.


I hope this helps. Good luck!
Thank you very much for these suggestions! They must have taken you time to type out and I appreciate your help very much. As I said above I'm unable to give this my full attention at present but I'll certainly try them out in the next couple of days when I can get chance!

Thanks very much!

---

### Post by Copperline on 2010-05-07
> **jrop said:**
> Well, I think I might be on to something now.  I downloaded the 64-bit version of the desktop live cd (this may or may not work for the 32-bit--I haven't tested it) and **unplugged all of my usb devices** (except for what I considered to be the essential ones).  I was then able to boot into 10.04 without any error messages (and yes, without even hitting the spacebar when the first screen comes up).

I have yet to actually try installing Ubuntu 10.04 since this is finals week, and I'm not sure yet if I want one more thing on my plate just incase it doesn't work. ;)

Anyway, I'm excited about the possibility of this working.
I know the feeling of a full plate! Unfortunately I did try removing all peripherals apart from the absolutely essential and it still didn't work! However...this is a good idea too and I'll dig out an old ps/2 connector keyboard and mouse to see if disconnecting my USB keyboard and mouse does the trick. Good luck with your finals btw! Hope we finally get somewhere with this because 10.04 looks pretty good to me.

Cheers
Copperline

---

### Post by Copperline on 2010-05-09
OK - latest update on this strange little saga.

I have tried all the methods listed above:

First tried booting with nomode option and the installer failed giving me the same result as before. I then tried booting selecting a different one of the other boot options available when pressing F6 until I had tried them all and the installer still failed on each one at exactly the same time.

I then tried removing all USB devices and replaced my USB keyboard and mouse with standard (working) ps/2 ones. The installer still failed.

I then tried ciamele's suggestion and made a LiveUSB using the LiveCD environment. I felt this one had promise but the system just hung repeatedly at the scrolling dots and never progressed any further.

I can't help feeling something is not right here...surely I shouldn't have to do all these crazy things to get it to work - I've never had a problem with any other LiveCD of any other Ubuntu version I've made ever - they have all worked perfectly.

If anybody can shed any light on the script left at the top of the screen:

**(process:312):GLib-WARNING --: getpwuid_r(): failed due to unkown user id (0)**

I'd be grateful as I'm sure the error lies here.

Would anybody have any other suggestions at all please? I'll happily try anything!

Cheers
Copperline

---

### Post by Rasa1111 on 2010-05-09
Hi Copperline,
darn, sorry it still is not working properly for you. :(

I have no idea what that message means..
but I see there are quite a few who have gotten the same..
[https://bugs.launchpad.net/ubuntu/+bug/531027](https://bugs.launchpad.net/ubuntu/+bug/531027)
[http://markmail.org/message/ch6uyh3itohhkpea](http://markmail.org/message/ch6uyh3itohhkpea)


 I will try finding something useful...
but Im kinda n00b so Im not good with these things. lol

anyone else know a fix?

---

### Post by Copperline on 2010-05-10
Thanks for your message Rasa1111. I have had a look around myself and I've seen so many others having the same error...perhaps somebody will work out why? I'm just grateful that I still have good old Karmic running quite happily here! That doesn't much help me for the people who's Ubuntu machines I support who want the latest version though and of course I am keen to get it running myself.

Cheers
Copperline

---

### Post by Copperline on 2010-05-10
Do any pros have any idea why this is happening at all? I'd really appreciate your input if you can!

Cheers
Copperline

---

### Post by RJARRRPCGP on 2010-05-10
Looks like you have failing hardware. Sorry :(

---

### Post by Copperline on 2010-05-10
> **RJARRRPCGP said:**
> Looks like you have failing hardware. Sorry :(

Oh dear...really? Would I be able to ask you why you think that is and what's likely to be failing? It's likely that I will be able to test and change out the offending part whatever it is...or at least I'd like to properly know what is going on!

I must admit I had considered that my hardware might be at fault but thought it unlikely...as Windows 7, Vista Premium, XP Pro and Karmic all work fine and I would expect resource-hungry Vista at least to be causing trouble...but it's running well. My only issue with either software or hardware that I run on this machine is with 10.04...and only with an actual install as the LiveCD environment is fine. Conflicts between my different OS's can't be occurring either as I am attempting a clean install of 10.04 on a new HDD.

Cheers
Copperline

---

### Post by jrop on 2010-05-11
> **RJARRRPCGP said:**
> Looks like you have failing hardware. Sorry :(

Failing hardware?  Well, that makes two of us-- having the exact same problem?  And Window 7 and Ubuntu 9.04 run and installed perfectly on my system.

I do tend to think it's hardware-related, but I seriously doubt that this problem is due to hardware failure.

I'm stumped. :confused:

---

### Post by Copperline on 2010-05-12
I doubt very much that this issue is due to failing hardware. I would find that diagnosis easier to accept were it not for the fact that my system performs perfectly with my other installed OS's...even MS Vista which is notoriously dreadful. Karmic Koala works perfectly well and I never have a problem with it. LiveCD's of Karmic work exactly as expected.

Today I had a technician friend test my whole system (and he *really* went over it in detail) and everything was found to be functioning fine - no problems with BIOS settings; (inc. BIOS battery); power supply is functioning well within normal tolerances; memory checked and is 100% fine; graphics (both onboard and integrated) have been checked and show no problems; HDD function is fine with no bad sectors or SMART results; DVD drive is fine...produced CD and DVD which were checked and show 0 read/write errors.

Doesn't seem like failing hardware to me!

Would anybody reading this have any other ideas? I don't want to give up on 10.04 but I'm seriously considering it. 9.10 hasn't given me the slightest problem.

---

### Post by srtor on 2010-05-12
Failed to install 10.04. Must be something wrong with installation process.

---

### Post by Rasa1111 on 2010-05-13
> **Copperline said:**
> I doubt very much that this issue is due to failing hardware. 

Doesn't seem like failing hardware to me!

Would anybody reading this have any other ideas? I don't want to give up on 10.04 but I'm seriously considering it. 9.10 hasn't given me the slightest problem.


 Hi Copperline...
Sorry your issues remain. 
 I would agree, it doesn't sound like failing hardware. 
sadly.. more like failing software. 

 As good as Lucid has been for me.. 
lately.. [ the past 2-3 days or so], it has been acting uncool. lol

Out of nowhere,  my screen will go black, and the purple ubuntu screen flashes for a second with pixelated boxes on it,  then goes back to black, and starts flashing the black screen, half covered in white vertical lines. 

It has happened to me 3 times today, since 10:30 this am [now 12:56]
Last night it did it at least 3 times, probably more. [ while working on things, and losing them]

As much as i loved Karmic, 
I really love Lucid, 
and it sucks that I might have to switch back, and start all over again with karmic if this crap keeps up. 

 It sucks worse that many people are still having these problems and are in the same situation(s). 

I mean, really.... I do love Ubuntu...
but wth :confused: it shouldnt be this big of a problem.

---

### Post by Copperline on 2010-05-13
Hi Rasa,
Unfortunately I think you're right with the failing software theory there.

Although Lucid does have some nice new features...they might as well not exist if the basic system is un-installable (in my case) or very unstable (as in yours and many others).

Unless somebody wiser than me manages to come up with an explanation or even a solution for these issues I think I'll have to stick with Karmic and wait cautiously for the next release...hoping that the many little problems will have been ironed out.

I've spent quite a lot of time trying to get this to work now and tried all sorts of things that I've never had to do before with any distro...and none of them have worked :) My hardware works fine with all of my other installed systems so I'd reluctantly have to put the blame entirely with Lucid.

This said...I have actually managed to get Lucid to work properly as a Live CD and also to install on a computer that I quickly put together from a few old bits and pieces that were lying around unused. It does seem good although I haven't tested it extensively and several services did crash repeatedly. My two attempts at a Live USB just didn't work. I just wanted to see if I could actually get it to work just once!

Unfortunately - that cannot possibly be my main system as it is so dreadfully old that I'd never get anything done and it doesn't represent too much of an improvement over Karmic...which I am currently using and have been using all week without issue.

It's a shame...but if srtor is correct and it's the installer...I'm never going to get off the ground with it!

---

### Post by Rasa1111 on 2010-05-13
dang. :(

 I have been wondering...
if in 6 months from now ~ we [all of us having issues with 10.04] re-downloaded Lucid LTS~
if we would still have these same problems?

or would, Canonical have 'fixed' these things by then? 

I mean, Will they be working on this until they actually get it right.. 
and then release the working version? 

 or to put it another way........
if/when they actually do fix this....
will they remove the version they have up for download now, and put something that works for "everyone' up?  or how does this work?
 OR~ are we supposed to rely on updates to fix it?
but, seeing as update manager doesnt open by itself anymore and inform you when you need to update..
and you have to just guess or check when you think you might need an update....
I dont see how that will work out well.

so how do they go about taking care of these issues? 
anyone? lol

---

### Post by Copperline on 2010-05-13
I would imagine the solution depends on how ingrained or widespread the problems are.

During the alpha and beta tests a lot of the bugs should get removed - certainly this 'installer failing with unrecoverable error' problem has been hanging around for a few months now. I did beta test 10.04 and it gave me the same problem as the final release (installer fails). I had hoped that this would be sorted by final release but ununately this isn't so and it's quite a stumbling block.

I don't think that the base system available for download will be removed as it has now shipped for final release...although I may be wrong. I think it's unlikely Canonical will want to admit to it requiring such drastic action and I'm not sure that it needs it. The ususal advice on this one is to wait a month or so at least after release and then download...as everybody else will have fallen into all the little holes and worked out how to get out again. The solutions...those that are possible...will likely be included within the download then as they will have been sent to the repositories.

I would think that the updates should provide improvements...if it is possible to improve any failing programs and services this way of course. I'm not holding my breath, however.

Looking at things myelf, I think what has happened with this release is that too much has been attempted all at once. This is a LTS release and so the developers have tried to get things in and change things more than ususal. I don't think the developers have released a bunch of buggy code in a rush...I think that these teething problems are always going to happen when a large overhaul is carried out - and a large amount of the system has been changed.

There are many very cool things in this new release, (apart from, in my own opinion, the truely ridiculous decision to move the mini, maxi and close buttons to the other side of the window, whilst leaving the scroll bar and the menu options over at the right)...but cool things are no use if they can't actually be used.

If I were not already a fairly pasionate linux user (and if I didn't work in I.T. for a living) I honestly would have given up long ago! I wouldn't think 10.04 would be a good release to show to somebody coming to Ubuntu for the first time...they could be forgiven for thinking that Ubuntu isn't as good as it actually is - and you only need to put somebody off something once. Needless to say, I've advised everybody who I support who also runs Ubuntu to avoid this new release for a bit - they'll lose confidence in my judgement if they have the same problems I've had.

I've recently been implementing Windows 7 and I have to say that at this point...there's no contest - unfortunately 7 wins hands down.

P.s. I also noticed on my test system that did work with 10.04 that the CPU (a not exactly sluggish Athlon 64 3800+ 2.8GHz) was completely maxed out when only running Firefox with the Google page displayed. It stayed like this until I closed Firefox. Another bug of course...but as I spend a large amount of my day when working from home online...this just won't work out!

(I do apologise if this 'essay' does not count as relevant to this forum section!)

---

### Post by SolarEmber on 2010-05-14
I have the same problem as you I can not install Ubuntu 10.04 or even kubuntu 10.04 but I installed Ubuntu 9.10 and linux mint 8 fine just to make sure my hardware is fine, but i found out that my video card is not supported by the new ubuntu and kubuntu releases, I'm probably just gonna save money and build a windows 7 machine

---

### Post by jrop on 2010-05-15
BTW, what kind of video card do you all have?  Mine is an nvidia GTS 250.  Could this be the problem, because doesn't the new release utilise the open-source drivers for nvidia?

---

### Post by SolarEmber on 2010-05-15
I'm using the Intel G33/G31, but I have read some threads where lots of people are having problems with the new ubuntu and some nVidia cards

---

### Post by Rasa1111 on 2010-05-15
> **SolarEmber said:**
> I have the same problem as you I can not install Ubuntu 10.04 or even kubuntu 10.04 but I installed Ubuntu 9.10 and linux mint 8 fine just to make sure my hardware is fine, but i found out that my video card is not supported by the new ubuntu and kubuntu releases, **I'm probably just gonna save money and build a windows 7 machine**


hope not.

 my last problem I mentioned..
seems to have stopped and al is back to normal now..
apparently it was google chrome doing something to my system, making it crash,
no idea what.. but since I went back to firefox...
Lucid is beautiful again. :)

---

### Post by Copperline on 2010-05-15
I'm glad things are working for you Rasa, no such luck for myself! 
I've failed completely in trying to get Lucid to fresh-install and I think I'm just going to stick with Karmic. Unfortunately nobody has really come up with a solution to this 'installer fails with an unrecoverable error'
issue...so I think it is unlikely to be actually solved. I'm pleased that all my checks have shown
that my hardware is functioning without fault though...I was worried for a while there!

---

