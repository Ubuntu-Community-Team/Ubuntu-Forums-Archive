---
title: "Wubi fails yet again and questions regarding shrinking/partitioning. Need help"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by Nexiros on 2010-03-10
Hello,

First time posting here so be kind ^_^. I used to use  Linux Ubuntu on my old laptop (Windows Vista 32-bit) installed via Wubi  and loved it, I needed it for my Uni work as terminal was key.
Anyways,  recently, I purchased a new computer (Windows 7 64-bit) and found Wubi  very troubling to install. After close inspection, I realised that Wubi  does not yet support Windows 7 and the 64-bit had issues. I did a little  research and found that if I messed around with the destination name  (--32bit) or something like that while also running the Wubi installer  in Windows Vista SP2 compatability mode, that it worked and installed  fine :D.
My excitement was soon cut short when I tried to reboot  after installing the new updates that it had found. It then came up with  the sh: grub shell. It did this with my old laptop with the recent  update and I normally typed something in to fix it but when I typed the  exact same thing into my system, it said something to do with my  processors not responding QQ. Anyways, I think I'm gonna give up with  Wubi, as obviously, I can't get anything to work so...meh. 
I  currently have my Windows 7 stored on my SSD (64gb) and my HDD (1.5tb)  contains all my personal stuff and non-boot programs. My question is,  can I install Ubuntu from a CD (I've just written one from the Ubuntu  site) on my SSD without formatting my SSD (etc, does shrinking Windows 7  and making space by partitioning for Ubuntu format everything? will I  lose Windows 7?) Also, it recommends that I defragment the drive which  I'm going to use for Ubuntu but cause I would be installing on my SSD,  that would mean defragging my SSD which = bad. 
Erm...any advice  anyone could give me for how to get Ubuntu onto my PC would be greatly  appreciated.
My email is [email]weed89@hotmail.co.uk[/email] if you want to contact  me persoanlly. Look forward to your responses. TY again.

Chris  a.k.a Nexiros

---

### Post by garvinrick4 on 2010-03-10
Wubi and 64 bit is not a problem at all. It is a nice learning experience for Linux just because you can uninstall from within the folder in Ubuntu in C: drive if you make a mess of it. Wubi is just a folder inside of Windows and attaches to Windows boot manager bcdedit. A pretty simple install, choose Wubi type in size and password click Go.

 To install boot off of your Burned CD of Ubuntu and just follow the instructions. Let it pick out the partition and will make a extended partition and put a logical partition for your Ubuntu and one for a swap. It will tell you what it is doing at all times, just stay focused. gparted is good software. 
 Only allowed 4 primary partitions for each drive and Windows7 has  
 3 at install if you have a recovery also. That is why the extended partition and can put as many logicals as need be inside.
 Do not use manual for first install, a personal opinion of course. First study should be gparted, fstab, grub2 and Live CD.

---

### Post by Nexiros on 2010-03-10
I understand how Wubi works in the sense that it doesn't actually install as a system and is just a folder that you can boot from but "A pretty simple install, choose Wubi type in size and password click Go." It appears its not that easy, I just did another install of Wubi, it installed fine and I was like yay. But when I enter Ubuntu after its fully installed, it comes up with, Package Manager Updates and Important System Updates, stuff like that. When I choose to just ignore them, I can keep Ubuntu working fine, I can reset it, and it will be cool, but as soon as I update anything, it seems to boot with this:

GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions ]

Sh: grub > _

Now as stated, I managed to enter things in this in the past, in fact, I'll give you what I typed:

set root=(hd0,*whatever my number is e.g 2*)
linux (loop0)/boot/vmlinuz-2.6.31-20-generic pae root=/dev/sda*whatever my number is e.g 2* loop=/ubuntu/disks/root.disk ro
initrd (loop0)/boot/initrd.img-2.6.31-20-generic pae
boot

O.K, so now you know what I typed, anyways, on my old laptop, this would work fine and would boot ubuntu however, with this PC, it doesn't seem to work. All it comes up with is either (previously) tries to load my processors and fails or (what it is doing now) just not recognising anything from any of my hd0 things. 
I type in "ls" to see what I have, I have (loop0) (hd0) (hd0,2) (hd0,1) (hd1) (hd1,1) (hd 1,2) (hd2) (hd2,2) (hd2,1). I've tried them all and they can't seem to find anything after I type in "linux (loop0)/". boot should come next but oh well.
Anyways, In the past, I've also tried just updating everything bar the grub stuff and then it does something interesting. After selecting Ubuntu and then vmlinuz bla bla bla from the other boot screen. It takes me to the Ubuntu Logo, you know the one that flashes white and fades every second or so, but this logo isn't flashing. It just is white and doesn't do anything ¬_¬.
So unless you can help me with this problem which I'd really appreciate btw :) I can't see myself moving forward with Wubi.

Also, you didn't seem to answer my question about defragging my SSD, good or bad thing to do? Also, the main point, which is what's holding me back from doing to CD boot atm, if I go ahead with what you say, just booting the CD. Will I lose everything on my C: drive cause surely when you partition, you format, and when you format, doesn't it just wipe everything??? 

[http://www.youtube.com/user/NixiePixel#p/u/51/GhnLk3gviWY](http://www.youtube.com/user/NixiePixel#p/u/51/GhnLk3gviWY)

Also, how about this way of installing, is this safe to do (not deleting my data (Windows 7 and anything else on my C: drive)).
I've heard of gparted, I'll give that a look, but can you get back to me on this Wubi issue/my other questions please. 

Many thanks for the first post btw.

---

### Post by garvinrick4 on 2010-03-10
Go into your windows and at command line type Code: bcdedit


Post the results please:
It is your windows boot manager.

---

### Post by garvinrick4 on 2010-03-10
gparted is the default partitioning software ubuntu uses on install.

[https://wiki.ubuntu.com/WubiGuide#Introduction](https://wiki.ubuntu.com/WubiGuide#Introduction)


[http://ubuntuforums.org/showthread.php?t=1407130](http://ubuntuforums.org/showthread.php?t=1407130)

---

### Post by Nexiros on 2010-03-10
Already tried replacing the wubildr file, I installed Wubi, replaced the wubildr in my C: drive (where the other broken one was) and restarted. Normally, w/o doing this, at least Wubi installs Ubuntu on restart and does the setup, this however sent me straight to the grub screen so...again. FAILED. I really don't know what I'm doing wrong :(
I just really want Linux Ubuntu.
Also, again, does using gparted wipe windows off my C: drive?

---

### Post by Nexiros on 2010-03-10
Windows Boot Loader
-------------------------
identifier                         {current}
device                             partition=C:
path                                \Windows\system32\winload.exe
description                       \Windows 7
locale                              en-US
inherit                            {bootloadersettings}
recoverysequence           {e97261a5-f01b-11de-a35f-aef359132e86}
recoveryenabled              Yes
osdevice                          partition=C:
systemroot                      \Windows
resumeobject                  {e97261a3-f01b-11de-a35f-aef359132e86}
nx                                   OptIn

Real-mode Boot Sector
---------------------------
identifier                         {e97261ab-f01b-11de-a35f-aef359132e86}
device                             partition=C:
path                               \ubuntu\winboot\wubildr.mbr
description                      Ubuntu

---

### Post by garvinrick4 on 2010-03-10
> **Nexiros said:**
> Already tried replacing the wubildr file, I installed Wubi, replaced the wubildr in my C: drive (where the other broken one was) and restarted. Normally, w/o doing this, at least Wubi installs Ubuntu on restart and does the setup, this however sent me straight to the grub screen so...again. FAILED. I really don't know what I'm doing wrong :(
I just really want Linux Ubuntu.
Also, again, does using gparted wipe windows off my C: drive?
No gparted will not wipe out your C: drive. unless you tell it to.

First thing is to go to Windows and defrag once or twice.

Put Ubuntu CD in tray and start computer, select install.

Will ask a few questions answer then will go into gparted where it will
select a size to install on it thinks it needs. Stay focused and answer questions
from page to page. Do not use manual install, that is for more experienced users.
If you understand what you are trying to do all should go smooth. If you have no idea
what you are trying to do read about partitioning basics, gparted basics and such.
 Is not difficult if you stay focused gparted in Ubuntu just about does it all for you.

---

### Post by garvinrick4 on 2010-03-10
> **Nexiros said:**
> Windows Boot Loader
-------------------------
identifier                         {current}
device                             partition=C:
path                                \Windows\system32\winload.exe
description                       \Windows 7
locale                              en-US
inherit                            {bootloadersettings}
recoverysequence           {e97261a5-f01b-11de-a35f-aef359132e86}
recoveryenabled              Yes
osdevice                          partition=C:
systemroot                      \Windows
resumeobject                  {e97261a3-f01b-11de-a35f-aef359132e86}
nx                                   OptIn

Real-mode Boot Sector
---------------------------
identifier                         {e97261ab-f01b-11de-a35f-aef359132e86}
device                             partition=C:
path                               \ubuntu\winboot\wubildr.mbr
description                      Ubuntu
Has wubildr.mbr installed is ok.

---

### Post by garvinrick4 on 2010-03-10
Go into Windows C: drive to Ubuntu right next to Users and open and select uninstall.
Go back to bcdedit and make sure no more wubildr.mbr in selections. 

Start your install with Booting off your Live CD of Ubuntu.

---

### Post by Nexiros on 2010-03-10
I just ran the wubi installer and thats what it installed, it didn't come up with any error messages if thats what you mean. It just came up with Wubi has successfully installed, to complete the installation, bla bla bla, needs to restart.
I swapped the wubildr file for the one that the the ubuntu forums recommend (the fix to the bug one) and the wubildr.mbr file was left as I didn't think that anything was wrong with it...? Is there?

Once again, I need to know that my C: drives data (including Windows 7) will be safe and untampered with if I run the Live CD. Otherwise, I won't do it as I'll live in fear as I don't have any Backup Utility atm.

---

### Post by garvinrick4 on 2010-03-11
> **Nexiros said:**
> I just ran the wubi installer and thats what it installed, it didn't come up with any error messages if thats what you mean. It just came up with Wubi has successfully installed, to complete the installation, bla bla bla, needs to restart.
I swapped the wubildr file for the one that the the ubuntu forums recommend (the fix to the bug one) and the wubildr.mbr file was left as I didn't think that anything was wrong with it...? Is there?

Once again, I need to know that my C: drives data (including Windows 7) will be safe and untampered with if I run the Live CD. Otherwise, I won't do it as I'll live in fear as I don't have any Backup Utility atm.
When you run a LIVE CD it is just that. It is running off of the CD has nothing to do with your Hard drive. When you start to install it will then partition your hard drive. If the fix that the bug report did the job and you have your WUBI running fine then just use that. You seem to be very hesitant about installing Ubuntu alongside your Windows in its own Partitions. Go with what you feel comfortable with. You have all the tools and instruction to do either so enjoy yourself with Linux.
As for the bug report, it looked a bit like your WUBI problem so I gave it to you to read and do what you wanted with. If it fixed your problem then great. Tell the people how you solved and mark your thread as Solved.

---

### Post by Nexiros on 2010-03-11
Nope, Wubi still doesn't work after the apparent bug fix, sorry, forgot to mention that it failed again :P
I'll look into the gparted thing and the Live CD install. TY anyways for trying with the Wubi GRUB bug.

---

### Post by Nexiros on 2010-03-11
Its just come to my attention that I probably haven't explained my situation well as from what my mate is saying, from what you've said, you think that my C: drive has more than one partition, but I've checked on my Disk Managemet, and my C: drive only has one partition. My mate says that if I ever want to make a new partition on a drive, that I have to format whatever is on my drive to get the new partition in place.
Sorry if I mislead you into believing I have more than one partition. I only have one :(

---

### Post by garvinrick4 on 2010-03-11
> **Nexiros said:**
> Its just come to my attention that I probably haven't explained my situation well as from what my mate is saying, from what you've said, you think that my C: drive has more than one partition, but I've checked on my Disk Managemet, and my C: drive only has one partition. My mate says that if I ever want to make a new partition on a drive, that I have to format whatever is on my drive to get the new partition in place.
Sorry if I mislead you into believing I have more than one partition. I only have one :(
When you install from Ubuntu Live CD it go's into gparted and does the formatting for you.
gparted does everything except kiss you good night, boot up the CD and go.

---

### Post by Nexiros on 2010-03-11
OK, one final question...I hope ^_^.
From what I've gathered:
1. Installing from the CD uses gparted.
2. Gparted can basically create a new partition from the free space on my C: drive.
3. If I have Windows 7/startup programs already on my C: drive, then it won't format them (wipe them) as long as I format the correct partition (the new one that I would hopefully create).
4. It would only format the new partition that I'm going to run Ubuntu on leaving my Windows 7/startup programs unaffected.
5. It wouldn't kiss me goodnight? :O :(

Is this all correct. If so, I can go ahead with the following tutorial I guess:

[http://www.youtube.com/watch?v=w8a-smrPlvE&feature=related](http://www.youtube.com/watch?v=w8a-smrPlvE&feature=related)

OFC, will be using Ubuntu 9.10 instead though :)

Reply soon so I can install it. I can't wait anymore lol xD

---

### Post by presence1960 on 2010-03-11
> **Nexiros said:**
> I understand how Wubi works in the sense that it doesn't actually install as a system and is just a folder that you can boot from but "A pretty simple install, choose Wubi type in size and password click Go." It appears its not that easy, I just did another install of Wubi, it installed fine and I was like yay. But when I enter Ubuntu after its fully installed, it comes up with, Package Manager Updates and Important System Updates, stuff like that. When I choose to just ignore them, I can keep Ubuntu working fine, I can reset it, and it will be cool, but as soon as I update anything, it seems to boot with this:

GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions ]

Sh: grub > _



[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Nexiros on 2010-03-12
presence1960, I've already tried that solution but it doesn't help, I replaced the "faulty" wubildr in my C: drive (where I installed Ubuntu) and all it did was boot into the "grub:sh>" prompt. :(

---

### Post by garvinrick4 on 2010-03-12
> **Nexiros said:**
> OK, one final question...I hope ^_^.
From what I've gathered:
1. Installing from the CD uses gparted.
2. Gparted can basically create a new partition from the free space on my C: drive.
3. If I have Windows 7/startup programs already on my C: drive, then it won't format them (wipe them) as long as I format the correct partition (the new one that I would hopefully create).
4. It would only format the new partition that I'm going to run Ubuntu on leaving my Windows 7/startup programs unaffected.
5. It wouldn't kiss me goodnight? :O :(

Is this all correct. If so, I can go ahead with the following tutorial I guess:

[http://www.youtube.com/watch?v=w8a-smrPlvE&feature=related](http://www.youtube.com/watch?v=w8a-smrPlvE&feature=related)

OFC, will be using Ubuntu 9.10 instead though :)

Reply soon so I can install it. I can't wait anymore lol xD
Enjoy your Linux. Go to it. I think you got it.

---

### Post by Nexiros on 2010-03-13
O.K, I've just tried installing it via the LiveCD and I got as far as the partitioner. It said I had 3 main parts. sda, sdb, sdc. sda being my hard drive with 1.5 TB space, with some of it being used. sdb being my SSD (C: drive) with 64GB space with 30GB odd being used. sdc being the a fat32 type and being 4GB odd. But thats my memory stick, so DW about sdc.
Anyways, when I click on sdb (C: drive what I'm trying to get Linux Ubuntu 9.10 onto) and click forward. It makes the 64 GB all free space??? Meaning, its basically getting rid of all thats on there (Windows 7). I then made a new partition, being Primary, 20000MB (20GB) at the End and with the root being "/".
I don't want to lose Windows, but as I'm aware, I need to install Windows first anyways. Am I doing this right? Or have I gone wrong somewhere. Help PLZ.

---

### Post by Mark Phelps on 2010-03-14
> **Nexiros said:**
> I don't want to lose Windows, but as I'm aware, I need to install Windows first anyways. Am I doing this right? Or have I gone wrong somewhere. Help PLZ.

Where you're going wrong is following advice to let the Ubuntu installer shrink your Win7 partition.  That's a pretty good way to corrupt your Win7 OS so it won't boot anymore.

Did you first go into Win7 and use the Backup function to create and burn a Win7 Repair CD?  Until you've done that, don't do anything with the partitions.

If the partition situation looks "odd" with the Ubuntu partitioner, then don't use it!

Instead, boot into Win7 and (after burning the Repair CD), use it to shrink the Win7 OS partition).  Leave the unallocated space empty.

Then, when you boot the Ubuntu installer, select the largest free space.  If it shows that OK, then proceed. IF it does not, then do Manual Partitioning to create the partitions.

---

