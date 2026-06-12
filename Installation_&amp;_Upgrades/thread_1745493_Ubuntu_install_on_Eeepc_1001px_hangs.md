---
title: "Ubuntu install on Eeepc 1001px hangs"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by mistamidget on 2011-05-01
FAYI,
I had 10.10 running with no problems on my Eeepc so decided to download and upgrade to 11.04 this weekend.
First, when suggested by the system, I opted for a distribution upgrade which went ok until reboot where it hangs loading the desktop. Need to hold the power button to reboot. same everytime.
So though I would do a full install.
Initially, and twice, after typing my wi-fi key the install switches to a shell and scrolls huge amounts of stuff at full speed. I cant stop it using ^s so rebooted and tried again. same.
Next I connected it to the router using an ethernet cable and got to the "Preparing to install Ubuntu" screen where it just sits and never advances. System still running at least.
Switching to a shell, top says the only thing using the CPU is top and Xorg, and an ifconfig says 
there is nothing happening on the network.
Tried this twice but exactly the same.
Does anyone have a clue as to what would be a good way to proceed from here, otherwise I will tell my wife I need a brand new netbook :-D
Cheers,

---

### Post by Dutch70 on 2011-05-01
That depends. If you're wife let's you...I mean gets you another one, what do you want for that one? :) ...j/k

I'm not sure but it may just be that the servers are overloaded. 

Did you check the md5sum of the downloaded .iso?
As well as checking the live cd/usb for defects?

Also select "Try Ubuntu" before you install it to make sure 11.04 will run without any problems on your hardware. 
Natty will be buggy for a couple months.

---

### Post by mistamidget on 2011-05-01
> **Dutch70 said:**
> That depends. If you're wife let's you...I mean gets you another one, what do you want for that one? :) ...j/k

I'm not sure but it may just be that the servers are overloaded. 

Did you check the md5sum of the downloaded .iso?
As well as checking the live cd/usb for defects?

Also select "Try Ubuntu" before you install it to make sure 11.04 will run without any problems on your hardware. 
Natty will be buggy for a couple months.

Would like to try a HP or Lenovo netbook but probably should persevere at least 1 day ;-)
Just did a cd check and got no problems and am now doing a memtest which will take some time on 2gb. I have already done this a few times but wont hurt to do it again.
Are the servers involved at the early stage of the install, I rebooted last time after only 15mins. I'll try again after the memtest and let it hang for at least an hour or so.
I'll keep you posted, Cheers,

---

### Post by mistamidget on 2011-05-01
Update!
Ok so the memory test is fine and so did the "try live" option.
It loaded and seemed ok but did the same shell with debugging lines scrolling at the speed of light thing again when enabling wi-fi.
So rebooted by forced reset and disable the wireless in the bios though if 11.04 doesn't work with wireless that's a show stopper.
Restarted in live mode again and selected the install option.
It's now at the Preparing to install Ubuntu screen and just sitting there again. So I'll give it an hour to respond then put 10.10 back and wait for 11.05.

---

### Post by mistamidget on 2011-05-01
So, had to force a reboot again so I'm re-installing 10.10 now.

If it works my wife wins and no new netbook,
otherwise, I'm in luck, so which will it be the HP or Lenovo ??

uh,oh as I'm typing I just got straight past the "Preparing to install Ubuntu" screen to the Allocating drive spacescreen so it looks like 11.04 is a no go on Eee Pc's but 10.10 is still seamless.
Guess Aptitude is going to be busy soon.

---

### Post by mistamidget on 2011-05-01
Me again from Firefox in my 10.10 re-install.
Went beautifully sad to say so as I'm not interested in NOT using Ubuntu looks like we Asus 1001px users should wait for the 11.04 SP1 and stay on 10.10.
Cheers,

---

### Post by Otustelija on 2011-05-04
Just tried Natty on my 1001PX and hangs with a backtrace, where Lucid and Maverick both worked fine. Did you report bugs already or should I?

---

### Post by mistamidget on 2011-05-05
Hi, Just trying Kubuntu 11.04 now to see how that goes I'll report on my progress here before bug reporting. Cheers,

---

### Post by Dutch70 on 2011-05-05
Well, you've been busy. 

There is no SP1, or 11.05, things get fixed in Linux either by the user or filing bug reports. 
If you want a good stable system that will be around longer than 11.04, stick with 10.04.2 LTS.

The next version of Ubuntu will be 11.10 in October & it will be buggy for a little while after it's release date also.

---

### Post by mistamidget on 2011-05-06
> **Dutch70 said:**
> Well, you've been busy. 

There is no SP1, or 11.05, things get fixed in Linux either by the user or filing bug reports. 
If you want a good stable system that will be around longer than 11.04, stick with 10.04.2 LTS.

The next version of Ubuntu will be 11.10 in October & it will be buggy for a little while after it's release date also.

Yes,  I understand. Kubuntu fails in exactly the same place so tried an install with the "connect to the 
Internet" un-ticked in case that was the problem but still hangs with the wheel spinning. The system is still running as I can shut it down but cant progress to the partition window. So, I'm going to get a HP, I suspect my wife will only not talk to me for a week or so (refer first post)
I'm posting from 10.10 so it can stay until 11.10 then :-)

---

### Post by martin.bartlett on 2011-05-09
Exact same problems here updating from 10.10 to 11.04...

BUT, on the boot menu, if you see an item named something like "Previous Linux Version", click on it and choose the first one. THEN you'll get in alright.

It means there is a nasty kernel or driver problem in the default kernel provided for 11.04 - unfortunately actually getting any more detail than that is pretty hard due to the nasty way it gets reported - nothing gets written to files, it all gets thrown up on the screen.

---

### Post by martin.bartlett on 2011-05-10
I have logged a bug (which has now been confirmed): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780030](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780030)

---

### Post by fezon000 on 2011-09-05
I have exactly the same bug on my Eeepc 1001px when I tried to install Ubuntu 11.04 or latest (for this moment) Mint distribution.

So thanks for information about proper work of Ubuntu 10.10.

---

