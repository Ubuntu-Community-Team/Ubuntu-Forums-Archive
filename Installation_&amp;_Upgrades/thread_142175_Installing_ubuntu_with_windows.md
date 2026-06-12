---
title: "Installing ubuntu with windows"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by Morik! on 2006-03-09
Im a windows user ( dont bite me plz ) and have been exploring linux recently. I would like to somehow get both os on my laptop. I was thinking of partitioning my HD. I currently have xp pro, and heard that i could have problems installing ubuntu. I was thinking of reformatting my whole HD and then installing both os using the following method:

ubuntu to partition drive, making windows partition come first. 
exit without finishing the installation. then install windows onto that first partition only. use ntfs. then go back to ubuntu and install on the second partition. itll ask if you want it to boot windows as well, choose yes. 
it will ask you if you want it to handle booting your system, say yes


I was wondering if there is any other way to install ubuntu, even though i already have xp pro installed.

---

### Post by andlinux21 on 2006-03-09
dont quote me but I think you can do a disk defrag and then try install ubuntu on the free space of your hard drive if you can set up the linux partitions then you should have no problem with the install.

---

### Post by Princey on 2006-03-09
I'd first try running Linux from a live CD to see if your hardware is fully compatible. If it is, then you can install linux (ubuntu) in that case, chosing as andlinux21 said. That's how I had linux on my first machine. Both it and Windows XP Pro shared the same drive. Since then, I've bought a new pc and  installed linux on a drive by itseelf.

---

### Post by Morik! on 2006-03-09
So i could just defrag my HD, and use the partitioning tool in the linux install right away?

---

### Post by Princey on 2006-03-09
Sure.

---

### Post by stuporglue on 2006-03-09
Yes but back up first. Any time you partition or resize partitions, you risk data loss. 

I've only personally seen it happen once, but it broke his Windows, and he lost all his Windows data.

My recomendation: 

1) Delete useless stuff
2) Backup important stuff
3) Defrag

It's worked fine for me several times, you shouldn't have any problems.

---

### Post by maple on 2006-03-09
No, I dont think defragging will help. Unless there is some new resizing of NTFS partitions during install that I'm not aware of (which is possible). When you tell Ubuntu to use the free space it won't see any. It means unused and **unpartitioned** space. The easiest solution is to just reinstall Windows but tell it to only use a portion of the drive.

So if the drive is 20GB, tell windows to create a partition and use 10GB. Then once your done installing Windows (complete the installation) you can boot the Ubuntu Install CD and **then** tell it to use the free space, or just create your own partitions if your a bit more brave.

Hope this helps.

-maple

---

### Post by Morik! on 2006-03-10
using maples method, i would still have to reformat my drive. Or just reinstall windows?

---

### Post by noswal on 2006-03-10
I found this link usefull when installing on my desktop, which (still) has loss98
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by Coelocanth on 2006-03-10
[QUOTE=maple]No, I dont think defragging will help. Unless there is some new resizing of NTFS partitions during install that I'm not aware of (which is possible). When you tell Ubuntu to use the free space it won't see any. It means unused and **unpartitioned** space. The easiest solution is to just reinstall Windows but tell it to only use a portion of the drive.[/quote]

It should help. It will put all your files together closer to the 'front' of the partition. You can then use the Ubuntu install CD to resize the NTFS partition and reformat the freed space to install Ubuntu. This is what I did when I installed a dual boot with Win XP. I used the Ubuntu install CD to resize my Windows partition (it was one big 250 GB partition on the drive), reformatted a large chunk for the Linux OS and also made a FAT32 partition to share files between the two OSes.

Someone provided a link to Herman's dual-boot guide. I highly recommend it, as that's what I used to get up and running without re-installing Windows.

---

### Post by Morik! on 2006-03-11
awesome, im gonna look at that tutorial and try it out.

---

### Post by Morik! on 2006-03-11
ok i am at the installation screen of ubuntu.
It asks for full name of new user, then username for the account, then password. After I put in my password the installation seems like its loading...the pops right back asking for full name of new user. its a loop!

buggy installation? is there anyway to bypass this? 

im gonna keep it there on that page of installation because i already partitioned my hd and everything and dont want to mess anything up.

---

### Post by Liolikas on 2006-03-11
[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by munga_bill on 2006-03-11
Hey, Morik!, are you using the number keys over on your right-hand keypad for any numbers that might be in your password by any chance?
Because if you do, then you need to make sure your numlock light is on (press numlock key). Or just use your upper row of number keys above all your alphabetical ones on your keyboard instead.
That is one cause of the symptoms you are describing, and  it's easy to fix!
I hope that fixes your problem, Regards, munga_bill

---

### Post by Morik! on 2006-03-11
i aborted the installer and retried, and it worked the second time. Must have been a misread or something. Thx for all your help everyone. (now i just gotta find out how to manipulate linux, since i have been using windows all my life)

---

