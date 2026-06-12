---
title: "Getting A New SSD, Confused About Settings."
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by amira-uk on 2012-06-11
I've got a Samsung 128GB 830 series arriving this week and I've been looking into whether there are any special settings I need and I've found lots of information, however seen as I've messed things up before using info I've googled I thought I better just check.

I found an article relating to 11.04 that mentions these settings:

[LIST=1]
[*]Enable TRIM
[*]Disable access timestamp on files
[*]Adjust disk scheduler
[*]Moving log files to RAM drive
[/LIST]
1. I am installing Kubuntu 12.04, is there a graphical tool for enabling TRIM or will I have to figure out fstab?


2 and 3. Do I actually need to change the timestamp and disk scheduler settings or is that just a personal choice.


4. The article talks about prolonging drive life by not writing logs to it. I have no idea what normally happens with logs as I have never used them but would it be possible to have the logs writing on to my current hard drive (which will be my secondary drive) which is where my home directory will be.


Here is the article I took this info from [http://www.bitsbythepound.com/using-a-solid-state-drive-ssd-with-ubuntu-11-04-409.html](http://www.bitsbythepound.com/using-a-solid-state-drive-ssd-with-ubuntu-11-04-409.html)


Also I'll need to do the equivalent things in Vista, I haven't googled that yet but if anyone already knows a good link for that I'd appreciate it.


I won't have the drive and installation done until later in the week so if any of the information I need to do this is system specific I'll have to post it later this week.


Thanks for the help, sorry for the long post, wanted to make sure I've explained myself.

---

### Post by SlugSlug on 2012-06-11
Most 'guides' are refering to the older SSD's where limited writes was an issue.

This is not the case with newer SSD'd (some out last HDD's)

The only things you really need to do is enable trim (via fstab)
mine looks like:
```
UUID=bbec8d88-3790-4bff-b02f-92f32ffd8702 /               ext4    discard,errors=remount-ro 0       1
```and set your partition up [http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance) 


Also enable AHCI mode in BIOS


I didn't touch disk scheduler as I use mixed type drives (HDD+SSD)

---

