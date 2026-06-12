---
title: "Servers down??? ARGH!!!!!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by DarkStarAeon on 2007-04-21
Ok, I've been slowly downloading the upgrade (via update manager) for well over 32 hours now, it would stop and give an error now and then and I'd have to restart the update so it could pick up where it left off.

So now, just minutes ago, it was only a few files away from having fetched them all when quite suddenly it stops and I get this error:

> **Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.



This is the longest, most tedious upgrade I have ever done in my life. Ridiculous.

Seriously, I should have just stayed on 6.10.

I understand everyone and their brother is trying to upgrade right now, but I seriously thought Ubuntu would have the resources to handle the load. I was obviously very mistaken.

Worst part is, even if it does let me finish the upgrade, which right now it won't, I'm sure as soon as it finishes It'll reboot and have to deal with errors galore, seems like many have had to.

Ubuntu, great distro if you get it installed, but spend more time working on a stable upgrade than on cranking out something new every 6 months, why rush it?

argh, back to the grind...

---

### Post by jdong on 2007-04-21
Sorry about the hectic situation; there are literally millions of users pounding the upgrade servers right now, and at 700MB or more of upgrades per person, even the most prepared ISP has issues dealing with that kind of load...


My best suggestion is to wait a few days and try it again, and hope for better luck. I wish I could do something to help :)

---

### Post by DarkStarAeon on 2007-04-21
I'm just frustrated mate, I was so close. Over 32 hours of patience crapped out eventually, I had like 10 more files to go. argh.

I know, I know...everyone is hitting it up, and it's a lot to download, don't get me wrong, I love Ubuntu, I just wish you guys had posted a note in the Update Manager saying it might be best to wait or something like that. I started the download before I'd had my first cup of coffee and didn't even think about the server load.

sigh.

---

### Post by thegrimgod on 2007-04-21
Im gettin this "Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)" hope its their server and not somethin i did lol, but if u know if i messed up somewhere pls let me know :)

---

### Post by jdong on 2007-04-21
> **DarkStarAeon said:**
> I'm just frustrated mate, I was so close. Over 32 hours of patience crapped out eventually, I had like 10 more files to go. argh.

I know, I know...everyone is hitting it up, and it's a lot to download, don't get me wrong, I love Ubuntu, I just wish you guys had posted a note in the Update Manager saying it might be best to wait or something like that. I started the download before I'd had my first cup of coffee and didn't even think about the server load.

sigh.

Well fortunately no changes are done to the system (other than reconfiguring the updater to look for Feisty upgrade path) until everything is fully downloaded, so it's not the end of the world if the download can't finish right now....

---

### Post by DarkStarAeon on 2007-04-21
I got that too, it's just not available right now. sigh

Wait awhile and try again then.

---

### Post by jdong on 2007-04-21
> **thegrimgod said:**
> Im gettin this "Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)" hope its their server and not somethin i did lol, but if u know if i messed up somewhere pls let me know :)

Yeah, that's the server hammered... It doesn't look like you did anything wrong :)

---

### Post by DarkStarAeon on 2007-04-21
> **jdong said:**
> Well fortunately no changes are done to the system (other than reconfiguring the updater to look for Feisty upgrade path) until everything is fully downloaded, so it's not the end of the world if the download can't finish right now....

Actually I can't add or remove programs right now, it won't let me.

But I know it's not the end of the world, it's just really, really frustrating.

---

### Post by jdong on 2007-04-21
> **DarkStarAeon said:**
> Actually I can't add or remove programs right now, it won't let me.

But I know it's not the end of the world, it's just really, really frustrating.

Right, the package manager right now is configured to only look for Feisty packages. You can open up /etc/apt/sources.list with a text editor, replace all feisty with edgy, then perform a list reload, and it will look for Edgy packages again.

---

### Post by DarkStarAeon on 2007-04-21
That's true, I could just do that. thanks.

If Feisty doesn't end up installing properly though, I may send Ubuntu the hair I rip out of my head. lol

---

### Post by DougieFresh4U on 2007-04-21
You could also try another country code. I had switched mine to gb as I always get a better download speed than I do here in the states. Just a thought.:)

---

### Post by DarkStarAeon on 2007-04-21
Tell me where and how and I'm on it.

---

### Post by jdong on 2007-04-21
in sources.list, replace all instances ca.archive.ubuntu.com, us.archive.ubuntu.com, or archive.ubuntu.com with:

mirror.anl.gov




If you manage to overload the Argonne National Lab, please let me know. I'll personally mail you a trophy. :D

I'm not trying to say this as a rub-salt-in-wound joke, but [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) lists a bunch of mirrors from all around the country, their completeness, etc. You can also try those if this mirror doesn't work. Of course, if launchpad gets hammered and goes down....

---

### Post by bearcat on 2007-04-21
> wait a few days and try it again

I know it's hardly the end of the world or anything, but quite frankly, when I upgrade my operating system should be *my* choice, not something I have to line up for three or four days to do. Any operating system that I can't upgrade the very *minute* an upgrade is made available, if that's when I want to do it, needs to do some *serious* thinking about whether it wants to be taken seriously or not. The average Windoze user sure as hell isn't going to put up with "what do you mean, I have to wait a week to get an upgrade that's already available?" if he can just go down to his local Best Buy and buy a copy of Vista in an hour flat.

---

### Post by DarkStarAeon on 2007-04-21
Geesh, I'm just not thinking today. That was obvious on how to do that, I must need more coffee. lol

Ok, I want a trophy! I'm going to try! hahaha.

Ahh, thanks, I wish I'd known about that list before!

---

### Post by DarkStarAeon on 2007-04-21
> **bearcat said:**
> I know it's hardly the end of the world or anything, but quite frankly, when I upgrade my operating system should be *my* choice, not something I have to line up for three or four days to do. Any operating system that I can't upgrade the very *minute* an upgrade is made available, if that's when I want to do it, needs to do some *serious* thinking about whether it wants to be taken seriously or not. The average Windoze user sure as hell isn't going to put up with "what do you mean, I have to wait a week to get an upgrade that's already available?" if he can just go down to his local Best Buy and buy a copy of Vista in an hour flat.

You're preaching to the choir man, I feel the same. But the reality at the moment is we have to wait.

---

### Post by heimo on 2007-04-21
> **bearcat said:**
> I know it's hardly the end of the world or anything, but quite frankly, when I upgrade my operating system should be *my* choice, not something I have to line up for three or four days to do. Any operating system that I can't upgrade the very *minute* an upgrade is made available, if that's when I want to do it, needs to do some *serious* thinking about whether it wants to be taken seriously or not. The average Windoze user sure as hell isn't going to put up with "what do you mean, I have to wait a week to get an upgrade that's already available?" if he can just go down to his local Best Buy and buy a copy of Vista in an hour flat.

How many other mirrors did you try? Try couple different if the first one doesn't work.

---

### Post by sumgi on 2007-04-21
> **jdong said:**
> in sources.list, replace all instances ca.archive.ubuntu.com, us.archive.ubuntu.com, or archive.ubuntu.com with:

mirror.anl.gov




If you manage to overload the Argonne National Lab, please let me know. I'll personally mail you a trophy. :D

I'm not trying to say this as a rub-salt-in-wound joke, but [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) lists a bunch of mirrors from all around the country, their completeness, etc. You can also try those if this mirror doesn't work. Of course, if launchpad gets hammered and goes down....

You are a huge life saver, after changing my destination server my dl speed went from ~24 kb/s to around 400! That's 7 hours vs 15 min!!!

---

### Post by DarkStarAeon on 2007-04-21
you guys were right, that made a **huge** difference, thanks! :)

---

### Post by jdong on 2007-04-21
Awesome, glad to hear that.

P.S. There's no need to lecture us about the importance of readily available download servers to handle this highly anticipated upgrade. However, we can't do anything about it, and nobody involved with Ubuntu is sitting there deciding "hmm, let's not prepare to handle the bandwidth so we can watch people try desperately to upgrade" :). Keep it constructive :)

---

### Post by DarkStarAeon on 2007-04-21
I wasn't lecturing anybody, I was just saying I was frustrated, I don't think it's unreasonable to say that. I said I thought you guys would be able to handle the mega-load, and I said I was mistaken in thinking that. I realize the servers are slammed, I've said that in other threads before I made this one. Never said it was a conspiracy, lol. 


Anyway, thanks for the help mate :)

---

### Post by jdong on 2007-04-21
Not a problem, it's all cool.

It brings no pleasure to any of us that users aren't able to get their anticipated upgrade to this wonderful operating system ;-)

---

### Post by bearcat on 2007-04-21
> How many other mirrors did you try? Try couple different if the first one doesn't work.

I'm not talking from a personal perspective here; I'm in the process of downloading the upgrade from a mirror right now. What I'm talking about is the fundamental principle: if you want Ubuntu to become a serious challenger in the desktop operating system market, expecting people to magically *know* that they should change their download mirror -- or how to do that -- simply isn't going to cut it. 

What I'm seeing here is a flawed assumption that what seems obvious and straightforward to a hardcore Linux geek is also going to be obvious and straightforward to an average computer user. T'ain't necessarily so, is all I'm sayin'. Find a way to communicate the possibility and the value of doing this, as well as the process for actually doing it, a bit more effectively and clearly next time, is all I'm sayin'. I had to piece together information from five or six different threads in this forum to find out (a) where any alternative mirrors were located in the first place, and (b) how to actually get Upgrade Manager to go to one of them instead of the master server. That information should have been more easily available to me in the first place -- but not only did I have to hunt it down, I had to search and search just to even get a basic *explanation* of what I *still* had to *hunt* for. That's all I'm sayin'.

---

### Post by heimo on 2007-04-21
That's cool bearcat. And I disagree with you.

---

### Post by DarkStarAeon on 2007-04-21
> **jdong said:**
> Not a problem, it's all cool.

It brings no pleasure to any of us that users aren't able to get their anticipated upgrade to this wonderful operating system ;-)

That's exactly it, it is wonderful, that's why we act like junkies needing our fix if we can't score the latest and greatest Ubuntu! lol

---

### Post by heimo on 2007-04-21
> **DarkStarAeon said:**
> That's exactly it, it is wonderful, that's why we act like junkies needing our fix if we can't score the latest and greatest Ubuntu! lol

[Upgrade early, upgrade often]("http://www.catb.org/%7Eesr/writings/cathedral-bazaar/cathedral-bazaar/ar01s04.html"). ;)

---

### Post by tiddy on 2007-04-21
The Bittorrent tracker is also down I think. But tis not such a big problem.

---

### Post by heimo on 2007-04-21
> **tiddy said:**
> The Bittorrent tracker is also down I think. But tis not such a big problem.

Yeah, it seems to be.  My uploads had stopped somewhere around 10GB. I'd like to donate some more bandwidth.

---

### Post by DougieFresh4U on 2007-04-21
> **bearcat said:**
> I'm not talking from a personal perspective here; I'm in the process of downloading the upgrade from a mirror right now. What I'm talking about is the fundamental principle: if you want Ubuntu to become a serious challenger in the desktop operating system market, expecting people to magically *know* that they should change their download mirror -- or how to do that -- simply isn't going to cut it. 

What I'm seeing here is a flawed assumption that what seems obvious and straightforward to a hardcore Linux geek is also going to be obvious and straightforward to an average computer user. T'ain't necessarily so, is all I'm sayin'. Find a way to communicate the possibility and the value of doing this, as well as the process for actually doing it, a bit more effectively and clearly next time, is all I'm sayin'. I had to piece together information from five or six different threads in this forum to find out (a) where any alternative mirrors were located in the first place, and (b) how to actually get Upgrade Manager to go to one of them instead of the master server. That information should have been more easily available to me in the first place -- but not only did I have to hunt it down, I had to search and search just to even get a basic *explanation* of what I *still* had to *hunt* for. That's all I'm sayin'.
Excuse me?? I am not no Ubuntu "geek" by all means, with that out of the way if you would have a look in Synaptic Package Manager>Settings>Repositories- You wil see **"Download from"** and a drop down list which has "Other"  Thank you very much!!

---

### Post by kvonb on 2007-04-21
> **bearcat said:**
> I know it's hardly the end of the world or anything, but quite frankly, when I upgrade my operating system should be *my* choice, not something I have to line up for three or four days to do. Any operating system that I can't upgrade the very *minute* an upgrade is made available, if that's when I want to do it, needs to do some *serious* thinking about whether it wants to be taken seriously or not. The average Windoze user sure as hell isn't going to put up with "what do you mean, I have to wait a week to get an upgrade that's already available?" if he can just go down to his local Best Buy and buy a copy of Vista in an hour flat.

Well here's an idea, why not donate some money to the Ubuntu project for extra bandwidth .

The bandwidth that is offered to you FREE of charge could probably do with the extra funds.

The "I demand everything free, and I demand it now" attitude is extremely unbecoming.

---

### Post by MikeBlyth on 2007-04-21
OK, here's my perspective as a new user. I installed Ubuntu yesterday, knowing nothing about it except that it was supposed to be easy, and it was a one-dvd download. I've been using Fedora for the past couple of years and am more than a newbie but less than expert on the ins-and-outs of upgrading, packages, etc.

My first reaction was that I was blown away when I discovered how easy the install was. Incredible. So yesterday I installed one game (the system is for my son) -- also amazingly easy. I went to install another game and bam! started getting the "conflicts with other installed software" message. Tried uninstalling one game, all the games. Found that even so I couldn't install *anything*. Naturally, I figured my system was broken, not that some servers somewhere were busy. It took quite a while of searching the web & this forum for the error message before I found this thread and discovered (1) it was not my problem and (2) I could get around it by editing sources.list. 

So, kudos to all you you developers for this distro and how easy it is to set up. In this one issue, though, you really should protect the user better. It shouldn't be too hard for the add/remove application to give a better analysis of the problem. You could even set up your servers somehow to communicate a condition to the download manager. Whatever it takes. Sure, it may not take much Linux knowledge to figure out the problem (more than I had, though) but that is not the issue, it seems to me as a new user. Rather, if indeed you're targeting new users without Linux knowledge, you need to coddle us, woo us from the security of whatever system we're already using, and keep us long enough to get us hooked. Just a thought.

---

### Post by NickPresta on 2007-04-21
To be completely fair, when your system breaks or a similar error occurs in Windows, you still have to search the web with cryptic error codes and such too.

I understand where you're coming from though.

---

### Post by DarkStarAeon on 2007-04-21
Ok, here's how it went, the good, the bad, and the uhhh feisty:

After 33 hours of fetching files it finally continued on to finishing the upgrade. I was asked repeatedly about whether I wanted to keep old files or replace them, I knew a few of them and was glad it asked as I wanted to keep them, but several I had no clue what they were and just decided to keep them, I guessed correctly it seems.
So then after that, it did a few other things and I watched progress bars fill up as it did so. Then it said the upgrade had completed and I clicked the button, however, a blank dialog opened then everything froze expect my mouse. So, I decided to wait. 1 hour later nothing happened.
So I did Alt+F4 and closed the dialog and that worked. Which my system unfroze immediately. weird.

So, it was supposed to reboot on it's own but didn't, I'm guessing that blank dialog that opened was asking me if I wanted to reboot, but I of course couldn't read it. That happens though, so whatever.

I reboot the computer and sure enough X crashes and fails to load. I was prepared for this though...

I had written down all the commands people had posted on how to uninstall then reinstall graphics drivers for nvidia, however, even though I had removed Envy, they still wouldn't load.
So I used wget to get the new unstable version of Envy and within seconds I had my GUI back.

So the new login screen opens (very nice by the way, slick) and I log in.

I get a message about me using restricted drivers and I click on it so I can the restricted drivers manager, nice touch.

After that, Feisty Fawn has run absolutely beautifully. I have to admit I am very impressed, and feeling a little bad for giving the Ubuntu crew some minor grief about my frustrations I had upgrading.

**Anyway, here are some _positive_ notes now that Feisty Fawn is up and running:**

1. Holy crap my system is faster!!! Nice! I have a 2.8 GHz dual processor, 4 GB of RAM, etc. it's a fast computer and I was impressed on 6.10 with how much faster my system was than when I was on Windows, but with Feisty Fawn I feel like this thing is going so fast it's going to start flying! Awesome :)

2. VMware works about 1,000 times better. It was ok before, but it starts up faster, runs smoother and I have almost zero lag on the mouse now. This is awesome. Thank you!

3. The internet connection manager is awesome, and even better is my internet connection stayed set up during the upgrade. Also, I noticed my internet connection seemed dramatically faster, so I checked, and my download speeds now are 3 times what they were on average before! This I like!

4. All the new programs/apps/etc available are very cool. :)

5. The interface changes are subtle, but slick, I like it. 

6. Changing my mirrors in the sources list really helped with everything both pre and post install, (thanks jdong!).

7. The disk useage anazlyzer rocks.

8. Overall, everything is..well..better!

9. I had a highly customized theme with a lot of extras added in, and I was very worried about this being an issue during upgrading, the only problem I had was during the install it said something about the human theme icons having a problem, so I switched back to the default theme real quick and the problem was solved, then I just switched back to my custom theme after the reboot and X reconfiguration mentioned earlier.

10. I don't know how, or why, but my graphics card seems to be working much better. Don't care how it happened but glad it did!

So it was definitely worth the frustrations of upgrading. :)

Lessons learned: Next time, I'll wait to upgrade until the bulk of users are done upgrading. Very glad I came on the forums though and took notes for possible bad scenarios just in case. Also, I'll always check to see if Envy has a new version for the latest version of Ubuntu first, because Envy is the only thing that seems to get my graphics card happy. 

Only minor gripe: Tired of editing /boot/grub/menu.lst every time there is an upgrade to anything major, I dual boot Ubuntu and PC-BSD and it's not a big deal, but it's just one thing I wish I didn't have to do.

Very glad I didn't have to do a fresh install, that would have been a nightmare for me as I have almost every single program on my computer customized to some extent and I would not want to re-do all my settings.

Feisty Fawn is even better than Edgy, nice work Ubuntu crew!

---

### Post by LLauranzonIII on 2007-04-21
same problems trying to get the upgrade.  i'll just give it a week or two.  no hurry here.

---

### Post by jdong on 2007-04-22
> **DarkStarAeon said:**
> Ok, here's how it went, the good, the bad, and the uhhh feisty:

After 33 hours of fetching files it finally continued on to finishing the upgrade. I was asked repeatedly about whether I wanted to keep old files or replace them, I knew a few of them and was glad it asked as I wanted to keep them, but several I had no clue what they were and just decided to keep them, I guessed correctly it seems.
So then after that, it did a few other things and I watched progress bars fill up as it did so. Then it said the upgrade had completed and I clicked the button, however, a blank dialog opened then everything froze expect my mouse. So, I decided to wait. 1 hour later nothing happened.
So I did Alt+F4 and closed the dialog and that worked. Which my system unfroze immediately. weird.

So, it was supposed to reboot on it's own but didn't, I'm guessing that blank dialog that opened was asking me if I wanted to reboot, but I of course couldn't read it. That happens though, so whatever.

I reboot the computer and sure enough X crashes and fails to load. I was prepared for this though...

I had written down all the commands people had posted on how to uninstall then reinstall graphics drivers for nvidia, however, even though I had removed Envy, they still wouldn't load.
So I used wget to get the new unstable version of Envy and within seconds I had my GUI back.

Yeah, I can see that happening too... if you had been using 100% repository drivers, the upgrade would've worked, but it's expected you'd have to run Envy again if you used it to install drivers initially. 

> 
1. Holy crap my system is faster!!! Nice! I have a 2.8 GHz dual processor, 4 GB of RAM, etc. it's a fast computer and I was impressed on 6.10 with how much faster my system was than when I was on Windows, but with Feisty Fawn I feel like this thing is going so fast it's going to start flying! Awesome :)

A lot of speed improvements went into core libraries. Try this: Open Openoffice. Close it, then open it again. The second time on my 1.6GHz Core Duo, it launches in under 1 second. Kudos!

> 
2. VMware works about 1,000 times better. It was ok before, but it starts up faster, runs smoother and I have almost zero lag on the mouse now. This is awesome. Thank you!

Supposedly there's some VMI virtualization layer support in Feisty, or maybe Feisty's kernel is simply improved :D

> 
7. The disk useage anazlyzer rocks.


This has been one of my FAVORITE features of Feisty -- the new views are much more informative!

---

### Post by DarkStarAeon on 2007-04-22
Yeah seriously that disk useage analyzer is awesome, such a simple thing but incredibly useful!

Haha!!! Dude, I just did that with OpenOffice, you were not kidding! wow that's fast! :)

Yeah whatever it is, VMware works incredible now, Ubuntu team did a great job speeding things up.


You know what else I just noticed? It finally shows all 4 GB of RAM instead of just 3.5 like it did before! yay!

I do wish I could access files on PC-BSD on my other drive like the people who have Ubuntu/Windows dual boot installs, but can't have it all I guess, lol.

---

### Post by bearcat on 2007-05-05
> Well here's an idea, why not donate some money to the Ubuntu project for extra bandwidth .

The bandwidth that is offered to you FREE of charge could probably do with the extra funds.

The "I demand everything free, and I demand it now" attitude is extremely unbecoming.

kvonb, one of the reasons I use Linux is that I'm living on disability insurance and can just barely make ends meet month to month as it is. I don't *have* the money to donate. If I could *afford* to pay for software, frankly, I'd probably have stuck with Windoze.

So I'll kindly thank you to spare me the passive aggressive "pony up the cash or shut your self-centred cakehole" routine, which is every bit as unbecoming.

---

### Post by jdong on 2007-05-05
Infrastructure is not something that builds up overnight.... Ubuntu has a gigantic user base, and the bandwidth required to service this user base can be unfathomable on peak times -- it is easy to say "Canonical should be able to service all these users", but very tough to implement.

"Pay or shut it" will never be an official stand on the quality of service with Ubuntu. If it ever gets to the point where somehow paying buys you a more elite Ubuntu experience, I would personally seriously reconsider my choice of distribution.

---

