---
title: "Telling Ubuntu to use a FAT32 partition as Swap?"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2010-04-05
Is this possible?

I'm installing a new SSD this upcoming weekend.  My thought was to go easy on it so it lasts longer by putting my swap files on a mechanical drive instead of the SSD.   I don't - however - want to waste space for swap files.  It would be nice if I could use the same 6GB FAT32 partition for swap files for both Windows 7 and Ubuntu. 

Is this possible?

It might not even be necessary though, I haver enough RAM that I rarely use the swap file at all (I've even considered going without swap all together), so it probably won't pose a huge load to the drive.

Appreciate your input.

Thanks,
Matt

---

### Post by ubunterooster on 2010-04-05
SWAP is a different filesystem and won't work in another ;'(

EDIT: I have no swap as I've never seen it used

---

### Post by mattlach on 2010-04-05
> **ubunterooster said:**
> SWAP is a different filesystem and won't work in another ;'(

EDIT: I have no swap as I've never seen it used

Really?   You've never used a swap partition?

I've always created one ever since my first slackware linux install back in the 90s, then on Gentoo which I used for years and now on Ubuntu (cause I got tired of the constant required maintainence)

The rule of thumb is to always ahve at least the same amount of swap space as your RAM.  Is this no longer recommended?

---

### Post by Slim Odds on 2010-04-05
> **mattlach said:**
> ...
The rule of thumb is to always ahve at least the same amount of swap space as your RAM.  Is this no longer recommended?

Rules are made to be broken..... ;)

I don't want to make a long story out of this, but if you have 4GB or more on a desktop system, there is no practical reason to have swap (except for hibernation).

I know that some people will throw a hissy fit when I say that, but it's true.

swap is basically for situations when your RAM is not enough to match the requirements for the combined use of all your running programs. There was a time then that happened a lot. But not with the kind of large memory spaces these days.

Servers are a whole other story.

I you really feel the need to run all of the applications that you have installed at the same time, then give your system plenty of swap space.

---

### Post by mattlach on 2010-04-05
> **Slim Odds said:**
> Rules are made to be broken..... ;)

I don't want to make a long story out of this, but if you have 4GB or more on a desktop system, there is no practical reason to have swap (except for hibernation).

I know that some people will throw a hissy fit when I say that, but it's true.

swap is basically for situations when your RAM is not enough to match the requirements for the combined use of all your running programs. There was a time then that happened a lot. But not with the kind of large memory spaces these days.

Servers are a whole other story.

I you really feel the need to run all of the applications that you have installed at the same time, then give your system plenty of swap space.

Thank you.

Just a quick question.  If I should omit swap space on my system, and I somehow do something that uses up all of my 6GB of ram (like accidentally open two instances of VMware) how does the system behave?  

Will it just crash on me, or will it politely inform me that I am trying to do something silly and stop me from doing it?

---

### Post by ubunterooster on 2010-04-05
without enough generally it slows to a crawl.
I have used swap before (last I heard you should have double your RAM) but never has it been used. Not sure about hibernation; never needed to try it. Either sleep, on, or off for me.

---

### Post by DMcCunney on 2010-04-05
> **mattlach said:**
> 
The rule of thumb is to always have at least the same amount of swap space as your RAM.  Is this no longer recommended?
The rule of thumb I use is twice installed RAM, but whether I use a swap partition at all depends upon installed RAM.

Swap is part of virtual memory.  If more physical RAM is needed for something that is available, the OS can swap least recently used memory pages to swap to clear RAM, and swap them back in if something tries to access them.

If you have a lot of RAM, you may not *need* swap.  My desktop triple boots Win2K, WinXP, and Ubuntu 9.10, and has 4GB RAM.  I don't use swap, as Ubuntu can run entirely in RAM.  (A previous motherboard had a problem where drives could disappear while the system was up and running.  I had the Ubuntu drive drop out of the system once while I was *in* Ubuntu, and didn't even *notice* till updates started failing to install, because the file system they were being written to no longer existed.  Ubuntu was running in RAM and unfazed.)

On my old notebook with 256MB RAM, I use a 512MB swap partition, created in GPartEd.  I originally installed Xubuntu, but it was snail slow.  Wiping and re-installing 9.10 from MinimalCD on an ext4 file system with Xfce4 and friends fetched via apt-get was much better.

It's certainly possible to use an SSD as swap.  The concern is wear on the drive.  Flash media has a limit of about 100,000 *writes* before bits start going bad, but the drive circuitry should migrate data from failing areas and mark them as bad, so you would see a graceful degradation if you saw anything at all.

Depending on the SSD, you are likely to upgrade to a bigger, faster one well before you actually notice effects of wear.
______
**Dennis**

---

### Post by Slim Odds on 2010-04-05
> **ubunterooster said:**
> without enough generally it slows to a crawl.
...

Which is exactly what will happen if a system starts actually using swap.

The spinning hard drive (magnetic media) is always the slowest thing in the system (compared to CPU and RAM). So once the system starts swapping, you'll slow down dramatically even if you have the "right amount" of swap space.

With 6GB of RAM you should be in pretty good shape. You should just be careful not to launch too many RAM hogging VM's or whatever. Create a script to check the RAM space before launching.

I run my Win7/Lucid dual boot without swap and run quite a few programs without issue. It has 4GB. You'd be surprised how much space that really is. My first Windows PC had a 2GB hard drive  ;)

---

### Post by &lt;&lt;joe&gt;&gt; on 2010-12-29
> **ubunterooster said:**
> SWAP is a different filesystem and won't work in another ;'(

EDIT: I have no swap as I've never seen it used

Today it is possible to do this. In 2006 it may not have been.

It is true that there is a different file system in your swap partition. It is not however true that you cant put a swap **file** inside of another file-system. 
[https://help.ubuntu.com/community/SwapFaq#Four-step Process to Add Swap]("https://help.ubuntu.com/community/SwapFaq#Four-step Process to Add Swap")

---

### Post by presence1960 on 2010-12-29
> **mattlach said:**
> Really?   You've never used a swap partition?

I've always created one ever since my first slackware linux install back in the 90s, then on Gentoo which I used for years and now on Ubuntu (cause I got tired of the constant required maintainence)

[COLOR="Red"]The rule of thumb is to always ahve at least the same amount of swap space as your RAM.  Is this no longer recommended?
[/COLOR]
You left the important part of the rule out: if you want to hibernate you need at least as much swap as installed RAM. 

I have 4 GB swap partition but have never seen it used in over 2 years.

---

