---
title: "help with dual boot"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by latenightrob on 2010-01-13
HI there, newbi to Ubuntu and I have a question.  I bought a new computer (laptop HP DV6-1375dx) and I want to set a dual boot with win7, like I did with my desktop (clean install) 
However, my question is, with the new laptop all I have is the rescue disks vs. having the single OEM version.   IS that a problem?  for the desktop I followed lifehackers article "Dual boot win7 and ubuntu in perfect harmony."  no problems at all.

what I am afraid of is formatting the new hard drive and the recovery partition and not being able to use the disks for some reason....am I over-reacting?

Thanks for reading.

rob

---

### Post by darkod on 2010-01-13
This is what I would do:
Read your manual. The restore discs and recovery partitions these days might work in two ways generally. Number 1 is the restore disc deletes your whole hdd and then recovers win7 image as the factory default was. In this case, if you ever need to restore win7, it would destroy not only ubuntu present on the hdd, but also all your data on any windows partitions you might have. Number 2 is that the restore disc will just recover win7 from an image to any partition you want it to. But this option is not very common.

If your rescue discs delete your whole drive, I consider them completely useless. The same goes for a recovery partition. As a much better alternative, read about a function in win7 called Backup & Restore. In short, it creates image of your current win7, and you don't even need to save this image to DVDs (it may take a number of DVDs depending on size). You could save the image as single file on external hdd, and just create startup cd/dvd with the same Backup & Restore tool.

If I understand this function correctly, in future you could use the existing ntfs partition (or even create a new blank one), boot with the startup cd created and use the image from the external drive to restore your win7 as it was at time of backup. Much better than having your hdd erased by the rescue discs supplied.

After you've figured out how you want to proceed, having a dual boot of win7 and ubuntu is not an issue at all.

---

### Post by garvinrick4 on 2010-01-13
First of all you could not burn a set of 3 DVD's for your OS of 7?

If you boot off of a Live Ubuntu cd and install it is going to ask you how much room do you
want for Linux as long as you let it do its thing and do not press manual.
gparted will show you what it is going to do to your drive and you can accept or quit.
Anyway the manual install is the real trouble if you are new. Just stay focused on what you
are doing. Nothing is a quarantee but gparted partitioning program Ubuntu uses is pretty darn good.  Windows 7 has three of the primary partions already, System, OS, recovery (they call it Vista or Linux reads it as Vista but it is recovery). It will make an Extended partition and put
Ubuntu and swap inside of the primary extended. You can even put more Linux OS's inside that extended partition in future. Reading material Link below.


[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by latenightrob on 2010-01-13
Darko, Interesting, I just scanned through the manual and it doesn't say which of the two ways the recovery disks will perform, (erase all hd or not), but I did think of another question, I updated my step-daughters laptop with win7 64 bit version (upgrade via that student offer) Can't I just use her copy of win7 to install but use my license #?
Thanks for the help
Rob

---

### Post by latenightrob on 2010-01-13
garvinrick-  "First of all you could not burn a set of 3 DVD's for your OS of 7?"
I did that and have the disks, I was/am just worried since it is a rescue and supposed to restore to factory settings that I would mess that up by changing around the hd (space wise) and have the disks not work, b/c it is not exactly factory settings....you know what I mean?

---

### Post by SteveHillier on 2010-01-13
> **latenightrob said:**
> Can't I just use her copy of win7 to install but use my license #?

You may be able to and again you may not be able to.
I haven't tried with Win 7 but under XP the installer can detect difference between Home & Professional product keys and can detect upgrade v OEM v retail versions.
I suspect MS may have got this one covered so I would err on the 'won't work' rather than the 'will work'

---

### Post by darkod on 2010-01-13
> **latenightrob said:**
> Darko, Interesting, I just scanned through the manual and it doesn't say which of the two ways the recovery disks will perform, (erase all hd or not), but I did think of another question, I updated my step-daughters laptop with win7 64 bit version (upgrade via that student offer) Can't I just use her copy of win7 to install but use my license #?
Thanks for the help
Rob

Yeah, that's also an issue these days, lack of information. If you go the Backup&Restore route, you don't really care what your dvds and recovery partition do. And by deleting the partition you would also free space on your hdd.
I would google for the "windows 7 backup & restore" and read some tutorial. If the tutorial says you can use startup cd + image to recover win7 on any partition you create, great. And I think it would.

You can literary wipe the drive with Gparted for example, create primary ntfs partition with size you want dedicated for win7, restore win7 with the above process. Then if you want second ntfs partition, possibly to share data, create it too.
Then just use ubuntu installer and Use Largest Available free space option, or create partitions manually, anyway you want. Job done.

---

### Post by darkod on 2010-01-13
PS. Look at the option on the left.
Create image backup.
Create system recovery disc.

I guess this is all you need but I don't know for 100% sure. You'll have to dig around. :)

---

### Post by presence1960 on 2010-01-13
> **latenightrob said:**
> Darko, Interesting, I just scanned through the manual and it doesn't say which of the two ways the recovery disks will perform, (erase all hd or not), but I did think of another question, I updated my step-daughters laptop with win7 64 bit version (upgrade via that student offer) Can't I just use her copy of win7 to install but use my license #?
Thanks for the help
Rob

Yes you could as long as your 7 editions are the same. If she has 7 Ultimate then you can use it to install Ultimate only. If you have a different version of 7 when you enter your product key it will be rejected.

---

### Post by latenightrob on 2010-01-13
I am going to try the win7 (that I got for the step-daughter) first and if that doesn't work then I will restore back with the restore disks and go from there, I will post an update....

ps we do have the same versions of win7

---

### Post by darkod on 2010-01-13
> **latenightrob said:**
> I am going to try the win7 (that I got for the step-daughter) first and if that doesn't work then I will restore back with the restore disks and go from there, I will post an update....

ps we do have the same versions of win7

Give it a shot but the difference is that it's an upgrade version. Like mentioned already, it might prevent you from clean install, it might only offer upgrade.

---

### Post by latenightrob on 2010-01-15
update, I was successful using the upgrade copy on win7.  though I had to call into microsoft  to get the key to work.  I thought it was going to tell me I wasn't allowed to use the upgrade version for a clean install, but instead had me call an automatic system and that was all.  

to set up my dual boot I used the "dual boot with perfect harmony" article from lifehacker.com with no problems.

thanks for all the help

---

### Post by SteveHillier on 2010-01-15
> **darkod said:**
> Give it a shot but the difference is that it's an upgrade version. Like mentioned already, it might prevent you from clean install, it might only offer upgrade.

I haven't run an upgrade since the early days of XP.  What you could do then is install to a brand new clean machine and part way through the install it would ask for you to insert the system disk of the version you were upgrading from.

---

### Post by mySpaceTimFrentz on 2010-01-26
Here is my errors-
 
I put CD in and reboot and get this:
 
[SIZE=2]no suitable page frame found
Primary not ULtraDMA
no disk to use XDMA not loaded
 
What does this mean? What am I suppose to do?
 
It has me confused because I see no similar errors being listed on support threads.
 
thanks you,
 
Tim
[/SIZE]

---

### Post by presence1960 on 2010-01-26
> **mySpaceTimFrentz said:**
> Here is my errors-
 
I put CD in and reboot and get this:
 
[SIZE=2]no suitable page frame found
Primary not ULtraDMA
no disk to use XDMA not loaded
 
What does this mean? What am I suppose to do?
 
It has me confused because I see no similar errors being listed on support threads.
 
thanks you,
 
Tim
[/SIZE]

It would be a good idea to start your own thread because the title of this one is not anything like the problem you are facing, which may cause those who can help you to pass this thread over.

Besides it hard enough trying to help one person without another hijacking the thread. it makes it really difficult to keep track and help anyone. Please start your own thread.

---

