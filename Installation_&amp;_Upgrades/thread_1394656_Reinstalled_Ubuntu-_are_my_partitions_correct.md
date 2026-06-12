---
title: "Reinstalled Ubuntu- are my partitions correct?"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by jimmyUT on 2010-01-30
So I ended up having to reinstall Ubuntu on my thinkpad with Dual boot XP

Here is what I have for partitions

100 G HDD
---52 G IBM Preload ( XP)
---5.2  Service 001 (Lenovo Rescue & Recovery)
---6 G Extended (contains logical partitions) shows unrecognized file system
     ----6.0 G Swap Space
---37 G file System (ubuntu)

You should be allowed 4 partitions on a HDD, so why did it do the 6.0 Extended and then make the swap a logical partition?

Should it be this way or can I delete the swap and make the extended the swap?
Karmic seems to be running slower than it was beefore since I reinstalled and I was thinking this might be why.

Any info would be greatly appreciated.

Thanks!!!!

---

### Post by phillw on 2010-01-30
> **jimmyUT said:**
> So I ended up having to reinstall Ubuntu on my thinkpad with Dual boot XP

Here is what I have for partitions

100 G HDD
---52 G IBM Preload ( XP)
---5.2  Service 001 (Lenovo Rescue & Recovery)
---6 G Extended (contains logical partitions)
     ----6.0 G Swap Space
---37 G file System (ubuntu)

You should be allowed 4 partitions on a HDD, so why did it do the 6.0 Extended and then make the swap a logical partition?

Should it be this way or can I delete the swap and make the extended the swap?
Karmic seems to be running slower than it was beefore since I reinstalled and I was thinking this might be why.

Any info would be greatly appreciated.

Thanks!!!!


Hi, when you have dual boot system, Ubuntu seems to always pop swap onto an extended partion. this is handy if you ever need an new partion, like /home  which is advised once you have gotten used to Ubuntu.

/swap ... As to why you have 6GB allocated to it ??? The general 'rule of thumb' is 1GB or what ever your RAM is, which ever is greater.

Maybe time to consider hiving off your /home area into the extended partition.

If you think your computer is running slow, then you need to check if swap is actually being used ..

a quick ```
swapon -s
``` will tell you that.

Regards,

Phill.

---

### Post by jimmyUT on 2010-01-30
I have 3GB Ram, so should swap be 3 then?  If so how do I change that?

I used terminal to run 

swapon -s and this is what popped up:

jim@T60:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    5855652    0    -1

I am still a beginner with Ubuntu, so sorry for all the questions

---

### Post by NightwishFan on 2010-01-30
Do not worry about the SWAP. Unless you are pressed for space, you can have as much as you want. Besides, it can be a hassle to resize it with an installed system. I normally use 2*RAM unless I have A LOT of ram.

---

### Post by phillw on 2010-01-30
> **jimmyUT said:**
> I have 3GB Ram, so should swap be 3 then?  If so how do I change that?

I used terminal to run 

swapon -s and this is what popped up:

jim@T60:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda5                               partition    5855652    0    -1

I am still a beginner with Ubuntu, so sorry for all the questions

as previously said, if you have 3GB RAM, then 6GB of swap will not hurt.

With 3GB of RAM your swap area will be sat there doing nothing for 99% of the time. (If you open a picture file in GIMP that is 1GB in size, then it will get used).

When you say 'slow' in what way slow ?  Browsing, document processing / opening pictures / playing music .... etc...

Regards,

Phill.

---

### Post by jimmyUT on 2010-01-30
I guess "slower than before reinstall" would be more accurate.  Before I reinstalled, I would click on a program to open and it seemed instant, now maybe a 2 second delay or so.  It seemed faster than Window XP before, now xp seems  faster than ubuntu with everything except boot up process.  Ubuntu is like 20 seconds ad xp is closer to 45

Web Browsing is way faster on Ubuntu which I also can't figure out why ??

I pay for a 8mps Up 2 mps down connection.  If I use firefox on XP and go to speakeasy I consistently get numbers close to that, but when I am using firefox on Karmic, I get 16-20 M up and 4 M down  ... can anyone explain that one???

---

