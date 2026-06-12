---
title: "config BIOS so files on 4 HDs can be copied to a larger Tbit drive"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by ken78724 on 2016-01-11
Please help me keep my New Years Resolutions.

 How must I set the BIOS to make my WD 1 Tbit HD boot first, then allows me to copy what's on my 750g maxtor 15.10 wily; 80g Seagate and 120 g Seagate. ???

I'm a noob when it comes to this simple question that arose after learning I mislaid my password and cannot open my  80g Seagate and 120 g Seagate. 

Moreover, I have the same problem on 10 other HDs on which it appears I have mislaid their passwords as well.

if it makes a difference,  my WD 1 Tbit HD is running Ubuntu 15.10 Wily and some of the HDs I'm pulling from are as early as Ubuntu 7.04; Linspire 4.0; Win XP; and Berkeley PC5

My new years resolutions include
     1) get organized so I can hone down manuscripts and then sell I hope 7 books
     2) pay the piper, be friendly and learn how to do what is necessary with two eyes that are getting weaker and weaker

I need your help as I have been going in circles about a week. Peace be with you!!!

ken78724:KS

---

### Post by grahammechanical on 2016-01-11
Here is the problem from our point of view. We do not even know the make & model of the computer you have. We are unfamiliar with the BIOS setup utility. Changing settings in the BIOS has a small risk of doing something inadvisable. I do not think that it is wise to direct someone on how to change settings in the BIOS if we are unfamiliar with the actual settings utility being used.

The manufacturer's web site may have a PDF version of the motherboard user manual. That is if you do not have a hard copy of the motherboard User manual. And with a PDF version we can Zoom the pages.

On my machine I go to a Boot section of the BIOS. External USB drives are sometimes seen by the BIOS as external hard drives and not as USB devices. So, it is the boot menu to look through & not the USB devices menu. This is the case on my machine.

Regards

---

### Post by Mark Phelps on 2016-01-12
Somewhere in your BIOS settings you will have two parameters.  One sets the order of boot devices that your BIOS scans.  In that, you need to have the hard drive set as the first device.  The other sets the order of hard drives that the BIOS sees.  You need to have the hard drive you want to boot from set as the first of the drives.

The BIOS has nothing whatsoever to do with copying files -- of any size.  So, if you can't read or copy files from one drive to another, you have a very different problem and for that, you need to tell us what errors you are encountering.

As to password-protected drives, we can't help you there.  There is no way to bypass those passwords, as if there was, there would be no point in password-protecting drives in the first place.

---

### Post by ken78724 on 2016-01-21
thanks Mr. Phelps, I reviewed the 2 BIOS parameters and set my 1 T-bit WD hard drive as the first device then disconnected three HDs leaving me with the following results this morning 1-21-16 with these results on my Mirus P5GC-MX, BIOS 0314, 2007, 1 Tbit HD running 15.10 Wily. At this point I have abandoned any effort to copy files though that is needed so I may organize life goals.

this morning 1-21-16 my monitor crashed and I reported that mess as the Flicker err bug #1520583 & Bug 1511158 to the Launchpad write up associated with .  

my G-Partition Editor says the ext 2 file system is 62.65 MiB 26 % used
       1) UUID on this 1 t-bit WD hard drive dc41387a-ee90-463b-a5da-943003503b2b says 
       2) its size is 243.00 MiB
       3) its partition path is  /dev/sda1  on which its First Sector is: 2048; Last sector is: 499711 and total sectors is: 497664

I report this because there's been a warning that my 1 T-bit hard drive will not allow me to accept a 45 mb update nor will the bugs that I have cited go away. Surely this is a serious situation, which should be solvable. 

if I were a developer or even a tech, I would re-size the partition using my G-Partition Editor. Being 76, I am afraid to wipe out hard to get work done on my PC.

---

### Post by ken78724 on 2016-01-21
my OS sits in a very small partition, which needs to be reset. do advise steps I can use to overcome the problem and opine whether this might cause the flicker err crashes that occur practically every time I use this PC 

your help is most appreciated

---

### Post by oldfred on 2016-01-21
What video card/chip does this system have?
That often is the problem with video issues. You may need the correct driver.

Best to see all the boot details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If monitor is bad, cannot help on that.

---

### Post by ken78724 on 2016-01-28
Thx to grahammechanical, Mark Phelps, Old Fred and all who stop by ,,,,, my flickering monitor issue might be solved: 

By moving my 1 T-bit WD hard drive running on 15.10 to a backup clone PC and isolating hardware ?s and doing an auto-update early 1-28-16, I want to believe the BIOS Config questions may be solved. 

At least, the demands on me to move ahead with work are pressing thanks to knowledge from Ubuntu Forum and Launchpad bug solution specialists.

Many thanks for all you do!

Warm regards!!!
ken78724

---

