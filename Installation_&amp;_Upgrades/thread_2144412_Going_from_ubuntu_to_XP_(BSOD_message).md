---
title: "Going from ubuntu to XP (BSOD message)"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by deejved on 2013-05-12
Hi guys.
 
I've been checking hundreds of forums, and I didn't find the right  answer, so I decided to post my problem here. I might not be in the right topic, because i didnt know where to put it.. so sorry about that. So here's my story.
 
I was running Windows XP with Ubuntu installed along. All fine. Then I  decided to install only ubuntu over windows, and I was using ubuntu for  few days (I did a clean install of ubuntu, so there was no windows  anymore). Still all fine. Then I realized that Ubuntu doesnt really fit  me.. So I wanted to go back to Windows XP. I booted the CD, Setup was  loading all drivers needed for setup, then it said: Setup is starting  Windows... , and when it should pop into Section where u format the  drives:
[IMG]http://www.tips4pc.com/images/Repair%20Windows.jpg[/IMG]
 
It didnt pop into this, but it gave me BSOD which looked like this:
 
A problem has been detected and Windows has been shut down to prevent damage
to yor computer.

If this is the first time you've seen this stop error screen, restart your
computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives
or hard drive controllers. Check your hard drive to make sure that it is
properly configured and terminated. Run CHKDSK /F to check for hard drive
corruption, and then restart your computer.

Technical information:

*** STOP: 0x0000007B (0xF7C7A524, 0xC0000034, 0x00000000, 0x00000000)
 
I have only one hard drive (SATA), and it worked without any problems  before installing ubuntu, and it stills works perfectly on ubuntu. I  also tried plugging in my old hard disk (never had other installed than  winxp), and I got the same bsod, at same section. Though my disk works  perfectly on ubuntu, it shouldnt be broken or anything. I know that  ubuntu formats hard drive to ext4 format, because ubuntu cant use ntfs,  so I tried formatting disk with disk utility in ubuntu to NTFS, but  still it didnt worked. I removed CMOS battery, and reseted BIOS settings  to default, but still nothing..
 
Im desperate for getting windows xp back on, so please help me.
 
Cheers, David

---

### Post by dino99 on 2013-05-12
ha ha, the builtin MS's bsod : they does not want you glancing outside their own crappy OS

simply use a formatting tool to really erase your hdd; then install again

---

### Post by deejved on 2013-05-12
> **dino99 said:**
> ha ha, the builtin MS's bsod : they does not want you glancing outside their own crappy OS

simply use a formatting tool to really erase your hdd; then install again

well, could you please give me some more info.. which formatting tool, etc? And one more problem.. as i said, i have only one disk plugged in. That means i have ubuntu installed on it. Can i use formatting tool and format the disk, while ubuntu is running? i dont rly understand that part. thanks for ur answer.

---

### Post by coldraven on 2013-05-12
> Can i use formatting tool and format the disk, while ubuntu is running?
No, you need to boot from a live CD or USB stick.
Then run gparted and delete any partitions that you find on the hard drive.
It should then say "Unallocated space" for the whole drive.
You need to click the "Apply" button at the top of the screen
You could either then create one big NTFS partition or just try installing XP on to the empty (blank) drive
I would try the latter option first, Windows is fussy and might prefer a blank drive.

---

### Post by Warprunner on 2013-05-12
> **dino99 said:**
> ha ha, the builtin MS's bsod : they does not want you glancing outside their own crappy OS

simply use a formatting tool to really erase your hdd; then install again

[SIZE=5][COLOR=#008000]***Wow***[/COLOR][/SIZE], sorry about my amazement but it's been literally years since I saw a BSOD. (Faithful Ubuntu User since 2008)

I have to agree.. "simply use a formatting tool to really erase your hdd; then install again" is the way to go. 

I wonder why Ubuntu didn't fit the need?

---

### Post by Bucky Ball on 2013-05-12
> **coldraven said:**
> No, you need to boot from a live CD or USB stick.
Then run gparted and delete any partitions that you find on the hard drive.
It should then say "Unallocated space" for the whole drive.
You need to click the "Apply" button at the top of the screen
You could either then create one big NTFS partition or just try installing XP on to the empty (blank) drive
*_I would try the latter option first, _*Windows is fussy and might prefer a blank drive.

This. Blank and Win will create it's own NTFS partition when it installs.

---

### Post by deejved on 2013-05-12
> **Bucky Ball said:**
> This. Blank and Win will create it's own NTFS partition when it installs.

i used ubuntu live cd, then i deleted all partitions with gparted, i also applied the operations, and it said Unallocatted space. So i suppose that the disk was empty but when i went to boot windows, same bsod all over again. im starting to suspect there should be something else wrong - not the disk, but maybe something deep in the computer or something.. i dont really know. And im getting really mad, as i am struggling with fixing it for 4 days now..

---

### Post by tgalati4 on 2013-05-12
You should keep the dual-boot configuration in case you change your mind again.  Having Ubuntu on a 2nd partition is like having a spare tire that you can drive really fast on--for the rest of the life of the car.

---

### Post by Mark Phelps on 2013-05-12
One thing you could try -- download and burn a CD of the Minitool Partition Wizard CD, boot from that -- and see if it can see the hard drive.

IF it can't, you may need to go into the BIOS and mess around with SATA settings.

---

