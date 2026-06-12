---
title: "A simple question on 10.04 partitioning"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by BastardNamban on 2010-05-05
Not new to linux, had 8.04 for a couple years, have a non-persistant working USB livedisk of my old 8.04 install with GParted and all my old programs/user data.

I have a laptop with a 120GB HDD, about 30 GB of which is held by an XP SP3 install solely for using a special XP only CAD program that is memory intensive, and a 2 GB partition for my XP TEMP to buffer the memory.

So- about 80 GB available free space remaining. I have a working liveCD of 10.04, and want to fill the rest of my HDD with a fresh install of 10.04.

I will do a 2 GB swap for my 2GB of memory- but I'm thinking of doing a separate / partition and /home partition. How much room do you all recommend for these with 10.04, as it is undoubtedly bigger than 8.04?

I'd like as much space as possible for personal files, obviously, but having a separate / partition to make upgrading easier would be nice- I just want to know some conservative recommendations for sizing it. I do plan on adding several, but not a ton of additional programs to Ubuntu not included.

Ideas?

---

### Post by antenna on 2010-05-05
I would probably recommend 10-15GB depending on how much you think you'll install.  My fairly conservative (not too much more than default) install is at nearly 4GB with a clean package cache (but it's usually a few GB).  My / is sized at 30GB but only because I have plenty of room.  10GB would probably be enough for me.

---

### Post by iskarion on 2010-05-05
I'm using (K)ubuntu since I think Dapper or Edgy and always had separate / and /home partitions. / with a size of 15 GB and I never had issues with free space on the root partition. And I have quite a few things installed. e.g. both Gnome and KDE. Currently with 10.04 I nevertheless still have 3 or 4 GB free on root (after cleaning apt cache).

So 15 GB should be plenty enough. Maybe even 10 GB if you are only using Gnome and don't install everything you can find in the repositories.

Btw. isn't 30 GB a bit much for an XP partition?

---

### Post by BastardNamban on 2010-05-05
So to be safe, 10 GB for / (root) partition, the rest for /home?

---

### Post by cosine352 on 2010-05-05
> **BastardNamban said:**
> So to be safe, 10 GB for / (root) partition, the rest for /home?

I have 20 GB and I am using only 9.5 GB. I have installed loooooooots of applications. So 10 GB will be fine for the root I will say.
I will give swap a little bit more than RAM. Before I had some problems with sleep/hibernation etc because SWAP was not enough.

---

### Post by BastardNamban on 2010-05-05
Ah, the 30 GB for XP- I put XP back on just for 1 program- Autodesk Inventor 2010. You need about 25 GB free just to install it. I had had a 16 GB temp partition just to install it- it creates that much in temp files during install!

It's an amazing program, and I regret that there just wasn't a way to make it work in wine in ubuntu, or I would have done it.

So that 30GB for XP is just for Inventor- and I have about 4.25 GB free after just it. It's worth it though, when I see what I can do with it.

---

### Post by BastardNamban on 2010-05-05
> **cosine352 said:**
> I have 20 GB and I am using only 9.5 GB. I have installed loooooooots of applications. So 10 GB will be fine for the root I will say.

I had, maybe, 15 programs installed on my build. I didn't go nuts with it. How many do you figure you have?

Also, I figured 2GB for swap, because that's the amount of RAM I have, and I believe swap is limited to a max of 2 GB, or at least I remember it being so for 8.04...?
If I can do a bit more, I will.

---

### Post by cosine352 on 2010-05-05
> **BastardNamban said:**
> I had, maybe, 15 programs installed on my build. I didn't go nuts with it. How many do you figure you have?

okay. 
> dpkg --get-selections > /Desktop/installed-software.dat

gives me 2592 applications installed. But the number should be more as I have some applications installed locally and will not be listed by that command.

---

### Post by oldfred on 2010-05-05
I thought I had downloaded lots of programs and I have only used 5-6GB and typically recommend 10-20GB where you have lots of room. You can get by with 6-10GB for root but if on the low end may have to keep track of space. Swap can be equal to RAM or slightly larger and the rest /home.

---

### Post by BastardNamban on 2010-05-05
Ok, I had what I thought to be a bright idea. I'm typing from my USB livedisk on an 8 GB usb key.

I thought, if I navigate to the / folder on the livedisk, which has all my old programs installed on it, and deselected /home, I could get an exact read of what my previous / was in size.

But somehow, over 13 GB of storage is showing up under properties. That can't even be possible, as the key is only 8 GB! I thought maybe one of the other partitions is being selected, but I can't find anything of the sort.

Can this method be useful, and if so, what should I select? If not, just tell me.

---

### Post by BastardNamban on 2010-05-05
Ok, I have a feeling I found part of the cause. It looks like my install is about 7.5 GB on the livedisk, sans things that are likely the storage size of the disk itself.

I will try a / root partition of 10 GB, and the rest of about 70 GB as my /home partition after about a 2.2 GB for my RAM as swap.

Thank you everyone, I appreciate the help):P

---

### Post by srs5694 on 2010-05-05
> **oldfred said:**
> I thought I had downloaded lots of programs and I have only used 5-6GB and typically recommend 10-20GB where you have lots of room.

I don't disagree with your suggestions, but I want to point out that the amount of space being consumed *right now* is not what you need to worry about -- the big concern is space that's consumed *temporarily.* This includes temporary user files (typically stored in /tmp and /var/tmp) and Ubuntu packages that are downloaded prior to installation and then deleted. Depending on how you use the system, you could easily get 1-10GB of temporary files. For instance, if you leave the system for months without upgrading and then upgrade half your packages all at once, you'll have a lot of package files that hang around temporarily. If a DVD-creation tool is configured to use /tmp for storage space, you might have as much as twice the DVD's size being stored there. (This one could probably be reconfigured to use space in /home, though.)

---

### Post by BastardNamban on 2010-05-06
I am going to mark this thread as solved- I ended up with:

32 GB XP partition, NTFS
10 GB / (root) partition, Ext3
75 GB /home partition, Ext3
2.4 GB Swap partition

My new build, all my programs, and custom settings for EVERYTHING were completely finished in one short afternoon. Everything. That's amazing to me- everything I had to compile or heavily fool with for weeks or MONTHS before to get working was integrated into synaptic now, and works flawlessly. Wireless works without me even fooling with NDIS wrapper. As soon as my first boot, it autoconnected! Even the things I never could get working, spellcheck inside Firefox, the audio volume buttons on the front of my dell 9300 linked to all speakers for normal volume control, works out of the box!

My mind is blown. Other than the stupid breadcrumbs issue with the item location path in nautilus, I love it all. Yes, even the button location- it's right above all the menu options, a much better place for them- less mouse movement.

I loved linux before 10.04, but now that I have 10.04, I'd say I'm a rabid addict- everything was so much simpler and working right away with this build, and it shows. It all just WORKS.

Now I can get my work done without screwing endlessly with compiling and special settings!

Thanks for all your suggestions on sizes everyone. :p

---

### Post by BastardNamban on 2010-05-06
I am going to mark this thread as solved- I ended up with:

32 GB XP partition, NTFS
10 GB / (root) partition, Ext3
75 GB /home partition, Ext3
2.4 GB Swap partition

My new build, all my programs, and custom settings for EVERYTHING were completely finished in one short afternoon. Everything. That's amazing to me- everything I had to compile or heavily fool with for weeks or MONTHS before to get working was integrated into synaptic now, and works flawlessly. Wireless works without me even fooling with NDIS wrapper. As soon as my first boot, it autoconnected! Even the things I never could get working, spellcheck inside Firefox, the audio volume buttons on the front of my dell 9300 linked to all speakers for normal volume control, works out of the box!

My mind is blown. Other than the stupid breadcrumbs issue with the item location path in nautilus, I love it all. Yes, even the button location- it's right above all the menu options, a much better place for them- less mouse movement.

I loved linux before 10.04, but now that I have 10.04, I'd say I'm a rabid addict- everything was so much simpler and working right away with this build, and it shows. It all just WORKS.

Now I can get my work done without screwing endlessly with compiling and special settings!

Thanks for all your suggestions on sizes everyone. :p

---

