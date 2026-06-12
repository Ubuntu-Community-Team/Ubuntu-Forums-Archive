---
title: "need expertise on determining partition size and stuff."
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2010-11-28
I'm setting up a dual boot partition. so far I have windows 7 partitioned on my toshiba laptop. I have 150 gig's of unallocated space. I was hoping that the new ubuntu 10 would have the guided partion option so that I could choose "use largest ammount of contiguous free space" but it doesnt have that option and is asking me to input everything manually. I want to leave 40 or 50 gigs for the ubuntu os and create a seperate ntfs partition for storage so i can access my files while im on either operating system. If someone could please help me by describing what I need to do to accomplish this I would greatly appreciate it. Thank you.

---

### Post by sent17inel on 2010-11-29
bump.

---

### Post by sent17inel on 2010-11-29
super bump!  

:P haha  just kidding. but to be more specific I just need help with laying out like swap space and boot loader stuff. I never learned the specifics. Not having the "Guided partitioning" option is really hindering me.

---

### Post by Bucky Ball on 2010-11-29
/ =15Gb
/home =?
/swap =2Gb

Basic setup.

---

### Post by sent17inel on 2010-11-29
> **Bucky Ball said:**
> / =15Gb
/home =?
/swap =2Gb

Basic setup.

so 15 gb for the root os?

and /home I would say 30 gb just to be safe.

and /swap  =2gb?  i have 3 gb of ram on a 64 bit operating system.  is 3 gb swap better?

---

### Post by wayne128 on 2010-11-29
> **sent17inel said:**
> I'm setting up a dual boot partition. so far I have windows 7 partitioned on my toshiba laptop. I have 150 gig's of unallocated space. I was hoping that the new ubuntu 10 would have the guided partion option so that I could choose "use largest ammount of contiguous free space" but it doesnt have that option and is asking me to input everything manually. I want to leave 40 or 50 gigs for the ubuntu os and create a seperate ntfs partition for storage so i can access my files while im on either operating system. If someone could please help me by describing what I need to do to accomplish this I would greatly appreciate it. Thank you.

There are many method on allocation and most will work.

As for my experience, since you have Win7 already, its data partition is ntfs format and can be shared easily with any Linux OS, what essentially means you can simply set up Linux with a swap of about 2-4G size and a / of about 20-30G, this is very large already. Many of my multi boot partition has Linux of about 10-20G.

When you started to download files and fill up more of your Linux OS partition, at some point, you can just move them over the win7 data partition and thus keep the Linux 'slim' 
When you log in on win7, you can read these files without issue.

The rest of unallocated space can be just left unallocated. Soon you might find yourself wanting to play with other OS and multi boot on the same drive, then you could just add logical partition on the unallocated space and play with new OS, without disturbing the existing win7 and first Linux OS. 
If you consider third and more Linux OS, you can share swap partition, most Linux OS installer can detect swap and activate it without you to make any selection.

---

### Post by sent17inel on 2010-11-29
> **wayne128 said:**
> There are many method on allocation and most will work.

As for my experience, since you have Win7 already, its data partition is ntfs format and can be shared easily with any Linux OS, what essentially means you can simply set up Linux with a swap of about 2-4G size and a / of about 20-30G, this is very large already. Many of my multi boot partition has Linux of about 10-20G.

When you started to download files and fill up more of your Linux OS partition, at some point, you can just move them over the win7 data partition and thus keep the Linux 'slim' 
When you log in on win7, you can read these files without issue.

The rest of unallocated space can be just left unallocated. Soon you might find yourself wanting to play with other OS and multi boot on the same drive, then you could just add logical partition on the unallocated space and play with new OS, without disturbing the existing win7 and first Linux OS. 
If you consider third and more Linux OS, you can share swap partition, most Linux OS installer can detect swap and activate it without you to make any selection.

thank you! this cleared up a lot! I guess the last time I tried to install manually I didn't fully understand the concept of / and swap space but I think I can do it. Im gonna try right now. Thank you for your explanation!

---

### Post by sent17inel on 2010-11-29
> **sent17inel said:**
> thank you! this cleared up a lot! I guess the last time I tried to install manually I didn't fully understand the concept of / and swap space but I think I can do it. Im gonna try right now. Thank you for your explanation!

it worked!!!  somehow i had the idea in my head from when i first tried it three years ago that it was hard and not worth my time. but i just did it and it was easy!!  :)  im sooo happy!!!  trying to crack wep using ubuntu and every other thing i worked on using the command line really made this seam easy in comparison!  :)  thank you for your explanation. I seriously had an epiphany when you wrote what you did.!

---

### Post by Bucky Ball on 2010-11-30
There is absolutely NO reason to setup a /swap larger than 2Gb on a modern machine running 3Gb of RAM. Do some research wayne128. :)

---

### Post by jocko on 2010-11-30
> **Bucky Ball said:**
> There is absolutely NO reason to setup a /swap larger than 2Gb on a modern machine running 3Gb of RAM. Do some research wayne128. :)
There is at least ONE reason for having a swap partition slightly larger than RAM: Hibernation. [Do some research]("https://help.ubuntu.com/community/SwapFaq#Why%20do%20I%20need%20swap?").
But if you don't use hibernation, you'll *probably* be fine with less swap. It all depends on what applications you use.

---

### Post by Bucky Ball on 2010-11-30
Research complete:

[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

I'll leave you to it here. Goodnight.

---

### Post by Towers of Creation on 2010-11-30
“I'm setting up a dual boot partition. so far I have windows 7 partitioned on my toshiba laptop. I have 150 gig's of unallocated space. I was hoping that the new ubuntu 10 would have the guided partion option so that I could choose "use largest ammount of contiguous free space" but it doesnt have that option and is asking me to input everything manually. I want to leave 40 or 50 gigs for the ubuntu os and create a seperate ntfs partition for storage so i can access my files while im on either operating system. If someone could please help me by describing what I need to do to accomplish this I would greatly appreciate it. Thank you.”


I believe it’s easier if you make your partitions I have time by booing from the Ubuntu install disc using the Gparted Gnome Partition Editor. It has a graphical interface whereas if you try to make the partitions directly during the install process it’s more DOS yucky looking.;)

---

### Post by SecretCode on 2010-11-30
> **Bucky Ball said:**
> Research complete:

[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

I'll leave you to it here. Goodnight.

Well researched:

> Therefore, your swap partition should be at least as big as your RAM size.
- which I agree with.

That article talks about a "high RAM" system as one with 2GB of RAM ... possibly a bit dated?

---

### Post by Bucky Ball on 2010-12-01
Uh huh. With 2Gb of RAM you'd be lucky to touch /swap. With 4Gb, unlikely.

---

### Post by wkulecz on 2010-12-01
> Uh huh. With 2Gb of RAM you'd be lucky to touch /swap. With 4Gb, unlikely.

When you touch /swap, performance goes to hell in a handbasket, but its way better than finding out how well every running program handles failed memory allocations! (often there will be bugs!)

Setting swap to 2X the installed RAM is still a very safe default and with todays enormous hard drive sizes just not that big a deal.  Think of it as cheap insurance.

I usually set swap to 2X the RAM I have, or 1X the max RAM the MB can support in case I upgrade the memory later.

You can always run without swap if you want, and notify program developers of bugs you find.

I often work on several projects at once switching between them organized by the multiple desktop feature, some occasionally remain idle for weeks or months when I get busy with more importatnt stuff, but its nice to be able to just click the virtual desktop and pickup more or less where I'd left off.  Often one virtual desktop will be a Virtualbox running Windows -- this alone can easily consume half your RAM depending on what version of Windows and its apps you are running (Win7 is pretty lame with much less than 2GB).

---

### Post by sent17inel on 2010-12-01
> **wkulecz said:**
> When you touch /swap, performance goes to hell in a handbasket, but its way better than finding out how well every running program handles failed memory allocations! (often there will be bugs!)

Setting swap to 2X the installed RAM is still a very safe default and with todays enormous hard drive sizes just not that big a deal.  Think of it as cheap insurance.

I usually set swap to 2X the RAM I have, or 1X the max RAM the MB can support in case I upgrade the memory later.

You can always run without swap if you want, and notify program developers of bugs you find.

I often work on several projects at once switching between them organized by the multiple desktop feature, some occasionally remain idle for weeks or months when I get busy with more importatnt stuff, but its nice to be able to just click the virtual desktop and pickup more or less where I'd left off.  Often one virtual desktop will be a Virtualbox running Windows -- this alone can easily consume half your RAM depending on what version of Windows and its apps you are running (Win7 is pretty lame with much less than 2GB).

I have 3 gigs of ram right now but next week I will have 8  :)

---

