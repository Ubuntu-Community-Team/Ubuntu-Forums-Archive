---
title: "Enthusiasm Waning Trying To Install Ubuntu 10.04"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by darren123web on 2011-05-25
<<< Edit >>>
*** Laptop went to repair shop.  Mobo was fried and needed replacing.

I'm hoping it was just a coincidence that the day before I installed Ubuntu, Windows was working okay, and after I installed Ubuntu, I started having problems....

Fingers crossed ;-)

As I said in my other post - Ubuntu has been rock solid on this PC - just my lappy that had problems.

<<< End Edit >>>
Hello All,

I hope that there is a solution to this ;-)

I'm a complete Linux newbie you might say, but I'll try to give clear information....

I thought it was about time to go for a Ubuntu install, and lose Vista on my laptop.

I thought it would be 'reasonably' straightforward as I'm okay with PC's, and Ubuntu seems about as mainstream as Linux gets (for people like me coming from Windows)

However, I'm stuck...

I have a disk with Ubuntu 10.04 LTS (trying this now, as I had similar problems with 10.10 and 11.04)

I did a clean install from CD with 10.04.
Laptop is IBM ThinkPad R61i
(I *think* I have the nvidia 140 M graphics card, but can't see anything on my screen now so not sure)
I think it's an Intel Core2Duo if I remember right, with 3 or maybe 4 Gb Ram.

Basically I have a black screen.  I've followed this sticky - [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535), but none of the keyboard shortcuts seem to make any difference on Booting up.

I've also tried booting from CD, and trying the keyboard shortcuts in the post above - but still black screen.

Don't know if this is relevant, but at first it just wasn't shutting down, so I'd have to kill the power button.

Software I'm trying to remember what I installed before it all went wrong, apologies :

All updates prior to installing anything.
Nvidia driver of some sort was installed when I enable Visual Effects.
Cairo Dock (uninstalled that as was jumpy)
Wine (and then 1password I think)
Inkscape
Gimp
Scribus
Dropbox
Netbeans

maybe Skype / Filezilla also. 

And a media codec or something similar I installed to watch a video - think the video was .avi format.

Ubuntu One was up and working I think.

My main question is, can it be done?  This is the 4th time this has happened with 10.04 now in 2 days - I just gave up with 10.10 and 11.04 in the end and thought sod it.

I think I have to have the applications above for work, and would absolutely love to get it all set up on Ubuntu Linux, but I need something stable.

Is there anyway I can rescue my laptop?

Anyway I can see logs of some sort, or any way to reinstall (as I say, tried booting from Disk, but still black screen...)

The only thing I haven't tried yet is sticking the Windows disk back in it.  Now I would laugh if that worked!

Yours in hope ;-)

Darren

---

### Post by Cpierce on 2011-05-25
The first thing I would do is re-download the 10.04 .iso and burn another CD as slow as possible. It could be a a bad install.

However, it sounds like you may have a bad stick of RAM. If you have two sticks installed, pull one out and try to boot. If that doesn't work, try to boot on just the other stick. Your Ubuntu installation may be just fine. 

Bounce us back after you have tried this. If it won't boot up on the new Live CD, then it most likely a hardware issue. There are a ton of wonderful, sharp people on here as a resource. And..........

Welcome to Ubuntu.

---

### Post by mörgæs on 2011-05-25
If all three releases fail, it is very unlikely that it is a bad burn. 

Memory problems could be the reason, but as the machine works with Windoze, I also think it is unlikely.

Adding boot options as explained here
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
is my best bet.

---

### Post by darren123web on 2011-05-26
Thanks very much for the responses guys,

Ubuntu now booting fine - didn't need to reinstall and all programs are still there.

What eventually resolved it for me was :

I suspected my CD/DVD drive to be dodgy, so I downloaded Ubuntu 10.04 LTS and the USB universal installer to a USB memory stick.

As soon as I plugged that in and hit the power button, the laptop just booted straight up.

No idea why, it just worked.

I'll be keeping that memory stick in the laptop bag at all times......

Thanks again for the suggestions,

Regards,
Darren.

---

### Post by darren123web on 2011-05-26
Solved - again!  I think that's good....

> **Cpierce said:**
> The first thing I would do is re-download the 10.04 .iso and burn another CD as slow as possible. It could be a a bad install.

However, it sounds like you may have a bad stick of RAM. If you have two sticks installed, pull one out and try to boot. If that doesn't work, try to boot on just the other stick. Your Ubuntu installation may be just fine. 

Bounce us back after you have tried this. If it won't boot up on the new Live CD, then it most likely a hardware issue. There are a ton of wonderful, sharp people on here as a resource. And..........

Welcome to Ubuntu.

Hi Cpierce - 

Was a bit reluctant to poke around with it - done plenty of that with PC's, but never with a lappy.

Just wanted to say thank you - whipped a 2Gb stick of Ram out (video I found on Youtube for a slightly different model - [http://www.youtube.com/watch?v=DC7E1TcdETE](http://www.youtube.com/watch?v=DC7E1TcdETE) - but this might help someone else out I suppose)

And bingo, booted.

I'll test this out over the next day or 2 and report back.

Thanks again guys.

Darren.

---

### Post by mörgæs on 2011-05-26
You are welcome. Please mark the thread 'solved'.

---

### Post by darren123web on 2011-05-26
I'm just gonna leave this open until I figure it out ;-)

Seems to be a similar issue at the moment now whichever stick of Ram I leave in there.

Common denominator at the moment is that removing the Ram (power off, battery out) then booting up again does at least get Ubuntu booted.

Then a few seconds later, it's white gloves and glow sticks in my office again with the Strobe Screen Laptop crew....

Any chance the Nvidia driver update thingy that happened when I selecte Appearance > Visual Effects could have damaged the video card?

I dunno, will report back anything I discover.
D

---

### Post by darren123web on 2011-05-27
Well, even the strobe effect died after a while.

Then it must have been 50 or so attempts at 'kill power > start laptop > black screen'

Laptop gone to local repair centre to see if it's a hardware fault.

Will post back.
D

---

### Post by foresthill on 2011-05-28
I had the motherboard on my desktop go bad (started beeping like crazy and would no longer post) while unsuccessfully trying to install 11.04 for about the 5th time. I hope using the install option "acpi=off" didn't burn something up, but I have my suspicions. 


Loved the comment about the white gloves and glow sticks. There's clearly not nearly enough good humour on this board lately. :D

Good luck with the repairs, and i hope they're covered under warranty. My new motherboard is due to arrive on Tuesday.

---

### Post by darren123web on 2011-05-28
> **foresthill said:**
> I had the motherboard on my desktop go bad (started beeping like crazy and would no longer post) while unsuccessfully trying to install 11.04 for about the 5th time. I hope using the install option "acpi=off" didn't burn something up, but I have my suspicions. 


Loved the comment about the white gloves and glow sticks. There's clearly not nearly enough good humour on this board lately. :D

Good luck with the repairs, and i hope they're covered under warranty. My new motherboard is due to arrive on Tuesday.

@forest - 

Yep, without Sense Of Humour, I'd have thought that Linux / Ubuntu was a pile of crap, and that my decision to move to open source was a really bad one.

Will post back once laptop back from repair guys - but see my post here - [http://ubuntuforums.org/showthread.php?t=1769648](http://ubuntuforums.org/showthread.php?t=1769648) - kind of balances out my experiences with my laptop...

Ubuntu has been an absolute joy to work with on my other machine (posting from it now) - just what I'd hoped for and I can't thank the guys and gals involved with providing it enough.

Hope you have luck with your hardware too.

Joyous piece of an OS to work with.  Superb.  Massive thank you to whoever has put in their hours on this stuff. ;-)

Darren.

---

### Post by foresthill on 2011-05-28
Massive thanks to the developers seconded here as well. When I first tried Linux about 10-12 years ago, it was pretty bad (a steaming POS, as a matter of fact) and you'd often spend an entire weekend doing something basic like try to get your sound card to work, and only succeed maybe half the time. Nowadays, most hardware like that works right away with no tweaking whatsoever.

This last release of Ubuntu was probably a minor setback, but I think in 2-3 months time, most of the bugs will be worked out, and we'll have an OS that's a major improvement over 10.10.

I'm never going back to Windows, that much is certain. And while some of us may gripe about Ubuntu from time to time, it's not like we paid any money for it. So there's very little grounds for complaining. And hopefully all of us know that since the OS is free, there are no warranties or money-back guarantees. It's like the sign next to the old rope swing at the lake says, "uSe aT oWn riSk".  :D

---

