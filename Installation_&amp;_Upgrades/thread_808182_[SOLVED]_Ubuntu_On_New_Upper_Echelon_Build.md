---
title: "[SOLVED] Ubuntu On New Upper Echelon Build"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-05-26
***I have just finsished building my dream machine and am os'less- I want to run a dual boot system with XP Pro (Am considering 64 bit) but canot get windows until I create my own slipstreamed installation media because I have a new Sata II 3.0gb/s HDD and XP doesn't come with native SATA Drivers!  I want to use Linux as my second OS and am considering 64 bit but thirty-two bit serves my purpose right now...I have my live cd and am getting ready to install-before I do so I want to know: will Linux work with all  this new High end hardware? *** _Here's my Build:_
[B]Gigabyte DDR3 Mobo w/Intel X-48 Northbridge,
2 GB DDR3 1333 Mhz OCZ Platinum,
Intel Core2Quad Q9300 45n 2.66 Ghz Processor,
Serioous Aftermarket Air cooling, (Zalman's top model Heatsink/Fan-Thermaltake HDD Fan, Thermaltake 120mm Case Fan, Scythe 120mm Case Fan, Three Stock Case Fans (Coolermaster)
Last But not Least...MSI 8400 GS (Nvidea)Graphics Card (Basic to get her running 'til I can put the latest ATI 3870HDX2 in!)
[/B]
***So, help!  What do you guys think?  Is this thing going to take Linux?  Should I go w/the regular Ubuntu/Kubuntu/Xubuntu or should I go with 64 bit Ubuntu?  Are there any installation issues with Sata II Optical Drives?  There certainly are with Windows but I must have it to game...I am also a Computer Information Tech-Developer/Infrastructure Specialist Student and do a lot of coding (Entry level practice stuff but still I code-I am using C language right now but will have to do quite a bit of VB and Dot Net stuff for school so I need that XP otherwise I would go straight Linux!  I am also into Security Testing so Originally I was going to go with Nubuntu (A pen-testers dream OS) but am holing off on that 'til I see what this baby is going to do with software on all this cutting edge hardware!  So any and everyone please reply asap!!!!!  I need to get an OS n this suckker so I can get to*** flying!  Thanks......

---

### Post by tamoneya on 2008-05-26
it should have all the drivers and what not that you need.  There should be very few hardware issues.  You will probably have to go get your video card drivers from restricted drivers but that is pretty standard.

Also the bold/italic text makes it harder to read IMO.  Just leave the text normal if you could.

---

### Post by theravenproject on 2008-05-26
Okay so-It looks like you are running some of the new hardware-any suggestions as to regular or 64bit flavors?  How is 64 bit different anyways?  Yeah Yeah no bold Italic! Lastly and PROBABLY MOST IMPORTANTLY: what do you mean by "Restricted Drivers?  In regards to my Video Card and where would I get these Restricted Drivers once I get my install done?  Please Advise!  Thanks

---

### Post by tamoneya on 2008-05-26
you go system -> administration -> Hardware drivers.  Then you check the driver to enable it.  For legal reasons dealing with open source OS and non-opensource drivers they cannot be auto installed but it is okay if you download an install it after the installation.  It is done through the restricted driver manager as described above.

Since you hvae 2GB of ram I would say stay with 32 bit.  It isnt worth the extra hassel unless you have 4 GB in my opinion.

---

### Post by theravenproject on 2008-05-26
Right on dude, thanks for the advice-I kinda figured that with the 64 bit....now all I have to do is figure out why in the heck my CPU won't boot into the live cd completely?  I am having problems w/the Ubuntu disc as well as the Kubuntu although the latter at least takes me to a command prompt where I at least gace some hope of installing someday wheras the Ubuntu CD freezes after I choose Start/Install at the options page and it takes me to a prompt that says "Ubuntu is in low graphics mode" then gives me the option to shutdown, continue or configure...after trying both continue and configure with no success other than freezing up after I go through the process of getting that far (Like 5/10 minutes into the Live Cd's boot time!) Anyways..Thanks for your help friend...Ahhh...(Sigh)  More Depressed than ever now.

---

### Post by tamoneya on 2008-05-26
I have a similar nvidia card.  I have found two things:
1. use safe graphics mode on the live CD
2. be patient since the liveCD is very slow.

---

### Post by theravenproject on 2008-05-26
Okay so you are saying that I can install this baby from safe graphics mode?  Seondly-be patient...I know this sounds stupid but how patient...how long do I wait before I assume that it is merely frozen and give up and besides...how slow can it be on a quad core q9300 w/ddr3 and all?  Thanks again my Persistent (And Patient) Ubuntu friend!

---

### Post by vexingmodstwo on 2008-05-26
> **theravenproject said:**
> Okay so you are saying that I can install this baby from safe graphics mode?  Seondly-be patient...I know this sounds stupid but how patient...how long do I wait before I assume that it is merely frozen and give up and besides...how slow can it be on a quad core q9300 w/ddr3 and all?  Thanks again my Persistent (And Patient) Ubuntu friend!

Yes, you can install it from safe graphics mode.

And I too thought that it had crashed but it was just doing its thing.  The install took about 30-40 minutes, but you've got a beefier system (I'm on a Dell Laptop and using VirtualBox) so it might be quicker.  Just let it go through the whole thing.  If you're going through the install for more than 40 minutes, then I'd worry.

---

### Post by theravenproject on 2008-05-26
P.S./ I am actually writing you from my old Dell Optiplex as I try and trouble shoot-I only have one Monitor and so I have to gather all the possible info given in reference to my prob, all possible solutions-possible future problems in case my solutions don't work so I can try and trouble shoot more before I unhook her again and make my way back to my dell... okay  just read what you said last 30 to 40 inutes but we are not even getting into the actual live cd here...I am not to the install point; this is all happening before the Live Cd brings me to the Gnome Desktop (I have been there before!) and I can click  on install...this is like right after you click on "Start/install Ubuntu" at the options screen you get right after post not the Install Icon at the Gnome Desktop!  So-does that change your reply or did you already understand that and what you said applies?  Sorry and thanks for your patience!

---

### Post by tamoneya on 2008-05-26
it has nothing to do with the speed of your processor.  You can only read data off of a CD so quickly.  I would just get up and make yourself some food or clean some dishes or do some homework.  Then if it is still "loading" then it is frozen.

---

### Post by theravenproject on 2008-05-26
Okay...Just so you know...my Pentium 4 Dell gets to the gnome desktop!  So I will keep trying...are there any advancced actions/options under f6 at the start screen?   Thanks for all of it I will keep trying!

---

