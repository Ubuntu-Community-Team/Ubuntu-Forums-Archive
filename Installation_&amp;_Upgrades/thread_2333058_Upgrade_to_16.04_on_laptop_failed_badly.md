---
title: "Upgrade to 16.04 on laptop failed badly"
date: 2016-08-06
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2016-08-06
I have upgraded four of my computers now, but the fifth, a Dell G60, failed spectacularly. During the upgrade, I was seeing "failed to fetch *this or that*" and messages of that sort. Also, during the install script, I got a few "failed to compile *whatever*". After the whole thing worked its was down to Reboot - and the machine rebooted - it all went sideways.

What I have now on my screen is a login prompt as if I was at a terminal. Ok, I've seen this before. I can log in, I can run various commands,, but I cannot start any sort of GUI.

  I ran the command "sudo apt update" and was told immediately:

"failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libc/"...[3 .deb packages]..." Temporaryt failure resolving 'us.archive.ubuntu.com'

There are three of these messages.

Also, during all this I am contunually getting:

"[  623.143639] sd 2:0:0:0: [sdb] Assuming drive cache: write through"
"[  674.854088] sd 2:0:0:0: [sdb] Asking for cache data failed"

Both of these messages appear periodically with no regard to what I am typing at the time.

I have a suspicion that I will have to start at the absolute beginning and completely reinstall every bit of the operating system and my software again. Fortunately, I make backups, but re-installing all the software will take a while.

Am I better off just wiping the HD and reinstalling 16.04 from a DVD?

Bill

---

### Post by WB0HYQ on 2016-08-06
UPDATE: I threw caution to the winds and issued three commands:

sudo apt update

sudo apt full-upgrade

sudo apt -f install

The first two completed quite fast - with only a few errors. To my astonishment, outside of a few "can't find it" errors, the third command began a long install session with a timeline across the bottom of the terminal screen. I marched slowly along, filling up the screen with all sorts of 'opening', 'removing', and 'updating' responses. In approximately 45 minutes, I was returned to my prompt with a request to restart.

When I did, there were some moments of blank screens, flashing screens, and then I had the familiar purple screen and a GUI login prompt. It started up slowly (as I figured it would after a major upgrade) but eventually I had my desktop back. The Unity bar at the left had a few missing icons on it, though. My screensaver (xscreensaver) was gone as well as a couple of others.

What mystifies me the most is the Ubuntu Software application. What happened to it? Why is it changed so drastically from the one in 14.04? I liked having a screenshot of what the software looked like. The app now doesn't show that. In fact, it is weird and I don't like it. The one this is does NOT do is list the add-on packaces and libraries that you could check to be installed at the same time. That  I really miss.

I think I can mark this as "solved", but I'm not sure how I did it.

Bill

---

### Post by Topsiho on 2016-08-07
Hi, I read your posts, as I am very much impressed by your mention that you've "been in computers since 1962", which is longer than most of us can say they are.
In1962 I was still sailing the seas as a ship's deck officer and then considered computers as quite utopian things. Never been to Ohio though :), had to be satisfied with such places as SF and NY (SF I liked very much).

I guess you put the upgrade procedure to a real test, upgrading a system with lots of (additional?) software, and probably not from the usual repositories and PPA's. If you upgrade from a not so usual situation to a new version of Ubuntu, then I guess (I never did this myself) you can expect the problems that you experienced.

I want to compliment you with your perseverance, and good luck with your new system,

Topsiho

Been in computers since 1980 (Acorn Atom) and programmable calculators since, I guess, 1975 (HP65).

---

### Post by WB0HYQ on 2016-08-07
Good morning, Topsiho. For the first 20 years, my computer expertise was gained in the US Navy as a hardware engineer and programmer. At first, we used Data General Nova's and SuperNova's, mostly as data-crunchers and, in a few instances, as a curiosity. Twelve years into my career, I was stationed at Skaggs Island, California where the Navy's centrol control point for the HFDF net was located. The computers used there were Burroughs D-825's (massive room-filling computers) and Bunker-Ramo BR-133's at each outstation. I taught programming classes for three years there and went on to finish my career running a department as a senior enlisted man.

Before I retired, Heathkit came out with their computer line of H-8 and H-89 computers, which I took to immediately. I used these computers, coupled with my ham radio hobby, by building interfaces between them. Then I retired and went to work for RCA in Camden, New Jersey for 5 years, building the replacement computers system for the one I used while on active duty. We used DEC PDP-8, PDP-11, and VAX mainframes. I stayed in the computer field right up until 2009, when I retired a second time.

Now, at 74, I still work at building computers for friends, designing web sites, and writing apps for Androids. All along, I was involved in UNIX/LINUX at times, but never in the mainstream. As for the upgrade from 14-04 to 16.04 you are probably right. I did test the upgrade system pretty severely. I had loads of specialized programs (mostly written by myself) on the machine and didn't want to simply wipe them out and start again, so I made a few educated guesses and managed to pull it through.

The first three computers upgraded easily but the fourth one really taxed me (and it) to the limit. It is running now, but very slowly for some reason. It might take three or four seconds for any app to start up and when it does, a window forms but it is filled initially with the background image and then the desired screen. I suspect that the X-driver for my NVIDIA card may be at fault so I am going to try and use one of the proprietary NVIDIA drivers and see if that helps. I'm relucant to do so because the last time I tried that, I had to reset back to the default driver.

Bill

---

### Post by plantmaven on 2016-08-07
Good work on the fix. I also had a fail on an HP 630 laptop. I kicked off the upgrade and it showed the steps it would complete. We left it and went to lunch. Upon return, apparently the laptop only got to the download and then asked if I wanted to upgrade. Pretty stupid question at this point, except it overheated the processor and the laptop crashed. On restart, the terminal prompt was the only access. I looked around to make sure the file system in tact, then sudo apt-get install. I had created a bootable DVD with the iso image, but no matter what I did, I could not mount the DVD. So, at the prompt, I entered "sudo apt-get install' and hit enter. It then began the install and the laptop rebooted into the new version with just a spurious System error here and there. I've seen these before with verision and I just cancel them. Eventually, they clear up. Hope this helps anyone else in the same boat.

---

### Post by WB0HYQ on 2016-08-07
Ah yes. I also saw a couple of spurious system faults and wanting to report them. I reported them and went my own way. Like you say, they eventuality clear up. I am hoping the overall sloth of the system will go away soon also as it is really slow.

Bill

---

### Post by Topsiho on 2016-08-07
I did two upgrades, and one clean install on a brand new laptop, which all went very smooth. Though, 14.04 is still the more stable system. When upgrading from 12.04 to 14.04 this was quite the same. So, with a little patience 16.04 will be as stable as a rock.
To  WB0HYQ: thanks for answering my post. I see you taught programming. Which reminds me that I forgot mentioning my experience while in the university: I had to teach myself Fortran IV when I had to compute something for the WSRT telescope in Westerbork, and after half an hour I decided I had to do this using the CDC computer of the university: by hand it would take some millions or more of years, and I didn't expect to live long enough for that. So I got some book on Fortran programming from the library. And programmed some thousands of spaghetti lines.

When taking a course on Pascal I discovered why it was such tedious work developing the Fortran programs.

That was around '72 or '73 or so.

Topsiho

---

### Post by WB0HYQ on 2016-08-07
I've picked up so many computer languages over the last 50+ years that I figure I know how to use around 30 of them. Initially, we used IBM cards fed into a reader or simple switches to toggle in machine language on a front panel. We've come a long way from that - thank goodness.

Bill

---

### Post by HippieDave on 2016-08-07
When I upgraded my Thinkpad X220 from 14.04 to 16.04 it has frozen everything.  When I boot up, I get a read out of "started" or 'starting' or 'created" this or that, but then the computer just sits frozen...I can't even open a terminal window.  What do I do?

---

### Post by WB0HYQ on 2016-08-08
Actually, Dave, what I would do is post this in a new thread instead of this one. When people see the "[Solved]" heading, they might just pass it by.

Not being able to open a terminal window would be a problem. What I'd suggest is burning an ISO copy of 16.04 and booting up with that DVD. Then check your file system with some of the tools on it to see if your HD is okay. If it is, then copy off all your important files (documents, music, pictures, etc) to an external drive and do a complete new install on your Thinkpad.

Bill

---

