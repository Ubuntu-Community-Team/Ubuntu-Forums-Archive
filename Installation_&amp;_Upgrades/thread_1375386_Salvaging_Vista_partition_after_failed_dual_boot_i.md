---
title: "Salvaging Vista partition after failed dual boot install"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by CaptConan on 2010-01-07
Hello. I wanted to start exploring web development and perhaps hosting my own server as well as learning about linux and all the things that go with it so I downloaded the ubuntu 9.1 Server edition and burned it to a CD. I thought to put it on my Dell laptop as it is newer than my main PC and I could bring it to and fro between class. It had Vista installed and I definitely wanted to keep that in the meantime until I got more familiar with Ubuntu. The laptop has a 320GB hard drive with a 10 GB recovery partition. I went ahead and formatted the 10GB to make room for ubuntu. Also I was able to "shrink" the main windows partition by 16GB to make even more room. I could not combine the two small drives but alas. I had hoped to use the 16GB partition for the main install and the 10GB for a necessary swap drive (I am completely new to all this).
So I reboot on the server CD and get to the partition section. I was following this guide here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
It seemed I did not want to do anything "guided" or "automatic" because the options were listing the entire drive and again i wanted to keep my vista untouched. So I go to manual partitioning and although the guide didn't go into enough detail I went ahead and assigned an "ext2" filetype to the larger partition and a "swap" to the smaller partition. Then I went to write changes to disk and after completing one of the two successfully the installer failed to configure the swap drive. I don't know why. I restarted to make sure windows was OK and surely it was not, as I got the dreaded "missing operating system" screen. I ran the windows recovery CD and lo and behold it could not find any drives at all, much less repair them. The data I had on the vista partition were not particularly vital, but it would be nice to have it back.

So my questions are, is there a way to recovery the windows partition? And how is the correct way to configure a dual boot system with Vista and Ubuntu 9.1 Server edition?

Thanks for all the help.

---

### Post by Mark Phelps on 2010-01-08
I'm guessing you can't boot into Vista, right?

I'm also guessing that's because you used the Ubuntu installer to shrink your Vista partition to make room for Ubuntu -- despite LOTS of posts advising folks specifically against doing that.

If you're talking about recoverying the use of Vista, since I'm also guessing you don't have a Vista installation DVD, you will need to go to the NeoSmart Technology forums, download one of their Vista repair CD images, burn that to CD, and boot from that repeatedly, performing Startup Repair each time.  Could take three boots to fix the boot loader corruption problems.

---

### Post by CaptConan on 2010-01-08
No I used the disc management tool inside vista to shrink it's own partition as noted here: [http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)
And I do have the Vista installation DVD. In fact, wanting to move forward I went ahead and just formatted the whole darn thing and reinstalled with Vista, however it seems my Driver disc is RMA so I put XPSP3 on it instead.

So now I'm back to the partitioner in Ubuntu 9.1 server. I'm having trouble finding a step by step guide to get this installed without once again, erasing my windows partition. Should I do guided or manual and then all the minute details? What file system should I use and how many partitions should I make? Again I'm really new at all this but I want to make a go of it. 

I have a 100GB NTFS partition for windows and the rest is available to Ubuntu now. (320 GB total drive space)

---

### Post by darkod on 2010-01-08
I'm not familiar with ubuntu server too much, but if it's similar to ubuntu, in your situation the guided mode might actually be better option.
You say you already shrunk vista. That would leave free unallocated space on your hdd.
In this case a guided option to install ubuntu into this unallocated space is better then manual partitioning if you're not familiar with it.
If vista was taking your whole hdd then the guided option might be problematic, or may not. But according to what you said, this is not your case.

---

### Post by oldfred on 2010-01-08
I  also like to have a NTFS partition for data to share between win & ubuntu. While you can read the windows install partition, sometimes windows is not happy with lots of writes/changes into its partition. Also I have read that it is good practice to have your windows data in a separate partition even if you are just running windows. I also share firefox and thunderbird profiles so I have the same data in both.

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

More dual boot examples, even if not exactly the same versions the processes are the same.
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by CaptConan on 2010-01-08
I got it running. I set a 100GB to / using ext3 and swap to 8GB (2x RAM) Grub recognized XP and it boots into windows fine.
I used manual mode in ubuntu partioning but made sure the NTFS partitions were untouched. 
I don't know why it didn't work with Vista but now works with XP. I think it had something to do with the way the disc came partitioned from the factory. After I formatted EVERYTHING and started from scratch there were no problems. Now I have my blinking curser... When do I start making money? :D

---

