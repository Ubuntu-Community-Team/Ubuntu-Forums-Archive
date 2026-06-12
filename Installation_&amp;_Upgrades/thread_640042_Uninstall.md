---
title: "Uninstall?"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by Browntown_01 on 2007-12-13
Hi I would really appreciate any help I can get here. Is it possible to un-install ubuntu 7.04 and re partion my drive so that the xp partion has the full HD again? I like ubuntu but I want to give my laptop with xp all the HD (still using ubuntu on the desktop though!) I would really love any help here! thanks!

---

### Post by ectospasm on 2007-12-13
Unfortunately I don't think a Free/Open Source solution to your problem exists.  Basically you're asking to remove the Ubuntu partition, expand the XP partition to take over the free space, and resize the XP filesystem to recognize the new space.  The only tool I can think of that will do that is Partition Magic, and I'm not 100% that it's even possible with that. 

I suggest backing everything up and then reinstalling XP from scratch, just to be sure.

---

### Post by Browntown_01 on 2007-12-13
Ok well thank you for your help!

---

### Post by maharbA on 2007-12-13
try using gparted on the Ubuntu live cd.

---

### Post by Browntown_01 on 2007-12-14
I actually tried that but gparted will only let me delete the ubuntu partion I cannot resize the windows partion. Unless I am doing something wrong?

---

### Post by Herman on 2007-12-14
I don't know what you are doing wrong, but Linux partitioners like GParted and other 'Parted based partitioners have been able to resize FAT32 and NTFS fie system partitions okay for years now.
 If it's an NTFS partition maybe it would be a good idea to run CHKDSK on it first though and defrag and then give it a test boot up  to make sure, 

Windows can make itself unbootable for some weird reasons. Last weekend I had a Windows computer that I was fixing  for someone. It couldn't be defragged because the operating system was too full. All it needed was a little partition resizing with [GParted -- LiveCD]("http://gparted.sourceforge.net/"). It should have only been a five minute job. 
It rebooted fine the first time after the resizing, and ran CHKDSK automatically, like it's supposed to after resizing. Then I defragged it and become unbootable after defragging with a lovely blue screen and a STOP error 'INACCESSIBLE_BOOT_DEVICE'. It seemd like window's own defrag utility killed it.   It took me all weekend to track the problem down. It could still boot, but only in safe mode. It turned out to be caused by (some certain other well known brand of software commonly associated with Windows) having a 'video compatibility' problem, (go figure! , what would that have to do with defragging? I guess the problem was there all along maybe, and when the drive was defragged enough to start working properly  it also worked well enough for the problem to show up?). 

Anyhow, here is the link to the GParted LiveCD docs on resizing, those should help you. [Resizing partitions with GParted]("http://gparted.sourceforge.net/larry/resize/resizing.htm"). I hope you have better luck with Windows than I do. Obviously you like it for some reason. :)

Don't forget to re-install your Windows boot loader's IPL in your hard disk's MBR before you delete your Ubuntu partition because you'll be deleting GRUB in the Ubuntu partition and unless you have another way to boot, such as [Super Grub Disk]("http://sgd.benjamin-butschko.de/"), you'll be unable to reboot. You can also use a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") from a Windows Installation CD to run FIXMBR and reboot.

Regards, Herman :)

---

### Post by mikewhatever on 2007-12-14
> **Browntown_01 said:**
> I actually tried that but gparted will only let me delete the ubuntu partion I cannot resize the windows partion. Unless I am doing something wrong?
Well, perhaps you just do not have any unallocated space to resize. Once Ubuntu partition is deleted that should be solved.

---

### Post by Browntown_01 on 2007-12-14
Thanks alot to both of you for the quick response! I really appreciate the help, and to Herman, I enjoy ubuntu as well but I have it on my desktop at home (bigger HDD) and now I am away at school with a laptop and I quickly realized I needed all the space I could find and some windows based programs. But thank you!

---

### Post by Herman on 2007-12-15
Well okay then, but let's hope Windows doesn't let you down and come down with a virus or anything like that. Browser hijacks are rampant in Windows at the moment. 
Just make sure you take your Ubuntu Live CD with you then, in case you need it for an emergency.  :)

Regards, Herman :)

---

### Post by Browntown_01 on 2007-12-15
Yeah haha, thanks!! I will keep it handy for sure

---

