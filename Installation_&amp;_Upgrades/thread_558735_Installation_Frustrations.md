---
title: "Installation Frustrations"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by MysticEdge on 2007-09-24
Hullo there,
How is everyone doing today? Prior to posting this thread I did my best to ask a few people and research on my own through previously posted threads because I hate reposters, but as I have found nothing on my particular predicament, posting a new thread seemed necessary.

Anyways, first things first, I was a windows user for the majority of my life, it was what I was first exposed to, however, after learning of Linux I have wanted to switch for several years now, just never had the chance. Well last week my laptop crashed, giving me the perfect opportunity to switch over to Linux. A savvy friend of mine recommended Ubuntu, so here I am. Now on to the issues.

First of all, the installation and the boot-up OS are both running EXTREMELY slow. For instance, after booting up the CD to install, and clicking on the "Install" Icon, it would take about 15 minutes to load up the first install window. And the seven steps it takes to configure the installer where it asks your location, name, partition information, and so on, took a combined total of two days to get through. Now that I finally got to the installation part, it get stuck at 15%. Now I researched on the forums to see what it might have been running so slowly, and I found that if you burn the boot disk at a high speed, it's difficult to read. I figured if I burned a new cd using my roommates laptop(the computer I am currently on) using a 1x burning format, that it would solve my problems. I did so, and to no avail, the sluggishness of the installation was still painful. However, I took another two days to try installing again.

So now I am looking at the installation progress bar that is once again stuck at 15% it's self proclaimed current task indicator stuck at: "Detecting File System".

The CD has also stopped reading, which concerns me. It's been stuck here for about 18 hours now, and since I've already tried rebooting and trying again, I thought I'd ask first.

I went on the Chatroom, but people were quite busy in there. The only kind of answer I got was to try the alternate CD. I was just wondering what you guys thought about this option? And if it would solve my issues. But I wanted to know a little more information as to WHY it would solve my problem, because I really don't know what my problem is at the moment.

Specs on the laptop are, Dell Inspiron 8600, 1.8 Ghz Intel Processor, 256 Mg of RAM, nVidia FX 5400 video card, 40gb Hard drive, 56x DVD player CDR/W Reader Writer. And I believe that's all the information about the lappy.

Sooo, what should I do?

Thanks for taking the time to read, I appreciate it.

---

### Post by Technophobia on 2007-09-24
Hi MysticEdge,

I have nearly the same laptop as you and ran into none of these problem. The only difference between our systems is the graphics card (i'm stuck with an ATI), amount of ram (I have 768mb), and hard drive capacity.


Few questions for you

1) What software did you use to burn the .iso image?

2) What .iso version did you download?

3) Can you invest in a CD-RW disk so you can save your self from bad burns?

4) Did you try the disc and ram tests when you first get to the Ubuntu disc boot screen?

---

### Post by djheadley on 2007-09-24
I would suggest more memory, at least 512 but 1g if you can..  I had trouble with my (older) laptop until I added more memory - it works pretty good for a 400mhz machine albeit slow.  The more memory you can put in a machine the better.

---

### Post by Rahmat on 2007-09-24
Let me ask

Is it still thesame laptop that crashed that you are trying to install Ubuntu on?

---

### Post by malfist on 2007-09-24
You know, you might want to follow the advice you got on the chatroom...those people usually know what they're talking about.

The liveCD will run extremely slow, once it is install it won't be so slow.

---

### Post by Syncstep on 2007-09-24
Mystic,

Ok... that now makes two of us.  I am trying to install 7.04 on my old Dell Latitude.  I wanted to salvage some life out of the Dell (it's a 600Mhz P3) and use it to run Slimserver software for my Squeezebox music streamer.  Being no stranger to Unix/Linux - I figure it will run smoother and faster than XP on this old hardware.

I downloaded the Ubuntu iso image to my other laptop (a Toshiba), checksummed the download (no issues), then burned the image to a disk using InfraRecorder (as recommended on the Ubuntu install page).  The Dell seemingly kept locking up after the main Ubuntu GNOME desktop loaded, or after the installer software got to the language selection option.  It was somewhat random... 

I got fed up and reburned it using the CD writer in the Dell just in case it was a compatibility issue.  And I also found out on one forum that my Dell has a compatibility issue with the touchpad and the powernow daemon (powernowd).  Find out if there are any particulars with your model of Inspiron - check it here: 

[https://wiki.ubuntu.com/LaptopTestingTeam/Dell](https://wiki.ubuntu.com/LaptopTestingTeam/Dell)

I made the fix and also turned off screensaver, and all powersave features for now.  That seems to have stopped the lockup but it is brutally slow.  I haven't yet gotten past the "english" selection (first option) in the install software... 

I'm keeping an eye on this thread... :-)

---

### Post by MysticEdge on 2007-09-24
First of all, thanks for the replies guys. It's been very helpful so far.

"Hi MysticEdge,

I have nearly the same laptop as you and ran into none of these problem. The only difference between our systems is the graphics card (i'm stuck with an ATI), amount of ram (I have 768mb), and hard drive capacity.


Few questions for you

1) What software did you use to burn the .iso image?

Active ISO Burner 1.1 as stated burned at 1x speed


2) What .iso version did you download?

Ubuntu Desktop 7.04

3) Can you invest in a CD-RW disk so you can save your self from bad burns?

Of course. Would that be better and easier to read that CD-R's?

4) Did you try the disc and ram tests when you first get to the Ubuntu disc boot screen?

No, but I am currently doing said test, and will notify you of the results.


And as far as the other reply, I don't think the memory would cause it to lock up like this, because the system requirements  for linux is 256. Although you are right, I need more, and have been wanting to get more, but funds are tight and such. But if necessary I could go out and buy some.

Again, thanks for the replies folks. I am so looking forward to being a linux user, it's been really rough having so much difficulty getting it onto my lappy. But you know what they say, something worth doing, is usually not easy, and something easy, is usually not worth doing.

Cheers

---

### Post by MysticEdge on 2007-09-24
> **Rahmat said:**
> Let me ask

Is it still thesame laptop that crashed that you are trying to install Ubuntu on?

Yes it is. I formatted the harddrive since then though.

---

### Post by MysticEdge on 2007-09-24
Another thing, I just checked to see if my particular laptop model had any issues, and I found none in Dapper, Edgy, or Feisty Herd 4.

As I am new to linux I don't know the difference between these versions and the Ubuntu 7.04 that I am trying to install. 
I'm sure it's on the forums somewhere, but I figured I'd mention it just to get a link for anyone else who reads this thread.

P.S. I tried to edit the previous reply, so I wouldn't have to reply three times in a row, but it wouldn't let me. Is that a moderator only option?

---

### Post by Technophobia on 2007-09-24
One problem I had about a year ago on another computer was that the CD drive was going bad. It would spin up and down and eventually give up. The way I solved this problem was by keeping the drive active on other things. I loaded up firefox on the live CD and just looked at random webpages for about 15 minutes and then the install finished. 

A reason for your inability to edit your post might have to do with the age of your account.

---

### Post by Loey on 2007-09-24
Hi Edge,

"May be" there are some issue in your hardware. Try this link it might help [www.howtoforge.com/perfect_setup_ubuntu_6.06](www.howtoforge.com/perfect_setup_ubuntu_6.06) make sure your online during installation. It takes some time... :popcorn:

LOEY

---

### Post by Syncstep on 2007-09-25
This is really really really annoying... it's so slow I can't always tell if it's locked up or still working away... 

... is there some sort of "fiddle prompt" I can launch so I know the computer is still going at it?  I've been assuming that it's working as long as it seems to be reading from the CD.  

I re-launched the installation yesterday after booting from CD in safe graphics mode, removing powernowd and disabling the screen saver.  That allowed me to get to step 2 (Where are you?) in the install fairly quickly but since then the gnome-power-manager icon has appeared on the desktop and I seem to have slowed to something slower than a crawl.  

If anyone has any experience with this slowness and has resolved it, I would love to hear from you.  I'm leery of trying something new if this horrible slowness is normal and I'd just end up throwing 24-hrs of installation time away.  

I'm having freakin' flashbacks of installing Novell Netware back in the 80's! 

Cheers,
S

---

### Post by MysticEdge on 2007-09-25
Hullo there folks.

First of all I would like to offer my deepest gratitude to everyone that offered tips and advice and responded to this ad.

Good News folks!!!

I am currently on the forums from my own laptop running Feisty Fawn 7.04 Linux. I am as happy as a kid on Christmas.

Now, for anyone else that is having similar difficulties that I have outlined in this post. Here is how I went about fixing things.

I downloaded the desktop addition of Edgy Linux, the 6.06 version of Ubuntu. And that ran and installed in about 15 minutes. After fiddling around in there for a few hours I then worked up the courage to try installing Feisty 7.04 on top of the working version I was running. And lo and behold it started up and ran just as it should with no half hour delays between set up options, and no freezing whatsoever.

By the way, I tried downloading the alternate and had many many problems with it as well. 

So here is a list of things I did to get Ubuntu Feisty installed on my laptop.

First of all, I made sure that I burned the boot disk with a valid ISO burner under the lower possible burn rate. Then when that was unbelievably slow, and froze during installation, so I downloaded and installed the earlier version of Ubuntu, Edgy. After installing that, I then installed version 7.04 on top of it and it ran perfectly...

I hope this helps anyone else who is having troubles. Thanks again guys.

Chalk one up for the windows to linux converts!

---

### Post by Technophobia on 2007-09-25
Glad to hear MysticEdge and I'm glad you didn't give up on Linux. I hope your findings help Syncstep.

---

### Post by Syncstep on 2007-09-26
It's ALIVE!!!

I would like to thank everyone for their contributions... you all finally tweaked my brain enough for me to decide to change to the *alternate *installation CD for 7.04.  

I downloaded the alternate image after dinner last night, ran the checksum, burned the image (on my Windows XP Toshiba laptop at 1x), and installed.  Ran like a dream in text mode - nice and fast.  Go figure: I've only ever installed Unix with text-mode install packages before - I should have thought of it earlier.  

Everything is running smoothly this morning.  I'm currently downloading updates/patches.  The only issue is that my Linksys wifi card isn't working - but I figured that it might not since it was no longer working properly in XP either.  I'm now connected via the RJ-45 instead and that's alright - and faster anyways.  

My only issue is that I can't seem to manually set the IP address for the Ethernet interface... it only wants to do DHCP?  I'll have to play with that after all the updates are done...

Dell Latitude C600
20 Gig harddrive
256Mb RAM

Runs like a dream so far...  :-) 

Cheers,
Stephane aka Syncstep

---

