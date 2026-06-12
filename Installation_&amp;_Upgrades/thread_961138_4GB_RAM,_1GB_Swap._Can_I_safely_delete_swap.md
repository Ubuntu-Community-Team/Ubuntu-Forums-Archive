---
title: "4GB RAM, 1GB Swap. Can I safely delete swap?"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by insanity54 on 2008-10-28
Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.

My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?

Thank you for your reply!

---

### Post by gvoima on 2008-10-28
> **insanity54 said:**
> Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.

My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?

Thank you for your reply!

short answer: No and No

No it's not recommended to delete swap, because it is always used. e.g. hibernation.

A 32bit system limits the memory mapping, so you will always see 3GB no matter what.
But a linux kernel 2.6 and newer should have native PAE support but you have to enable it. If the hardware can handle it. (and it should since pentium pro).
PAE will extend the address size from 32bit to 36bit. So after that you should see all of the 4GB. But the default kernel doesn't include PAE support, and it's distribution specific, I guess ubuntu doesn't either :)

---

### Post by insanity54 on 2008-10-29
Hmm. This is somewhat disappointing! Oh well. 

Thank you gvoima for your reply!

---

### Post by gvoima on 2008-10-29
You could try a 64bit linux instead of 32bit. If you have any specific reasons not to use 64bit (e.g. non-64bit hardware), then you are out of luck.

I'm guessing that trying to recompile the kernel with PAE support is a little bit overkill :)
But there's very good tutorials here to do that also.

---

### Post by sandy8925 on 2008-10-29
> **insanity54 said:**
> Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.

My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?

Thank you for your reply!

If you have Windows or any other OS installed check there and see if it can recognize all 4 GB of RAM.If others also have same problem then it maybe that your motherboard or CPU doesn't support 4 GB RAM or you have to use 64-bit editions.

---

### Post by cevans on 2008-10-29
> **insanity54 said:**
> Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.

My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?


If you don't use hibernation, doing away with the swap partition is probably safe. My most recent install doesn't have one. (edit: actually, now I need to go play around with fork bombing my computer to see how it reacts)

However, I don't think that will solve your RAM problem. If you don't want to run 64-bit, then I think that things like PAE are supported in other kernel packages; perhaps looking into the server kernel variant (linux-server) might be worthwhile.

---

### Post by SlonUA on 2009-05-29
> **insanity54 said:**
> Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.

My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?

Thank you for your reply!

Just install **linux-server** and U will see Ur 4GB. Selecting relative choice by this kernel on Grub boot menu =)
sudo apt-get install linux-server

Keep in mind, that U will have the same Ubuntu Desktop and Full Gaming =)
Yup, swap isn't necessary started from 2GB. Only in fact of using VERY specific software. 
So, U always can create swap using just file .. no necessary partition =)

---

### Post by insanity54 on 2009-05-29
Hmm. Interesting! I just might do that then! However, are there any downsides to using a server version of ubuntu as a desktop?

---

### Post by anarchyinc on 2009-05-29
> **insanity54 said:**
> Hello. I recently installed ubuntu on my new PC. When I set up my partitions (I did so manually) I set the swap size to 1GB. Hours after installing, I realized that ubuntu only recognized 3GB of the 4GB of RAM. My guess is that this is because I set my swap partition to 1GB, and 4GB is the maximum memory that 32 bit ubuntu can handle.
 
My question is this-- is it safe to just delete my swap partition? After doing so will ubuntu recognize all 4GB of physical RAM?
 
Thank you for your reply!
 
Swap memory comes from the hard drive, it does not take away from the ram. Also, you can remove /swap safely from your setup. swap is there for when you are running low on ram, just like windows VM, with 4 gigs of ram I wouldn't worry about running low. I don't know if ubuntu has a version of the "bigmem" kernal. You might want to test that out. It allows 32bit to run over 4 gigs of ram.

---

### Post by SlonUA on 2009-05-29
> **insanity54 said:**
> Hmm. Interesting! I just might do that then! However, are there any downsides to using a server version of ubuntu as a desktop?

Nope. Used on 8.10 and 9.04. Also with Ati and Nvidia binary drivers. Perfectly works =). Ubuntu Rulez =). 

Keep on mind to install, also linux-headers-server (just forget about it, it's for dkms)

So, Solution:
```
sudo apt-get install linux-server linux-headers-server
```

Please, post if any troubles will occur ;)

Some notes: Different between Desktop and Server it's only on Kernel Image and Meta-Pekages
aka type in shell 
```
tasksel
```
and U can convert ANY installation to ANY =))

!!!! Don't HIT on button OK, if U DONT'T wanna any changes .. It will revert Ur system to clean state with selected META packages
Just try test mode
```
tasksel -t
```

---

### Post by insanity54 on 2009-06-18
Hi all, 

I decided to try and get my full 4GB of RAM recognized. PS, I still have 1GB swap and plan to leave it that way. I ran the following command: 

```
sudo apt-get install linux-server
```

Doing so resulted in all 4GB of RAM being usable, but it has caused my display drivers to stop working, with an error that NVIDIA cannot start.

I started a new thread here:
[http://ubuntuforums.org/showthread.php?p=7476927#post7476927](http://ubuntuforums.org/showthread.php?p=7476927#post7476927)

Thank you all very much for your time!

---

### Post by ericab on 2009-06-18
```
sudo apt-get install linux-headers-server
```

---

### Post by insanity54 on 2009-06-18
Huh... That was painfully simple. It worked perfectly. ericab, Thank you kindly!

---

### Post by ericab on 2009-06-18
glad your back up and running :)

---

### Post by presence1960 on 2009-06-18
if your CPU is 64 bit capable the question you should be asking is _**why not 64 bit Ubuntu?**_

---

### Post by insanity54 on 2009-06-18
> **presence1960 said:**
> if your CPU is 64 bit capable the question you should be asking is _**why not 64 bit Ubuntu?**_

64 bit capable? No idea. I'm way out of my league here.

My CPU is an INTEL C2D E8500 3.16G 775 45N R

---

### Post by presence1960 on 2009-06-18
> **insanity54 said:**
> 64 bit capable? No idea. I'm way out of my league here.

My CPU is an INTEL C2D E8500 3.16G 775 45N R

is this your CPU? [http://geizhals.at/deutschland/a303350.html](http://geizhals.at/deutschland/a303350.html)

If so it is 64bit capable. basically almost all new CPUs are 64bit . Which means they are capable of running 64 bit OS, which will utilize all your RAM without having to mess with PAE. From what I have read using PAE may entail a performance hit. Key word is may. Why not just install 64 bit ubuntu. just about every package in the 64 bit repositories are the same as the 32 bit. For more info prior to making a decision read the stickys from our 64 bit section of our forum: [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

you paid the bucks for a 64 bit processor you may as well make use of it. Especially since the issues with Flash & Java have been worked out now.

---

### Post by ericab on 2009-06-18
i agree...
ultimatley you should have used the 64bit variant of ubuntu.

---

### Post by insanity54 on 2009-06-18
Yeah, that's my processor. Wow, I had no idea that 64 bit was even an option for me! I just might switch on over to 64 bit ubuntu! It wouldn't be hard at the moment because I just installed Ubuntu from scratch last weekend... I've still got all my files backed up!

Thanks guys!

---

### Post by presence1960 on 2009-06-18
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

That above link is from the 64 bit users section of this forum. I used that to install Flash. Worked on hardy, Intrepid & jaunty flawlessly for me.

There is a link for Java also on there. But I didn't use that Java install, so I can't comment on it.

I used this for java on 64 bit : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

This version is crisp & very snappy.

P.S. Thanks zika for the tutorial on that version of java!

---

### Post by ericab on 2009-06-18
> **presence1960 said:**
> [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

This version is crisp & very snappy.


couldnt have say it any better;
i think you too will see the 64bit variant is much.... smoother

---

