---
title: "Complicated Raid 0 Boot issue!"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by Jonnypowa on 2013-02-20
First, can I say I am not very good with tech.

So I'm trying to install ubuntu on a dual boot. I have a gaming laptop that has raid 0 with two 500gb hard drives, making it 1tb. I have two drives in windows - My first drive, OS Install, and my second drive, Random Stuff. So I go and make a new partition, cutting about 97gb off my hard drive random stuff. This 97gb is now unallocated space. (I just want to add that OS Install by default is 555gb in space, and Random Stuff was about 370gb in space, but 100gb was cut off for the partition). So I boot from a 12.04 LTS live cd, and go to GParted. But somethings wrong. It only notices OS Install as a used hard drive. The second drive, Random Stuff (270gb), and the newly made unallocated space (100gb) together, is all noticed as 370gb of unallocated space. The thing is though, I have a lot of data stored on the second drive Random Stuff, and I do not want to lose it. Even before I shrunk Random Stuff to 270gb in windows, it still noticed those 370gb of data as unallocated space. How do I make ubuntu notice the drive as allocated space and 97gb as unallocated space? I probably didn't explain it well so I will post screenshots. Thanks for the help!

EDIT: If its needed, my specs are:

Radeon 5870m
i5 480m
8gb ram
2x500gb(ish) Raid 0

---

### Post by dino99 on 2013-02-20
the rule is : create the raid0 after having made the changes with the hdds (formatting/installing, ....)

[http://www.petur.eu/blog/?p=480](http://www.petur.eu/blog/?p=480)
[http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration](http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration)

---

### Post by Jonnypowa on 2013-02-20
> **dino99 said:**
> the rule is : create the raid0 after having made the changes with the hdds (formatting/installing, ....)

[http://www.petur.eu/blog/?p=480](http://www.petur.eu/blog/?p=480)
[http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration](http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration)

Heres the issue - I bought the laptop with raid 0. The laptop specs by default have it.

---

### Post by darkod on 2013-02-20
First, OS_Drive and Random Stuff are only partitions. Don't call them drives because it creates confusion. Yes, I know MS calls them drives but that was very poor choice of wording and now most people call them drives making confusion with physical disk drives. :)

Second, and VERY IMPORTANT: As you can see on your first image, the disk 0 (the only disk, in other words the raid array), is Dynamic. That is MS proprietary format and linux doesn't work with it.

It either came like that, or windows converted it from basic to dynamic if you tried to make a fifth partition on msdos disk. It can have only 4 primary partitions.

Bottom line, if you want to, you can try converting it back to Basic disk. The EaseUS Partition Manager (or what ever it's called exactly), should be able to do it without loss of data. But just in case, MAKE A FULL BACKUP OF EVERYTHING IMPORTANT FIRST!!!!
Just because someone used it and it worked, it doesn't mean it can't fail in your case.

Also, I think in order to work, you will need to have maximum of 4 partitions, which you do right now. So even if it works, you will have to delete one, for example the restore partition. The restore software should have option to create a set of recovery DVDs and you don't need that partition after that. You can use the disks if you ever want factory restore.

DO NOT continue trying to install ubuntu on dynamic disk!

---

