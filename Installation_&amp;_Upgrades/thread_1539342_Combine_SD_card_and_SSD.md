---
title: "Combine SD card and SSD"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by hippickles on 2010-07-26
I have an Acer Aspire One ZG5 running Ubuntu NBR 10.04 with an 8 GB SSD and an 8 GB SD card. Is there a way to combine the SD card and SSD so that Ubuntu sees it as one 16 GB drive. I currently have everything installed on the SSD.

---

### Post by Goolie on 2010-07-26
> **hippickles said:**
> I have an Acer Aspire One ZG5 running Ubuntu NBR 10.04 with an 8 GB SSD and an 8 GB SD card. Is there a way to combine the SD card and SSD so that Ubuntu sees it as one 16 GB drive. I currently have everything installed on the SSD.


I highly doubt that you can, but I'm not well educated in said department.  Why do you want them to act as one?  Why don't you leave your main programs on one, and files you access every now and then on the SD?

---

### Post by snowpine on 2010-07-26
Personally I would not recommend it for 2 reasons:

1) The SD card is removable; you would not be able to boot/use your system without the SD card inserted!
2) Some netbook models (not sure if this is true of the ZG5) have trouble resuming from suspend when running from SD; the SD reader doesn't wake up quick enough and there is a "disk not found" type of error.

Rather, I would recommend keeping / and /home on the SSD (8GB is plenty) and using the SD card for storing your documents/music/videos/etc.

---

### Post by Joe of loath on 2010-07-26
Even better, set the SD card as /home. That way all the stuff you download will automatically be saved there.

---

### Post by Herman on 2010-07-26
> Even better, set the SD card as /home. That way all the stuff you download will automatically be saved there.I agree, I had a worse problem, I have an Asus EeePC 4g, (4GB SSD), with a 16 GB SD card, (I used to have only a 4GB SD card).

I went to the extra effort of writing down what I did in case somebody else is interested in doing something similar, [Ubuntu NetBook Install]("http://members.iinet.net/%7Eherman546/p28.html").

Mine is getting on towards two years old already and is still working perfectly well. When the first netbooks were made with SSD drives there were a lot of people who were skeptical of flash memory because they believed that flash would wear out very quickly. I have not found that to be true yet. Time will tell.
A larger / drive with more free space would enable the flash to have more free blocks for the wear leveler to work with, and so would last parabolically longer.
My 4 GB SSD runs at about 80 to 90 % full, even when I use special measures frequently to free up disk space. I would install more software if I had room.
 I wish I had 8GB to use for my / drive. You are lucky. :)

EDIT, My first SD card was 4 GB and it failed after a while, but it failed on the safe side, it just got hard to write to, but I can still read all the data that is on it. SD cards are not the same as SSD drives, they are much simpler devices designed primarily for their small size and especially for cameras. They probably don't have a 'controller' like a SSD or a USB flash memory stick does, or at least not one that's very sophisticated, (there's no room for one), and therefore wouldn't have wear levelling. So it would _not_ be a good idea to use one of those for root or for swap, as it can be expected to wear out rapidly under that kind of use. 
Your SSD drive, on the other hand, does have a disk controller, which would feature some kind of 'wear levelling', (the flash blocks are constantly shuffled and rotated so you're not wearing the memory out by writing to the same cell repeatedly for too long and hammering it to death). Your SSD drive can be expected to last quite a long time before it wears out, some say much longer than a hard disk. I am still waiting for mine to wear out before I'll know for sure. Mine is used for work that would have killed a hard disk long ago anyway, having the netbook running in a moving vehicle, on rough roads with a lot of vibrations and jarring. :)

---

### Post by sid1950 on 2010-08-02
Interested in your experience. I have an Acer One A110 16Gb which came with Linspire. I repartitioned it to try Suse 11.2, but found it too difficult to customize KDE to run on the small screen. I changed to Ubuntu 9.10 NBR and found it worked very well and would boot from cold in about 40 secs, and recover from suspend in about 5 or 6 seconds. I would occasional get a GUI freeze, sometime logging out would work, but if not, CTRL+ALT+BACKSPACE would always recover it. The only problem I have is that Firefox is slow to start, and will occasionaly hang after loading a very busy site.

I upgraded to 10.04 NBR and found that was slightly faster and more stable. I use it on the move every day for e-mail, and find the keyboard more than adequate for touch typing.

After some research I removed the swap partition but am not sure how much difference it made. There is some stuff on the openSuse website about this.

My questions for you are, have you tried running without a swap partition, and did it make any difference? And has anyone written a Howto for tuning Ubuntu on a SSD fitted netbook?

---

### Post by Herman on 2010-08-02
Probably the improvement you noticed between Ubuntu 9.10 and Ubuntu 10.04 would be due mainly to the change from the ext3 file system to ext4. The new ext4 file system is much better suited use in flash memory. I used to recommend reiserfs rather then ext3 but now I think ext4 is the best.
Another important improvement between 9.10 and 10.04 is that the partition in 10.04 will start at sector 2048 instead of the traditional sector 63, so it will be aligned on an erase block boundary, which is a big help for those of us with flash memory drives.

I use a swap file instead of a swap partition in most of my installations now, and I tune swappiness to 10 in flash memory drives or SSDs so the operating system will prefer the RAM, but the swap is available if needed. Even though my computers have plenty of RAM, I found that performance suffered if I didn't have a swap file.

I use either the noop or the deadline IO scheduler and my recommendations for how to set up the operating system to run in flash memory or an SSD are at the bottom of the page I linked to in my earlier post, [Ubuntu NetBook Install]("http://members.iinet.net/%7Eherman546/p28.html").

Regards, Herman :D

---

### Post by chrisinspace on 2010-08-02
I just got a netbook for my daughter this weekend and installed Ubuntu 10.04 NBR.  I'll have to try your suggestions the next time I can pry it from her hands. :)

Just curious...why do you use a swap file instead of a small swap partition?

---

### Post by Herman on 2010-08-03
:D I'm not really sure if it makes any difference or not. 
Given that the first partition is meant to begin at an erase block boundary for best performance and longest life for the flash, then probably the swap area too should ideally be created with its start point on an erase block boundary too. 
Rather than try to understand the maths necessary to work out where the swap area should begin, it I am hoping to avoid the issue by just having the swap as a file.
It's theoretical, and probably doesn't make much difference, if any. :D

---

