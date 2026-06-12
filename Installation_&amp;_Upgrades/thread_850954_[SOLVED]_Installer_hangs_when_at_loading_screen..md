---
title: "[SOLVED] Installer hangs when at loading screen."
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by BuckleyInDaHouse on 2008-07-06
Well I'm trying to install ubuntu 8.04 again using the LiveCD. I used this particular cd before for a previous installation on the same computer. It installed perfectly then, now when I click install or try to run it live it hangs after the bar moves up about 2-3 times after it is done bouncing back and forth. I know the cd's contents aren't corrupt seeing as it worked perfectly before. I also tried using the DVD version of ubuntu 8.04. I downloaded it and checked the md5 checksum and it matched the one on the site so I burned it using Nero and iso-burner both times I burned at 2X and I also check the data after burn, tried to boot from the DVD and it hangs around the same place sadly.

Does anyone have any idea what the problem is or could be?

     Thanks,
        Buckley.

---

### Post by zipperback on 2008-07-06
Use the option from the livecd boot menu and verify the media.

I know you said it worked before, but you should check it again, it might be that you have a scratch on it or something that wasn't there previously.

- zipperback
:popcorn:

---

### Post by overdrank on 2008-07-06
> **BuckleyInDaHouse said:**
> Well I'm trying to install ubuntu 8.04 again using the LiveCD. I used this particular cd before for a previous installation on the same computer. It installed perfectly then, now when I click install or try to run it live it hangs after the bar moves up about 2-3 times after it is done bouncing back and forth. I know the cd's contents aren't corrupt seeing as it worked perfectly before. I also tried using the DVD version of ubuntu 8.04. I downloaded it and checked the md5 checksum and it matched the one on the site so I burned it using Nero and iso-burner both times I burned at 2X and I also check the data after burn, tried to boot from the DVD and it hangs around the same place sadly.

Does anyone have any idea what the problem is or could be?

     Thanks,
        Buckley.

Hi and welcome, you can try when booting the cd press the F6 option and remove the quiet splash from the kernel line and this will allow you to see any errors. Also a cd can corrupt after time and wear. :)

---

### Post by BuckleyInDaHouse on 2008-07-06
Ok, Im going to try it again with the suggestions you guys/girls posted.

Well it looks like its stuck at "sd 2:0:0:3: attached SCSI generic sg6 type 0"

Doesn't make too much sense to me.
a little above that I see "end_request: I/O error, dev fd0, sector 0"

Mumbo jumbo.

---

### Post by overdrank on 2008-07-06
> **BuckleyInDaHouse said:**
> Ok, Im going to try it again with the suggestions you guys/girls posted.

Well it looks like its stuck at "sd 2:0:0:3: attached SCSI generic sg6 type 0"

Doesn't make too much sense to me.
a little above that I see "end_request: I/O error, dev fd0, sector 0"

Mumbo jumbo.

Try adding  noapic  in replace of quiet splash

---

### Post by wpshooter on 2008-07-06
Have you tried cleaning your CD drive ?

Make sure that the CD check that you are doing/referring to is the integrity check that is found on the intial Ubuntu boot screen menu.

---

### Post by BuckleyInDaHouse on 2008-07-06
I tried that noapic and it got passed where i got stuck at first, but then it came down to a new error talking about 

```
Unable to execute "/bin/sh" for rc-defualt no such file or directory"
and something about a "Main Process 7101"
```

---

### Post by PmDematagoda on 2008-07-06
As first requested by zipperback, did you check the CD for any defects?

---

### Post by BuckleyInDaHouse on 2008-07-06
I check it for defects using the ubuntu installer menu option and it said no errors was found.

---

### Post by wpshooter on 2008-07-06
Have you ran memtest ?

Also, is there any other (Windows), etc. O/Ss on the computer currently ?

Have you ran any diagnostics to check the integrity of the hard drive in this computer ?

---

### Post by BuckleyInDaHouse on 2008-07-06
Yea hard drive is fine and im running Windows XP ultimate edition or black edition one of them i forgot and its SP3.

I ran the memetest, and my computer powered off around the 8 bit test i believe. But no errors was shown on the screen.

---

### Post by Tagus on 2008-07-06
I have this problem too. After removing "quiet splash" from the command line, the final lines were

init: rcS main process (5365) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: no such file or directory
init: rc-default main process (6590) terminated with status 255

It's the same with "noapic" and without.

Also, it's not the CD. I've used three CD-RWs using InfraRecorder, Nero Express, and Roxio Easy Media Creator, two on my Vista partition and one on XP; they all fail the same way. The Ubuntu CD check at boot said the disks were fine.

This is a fresh install of Ubuntu.

---

### Post by BuckleyInDaHouse on 2008-07-06
Glad to know i'm not the only one having this problem, hopefully us both will find a solution with the help of this site. Google search didn't return to much help to me.

---

### Post by wpshooter on 2008-07-06
> **BuckleyInDaHouse said:**
> Yea hard drive is fine and im running Windows XP ultimate edition or black edition one of them i forgot and its SP3.

I ran the memetest, and my computer powered off around the 8 bit test i believe. But no errors was shown on the screen.

What do you mean, "it powered off around the 8 bit test" ?

Do you mean that the memtest session ended/computer shutdown without your intervention ?

If so, sounds like you may have either a power supply problem and/or a overheating problem.

---

### Post by BuckleyInDaHouse on 2008-07-06
The computer shutdown without my intervention. I don't see how I could have that problem since when I play intensive games it doesn't do that and my graphics card is hot along with the CPU and PSU. But would booting from a CD really overheat my computer so fast that it could only load 2-4 bars of the Ubuntu live CD?

---

### Post by Tagus on 2008-07-06
I ran the Windows memory diagnostic from my Vista/XP dual-boot screen. All tests were included; no problems found. (After the test was done, it auto-rebooted and gave me the results when I logged on.)

Buckley and I have the same problem.

---

### Post by BuckleyInDaHouse on 2008-07-06
I tried loading the .iso file into VirtualBox for windows and it loaded perfectly fine. IDK if it helps or not but I guess the ISO isnt bad. Any more suggestions?

---

### Post by BuckleyInDaHouse on 2008-07-06
Sorry to double post.

Does anyone know what the possible problem could be? I really dislike windows lol.

---

### Post by wpshooter on 2008-07-07
> **BuckleyInDaHouse said:**
> The computer shutdown without my intervention. I don't see how I could have that problem since when I play intensive games it doesn't do that and my graphics card is hot along with the CPU and PSU. But would booting from a CD really overheat my computer so fast that it could only load 2-4 bars of the Ubuntu live CD?

This tells me that you have something definitely wrong with your system.

You need to find what is causing this.  When you run memtest it should run indefinitely until **you** end it by hitting the ESC key.  Should not just stop of its on accord !!!

---

### Post by BuckleyInDaHouse on 2008-07-07
> **wpshooter said:**
> This tells me that you have something definitely wrong with your system.

You need to find what is causing this.  When you run memtest it should run indefinitely until **you** end it by hitting the ESC key.  Should not just stop of its on accord !!!

With that being said, only thing that has changed since my last install is that I added a gig of ram. I'm going to take it out and see what happens.

Edit: i took that extra gig and took the side of the pc off, when I enter thenmemory test both of my fans stop spinning LOL.  So I guess it is overheating... :(

Edit 2: Ok, Took out the ram, and Ubuntu continued loading. I think I might try to exchange the stick of ram, Good thing I found out within my 15 day return warranty lol. 

Thanks for all who helped.

---

### Post by wpshooter on 2008-07-07
Hold on there, if your fans stop with this RAM in there (and I am assuming that these are NOT fans directly on your RAM) then perhaps you have an insuffient power supply and not a bad RAM problem.

Take some of your original RAM out and put in the one that you recently purchased and run the memtest again before you send the RAM back.  You may need a stronger power supply.

P. S. - if one of the fans that is not working is your CPU fan, then STOP immediately before you damage your CPU and possibly other components.

---

### Post by BuckleyInDaHouse on 2008-07-07
The fans only stop spinning when I run the memtest, other then that they are spinning. They are spinning as we speak, Also the ram was working fine while I was on windows never really crashed or gave problems. All of it showed up into the DXDiag menu and the fans I was talking about was the one in the back putting hot air out and the cpu fan. And of course I know not to run it without the fans on lol. Ever tried touching the heatsink? Not a good idea lmfao. Thanks for the help Im going to check out my PSU.

---

