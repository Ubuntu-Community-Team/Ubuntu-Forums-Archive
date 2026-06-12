---
title: "Dual Booting"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by FinalShot on 2010-03-01
I'm planning on dual booting Windows XP SP3 Pro with Ubuntu 9.10, I'm following this guide [here](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm), I'm wondering will it work with SP3 + 9.10?

Also has anyone installed Ubuntu 9.10 while using a Asus P5QPL-AM Mobo?

(Third time I've typed out this...)

---

### Post by Old_Grey_Wolf on 2010-03-01
Those are the instructions for installing 8.04. Try Googling on <quote>Ubuntu 9.10 install step-by-step</quote>. The 8.04 instructions are not that different from those for 9.10; however, you may be more comfortable with the installation instructions for the current version.

---

### Post by FinalShot on 2010-03-01
I found this [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml), 3 or so Screenshots down is the portioning. It doesn't look that different to me.

---

### Post by Old_Grey_Wolf on 2010-03-01
> **FinalShot said:**
> I found this [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml), 3 or so Screenshots down is the portioning. It doesn't look that different to me.

Like I said, the instructions for 8.04 versus 9.10 are not that different; however, I was thinking that you may be more comfortable using the 9.10 instructions if you have never installed before. I have now idea what your personal experience or comfort level is.

Enjoy Ubuntu 9.10.:D

---

### Post by FinalShot on 2010-03-01
I have **plenty** of computer experience ;) Just no to familiar with Linux.

---

### Post by FinalShot on 2010-03-01
I decided to try this first on a virtual pc first, good thing I did. Anyway I popped the 9.10 cd in, installed it inside windows, then restarted selected ubuntu from the boot list, then it just sits here forever.

[img]http://img192.imageshack.us/img192/9259/53342078.png[/img]

---

### Post by FinalShot on 2010-03-01
Anyone?

---

### Post by FinalShot on 2010-03-02
](*,):mad:

---

### Post by bcbc on 2010-03-02
As Old_Grey_Wolf's signature says. Try it on LiveCD (without any changes to your computer). This will tell you if it runs on your machine. Ensure all your hardware is supported especially wifi before trying dual boot.

---

### Post by FinalShot on 2010-03-02
It works fine Live, and I don't use wifi. I just want to know how to fix the fact that it doesn't go past 2 lines of text and a black screen.

---

### Post by bcbc on 2010-03-02
So... you installed XP in a virtual machine, and then installed ubuntu inside that virtual XP (i.e. using wubi)?

If you are using wubi you should know that there is a major bug that prevents grub2 from reading files on an ntfs partition beyond the first 4GB. You can replace the wubildr file to fix this.

Why don't you just install ubuntu on the virtual machine?

---

### Post by FinalShot on 2010-03-02
That was just a test, I plan to dual boot on my actual computer. Also about that bug with wubi. Replace the wubildr file with what? Also should I used wubi to install ubuntu, or just boot from the disc that way?

---

### Post by bcbc on 2010-03-02
> **FinalShot said:**
> That was just a test, I plan to dual boot on my actual computer. Also about that bug with wubi. Replace the wubildr file with what? Also should I used wubi to install ubuntu, or just boot from the disc that way?

Here's a [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") for the wubi issue with replacement wubildr.

wubi installs ubuntu inside a file on your windows ntfs drive that is seen by ubuntu as a separate harddrive/partition. It's limited in some ways - e.g. can't hibernate/suspend - and the performance is not as good as a regular install, plus you run some risk of ntfs corruption if you get stuck and do a hard shutdown. But it's ok if you just want to see how ubuntu works.

---

### Post by FinalShot on 2010-03-02
Ok thanks, but can I boot the disc and install it that way?

---

### Post by FinalShot on 2010-03-02
I tried Booting the cd and installing it that way. Anyway when I get to the partition editor this is what it looks like.

[http://img203.imageshack.us/img203/6249/27235959.png](http://img203.imageshack.us/img203/6249/27235959.png)

And if I go to the manual editor looks like this.

[http://img155.imageshack.us/img155/9118/84247191.png](http://img155.imageshack.us/img155/9118/84247191.png)

How can I just install ubuntu without overwriting xp.

---

### Post by FinalShot on 2010-03-02
:(

---

### Post by MatadorMac on 2010-03-02
Not perhaps a direct reply to the situation but this is my experience doing similar.

I have a Windows XP SP3 machine with several hard drives, USB, Firewire and internal.  I tried wubi and Ubuntu and liked it until the broken dual boot upon linux update issue frustrated the heck out of me.

I downloaded the karmic Ubuntu ISO for 32 bit system and burnt a CD.  Loaded the CD, restarted and then followed the screen prompts to partition an internal hard drive I had set aside for this use leaving my Windows XP hard drive strictly alone.

Now when fresh starting my PC, the GRUB loader loads and I make my choice between UBUNTU and XP.  I have been through several Ubuntu automatic updates and no problems.  The only problem I have is not with dual booting but with the occasional Ubuntu update overwriting or otherwise destroying my ATI proprietary driver installation for my Radeo 2600 card.  Then I have to uninstall and reinstall the driver and until I discovered that the color profiling software I also installed was somehow preventing me successfully uninstalling or modifying the munched ATI driver setting file I was one frustrated Linux enthusiast.

I will say, that since doing away with WUBI and going the full dual boot/Ubuntu install I am one tremendously happy camper.  I have moved ALL my computing to the Ubuntu side of my Dr. Jekyll and Mr. Hyde PC.:D

Regards

MatadorMac
Alcalde, New Mexico

---

### Post by bcbc on 2010-03-02
So, are you installing linux in a virtual machine? It says you have a 16GB drive so I assume that's not your actual drive?
Try and list exactly what you are trying to do.

If you were doing a real install, you would want to manually partition your drive - shrink the main XP partition - and then install ubuntu onto that. But in a virtual machine this is unnecessary.

I did a quick search on using virtual box - this walkthrough looks good: [http://www.youtube.com/watch?v=n5ravk1H6DM]("http://www.youtube.com/watch?v=n5ravk1H6DM")

---

### Post by MatadorMac on 2010-03-02
> **bcbc said:**
> So, are you installing linux in a virtual machine? It says you have a 16GB drive so I assume that's not your actual drive?
Try and list exactly what you are trying to do.

If you were doing a real install, you would want to manually partition your drive - shrink the main XP partition - and then install ubuntu onto that. But in a virtual machine this is unnecessary.

I did a quick search on using virtual box - this walkthrough looks good: [http://www.youtube.com/watch?v=n5ravk1H6DM](http://www.youtube.com/watch?v=n5ravk1H6DM)

Hi.  I don't think what I did is a virtual machine.  I actually dedicated one whole internal hard drive, partitioned it into two and installed Ubuntu onto one partition and use the other for extended storage.  My XP installation resides on what is called my "Main Drive" which is a completely separate internal drive.

MatadorMac

---

### Post by bcbc on 2010-03-02
Actually I was replying to FinalShot :)

---

### Post by gordie69 on 2010-03-02
I'm running dual boot with W7 and ubuntu 9 and my system runs nice I really the u9 starts up quick and shuts down quicker then windows 
But I'm running it on a p4 2.4 with 2 gig dual channel memory and I love it.

---

