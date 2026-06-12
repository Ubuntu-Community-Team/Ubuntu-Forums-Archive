---
title: "Too many primary partitions on new HP laptop?? Please help!"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by Elaphe on 2011-09-03
Hello everyone!

I have searched on my own for a solution to this problem, but I'm still not sure what to do, so I'm appealing to the Ubuntu community for help. Thank you in advance for your consideration!

I have just received my new HP ProBook 4430s, from newegg, of course, however I can not seem to create a partition to install Ubuntu. After some searching, I have discovered that my "problem" is that HP has kindly used all four allowable primary partitions on the drive, and I'm not sure how to proceed. Personally, I'd like nothing more than to wipe the drive clean, and install only Ubuntu. However, I purchased this laptop with Windows pre-installed (sigh) because I am a student once again, and there are a couple of school related things that I _must_ have Windows for (sigh again!). Therefore, I'd like to keep my Windows partitions intact and functional, and one way or another I must, for the sake of sanity, install my beloved Ubuntu on this machine as well.

At this point, I'm considering two options, but I'd appreciate other suggestions as well. I'm considering deleting one of the small, HP specific partitions on the drive, but I'm concerned I may lose some functionality I may want/need in the future, such as the ability to reinstall windows from the recovery partition. Although other posts talked of deleting these partitions, no one made any mention of what they might contain. Mine are marked HP Recovery, which seems obvious enough, and HP Tools, which seems a little more vague to me. Does anyone have a better idea of exactly what is in the HP Tools partition, and what I lose if I delete it?

And my second consideration is that I am a student once again, and I *believe* I can purchase a copy of Windows 7 Pro at a significant discount. I am considering buying a full copy, and then doing a complete reinstall of Windows, thereby eliminating a lot of the so-called "bloatware" (which I must note is at a minimum on this new HP), and allowing me the opportunity to setup the partition table on a clean disc.

Could anyone offer me any other routes to follow? Please keep in mind, this is a new HP ProBook 4430s laptop, it came with no discs of any kind, but it has Windows 7 pre-installed. I MUST have both Windows for school, and Ubuntu for my sanity. I've posted a copy of my partition table via the Windows partition tool; should you need additional system information to help me, please just say so and I will reply right away.

Thank you again for your time and help!

-Elaphe

---

### Post by soumyabratapaul on 2011-09-03
Burn an image of Ubuntu in a disc or make a bootable USB. Then boot into the disc/USB, and then, when promted to use the Live CD or Install, choose the one, that says, Install. There you select, to use 50-50 of your HDD, which is selected by default. And you are done. Enjoy Ubuntu!

---

### Post by coffeecat on 2011-09-03
> **soumyabratapaul said:**
> when promted to use the Live CD or Install, choose the one, that says, Install. There you select, to use 50-50 of your HDD, which is selected by default. And you are done.

Please read the OP again. There are four primary partitions which is why this will not work.

@Elaphe, strange how the same problem comes in batches. :) Have a look at this thread from only earlier today.

[http://ubuntuforums.org/showthread.php?t=1838286](http://ubuntuforums.org/showthread.php?t=1838286)

And look at the post I link to in post #3 there. The thread and my linked post should answer all your questions, but post back if you need any more help.

---

### Post by MARP1961 on 2011-09-04
Do you really need the 'HP Tools' partition? Are these 'tools' vital? You could also use the 'Recovery Partition' as long as you burn recovery CDs first. If you have correctly burnt recovery disks, these should work when needed, making the recovery partition redundant too.

Obviously if you intend buying a Windows retail disk then you can start from scratch, repartition your hard drive and have a fresh Windows and Ubuntu with no 'bloatware'.

I presume redoing your partitions will invalidate any new computer guarantee? Check carefully before you proceed.

---

### Post by Elaphe on 2011-09-05
Hi guys!

Thank you so much for your replies, and I'm sorry I couldn't reply to them sooner!

I haven't made any changes to the system yet, but I have learned a few new things. Obviously, I could buy a new Windows disc and start from scratch, but my idea of exploiting my student discount on MS software will not work for me after all. I called MS and apparently the student discount applies ONLY to a downloaded, upgrade version of Windows 7 Pro. This means that I can not start the install from a freshly partitioned hard drive without a Windows OS. I would need to have a previous version of Windows installed to both start the Windows download/install process, and to verify that I have a legit copy of Windows to "unlock" the upgrade install. I would have been willing to pay for the student price of Windows, but I am not willing to pay full price just to get a disc with a full install of Windows 7.

So I called HP, and asked them what was in the HP Tools partition, and what, if anything, they could suggest I do to free up a primary partition. First, she told me that everything that's in the HP Tools partition is available for download from the HP website, however, she was not clear about whether this is a free download or not. But she also told me that they would be happy to send me install discs! She said they could send me one disc that has the OS, and one that has the drivers. With these disc, I *should* be able to reinstall Windows on a clean hard drive. The discs should have everything that is in both the HP Tools partition and the Recovery partition, which means I should be able to get rid of both partitions. I was told I should have the discs in just a few business days, and the discs, and shipping, were totally free.... And if it's free, it's for me ;-) But seriously, this sounds like just what I need, and so now I'm anxiously awaiting these discs :-) We'll see when they get here if I can really boot from the install disc.

Now, I have read lots of similar posts, including the one linked above by cofeecat, and I think it's clear that most people in my position delete the HP Tools partition, and most seem to not miss it much. I just felt like I just bought this machine, and I wasn't in a big hurry to go deleting things when I don't even know what they contain. But, it does seem like if I had to pick one to go today, I'd lose that HP Tools partition. Personally, I'm going to wait for my discs and see what they offer before I make any drastic changes to the system.

To coffeecat: I see you have deleted your HP Tools partition. Do you miss it? Did you lose anything you couldn't live without? Thanks!

To MARP1961: I'm not sure if anything I'm thinking of would void my warranty or not. I'm personally not concerned about that, but it's a great point, and maybe something others should consider. Thanks!

Thanks so much to everyone who has taken their time to try and help me! I very much appreciate it!

-Elaphe

---

### Post by coffeecat on 2011-09-05
> **Elaphe said:**
> 
To coffeecat: I see you have deleted your HP Tools partition. Do you miss it? Did you lose anything you couldn't live without? Thanks!

No. I backed up what was on it in the unlikely event of ever needing them before I deleted it. But I think you missed an important point from the threads I linked. Use the HP Utility from within Windows to create a set of restore DVDs. These duplicate the function of the recovery partition and can be used to restore the machine to its factory condition. You don't need a Microsoft Windows 7 install DVD and you didn't need to approach HP for a set of discs. Although it's good to hear that HP are prepared to supply them free. Other manufacturers tend to make a charge for this.

Also - while Windows 7 is still working. Make yourself a Windows 7 repair CD. This is not the same as an installation DVD or restore DVD, but includes some useful repair utilities that you may need one day. Some people find they need it only **after** they have made Windows unbootable. Here's a link describing how to make a repair CD for which you need Windows and Silverlight, unfortunately.

[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

---

### Post by Elaphe on 2011-09-05
coffecat, thank you so much for your input!

The only reason I'm not making my own recovery discs is because HP is sending them to me, and I'm too lazy to go get get some blank discs ;-)

As far as the Windows repair CD, I would not have known about that, so I really appreciate the tip! It's been a long, long time since I've had to mess with Windows, and I'm not at all familiar with its intricacies. Shoot, now it looks like I have to go get some blank discs after all...

Thanks again for your help, I really appreciate it!

-Elaphe

---

### Post by coffeecat on 2011-09-05
> **Elaphe said:**
> Shoot, now it looks like I have to go get some blank discs after all...

Well, at least you will only need one CD-R or CD-RW! :) The Windows 7 repair disc is only about 100MB, and there's only one. Whereas when I made my set of HP recovery DVDs (from my HP Mini netbook) I had to use DVD-RWs (obviously!), and each one weighs in at between 3.2GB and 4.1GB.

---

### Post by Elaphe on 2011-09-05
Yeah, and at this point I might as well get a few of each (CD's and DVD's), this way I can make additional copies of all of the backup media, since I'm sure to lose one set of discs if that's all I had. Thanks again for your help!

-Elaphe

---

### Post by Mark Phelps on 2011-09-05
If you have a version of Win7 that is working well for you, and you later want to restore it ... save yourself the trouble of having to reinstall everything from scratch by making your own image backup which you can then later restore and get what you have right now ...

That means that if you follow my suggestions, you can safely remove the Recovery partition and STILL have a way of restoring Win7 later, should you need to.

So, the way to do this is as follows:
1) Download and install the FREE version of Macrium Reflect (MR) in Win7
2) Use the MR option to create a Linux Boot Cd
3) Use MR to image off your Win7 setup to an external drive or to DVDs (a drive, or large enough USB stick, would be better).

Boot from the MR Linux Boot CD and confirm that the Restore operation can see the saved image files  -- by connecting the external drive or USB stick, or inserting the proper DVD -- but do NOT actually run the Restore.

However -- and this is important -- if you decide that removing your Recovery partition does not give you enough room for Ubuntu, then BEFORE you do the MR imaging, use the Win7 Disk Utility function to shrink the Win7 OS to make more room. And then, reboot into Win7 a couple of times to allow its filesystem to make the necessary adjustments.  Only THEN, make the image backup using MR.

---

