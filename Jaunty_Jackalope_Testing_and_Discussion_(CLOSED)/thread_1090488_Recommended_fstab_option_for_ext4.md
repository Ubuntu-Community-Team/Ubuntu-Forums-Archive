---
title: "Recommended fstab option for ext4"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-03-08
Talked with Theo T last evening about options in fstab & ext4....He is recommending a noatime option instead of the default relatime...read about his testing here:  [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

As we move towards SSD's, talking about how often the system writes to disk become more important.......So his blog post is timely & relevant.

---

### Post by calc on 2009-03-08
> **autocrosser said:**
> Talked with Theo T last evening about options in fstab & ext4....He is recommending a noatime option instead of the default relatime...read about his testing here:  [http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

As we move towards SSD's, talking about how often the system writes to disk become more important.......So his blog post is timely & relevant.

> Tytso
What else have we learned? First of all, for normal workloads that include data writes, the overhead from journaling is actually relatively small (between 4 and 12%, depending on the workload). Further, than much of this overhead can be reduced by enabling the noatime option, with relatime providing some benefit, but ultimately if the goal is to reduce your file system&#8217;s write load, especially where an SSD is involved, I would strongly recommend the use of noatime over relatime.


His blog entry just seemed to reconfirm my suspicions that SSDs really aren't suitable for real world use, at least not yet. If someone has to be concerned about mount options for standard desktop/laptop usage and how few writes overall occur on them, then developers would definitely need to be really worried about the drive dying in a much shorter timeframe from doing astronomical numbers of writes during compiles.

I'm personally avoiding SSDs for the foreseeable future and recently bought a 2.5" 500GB 7200rpm for my laptop. It does 100MB/s which is within the same order of magnitude of speed as SSDs but without the risk of death through "overuse".

---

### Post by autocrosser on 2009-03-08
If you want some good "food for thought"--follow the main blog on file systems <grin>......[http://thunk.org/tytso/blog/category/computers/linux/filesystems/](http://thunk.org/tytso/blog/category/computers/linux/filesystems/)
and read "Should Filesystems Be Optimized for SSD's?"

Good points there......

I have 1.5TB in my tower--the last Maxtor I bought (500GB) cost me US$69 + shipping from NewEgg, so I'm not planning on a SSD anytime soon---I'll wait until the market levels out a bit more (I tend to wait 6~12 months) before I move into one.......

---

### Post by jfernyhough on 2009-03-08
I've been using noatime,nodiratime for a while now - on ext3 and ext4 (I even used it back when I was experimenting with ReiserFS. Went to ext3 after a power outage killed the installation).

I've found no problems with this setup, and things do seem a bit nippier without the constant write-on-read.

---

### Post by calc on 2009-03-08
> **autocrosser said:**
> If you want some good "food for thought"--follow the main blog on file systems <grin>......[http://thunk.org/tytso/blog/category/computers/linux/filesystems/](http://thunk.org/tytso/blog/category/computers/linux/filesystems/)
and read "Should Filesystems Be Optimized for SSD's?"

Good points there......

I have 1.5TB in my tower--the last Maxtor I bought (500GB) cost me US$69 + shipping from NewEgg, so I'm not planning on a SSD anytime soon---I'll wait until the market levels out a bit more (I tend to wait 6~12 months) before I move into one.......

Having some optimization for SSD isn't a bad thing. The point I was making before was that if noatime (only a 4-12% improvement on writes) helps that much on prolonging SSD life then they are most likely not really suitable for real world use yet. And from what I have read about them only having cell lifetimes of several hundred thousand writes, I would be inclined to think they won't last nearly as long as hard drives.

Of course if you somehow optimize linux to not do any writes which prolongs a SSD's lifetime then you also help make hard drives perform faster as well. :-)

---

### Post by autocrosser on 2009-03-08
Yes--I'm looking at the cost per MB & cycle-life--when it gets to around $1 per MB I'll start thinking hard about it--And that would be for the "smart" SSD's that are running around at $400 or so right now.....

I do really see your point---you guys put quite a load on drives that the general user rarely equals--I tend to do more /.configure...make...make install/make clean than most users, so I "tend" to lean towards your group--I leave my system on 24/7 too...running BOINC that reads/writes small files to the drives constantly--I really want a drive that will hang in there for years of hard use.

I'm really wanting to test a SSD, but not at the current prices:(

---

### Post by calc on 2009-03-08
> **autocrosser said:**
> Yes--I'm looking at the cost per MB & cycle-life--when it gets to around $1 per MB I'll start thinking hard about it--And that would be for the "smart" SSD's that are running around at $400 or so right now.....

I do really see your point---you guys put quite a load on drives that the general user rarely equals--I tend to do more /.configure...make...make install/make clean than most users, so I "tend" to lean towards your group--I leave my system on 24/7 too...running BOINC that reads/writes small files to the drives constantly--I really want a drive that will hang in there for years of hard use.

I'm really wanting to test a SSD, but not at the current prices:(

Yea I want one too. Having fewer moving parts means less chance for damage in a laptop. But I also need a huge amount of space especially due to having multiple copies of openoffice.org source laying around (I maintain it for Ubuntu). Once reliable and cheap (< $150 USD) 256GB or larger SSDs are available I will probably buy one. However, I don't think that will probably happen until at least 5 years from now.

---

### Post by nanog on 2009-03-08
there are 240-250 gig drives available for ~$400ish now and we've been seeing priced reductions of about 50% every 6-12 months its just a matter of time before platter-based drives are obsolete. good riddance -- i've burnt my fingertips too many times.

---

### Post by autocrosser on 2009-03-08
If you have a desktop that is new enough for PCIe there is a really cool option---a bit too expensive right now---but just wait!!!!

[http://www.fusionio.com/Products.aspx](http://www.fusionio.com/Products.aspx)

max read is around 750mb per sec!!!!! (XFS filesystem with Redhat 5.2)

---

### Post by calc on 2009-03-08
> **nanog said:**
> there are 240-250 gig drives available for ~$400ish now and we've been seeing priced reductions of about 50% every 6-12 months its just a matter of time before platter-based drives are obsolete. good riddance -- i've burnt my fingertips too many times.

But not much improvement on the reliability front for SSD's. Intel's own SSD is only rated for maximum 20GB/day transfer, do more than that and it won't even last 5 years. If you do more than that in transfer the drive starts limiting the speed to where you can't possibly do more than that, so that your drive won't die in under 5 years. It is noted in the documentation for the drive from what a post that was referenced in Tytso's blog. I often do large amounts of disk io and so a SSD that can't do more than 20GB transfer in a day really isn't suitable for my use. Also, I have several physical HDDs without any SMART problems that are well over 5 years old... so it looks like they still have a very long way to go before SSDs can really replace HDDs.

---

### Post by nanog on 2009-03-11
Did not know about the 20 gb/day limitation. Thats not good.

---

### Post by autocrosser on 2009-03-12
Yes--they are not good enough right now--I'm waiting for another 6 to 12 months before moving into one--I really like the speed---but the lifespan to cost ratio leaves me cold....The best answer I've seen is the link I posted--750mb per sec will leave anything else made right now in the dust & using a PCIe slot makes good sense--the base speed & tight availability to the CPU is great--I just can't see paying $1200+ for 80G right now......When that is $150 or so---yes

---

