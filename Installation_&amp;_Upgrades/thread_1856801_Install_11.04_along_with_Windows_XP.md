---
title: "Install 11.04 along with Windows XP"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Ms. Daisy on 2011-10-09
I installed a new hard drive on my PC and successfully installed 11.04 Ubuntu from a flash drive (the built-in CD drive is toast).  I quickly fell in love with Ubuntu.  Then I had the unfortunate and regrettable idea to re-install Windows XP from my recovery CD (using a portable DVD drive I borrowed from a friend), with the intention of partitioning the drive & installing Ubuntu back again on it's own partition.  Ultimately I wanted to dual boot.  Windows completely erased the hard drive as expected and installed XP successfully.

Now using the exact same flash drive, I can't get Ubuntu to load.  I get the menu asking if I want to install or run live.  Either one I choose, I end up with a black screen and a lot of nothing happening.  EGADS, WHAT HAVE I DONE???  :cry:  I searched the documentation, the stickies, and this forum for similar issues to no avail, but that certainly doesn't mean that they don't exist.  Can someone point me to them?

(No clue if it matters, but I'm actually running the "memory test" right now off of the stick- so far so good).

---

### Post by raja.genupula on 2011-10-09
hey go with this

[http://ubuntuforums.org/showthread.php?t=1701745](http://ubuntuforums.org/showthread.php?t=1701745)

---

### Post by Ms. Daisy on 2011-10-09
Thanks for the response.  Although I wasn't really able to follow what the actual solution was on that thread.

I solved it by just burning a new installation CD using my friend's DVD drive.  Ubuntu is up and running.  However, I still have no idea why the stick worked once but then wouldn't work after I installed XP.

---

### Post by apollothethird on 2011-10-09
> **Ms. Daisy said:**
> Thanks for the response.  Although I wasn't really able to follow what the actual solution was on that thread.

I solved it by just burning a new installation CD using my friend's DVD drive.  Ubuntu is up and running.  However, I still have no idea why the stick worked once but then wouldn't work after I installed XP.

If you had booted to the stick and installed to the stick there's a good chance you used the hard drive as a boot loader to get to the installation on the stick.  After you reformatted the hard drive you removed the boot configuration for starting the OS on the stick.

If I'm right your installation is still on the stick.  There's a good chance you can run "update-grub" and have the stick's installation appear as one of the boot options.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Ms. Daisy on 2011-10-09
> **apollothethird said:**
> If you had booted to the stick and installed to the stick there's a good chance you used the hard drive as a boot loader to get to the installation on the stick.  After you reformatted the hard drive you removed the boot configuration for starting the OS on the stick.

If I'm right your installation is still on the stick.  There's a good chance you can run "update-grub" and have the stick's installation appear as one of the boot options.

I think I understand you.  You're theory is saying that I ran Ubuntu live on the stick without ever installing it on the hard drive, right?  But I used the stick to install Ubuntu onto the entire drive the first time with total success.  I used Ubuntu on the computer (without the stick's involvement) for a week or so.  Then I installed XP on the entire drive.  Then I tried to re-install Ubuntu using the same stick with total failure.  It's not a big deal because I overcame it by burning a CD & installing from that.  I just don't like unexplained problems because they are usually caused by some other issue that needs to be fixed.

---

### Post by Ms. Daisy on 2011-10-09
Wow. So it turns out the dual installation was a failure after all.  Windows kept freezing once I installed both systems.  Ubuntu is beautiful to look at and easy to use once you get it installed on your system, but good gravy- you have to be an expert to get it installed in the first place.

I decided just to erase the hard drive and install Ubuntu alone.  I need XP.  I need Ubuntu.  I also need to actually use this computer right now.   So once I learn Ubuntu & bash, I guess I'll try again. :sad:  

Feeling disheartened.

---

### Post by love2learn on 2011-10-09
windows is picky and needs the first few sectors of space on your hardrive to perform well. If you wipe the whole drive, install windows first. Then install ubuntu via live cd. you should be gravy. Windows (as long as it is first on the harddrive) should not be affected by ubuntu at all once both are installed. If it is flaky after you install ubuntu it was going to be flaky on your system anyway. 

Grub will update itself (although it doesnt look pretty) it will be functional without doing anything to it. 

If you need more help I will help as much as possible.

---

### Post by Ms. Daisy on 2011-10-09
You read my post before I edited it- sorry about that.  My frustration got the best of me. I've read so many other posts by frustrated newbies... I guess I've unwillingly joined those ranks. 


> **love2learn said:**
> If you need more help I will help as much as possible.

Thank you, very kind of you.   

> **love2learn said:**
>  If it is flaky after you install ubuntu it was going to be flaky on your system anyway. 

I hear you.  XP didn't become flaky until I installed Ubuntu, so you can see how I would think it was related. 

Any clue what would cause this flakiness in a system?  It's a brand-new hard drive, came with no software.  I've installed and erased about 6 times now, could that be messing with me?  Now I'm having trouble installing Ubuntu by itself on the entire hard drive. It installs and says it needs to restart.  I say OK and it never restarts, just gives me a black screen. Something is amiss and clearly needs to be diagnosed.

---

### Post by Ms. Daisy on 2011-10-09
Update: I finally installed Ubuntu.  Turns out it wouldn't install properly when I chose to install the third party software at the beginning.  But when I didn't click that box, it installed fine.

Now at least I can investigate this flaky computer from within.

---

### Post by love2learn on 2011-10-10
> **Ms. Daisy said:**
> You read my post before I edited it- sorry about that.  My frustration got the best of me. I've read so many other posts by frustrated newbies... I guess I've unwillingly joined those ranks. 

I hear you.  XP didn't become flaky until I installed Ubuntu, so you can see how I would think it was related. 

Any clue what would cause this flakiness in a system?  It's a brand-new hard drive, came with no software.  I've installed and erased about 6 times now, could that be messing with me?  Now I'm having trouble installing Ubuntu by itself on the entire hard drive. It installs and says it needs to restart.  I say OK and it never restarts, just gives me a black screen. Something is amiss and clearly needs to be diagnosed.


I completely understand your frustrations. I was like that back in 2002 with a debian install. It was much rougher then with dependencies to solve and what not. I truly understand how this can be difficult.

As far as the flaky aspect of your computer, I would need a more discriptive explaniation of what is going on. Is it going blank when your windows freezes? does the mouse stop working and that is considered a freeze? It may seem like the simplest detail and you want to keep from typing it, but it is often the simple details that clues in to the big problems.

Although I love that you are just installing ubuntu and forgetting windows, that was not your main goal. I would suggest getting windows to work fine on its own first. If there is a problem with windows, more than likely there is a problem with your hardware or drivers on your computer and we need to hash that out first. Once we get windows working properly, then we can go try ubuntu's live cd and see if everything works, and then while you are in the live cd, you should be able to install via a shortcut on the desktop. ( I actually havent tried 11.04 yet but I plan on installing it when my new laptop comes in on wednesday. My server, media center, and old laptop was on 10.04 still)

If you have the time and patience, we can accomplish your goal no doubt. If it is not that important to you then I dont want to steer you into regret. Either way I am subscribed and will be here when I am available.

Good luck!

---

### Post by Ms. Daisy on 2011-10-10
Thanks for your patience!  To reach my ultimate goal, I really do need XP and Ubuntu to both run successfully on this particular machine.  OK, I'll re-install windows XP professional which is what came on this computer when it was built way back in 2004.  May take me several days as I've got to borrow the DVD drive from a friend.  

In the meantime, here are my specs (you asked for descriptive, how's this for overkill?): HP Compaq Business Desktop dx2000 microtower.  I replaced the old 8 GB hardrive with a new Seagate 320 GB one.  Speed before & after is 7200 RPM.  Intel Pentium 4 Processor.  I added RAM to total 3 GB (4 is the max).  Original (and new) CD drive isn't recognized by the machine, so something's funky in the connection, cord, or bus that I haven't sorted out.  No wifi, just a standard ethernet connection to high-speed cable.  I disabled the on-board graphics and installed a NVDIA GeForce graphics card in a PCI slot.  I haven't really sorted out if I have exceeded the motherboard's or bus' capacity to process this new graphics card, but everything seems to be functioning fine.  That's all the tinkering I did inside (well, except for remove a huge amount of dust from inside the computer. Seriously.  That's nasty).
 
As for XP, I installed it after wiping out the new hard drive.  I let it install the 300 or so (!) updates from windows as well as the drivers for my printer & the graphics card.  Even installed my preferred anti-virus and firefox.  The whole process took roughly 6 hours, so I'm not overly excited to do it repeatedly.  I played around a bit to make sure it was functioning properly, bookmarking various websites and running software.  All was well in XP land.   I did NOT run a defrag because I figured it was a clean install and couldn't possibly be fragmented.  I'm also not sure how many times I restarted, but it wasn't more than 2.

Then I used the live CD to install Ubuntu along side XP.  I went with the partitioning that the software suggested.  Ubuntu installed without a hitch.  I updated, installed drivers, and played around on that to make sure it was running.  All was well in Ubuntu land.

Then I restarted and booted into XP.  Scan Disk automatically ran a check but not a full scan.  The XP desktop loaded.  For about 2 minutes upon startup, I could navigate around normally.  However, after about 2 minutes, the desktop froze, as in nothing was accessible.  The cursor moved around fine, but when it was over any icon or menu, I got the hourglass.  It never recovered.  My impression is that it didn't finish starting up completely but got stuck at a point (which made me think it couldn't find a startup file that got moved during partitioning).  I restarted several times with the same result.  I even tried to activate another scan disk quickly upon startup, but wasn't able to get to it before it froze.  I tried to boot in safe mode, but it would have none of that.  
 
Clearly I need to shut down & restart multiple times once I've gotten XP installed to flush out bugs, make sure it wasn't eventually going to freeze by itself anyway.  I'm wondering now: When I'm ready to install ubuntu, maybe I should schedule a full scan disk for XP right before I restart to the live CD, so that scan disk will run after Ubuntu installation before XP opens.  Or maybe I DO need to defrag before Ubuntu installation.  Thoughts?

---

### Post by love2learn on 2011-10-11
nice write up! I will refer back to that often as we go through the steps to get you fixed up. Questions for you. When you install your windows and it goes to partition the drive, what do you select? the whole drive? Half the drive?
 
If you select the whole drive I would run scan disk /defrag first before an ubuntu install. In my mind the scan disk will correct most of the bad sectors and the defrag will move most of the files to the front of the hard drive.
 
If you run with half the partition as ntfs and windows and leave the other half unformated for ubuntu then I would not worry about running scan disk or defrag as you are not messing with the partition that windows is on. Make sense? 
 
There are several ways to do what you are trying to do. You can dual boot side by side, you can vmware windows inside of linux/ubuntu or linux/ubuntu vmware inside of windows.
 
Its a fun and entertaining world with linux/ubuntu and it sounds like you like to tinker a bit as I see you know what you are talking about as far as internal computer parts. This should get fun and as long as we both keep level heads and a bit of patience you should be zooming around with a dual boot system in no time.
 
I just got my laptop in today and I plan on putting ubuntu on it tomorrow (I have a test I have to study for tonight or I would be playing with it now) I will update you with my progress as well and it will be fresh in my mind when you are ready for your install.
 
Good luck and keep me informed.

---

### Post by Ms. Daisy on 2011-10-12
Thanks.  To answer your question, Windows went on the entire disk.  I can't remember, but I don't think it gave me any automatic options for partitioning.  So I'll try again & defrag & run a scan disk when I re install.

I've read a bit about vmware, but it's not the ideal choice for me right now.  So I'm going to try and dual boot side by side.  I've been messing around with installing ubuntu on my Emac which is taking a phenomenal amount of time.  I hope to be working on the PC this weekend.  

Let me know how your laptop install goes!  Hope your test went well :)

---

### Post by love2learn on 2011-10-13
Thanks for the luck,

I passed my test with flying colors and that was my final so I have two weeks off to play. I have decided to wait until ubuntu 11.10 comes out to put it on my laptop. (should be available sometime tomorrow afternoon)

I think I am going to screen shot it and document it for a write up and I will throw it in here for a generic how-to.

Good luck with the emac and let me know when you start your desktop!

---

### Post by love2learn on 2011-10-14
Ok, everything went well and I am typing from a dual boot windows/ubuntu 11.10. I took a few screen shots when I could and I will probably put them together in the next day or so. 

Hows your emac coming?

---

### Post by Ms. Daisy on 2011-10-15
> **love2learn said:**
> Hows your emac coming? It's coming. It has become a bit of an epic battle. Ms. Daisy Vs. Little White Emac, the Emac is slightly ahead right now although I'm gaining on it. [http://ubuntuforums.org/showthread.php?t=1856556](http://ubuntuforums.org/showthread.php?t=1856556)
I'll be interested in seeing your screen shots.  I can only battle one machine at a time, but the PC will be next...

---

### Post by love2learn on 2011-10-30
I really did not like the new ubuntu with unity so i decided to wipe the drive and put Kubuntu on instead. I lost my screen shots in the process and didnt think about taking more for a new install. I will still be here for questions if you have any. I apologize about that!

---

### Post by Ms. Daisy on 2011-10-30
> **love2learn said:**
> I really did not like the new ubuntu with unity so i decided to wipe the drive and put Kubuntu on instead. I lost my screen shots in the process and didnt think about taking more for a new install. I will still be here for questions if you have any. I apologize about that!Interesting.  What didn't you like about 11.10?  The lenses look kinda cool.  Hard to get used to?

And I will be reinstalling XP once I figure out how to back up ubuntu 11.04.  I don't want to do a clean install.

---

### Post by apollothethird on 2011-10-31
> **Ms. Daisy said:**
> Interesting.  What didn't you like about 11.10?  The lenses look kinda cool.  Hard to get used to?

And I will be reinstalling XP once I figure out how to back up ubuntu 11.04.  I don't want to do a clean install.

I don't like all the extra clicks that are added to do things that were more efficient with 11.10.  With 11.04 it took two clicks to start an application.  With 11.10 it takes 4.  When you consider that I start hundreds of applications (many 10's of times) a day those extra clicks are very time consuming.

With 11.04 to start an applications, I'd click:

```
Click 1:  More Apps on the Launcher
Click 2:  My application from the recent list
```With 11.10 to start an application I have to click:

```
Click 1:  Dash Home
Click 2:  More Apps
Click 3:  Clear the last typed search
Click 4:  My application from the recent list
```I can't understand why the doubling of the clicks to start an application.  Of course I can hit super-a to bring up the More Apps screen, but that takes even more time in moving my hand off the mouse, searching the keyboard, then searching for the mouse again to continue.

I hope this oversight is fixed soon.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by love2learn on 2011-10-31
I agree. I did not like how things were hidden even more. It took me 2 minutes just to find the terminal and it would have taken longer if I didn't do a search for it. The menus did not make since and it was designed for a tablet pc or at least a touch screen and I am using a normal laptop. Ubuntu is banking on a future without normal computers and more touch screen stuff but in all reality a touch screen can not out perform a keyboard with things like office documents and school work which is what drives PC sales. Gamers will still need a mouse and keyboard to play most games so i really don't see a massive move to a touchscreen environment and since Ubuntu is designed for touch screens, I went with Kubuntu.



oh and as far as the backing up ubuntu. I love making my own live cd with remastersys. You can also use BackupPC as well.  Here are a few links to checkout.

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

[http://www.linuxlinks.com/article/20090105114152803/Backup.html](http://www.linuxlinks.com/article/20090105114152803/Backup.html)

[http://www.linuxlinks.com/article/20080412125404799/Keep.html](http://www.linuxlinks.com/article/20080412125404799/Keep.html)

---

