---
title: "Newbie with two partitions on Windows hard rive needs help!"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by Tamihania on 2006-03-24
I am sorry for my English and for being so new to Linux :oops:  ...

two weeks ago I decided to move from Windows after 10 years of using it - JUST USING! I feel like new to computers , too - but I try to learn!:) 
I've read so far a lot on different forums - tried out LiveCD of Ubuntu, PCLinuxOS and Kanotix - and decided to install Ubuntu for dual-boot of Linux and Windows - I am too silly to use only Linux yet!  - I have the Installation CD now - and read (also made notes) Installation HowTo'es.
Still I have the questions - because my Windows XP hard drive has two partitions:

1) BACKUP Primary FAT32 4GB        1,70GB Freespace (hidden)
2) HDD C   Primary NTFS  23,92GB   12,48GB Freespace (active).

So - my questions are: 
1) how am I to configure the partitioning - I want, of course, to resize NTFS partition to get as much space as possible for learning Ubuntu Linux :D - (I tried Qtparted from Kanotix LiveCD to resize it - but it did not work...) - what steps should I take?
2) what am I to do with BACKUP partition? (It is (was?) needed for the "communication" with my external hard drive...)

I would be very grateful  for any ideas and help - just, please, be patient with me [-o<  - I DO NOT KNOW ANY computer jargon...:(

My computer is laptop:

Packard Bell
Mobile AMD Athlon 
2400+
662 Mhz, 224 MB RAM

I am looking forward for your replies...'cause I cannot wait to install Ubuntu! :) 

BIG THANKS in advance,

Tami

PS. Of course - it should be - 'hard drive' in the title....sorry! I am also dyslexic...

---

### Post by xenmax on 2006-03-24
IMO re-sizing a partition is pretty risky and should not be tried without backing up data first!

---

### Post by Tamihania on 2006-03-24
[QUOTE=xenmax]IMO re-sizing a partition is pretty risky and should not be tried without backing up data first![/QUOTE]

Thank you very much for the quick reply! :D and for your warning...

I made a back up on my external drive two days ago - made "cleaning up", and defragmantation already, too :)

...I am ready to go forward I suppose - just have those doubts I mentioned about... but - even if Windows will "die" accidentally by my stupidity:oops:  - I decided to try Ubuntu anyway \\:D/ ...

Wishing you nice weekend - and looking forward for another advices-answers to my questions,

Tami :)

---

### Post by RRS on 2006-03-24
I found [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") to be quite complete and easy to follow.

The partition manager on the Ubuntu install disc will recognise your existing partitions and offer a manual setup option to resize during the installation proccess.

I believe the site covers this procedure in the "Fat32" section but I'd recommend reading thru all the options and directions provided first.

I also found the authers instructions quit helpfull in undoing mistakes I made during unninstall/reinstall.(had problems with X in 64bit, changed to 32)

Welcome, and have fun :)

---

### Post by xenmax on 2006-03-24
Good luck with your installation and Welcome aboard!!

---

### Post by Tamihania on 2006-03-24
[QUOTE=RRS]I found [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") to be quite complete and easy to follow.

The partition manager on the Ubuntu install disc will recognise your existing partitions and offer a manual setup option to resize during the installation proccess.

I believe the site covers this procedure in the "Fat32" section but I'd recommend reading thru all the options and directions provided first.

I also found the authers instructions quit helpfull in undoing mistakes I made during unninstall/reinstall.(had problems with X in 64bit, changed to 32)

Welcome, and have fun :)[/QUOTE]

Thank you extremely much for valuable links RSS :) (I've read only the part related to NTFS installation before...)

...and thank you and xenmax for good luck wishes - I will start installation just after reading instructions thoroughly!

Nice weekend to you all, Good People :D 

Tami

PS. This is the most friendly place I've ever met on the net! BIG THANK YOU! (I just hope I could be of any help for you in the future...ufff)

---

### Post by captainjiz2000 on 2006-03-24
if you want to completely anihilate windows and install linux afresh while still having that extra space that is partitioned on your hard drive. copy the data you want to keep to your external device and install the linux os either on an external device and if your computer is relatively new you could boot from an external device. use this option if you want to keep windows and if you don't just format the hard drive with the linux option that it gives you when it gets to that step it will also allow you to manually reconfigure it to change partitions, delete them, add them together, rename them, resize them, format them, and i think even defrag them....its relatively easy to do if you know any of the very low level computer jargon that goes on in everyday language such as format, partition, hard drive, NTFS, and Fat32. If this does not work out email me at [email]captainjiz2000@yahoo.com[/email] with a headliner that tells me i have talked to you on the ubuntu forums and i will try my best to help you out. Laterz

---

