---
title: "How fast does Ubuntu 6.10 Install"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by j.miller565 on 2006-12-16
How fast does Ubuntu 6.10 Install? just want to know

---

### Post by moffa on 2006-12-16
Took me about 15 minutes.

AMD 3700+
1 GB RAM
WD 250 GB SATA w/ 16 mb cache (i think)

---

### Post by Herman on 2006-12-16
On a modest computer like the one in my avatar, 400 mhz CPU, 128 mB ram, 30.0 GB hard disk, it used to take around an hour and a half.

I have another slightly newer test computer now, 
Acer Computer model: Acerpower SC  BIOS V4.0
Processor: Intel(R) Celeron(TM) CPU 1300MHz
Memory:   SDRAM 223396 kB = 224MB + 32768 kB share memory
                Buffers 19904 kB
             Cached  104120 kB        level 1 cache 32 kB,  level2 cache 256 kB
                 swap           0 kB
Hard Disk: 80026 MB       (80.0 GB)

In this one an Xubuntu 6.10 'Alternate' install took 27 minutes.

An Ubuntu Edgy Eft 'Alternate' CD install took 41 minutes

An Ubuntu Dapper DRAKE 'Christian Edition' 'Desktop' CD install took so long to open the first Window for Step 1 that I cancelled it after an hour.
This would be most likely due to lack of RAM.

Ubuntu Dapper DRAKE 'Christian Edition' 'Desktop' CD install , when the swap area is already made by a GParted LiveCD, took only 40 minutes.

I think it is interesting how having the swap area pre-made helps the 'Desktop' CD so much.

I expect in my other computers, around 3.0Gz CPU and 512 mB Ram, it would likely take around 25 or 30 mins for an install. Maybe I should try that and time it, just for interest's sake.

---

### Post by j.miller565 on 2006-12-16
did it ever seem like it froze it installed?

well I have a AMD Sempron 2800+ with 512MB of RAM plus 80 GB Hard drive.

---

### Post by Herman on 2006-12-16
Well the 'Installing the base system' bar takes a while. 
The 'Select and install Software' bar also takes the longest, if I remember correctly, and seems to pause at about 6% for a time.
Those two progress bars take up over half the time of the whole rest of the installation.

Why do you ask?

If you are experiencing a problem and your install is taking a long time it might be best to just wait, I have read reports here in Ubuntu Forums where the install has seemed as though it was frozen for quite while and then continued to finish a perfect install. I don't know why.

On the other hand if it has been sitting there for more than a couple of hours and you didn't do an md5sum on the downloaded .iso or 'check the CD for defects', then it might be time to start getting suspicious. Aborting the installation has never hurt any of my machines and I've done it lots of times.

---

### Post by j.miller565 on 2006-12-16
Because my looks like it has frozen and I have checked the disk and it says it's fine. I've been asking if I just need to wait and nobody has told me until now. Thanx a lot Herman and moffa

---

### Post by ciscosurfer on 2006-12-16
> **j.miller565 said:**
> Because my looks like it has frozen and I have checked the disk and it says it's fine. I've been asking if I just need to wait and nobody has told me until now. Thanx a lot Herman and moffaI have seen many people, including myself, say that this is an issue.  Don't know if it's a bug with the installer...

My best advice (sorry if it's already been mentioned) is to reboot and try the install again.  The first time my Edgy install hung like that, I had to go through the process 3 times before it would take.  On subsequent installs, it breezed right through.  Go figure. ;)

---

### Post by K.Mandla on 2006-12-16
> **j.miller565 said:**
> How fast does Ubuntu 6.10 Install? just want to know
Depends on the speed of the machine. My 2.26Ghz P4 takes about 20 minutes for a server, but my 300Mhz P2 took about two hours for a server. Full Ubuntu/Kubuntu installs will take longer; Xubuntu will add a little time too. :mrgreen:

---

### Post by j.miller565 on 2006-12-16
I have tried it for more than 10 times now and the best it has ever done is 1 quarter. Should I try the alternate CD or Dapper Drake (6.06.1)? Which do you reccomend to use?

---

### Post by Herman on 2006-12-16
I don't know if it matters which other one you try, they should all work. I'm typing to your from an Acer Aspire 3003WLMi notebook with AMD Sempron 3000+ and 512 MB RAM, and I have Breezy, Dapper and Edgy in it so far. 
I did quite a few test installs in it too. I have never had any problems.

I'm fairly sure my sister in law's Acer has the 2800+ AMD Sempron with 512 MB of RAMN and hers has Ubuntu in it too.

I think you have a good idea trying a different CD, any one should be better than the one you're using now. Good luck with the next one, I hope it works better. I'm sorry to read of anyone having problems like that, it must be terribly frustrating.

Maybe the 6.10 'Alternate' CD, but then I'm a little biased towards 'Alternate' CDs. 

Regards, Herman :D

---

### Post by j.miller565 on 2006-12-16
I was using Partition Magic 8. could I have screwed up there?

---

### Post by Herman on 2006-12-16
> I was using Partition Magic 8. could I have screwed up there? Well, it's against my personal beliefs to use Partition Magic, but I don't think it would be fair to blame Partition Magic is this instance without knowing lots more details about what is actually happening, or more accurately, what is not happening.

Can you say if it is freezing at the exact same place during your installs? And, if so , exactly what step does it freeze up at, of it is stalls during a progress bar, what % does it stop at? 
Does it say what it's trying to do when it stops? 'Configuring apt' or something like that?

Do you have a broadband internet connection, or dial-up? Is it plugged in while you are installing?

Have you tried the 'Alternate', or some other CD already?

Is there anything different or special about the computer?

Those are enough questions for now, sorry about asking so many, but it would be nice to be able to have a better guess at what the problem might be. You never know, it might be something simple that can easily be worked around.

Regards, Herman :D

---

### Post by Herman on 2006-12-16
Just for those who are interested in how long installations should normally take, as I said I might in an earlier post, I have timed three installations in my best computer. 

It's an Acer Aspire T310, 3.0 Ghz Pentium4 CPU, 512 MB RAM, ATI Radeon Graphics card, 80.0 GB IDE master hard drive, 30.0 GB IDE slave hard drive.

Xubuntu 6.10 'Alternate CD' installed in 18 mins 20 seconds, from the time of selecting 'install' to being logged into the running desktop.

Ubuntu 6.10 'Alternate CD' installed in 28 mins 33 seconds, from the time of selecting 'install' to being logged into the running desktop.

Ubuntu Dapper Drake 'Christian Edition' 'Desktop' CD install 16 minutes, 44seconds, from the time of clicking the 'install' icon on the desktop, to the time the system is fully booted and logged into. 
The 'Desktop' CD takes a while to get started, I didn't include that in the recorded time, so the 'Desktop' install has an unfair advantage in that it can take a lot of settings from the already set up live operating system. I don't know if it does or not.
I think the 'Desktop' CD install would still be the fastest though, even if I did include the time to boot the LiveCD in the installation time.

---

### Post by derjames on 2006-12-16
Ubuntu 6.10 'edgy' on VMware server took 15 min 45 seconds from starting the Virtual Machine to being logged into the desktop in a Core 2 duo T5600 laptop, 1GB RAM and Intel graphics adapter...

---

### Post by j.miller565 on 2006-12-17
Can you say if it is freezing at the exact same place during your installs? And, if so , exactly what step does it freeze up at, of it is stalls during a progress bar, what % does it stop at? **Looks like it stops at about 15% - 20%**

Does it say what it's trying to do when it stops? 'Configuring apt' or something like that? **Doesn't say a thing**

Do you have a broadband internet connection, or dial-up? Is it plugged in while you are installing?**I have a braodband connection and it is always connected to my computer**

Have you tried the 'Alternate', or some other CD already?**Na I haven't yet**

Is there anything different or special about the computer?**I reckon that my computer is average. Nothing special to it what so ever. I put in a wireless network card in, another 256MB RAM (total = 512MB) and I put in an AGP card, a nVidia GeForce FX 5200**

---

### Post by j.miller565 on 2006-12-17
Oh yea, the CD drive stops flashing at 15% - 20% too. Plus I added  a DVD drive as well

---

### Post by az on 2006-12-17
> **j.miller565 said:**
> Because my looks like it has frozen and I have checked the disk and it says it's fine. I've been asking if I just need to wait and nobody has told me until now. Thanx a lot Herman and moffa

There are no long periods of inactivity during which there are no signs of life from your computer (disk light flashing, disk churning, cdrom seeking).  The progress bar is somewhat coarse and can remain stuck for a while, but not in the absense of the above signs.

---

### Post by j.miller565 on 2006-12-17
I waited 2 hours yesterday without any luck :( should I try Dapper Drake instead? BTW, this is my first time using any Linux OS.

---

### Post by az on 2006-12-17
> **j.miller565 said:**
>  should I try Dapper Drake instead?

Absolutely.

 > **j.miller565 said:**
> 
BTW, this is my first time using any Linux OS.

More of a reason to go with Dapper.

---

### Post by j.miller565 on 2006-12-17
I'm going to try Ubuntu 6.10 for the last time until I download Dapper. I'm going to let it install over night. Hopefully that may work otherwise I'm going to Dapper

---

### Post by j.miller565 on 2006-12-17
Didn't install. going to try Dapper today

---

### Post by j.miller565 on 2006-12-18
Hey guys the alternate CD worked and I´m now using Ubuntu 6.10 and I´m so happy that I have it. Thanks guys for the help

---

### Post by Herman on 2006-12-18
Hey great! :D
Congratulations! And happy Ubuntuing.
You have a lot of patience and persistence, you will eventually succeed in everything you set out to do.
Regards, Herman.

...and no, I didn't read that line out of a fortune cookie, I made it up myself! LOL   :D

---

