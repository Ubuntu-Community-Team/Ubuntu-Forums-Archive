---
title: "Too many people still have video driver issues, better drivers needed"
date: 2008-11-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-11-01
Just a look thru the forums and you know what I mean.
This is an issue that windows left behind a long time ago and a video driver is foundational for the entire ubuntu experience.

I dont know what the solution really is but it really should be better and easier to get drivers working. No one should have to read thru forum posts telling you what to try and type stuff into the terminal. 

No one in windows uses their vga driver, except when they dont have a proprietary driver working.
No one should ever get a black or white screen, or ever get 640 by 480 or worse. 
One time when trouble shooting, I had ended up with 400 by 300 something.

---

### Post by Naddiseo on 2008-11-01
I'd like to see the nouveau drivers get to a point where they're fast enough to compete with nv. I've been having problems with nv, vesa, and nvidia since intrepid alpha 6, the only driver that 'works' for me is nouveau. I expect that the nv/vesa issues are bios settings, though still shouldn't happen.

---

### Post by Eclipse. on 2008-11-01
This is **not **ubuntus fault.

Unless nvidia releases the source code for the drivers there is always going to be this problem.

Yes there is projects like nouveau but trying to reverse engineer these drivers isnt easy and will take a long time until be get a decent finished product.

---

### Post by Slug71 on 2008-11-01
I think we all need to start bugging nvidia and ATI for better or newer source codes to be released.

---

### Post by Naddiseo on 2008-11-01
> **Eclipse. said:**
> This is **not **ubuntus fault.

Unless nvidia releases the source code for the drivers there is always going to be this problem.

Yes there is projects like nouveau but trying to reverse engineer these drivers isnt easy and will take a long time until be get a decent finished product.

Yes, I know it's not ubuntu's fault, I didn't even mean to imply it was. But, ubuntu can still help out projects like nouveau - if they aren't already -  to bring down that "long time"

---

### Post by ronacc on 2008-11-01
I have been using nvidia cards and nvidia propriatary drivers since I started building my own boxes a long time ago . The only times I have had problems are 

1 briefly when a new series kernel appears that it takes nvidia a week or so to catch up to.

2 When the devs of some particular distro ( I am not singleing out Ubuntu here) do something that blocks the installation of the drivers .

---

### Post by plun on 2008-11-01
> **ronacc said:**
> 
2 When the devs of some particular distro ( I am not singleing out Ubuntu here) do something that blocks the installation of the drivers .

Well, I dont know what happened but it must be something wrong with Jockey.

Ubuntu Geek posted a long manual... 

**Common Problems and Solutions for Nvidia restricted drivers after Ubuntu 8.10 (Intrepid Ibex) Upgrade**

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

---

### Post by ronacc on 2008-11-01
must be something that happened late in RC or at release . I am using the jockey (dkms) method this time around since it has actualy been working for a change , and have been since the repos opened for intrepid , and just for reference I am amd64x2 and 7600gs . and all has been smooth for me except for that glitch with the old drivers not getting deleted from /var/lib/dkms , but that was fixed early on . What ever it is does not affect already installled modules , I am still 100% here .

---

### Post by emshains on 2008-11-01
Hell yeah, they should be giving their drivers to the public, right ?
We're not paying them for software, we are paying them for the hardware and we're also paying them so the hardware works. Although I have a comp with a 9600 radeon, it has "some" driver issues. It paradoxically can run counter-strike 1.6 with wine through openGL, but can't play native openGL games. But it can't play wow. 

But I tend to buy what works, mostly (if there is a choice) I buy what works best with linux, because if a manufacturer can't adopt to my needs, why should I pay for something it sells. Heck, why should we try to make it work, if we are paying for it ? 

Though, I have never got driver problems with nvidia, I use the drivers that I can get from their website, and I am happy with them.


And another thing. You may see a lot of driver-issue topics, but thats because people are posting to get things to work, right? But why should I post if everything is working ? So you can't say that too many people have problems with their dirvers, because you don't know how many people don't have any problems at all. Because ubuntu is now a pretty popular operating system, there are more and more people using it, without even knowing such website as ubuntuforums.org, just because ubuntu came preinstalled or was installed by some other guy that "knows computers", so you can't even calculate how many people are using it. Thus, you  can't say that there are TOO MANY problems, but you can say that there are problems. 

Its also pretty hard to make good drivers for linux, since there are so many posibilitys that one driver will/won't/fight with another driver, since one part of the hardware drivers are made open source, the other by the manufacturer, thats why my wi-fi sucks.

---

### Post by PendragonUK on 2008-11-01
I can't comment on the quality of the drivers cos my screen is black! Why of why have they removed the ability to correctly specify your monitor?!? I have the manual, I can type in the numbers... "No, we know better, ubuntu shall detect the correct settings for your monitor"... ********! There is no fall back positions, at no point dose it say "is this correct monitor?" and give you the option of say hell no that's not the correct monitor. Click on the "advanced" and fill your boots...


Sorry if this sounds like a rant, I have been at this for a couple of days now...

PS editing the xorg.conf dose not work anymore.

---

### Post by dagrump on 2008-11-01
Looks like the only people that are having issues are the ones with sli setups, load the nvidia drivers, & no X. I ran into this issue, & tried to work around it, got ticked & reinstalled 8.04.1. 
Basically it's a huge regression, no excuses accepted. You can't keep your base if you break things  ie see vista! 
I did a clean install on a single card machine & yeah the stupid pop up in the upper tray didn't fly, but system>admin>hardware drivers installed fine. My other box w/ a pair of 7600 gts in sli gives a black screen even after designating my primary video card in xorg.conf, wherein hardy works as expected.
Who's to blame nvidia, or ubuntu for changing the expected way X loaded? Looks like maybe someone should have thought about the facts that the drivers were written to interact one way, if you change things, they won't work as designed.
I see enough blame to spread around, now, that was & this is moving forward. 
The parties that borked sound, yeah pluseaudio,  I'm lookin at you, and those that decided to change xserve & such, well the blame rests firmly at their feet.
Oh yeah, it's kinda like the new look? It still looks like a 2nd grader designed it, & only had 1 crayon, a nasty old brown one. This is one Ugly old goat, I thought they wanted looks to rival a Mac, well that sure ain't something brown can do for you. 
As you all can see, my frustration level is really getting up there. Make things work w/o major regressions, & no more ugly brown crud, is that too much to ask?

---

### Post by plun on 2008-11-01
Well, we cannot blame anyone just doing things better.

There must be better tests for changes in basic functions.

- PulseAudio, a call for testing and then just a mess with bug reports.  "psyke83" tried with his thread.

- Graphic drivers, the same, there must be a test program with sequenses how to test and how it should work.

Developers cannot hide themselves inside mailingists, IRC and bug reports....  maybe we are cannibals but there must be test programs !!! IMHO....

---

### Post by cariboo on 2008-11-01
I found a lot of people were to impatient to wait for the driver installation to finish, or the drivers didn't download because the servers were to busy. My suggestion would be to have the progress bar indicate what it is doing, instead of just saying installing for what seems like a long time, then all of a sudden jumping to 60%.

I personally had a hard time downloading the drivers as the Canadian server was so busy. I eventually had to change to the main server to download the driver and dependencies. It took about half an hour before I had working drivers, this was a clean install using the alternate install cd.

Jim

---

### Post by ronacc on 2008-11-01
one of the problems with open source community efforts is that everyone looks after their own project ( or segment of same) and may not worry so much if they break someone else's and there is no "top level" authority with the power to say fix it or else in the sense that gates had or jobs has , so much of opensource is unpaid volunteer work.

---

### Post by jerrylamos on 2008-11-01
If ubuntu 8.04 runs fine, and the only thing changed was to go to 8.10 then it is ubuntu 8.10's fault. 

In my case compiz 1:0.7.8-0ubuntu4 locks up my thinkpad tight.  Since 8.04 works, then it is indeed ubuntu's fault.  That's what changed.

The "official fix" compiz 1:0.7.8-0ubuntu4.1 merely blacklists many intel graphics so compiz isn't run.  

The "correct fix" should be for ubuntu to use the 8.04 level of compiz on hardware it knows 8.10 compiz will freeze up.

My personal opinion it would be pretty arrogant for compiz to expect many different drivers to have to be changed just for compiz.  Compiz should pay for the drivers to be changed to accomodate compiz.

Jerry

---

### Post by plun on 2008-11-01
> **ronacc said:**
> one of the problems with open source community efforts is that everyone looks after their own project ( or segment of same) and may not worry so much if they break someone else's and there is no "top level" authority with the power to say fix it or else in the sense that gates had or jobs has , so much of opensource is unpaid volunteer work.

Well.. it must be possibe to organiae things despite of that.

"Sitting in the ****" or make something possible. 

Ubuntu users can write thousends of Brainstorm ideas and nothing happens...  just words and discussions.

Debian is even better to discuss, discuss and discuss...never ending...:)

---

### Post by bamboo.7 on 2008-11-01
> **dagrump said:**
> Looks like the only people that are having issues are the ones with sli setups, load the nvidia drivers, & no X. I ran into this issue, & tried to work around it, got ticked & reinstalled 8.04.1. 
Basically it's a huge regression, no excuses accepted. You can't keep your base if you break things  ie see vista! 
I did a clean install on a single card machine & yeah the stupid pop up in the upper tray didn't fly, but system>admin>hardware drivers installed fine. My other box w/ a pair of 7600 gts in sli gives a black screen even after designating my primary video card in xorg.conf, wherein hardy works as expected.
Who's to blame nvidia, or ubuntu for changing the expected way X loaded? Looks like maybe someone should have thought about the facts that the drivers were written to interact one way, if you change things, they won't work as designed.
I see enough blame to spread around, now, that was & this is moving forward. 
The parties that borked sound, yeah pluseaudio,  I'm lookin at you, and those that decided to change xserve & such, well the blame rests firmly at their feet.
Oh yeah, it's kinda like the new look? It still looks like a 2nd grader designed it, & only had 1 crayon, a nasty old brown one. This is one Ugly old goat, I thought they wanted looks to rival a Mac, well that sure ain't something brown can do for you. 
As you all can see, my frustration level is really getting up there. Make things work w/o major regressions, & no more ugly brown crud, is that too much to ask?

This is simply not true i do not have a sli setup up I have a quad core cpu so the sse issue does not apply to me and i have a nvidia geforce 7350 le supported by the proprietary drivers (Has worked since 7.10 (so this is a problem with ubuntu most likely))on a fresh install yet when i enable nvidia-glx-177 and reboot it sends me to low res mode. even though once im logged on it assures me that its activated and there is new drivers in use. And i am not the only one. There are many gfx card issues with the 8.10 release for many reasons some xorgs fault some ubuntu and i think very few are nvidias fault.:( bad choice ubuntu to include the new xorg with out you broke a lot of peoples setups well back to f*ckin 8.04 until you can  get this mess straightened out. Seems to be a lack of quality control here lately things are supposed to get better with each release not worse. Ubuntus bug #1 will not get fixed as long as this kind of bush league development continues. People should have to spend 3 days trying to get their computer to work! ubuntu i love you but and very disappointed in you.

---

### Post by dagrump on 2008-11-01
I'm sorry, didn't realize non SLI setups were breaking, I have ran 8.10 since pre alpha 1, started in virtualbox & went to metal at alpha 2. This machine had a few minor quirks, but nothing major.
Did a clean install today, installed nvidia 177.8 drivers, no issues. Therefore I assumed single cards were fine. I have 3 desktops, 2 have SLI setups & I tried to get II running on 1 of them, starting @ alpha 6, then beta,& RC still no luck. 
I ain't the sharpest knife in the drawer, but I can read the writing on the wall, it was broken. I didn't waste anymore of my time fighting it.

---

### Post by bamboo.7 on 2008-11-01
> **dagrump said:**
> I'm sorry, didn't realize non SLI setups were breaking, I have ran 8.10 since pre alpha 1, started in virtualbox & went to metal at alpha 2. This machine had a few minor quirks, but nothing major.
Did a clean install today, installed nvidia 177.8 drivers, no issues. Therefore I assumed single cards were fine. I have 3 desktops, 2 have SLI setups & I tried to get II running on 1 of them, starting @ alpha 6, then beta,& RC still no luck. 
I ain't the sharpest knife in the drawer, but I can read the writing on the wall, it was broken. I didn't waste anymore of my time fighting it.

Sorry not trying to go off on  you this is just brining this to everyones attention!

---

### Post by ronacc on 2008-11-01
a couple of thoughts , didn't ATI opensource their driver ? I don't have any ATI stuff ao I don't follow it. From the posts in the intrepid forum they seem to have just as much trouble as those of us with nvidia GPU's .
Also does anyone know if alberto has an SLI setup to test with ? He seems to be carrying alot of the load with the Nvidia drivers .

---

### Post by autocrosser on 2008-11-01
Well. I have a working nVidia SLI set-up...if anyone wants to know how to do it--just ask (PM me). 

PendragonUK--most of the problem is with the new way that Xorg has decided to go...you can look thru the closed Intrepid forum & most likely find the answer....

As far as SLI--I E'd Alberto when I needed to setup SLI--he came back with a one line answer that took care of the issue....

This Xorg update has been hard on everyone--in time the problems will be smoothed out--but in the period between then & now--hang in there--I'll answer anything I can & don't be afraid to post to the Xorg.requests list:  
[EMAIL="xorg-request@lists.freedesktop.org"]xorg-request@lists.freedesktop.org[/EMAIL]

---

### Post by smartboyathome on 2008-11-01
> **ronacc said:**
> a couple of thoughts , didn't ATI opensource their driver ? I don't have any ATI stuff ao I don't follow it.

They did release the _specifications_ so an open source driver could be created, but right now the driver is still incomplete and many people still use fglrx (the proprietary driver).

---

### Post by dagrump on 2008-11-02
Well with a fresh start & digging thru the bone pile that is the intrepid archives, I have a working X.
Fresh install, let it snag the updates, then used synaptic to grab the 177 drivers. After the installed reboot & end up @ tty1, logged in, then "sudo nvidia-xconfig, gave my password, it wrote a new xorg.conf file. then "sudo nano /etc/X11/xorg.conf" & added BusID  "01:00:0" to the device section. control o, to save, control x to quit. Then sudo shutdown -r now, rebooted the beast & X is back. I used lspci to get the busID before I installed the drivers, but you can run it from tty1. 
I used to info from one of autocrosser's posts, but this time I got it right.

---

### Post by autocrosser on 2008-11-02
Glad it helped--The BusId answer was Alberto's, I just posted it. I have a minimal xorg.conf that will do what the new xorg wants--you also need to take a look at this thread: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

There are a couple of performance adjustments that make things much better in most cases...

I can post my xorg.conf & how I added things to my Gnome session if anyone wants--or you can find all the info in the closed Intrepid forum...

---

### Post by gnomeuser on 2008-11-02
> **smartboyathome said:**
> They did release the _specifications_ so an open source driver could be created, but right now the driver is still incomplete and many people still use fglrx (the proprietary driver).

They also Hired Alex Deucer to do nothing but work on this, as well as Red Hat' Dave Airlie working on ATI and Luc Verhaugen over at Novell also working on ATI card support (though he works on RadeonHD not the standard Radeon driver). ATI are being responsive to the community both in providing work and helping us get specifications, not just for the latest models but for older cards as well so everyone should get equal support.

The ATI cards are probably the best supported today by free software drivers, mostly since Intels drivers are tracking the very tip of X development so the current state is a bit in flux due to a rewrite. Aside that, Intel are very very good as well and always sure to be working well.

Basically you should have 3D support and kernel modesetting on radeon cards from r100 till r600 models (so not the very latest models) with very few issues. If problems are discovered they generally tend to get resolved quickly.

---

### Post by jerrylamos on 2008-11-04
It's not "people" having video driver issues, it's "Ubuntu" having issues using video drivers.

Where to find Ubuntu "drivers, X, and compiz" that work?  My case in point IBM Thinkpad:

8.04 X, compiz, drivers work fine.  Big point, they don't hang up the system.  CD Live works, upgrades work.

8.10 X, compiz, drivers hang up the system even on upgrades.  "Official 8.10 fix", disable compiz ! for many Intel graphics chips.  Clue - there are LOTS of Intel graphics chips out there on lots of pc's. 

Jaunty is to get the "Official disable compiz fix" too.  So maybe it will boot with compiz disabled.

Launchpad Bug reported:  August 19, #259385.  As of Intrepid release two+ months later, not fixed.

Lots and lots of posts of people trying official released 8.10 Ubuntu and not booting because of this.  CD Live is one matter, Upgrade users are "up the creek without a paddle".  Yes, I have a workaround in the bug report, for as many users trying out 8.10 that can still get to the internet somewhere and know where to look.  Sure helps to know the command line.

Better fix: have compiz OFF by default!  Perhaps a boot option at least.  Compiz with its "eye candy" and "animations" may well break X, drivers, and graphics hardware when other code like Internet, Office, digital photos, local lan still work fine.

So I'll try Jaunty shortly - wonder if it will even boot?  O.K., I'm a glutton for punishment, and have backups.  Some times that doesn't even work when early Hardy Alpha install formatted all quad boot partitions on both hard drives.

Jerry

---

### Post by klange on 2008-11-04
The reason for the horrible Intel performance in Intrepid over Hardy was the work that went into - and was then ripped out of - the X server for that release. Luckily, the new stuff is already in place and should be working for the next release of the X server...

---

### Post by Changturkey on 2008-11-04
So the X4500 has terrible performance?

---

### Post by ShirishAg75 on 2008-11-04
I haven't had good experience with the Intel 845 chipset graphics ever. Every once in a while, when I reboot the system, at the login the screen goes black. Also rebooting and trying the kernel doesn't work. What works is going to recovery, maybe trying to fix the x server, going to the the root, spending sometime there, and after sometime trying to do an startx, then working on the same for sometime. Then exiting X, shutting down the system from login and then starting afresh. This time most probably will get the login screen. Once the login screen I get then no issues (usually) .

---

### Post by robert114 on 2008-11-05
gnomeuser, would you recommend a r600 model card?
I'm having a lot of trouble with Nvidia. And to be honest, i'm getting sick of it! (grey titlebar corruption, purple title bar corruption and other regression troubles) My laptop (Intel) hasn't had any troubles at all in the past two years can't say that with my Nvidia based desktop. So i'm considering changing to ATI I like the fact they support the opensource projects and recently showed more commidment to Linux.

BTW I ment in combination with the opensource driver having 3D support and Compiz

Thanx Robert

---

### Post by krazyd on 2008-11-05
> **robert114 said:**
> gnomeuser, would you recommend a r600 model card?
I'm having a lot of trouble with Nvidia. And to be honest, i'm getting sick of it! (grey titlebar corruption, purple title bar corruption and other regression troubles) My laptop (Intel) hasn't had any troubles at all in the past two years can't say that with my Nvidia based desktop. So i'm considering changing to ATI I like the fact they support the opensource projects and recently showed more commidment to Linux.

BTW I ment in combination with the opensource driver having 3D support and Compiz

Thanx Robert
The r600 series cards **aren't** properly supported (accelerated video / 3d) by the open source drivers - only up r500 I'm afraid. Due to deficiencies in the current X-server, which are currently being worked on, the open source drivers can't redirect opengl applications through a compositing window manager either - it is drawn directly to the screen and has horrible performance. full-screen 3d works well though.

more info: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

---

### Post by bamboo.7 on 2008-11-05
Seems my problem was with my tvtuner card (hvr 1600) was not letting my nvidia card get recognized. removed card all is fine. so anyone with a m8120n hp or just the hvr 1600 might be having this issue!

---

