---
title: "Installation woes"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by SimonDavies on 2012-04-28
I come from a Windows background but recent experiences with Win 8 have lead me down a path to (hopefully) enlightenment.

I started having a look at 12.04 about a month ago, using a daily build on my laptop and later on my desktop to get a feel for the OS and up to date I have been impressed with what I saw.... until recently.

I did an in-place upgrade on my laptop which went smoothly and the laptop is running really well (Dell), however my main rig (Asrock Z68, Intel i7 2600K with Nvidia 580GTX) just seems to be plagued with issues.

Rather than doing an inplace upgrade I decided to go down the route of fresh install, first of all I couldn't even get the loader to display properly if using my main 580GTX as the display, I would get the main screen load up but at that point nothing, no mouse movements, no keyboard responses, nothing. I then changed over to my onboard display (Intel HD3000) but to do that I have to BIOS switch it over otherwise it still tries to use the PCIE card.

Installation begins, in the past when I have installed Ubuntu it took maybe 10 minutes (I install it onto an SSD and have a 50mb connection at home), the last couple of times however took an age. I then discovered that my new (1 month old) SSD was showing bad blocks so thought OK, fair enough dodgy SSD. I then replaced that with a new 90gb SSD (Kingston) and things went from bad to worse.

My installation last night took me over 2 hours and at the end of that 2 hours I was left with a system that showed me a black screen, so back to Windows 7 I went to have a game of Warcraft (the pretty much only reason I haven't moved to a *nix OS at the moment is my gaming). Come this morning I plug the SSD back in, swap over the displays again and power on my machine to do a fresh install but get side tracked and miss hitting f11, lo and behold my desktop loads into the main Ubuntu screen and shows no sign of having any kind of Nvidia display drivers being installed on it.

With issues like these it's little wonder that a lot of Windows users stick with Windows because unfortunately (for the most part) it just works. I was having much more success with 12.04 beta 2 than I am with the RTM and honestly am beginning to wonder to myself whether it's really worth the hassle because the OS still isn't really working as expected, the Software center isn't showing the same applications that the beta did (trying to install CrossOver which simply doesn't show in the Software center for me) and the missing Nvidia driver issue is starting to make me question my initial zeal where Ubuntu is concerned.

At the moment I do understand that the servers are taking a hit and that could explain the delays in installations but as a user who comes from a Windows background I kinda just expect my hardware devices to work and at the moment am struggling to get the card drivers installed again.

Fresh install number 4 of this week here we go :( and should this installation not go smoothly then it may be time to look at a different distro.

---

### Post by mebunto on 2012-04-28
I've been a Ubuntu/Kubuntu convert for some years.  I'm using Kubuntu 12.04 release with a similar processor to you.  I was using Kubuntu 11.10 without any problems and I decided to install 12.04.  I've found that at the moment it is crashing and rebooting of its own accord .... I guess I'm saying that 12.04 looks unstable.  I suggest that you try 11.10 and I doubt that you will have any major issues, new releases can be a bit flaky for some but they improve over time. Ultimately it's quite liberating to be free of expensive Windows stuff.

---

### Post by shumifan50 on 2012-04-28
My feeling is that 11.04 onwards is a step backwards in the life of Ubuntu. Unity might be grat for tablets(or not), but for serious work it requires too many key strokes/clicks to get to the app you want, and many times it is a nightmare to find it. Currently this can be somewhat circumvented by installing gnome-panel and changing your settings during login to get the old more familiar interface.
Some of the bad things in Unity:

1. It has a mind of its own where a window will be displayed. You can drag it to where you want and in a while it gets moved back to where you DONT want it.
2. Upgrading an 11.10 to 12.04, from CD, in place corrupted the installation now requiring a fresh installation.
3. Keeping multiple windows visible on the desktop has become more challenging.
4. As a touch interface Unity is not good as it still has the tiny buttons to minimise/close an app. I have an inspiron duo with capacitive touch screen (so no accurate stylus) and this is almost unworkable in tablet mode.
5. Finding what you are looking for is a nightmare. What used to take 2/3 clicks is now many more clicks and much reading.


I would recommend 10.04LTS but it is no longer supported, what a shame.

---

### Post by kc1di on 2012-04-28
there are likely serveral problems that need fixing. 
one of which is Nvidia drivers are not working with compiz at the moment.  Which is causing compiz to  crash.  if you can get to the ubuntu 2d session then you can disable nvidia propriety drivers that may help in the screen being black.

other than that I would suggest what another already has go back to ubuntu 11.10 for the time being and wait awhile till some of the bugs are worked out in 12.04.  It's a good release but some bugs will take time to fix as they are reported.

Cheers :)
D ;)

---

### Post by Cheesemill on 2012-04-28
> **shumifan50 said:**
> I would recommend 10.04LTS but it is no longer supported, what a shame.
10.04 is supported for another year on the desktop and another 3 years for the server version.

---

### Post by grahammechanical on 2012-04-28
You say

> With issues like these it's little wonder that a lot of Windows users stick with Windows because unfortunately (for the most part) it just works. I was having much more success with 12.04 beta 2 than I am with the RTM and honestly am beginning to wonder to myself whether it's really worth the hassle because the OS still isn't really working as expected, the Software center isn't showing the same applications that the beta did (trying to install CrossOver which simply doesn't show in the Software center for me) and the missing Nvidia driver issue is starting to make me question my initial zeal where Ubuntu is concerned.

You would have exactly the same problems with Microsoft and Apple products if they were brought over the counter and installed on who knows what variations in hardware.

Nvidia drivers are proprietary and are not the responsibility of Ubuntu. Crossover is a commercial product which you purchase from the Codeweavers web site and also proprietary. I doubt very much if it was ever available thought the Ubuntu Software Centre. Perhaps you are confused over Wine. which most certainly is in the Software Centre.

The Linux developers are always playing catch-up with the hardware with little if any support from the hardware makers. A lot of Windows users stick with Windows because they know of nothing else and are not given a choice.

Ask for help by all means but remember when you express an opinion, you invite me to express my opinion. And my opinions will always disagree with your opinions. Be sure of that.

---

### Post by keepitsimpleengr on 2012-04-28
> **Cheesemill said:**
> 10.04 is supported for another year on the desktop and another 3 years for the server version.

Well, 10.04 LTS is not quite fully supported.  I have to manually install the nvidia driver at each kernel upgrade because 10.04's nvidia-current doesn't support my year old video-adapter.

[INDENT]On the other hand I get the latest/greatest driver! :wink:[/INDENT]

---

### Post by keepitsimpleengr on 2012-04-28
> **SimonDavies said:**
> I come from a Windows background but recent experiences with Win 8 have lead me down a path to (hopefully) enlightenment.
 &#8943;  &#8943;
Fresh install number 4 of this week here we go :( and should this installation not go smoothly then it may be time to look at a different distro.

I have had horrific experiences installing and upgrading Ubuntu, some of which could be laid at my own feet.  But here's my advice:[INDENT][LIST]
[*]Of all the distros, and with all it's rough edges, Ubuntu survives and provides.
[*]Release upgrades are consistently problematic, *tempus est optimum sanator* (Time is the best healer) impatience is the enemy.
[*] Non·mainstream hardware (*e.g.* not found in widely distributed commercial packaged systems) can present real headaches.
[*]Real assistance is available from an large, energetic, passionate, sometimes raucous but always there community.  But thinking is essential. Politeness is rewarded.
[*]As in *Si vis pacem, para bellum*, for Linux S*i vis nova, prior facere exemplum* (roughly… "For success in release upgrade, back up your existing system").  And prepare to redo it again.
[*]When dicouragement and frustration arise, remember *Vista!*
[/LIST][/INDENT]
If it makes you feel any better I will be upgrading a 10.04 LTS, three 10.10 (two with Mythtv 0.24 to 0.25) on 64 bit hardware, and an 11.04 & 11.10 with Gnome desktops on 32 bit hardware, one of which is a poorly supported laptop.   In preparation, I have padded the walls of my home office. ;)

---

### Post by critin on 2012-04-28
> **grahammechanical said:**
> You say



You would have exactly the same problems with Microsoft and Apple products if they were brought over the counter and installed on who knows what variations in hardware.

Nvidia drivers are proprietary and are not the responsibility of Ubuntu. Crossover is a commercial product which you purchase from the Codeweavers web site and also proprietary. I doubt very much if it was ever available thought the Ubuntu Software Centre. Perhaps you are confused over Wine. which most certainly is in the Software Centre.

The Linux developers are always playing catch-up with the hardware with little if any support from the hardware makers. A lot of Windows users stick with Windows because they know of nothing else and are not given a choice.

Ask for help by all means but remember when you express an opinion, you invite me to express my opinion. And my opinions will always disagree with your opinions. Be sure of that.


+1


Hardware and drivers are made especially for Windows OS and its apps.  They are sold already installed on those machines, of course they work out of the box--they're made for each other.  Given the code from microsoft drivers are built/tested months before a release to the public.   linux can't work with closed code to do this.  And the OEM is restricted to ONE machine only...When it breaks you can just buy another.

Using open source I have no issues with drivers.

---

### Post by SimonDavies on 2012-04-28
> **grahammechanical said:**
> You say

You would have exactly the same problems with Microsoft and Apple products if they were brought over the counter and installed on who knows what variations in hardware. 

Actually pretty much most of the software and hardware I have purchased over the counter and installed have pretty much worked over the years, infact the only product I can remember having this many problems with was MS Fista.

> **grahammechanical said:**
> Nvidia drivers are proprietary and are not the responsibility of Ubuntu. Crossover is a commercial product which you purchase from the Codeweavers web site and also proprietary. I doubt very much if it was ever available thought the Ubuntu Software Centre. Perhaps you are confused over Wine. which most certainly is in the Software Centre.

When I have a beta product that works better than the RTM I get a little worried, surely the nvidia drivers for my nearly 18month old card aren't that 'new' that I need to worry about getting them to work in Ubuntu or do I? I know that they work perfectly well in 11.04 and 11.10 as well as 12.04 beta 2 but they sure as hell didn't work quite nearly as well in the fresh install of 12.04

As far as the Crossover application is concerned I may have installed it from the Software center when it was downloaded but I was sure I had done so from within the last couple of weeks.

> **grahammechanical said:**
> The Linux developers are always playing catch-up with the hardware with little if any support from the hardware makers. A lot of Windows users stick with Windows because they know of nothing else and are not given a choice. 

Again, this is an 18 month old card, it's not like I was trying to get a GTX680 installed and working and expecting the whole bells and whistles to be working straight away.


> **grahammechanical said:**
> Ask for help by all means but remember when you express an opinion, you invite me to express my opinion. And my opinions will always disagree with your opinions. Be sure of that.

Maybe and maybe not, just because I come from a Windows background doesn't automatically mean that our opinions will differ but if you are basing all of your disagreement on my Windows background then you're part of the problem with adoption of Linux by Windows Users because of your elitism attitude.

Now as far as my issues are concerned I am now running a stable 11.10 installation with my Nvidia drivers working, still not finding Crossover in the Software Center but I haven't spent too much time looking at the moment due to family commitments (my 5yo son will only take so much of me doing apt-get updates\upgrades from a terminal session).

---

### Post by kc1di on 2012-04-28
> **SimonDavies said:**
> 
Now as far as my issues are concerned I am now running a stable 11.10 installation with my Nvidia drivers working, still not finding Crossover in the Software Center but I haven't spent too much time looking at the moment due to family commitments (my 5yo son will only take so much of me doing apt-get updates\upgrades from a terminal session).


Crossover Linux if that's what your talking about is a piece of software that must be paid for and you can find it here:
[http://www.codeweavers.com/]("http://www.codeweavers.com/")

But it is an implementation  of Wine which is open source and free it's in software center.  
you may have to do the work of getting you windows software to work through it though - Here is there webpage you may want to look it over before deciding. 

[http://www.winehq.org/]("http://www.winehq.org/")

---

### Post by mebunto on 2012-04-29
> **SimonDavies said:**
> I am now running a stable 11.10 installation

Perhaps others may miss your post, but I didn't.  Well done, the cheers are ringing out in Harrow!

I've found Precise to be less than Precise ... I'm trying a last resort which is to get the latest stable kernel (3.3.3-030303) and it seems to be stable so far (as I'm writing this post).  3.2.0-24 is the kernel that I had before.

5-year olds do have a habit of not understanding the importance of kernel upgrades over Ben Ten .... but in time they will.

Just a footnote.  I managed to upgrade the kernel to 3.3.3-030303-generic from a terminal and all the instability disappeared. The machine hasn't crashed in 24 hours now. I also note an xorg update this morning. So it may be worth your while to go to a terminal when you boot ctrl-alt-f1 and update the kernel using dpkg.

---

