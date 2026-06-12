---
title: "Impending Gutsy installs on 3 computers"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Jay Car on 2007-10-19
Hello,

I am preparing for the task next week of installing Ubuntu (Gutsy) on 3 computers for friends.  I do not have the computers yet, so I don't have the full specs, all I know about them is that two are MSI motherboards, AMD processors, via chipsets and both have 1Gig of RAM.  

These are brand new machines that have no system on them...as yet.  They are virgin machines (blush).  However, the CD that came with the motherboard has Windows-only drivers.  I've installed various versions of Linux on older machines, but have never had brand new, never-been-touched hardware to work with before.  I'm not sure whether to be happy, or worried.

The people these machines belong to live in a rural mountain area and do not have access to DSL or cable Internet service...which makes me nervous as I've never enjoyed installing modem drivers on Windows, the last time I even tried has been many years ago.  I've never had the opportunity to try it with Linux.  I have no clue about modems anymore.  

The third machine is an old Win98 HP that may or may not work, so that will be the last one I tackle. 

They will be bringing all three machines to me tomorrow.   

What I'm doing tonight is acquainting myself to the Ubuntu forums and reading through as many posts as I can to collect information.   

I'd also like to say hello to all.  I'm very appreciative of having such a nice resource available, it makes me feel better.  I have an idea I'll be needing it.  Maybe, by the time I am finished with these computers, my experiences will also be helpful to others.

Thanks for being here for all of us!
Jcar

---

### Post by Wiebelhaus on 2007-10-20
The MSI boards & Peripherals modems,NIC,Drives will be picked up by Ubuntu's excellent hardware detection , Use "Vesa" video drivers which is used by default anyway , you would need an ethernet connection to install the restricted GPU drivers , but Vesa works , no worries.


for the older machine you may wanna look into a ["Low Mem installation" ]("https://help.ubuntu.com/community/Installation/LowMemorySystems") you'll learn a hell of allot during that process!

Welcome , any issues you have you have the best community in the world willing and eager to help.

Good luck mate!

---

### Post by xcafeus on 2007-10-20
it should be ok as long as its not HP and it doesnt have raid0 :) :) ...

---

### Post by Chilongola on 2007-10-20
You should be good to go with default detection.

---

### Post by R.Bucky on 2007-10-20
Agreed with default detection. I bought a brand new eMachines T5230 and did not even give Vista a chance to load before wiping it clean. Started out with Ubuntu 7.04 and recently moved to Gutsy. No serious problems so far. Try the xubuntu for the uber-low memory machine at first. Make a selection of Live CD's or Mandriva 2008. I do not like KDE, but this new distro is killer.

---

### Post by Jay Car on 2007-10-20
Thanks for all the tips.  The computers should be here today so I'll know more about them and can post more specific details later.  I also have several versions of Ubuntu and Kubuntu, as well as the most recent Mandriva release ready to go for the two brand new machines (just in case).  

For that old HP I'll probably use Knoppix first to see if the machine even works at all.  If it does I had planned to try installing Damn Small Linux on that one.   

I've mostly muddled along on my own, learning how to install and use various Linux distros over the last couple of years.  It's been fun to do.  However, it's one thing to muck around with my own computers, it's a whole different responsibility to do it for other people.  I'm a little nervous, so I'm VERY glad you all are here to help.  (I'm a grandmother, by the way.  I hope that doesn't scare anyone :)

Thanks!
J

---

### Post by Chilongola on 2007-10-20
> **Jay Car said:**
> Thanks for all the tips.  The computers should be here today so I'll know more about them and can post more specific details later.  I also have several versions of Ubuntu and Kubuntu, as well as the most recent Mandriva release ready to go for the two brand new machines (just in case).  

For that old HP I'll probably use Knoppix first to see if the machine even works at all.  If it does I had planned to try installing Damn Small Linux on that one.   

I've mostly muddled along on my own, learning how to install and use various Linux distros over the last couple of years.  It's been fun to do.  However, it's one thing to muck around with my own computers, it's a whole different responsibility to do it for other people.  I'm a little nervous, so I'm VERY glad you all are here to help.  (I'm a grandmother, by the way.  I hope that doesn't scare anyone :)

Thanks!
J

Don't worry I am a grandfather turn SIXTY TODAY!!!!!!!

---

### Post by xcafeus on 2007-10-21
> **Jay Car said:**
> Thanks for all the tips.  The computers should be here today so I'll know more about them and can post more specific details later.  I also have several versions of Ubuntu and Kubuntu, as well as the most recent Mandriva release ready to go for the two brand new machines (just in case).  

For that old HP I'll probably use Knoppix first to see if the machine even works at all.  If it does I had planned to try installing Damn Small Linux on that one.   

I've mostly muddled along on my own, learning how to install and use various Linux distros over the last couple of years.  It's been fun to do.  However, it's one thing to muck around with my own computers, it's a whole different responsibility to do it for other people.  I'm a little nervous, so I'm VERY glad you all are here to help.  (I'm a grandmother, by the way.  I hope that doesn't scare anyone :)

Thanks!
J

> **Chilongola said:**
> Don't worry I am a grandfather turn SIXTY TODAY!!!!!!!


NO WAY!! You guys are COOL. :lolflag:

---

### Post by Jay Car on 2007-10-21
> **Chilongola said:**
> Don't worry I am a grandfather turn SIXTY TODAY!!!!!!!

Here's a Belated Happy Birthday To You! 

Funny thing is that my own birthday is only a little over a week away now (Oct 30), but I probably won't tell anyone exactly _which_ birthday it is.  :)

I've receieved the computers that I'll be working on over the next few weeks.  I haven't unpacked them yet, but I did open the box with the motherboard guides and Windows-only driver CDs.

One is a:
MSI K9K Neo V2/V3
NVIDI nForce 520/560 Chipset
Designed for Socket AM2 Athlon64X2 Processors

The other one is a:
MSI K9VGM-V
VIA K8M890 Chipset based
Designed for AMD Athlon 64/FX/X2 Processors

I've searched for these motherboards in several hardware compatibility (and incompatibility) lists, but so far have not found them.  I don't know if that's a good sign or not.  Maybe I just didn't look far enough, or missed seeing them in the many long lists.   

These machines will be the first installations I've ever done where there's been no other system software already installed. My inclination is to fire them up the first time using Knoppix, just to see if everything works.  But maybe I'll just dive right in using one of my Ubuntu Live CDs.  

Since Gutsy is still such a new release, would it be wiser to try an older version first?   (I'm not usually so indecisive, I'm just a little nervous about these machines because they aren't my own)

Anyway, when I get them set up and plugged in, I'll probably be back with more serious questions (I'll do my best not to be too annoying).  Thanks for being here as support.  

J

---

### Post by Chilongola on 2007-10-21
Great and thanks Jay!
Just assemble load the cd and watch everything fall into place.:guitar:

---

### Post by bliffle on 2007-10-21
You mentioned 'modem' and that raises a red flag because there is quite a bit of fiddling required to use dialup modems (especially so-called "winmodems" because some hardware is replaced by software to save a few pennies), and there also may be some problems with "WiFi" wireless 'modems'.

First sign of trouble report back here! Make a clear concise topic for each separate problem.

And check the MD5SUM on your 7.10 CD! It's not uncommon to get a bad burn. When/if the CD boots up use the Check CD feature first. Requires about 5 minutes and well worth it.

Pay attention to what your elders say! I'm just over 70 and have oodles of computer experience!

---

### Post by Jay Car on 2008-02-08
I know this thread is very old, and I am embarrassed that it has taken me so long to get this set of computer projects finished up, but life and work tend to interfere with our plans sometimes.  

However, I've done it now, and am so amazed at the results.  I am sure I'll run into things that I don't know how to do, but so far I've been able to figure most things out.  I've even TRIED to cause problems with two of these machines, like installing old hardware or plugging in scanners and printers, but so far they've handled everything I've thrown at them.  

So, if anyone hears or reads the old line about "Linux isn't ready for grandma" just send 'em to me, I'll give 'em an earfull!  One of the computers will be going to another grandmother, and she is quite pleased with what she saw when she visited this week.  I still need to teach her how to use it, which means I need to learn more too, but so far this little project has been a grand success and a fun learning experience.

Just wanted to tell someone.  I posted some of this already, somewhere on this forum last night, but can't find it now.  So, I thought I'd post here too.  

A big thank you to Ubuntu Forums and everyone that helps us newbies.  I may not have posted problems, but the forums provided a lot of information when I had questions or needed to learn something before I tried on my own. It's an incredibly valuable service and very appreciated. 

Jill Carpenter (alias: Jay Car)

---

