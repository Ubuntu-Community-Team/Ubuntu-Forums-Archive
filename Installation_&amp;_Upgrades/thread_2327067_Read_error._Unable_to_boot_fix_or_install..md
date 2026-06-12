---
title: "Read error. Unable to boot fix or install."
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by arthur24 on 2016-06-07
Ive been getting errors. When i boot ubuntu I get the (read error)
And just that. Ive been getting them ocasionally on and off. Now the computer wont boot at all. I had the same error on my previous 14.04 install. Now I installed 16.04 on a different harddisk as I suspected harddisk failure.

When i try to boot from a live cd with the intention to scan the harddisk for errors i get.

Ata1.00: failed command: read fpdma queued. 

Cmd 60/01........(lotsa numbers)........tag 27 ncq 512 in
Res 40/00..........(lotsa numbers).......Emask 0x10 (ata bus error

And about 1-200 of similar lines of code.

Eventually the live cd does load. But sometimes it doesnt and the live cd environment hangs at the ubuntu background without any install prompts.

This maybe because i have a Nvidia gpu and I need to add nomodeset. But I cant do this because the whole live cd environment hangs.

I used this cd 3 days ago on the same pc to install ubuntu without problems. Because i got the read error on my old 14.04.

Now the problem has expanded in the ways i just explained and I have no idea whats going on here.

If you need more info. Please ask.

Edit: I also get the "failed command", "res" and "cmd" errors when i try to boot ubuntu from the hdd. Occasionaly ubuntu does finish booting correctly. Rarely thoufh

---

### Post by grahammechanical on 2016-06-07
So, you have two hard disks. One with 16.04 on it and the other with 14.04 on it. Can you load into 16.04? Are you able to use 16.04 to backup your important data on the 14.04 disk to the 16.04 disk?

When you installed 16.04 from this DVD did you use the nomodeset option? If you did not need to add nomodeset to the boot parameters of the live session at that time then why do you think that the errors you are getting loading 14.04 from the 14.04 drive are related to the Nvidia GPU? Are you getting these errors

> Ata1.00: failed command: read fpdma queued. 

Cmd 60/01........(lotsa numbers)........tag 27 ncq 512 in
Res 40/00..........(lotsa numbers).......Emask 0x10 (ata bus error


during the loading process of the live session? Or before the live session begins to load? In other words, is it the motherboard that is reporting these errors during its Power On Startup Tests (POST)?

I can tell you this, Ata1 = the first hard disk. If it is an ATA drive then it is an old drive. SATA drives have been around for a long time. Please tell us the hardware specifications of this machine.

Regards.

---

### Post by arthur24 on 2016-06-07
I might have been a bit unclear (may be due to the fact that I typed on my phone)
 I had 14.04 installed.
 I erased the disk with 14.04 prior to installing 16.04.
16.04 is installed on a different harddisk because I expected harddisk issues in the first place. Besides the "read error" also the Ata 1:00 errors were displayed on my old 14.04 setup. Which was installed on a different harddisk. 
And I have severe doubts that this is a 1/1million case were both harddisks are at fault.
All harddisks except one are pretty new. I haven&#8217;t installed Ubuntu on the older harddisk ever and I have 5 harddisks in total.
 
 
 I&#8217;m very sure the error messages are not part of the POST.
 
 
 The computer actually boots from the live cd.  
 This is clear because  
 
 
 1: The CD drive starts spinning.
 2: The error messages are also displayed when attempting to boot the installed 16.04.
 
 
 When booting Ubuntu the loading bar is displayed for a short time but dissapears followed by the error messages. These are the same error messages when booting the live CD, after the CD drive becomes active.  
 
 
 However, to me the problem could be due to anything, and yes also the motherboard even although the errors are not part of the post.  
 
Occasionally Ubuntu does boot. I&#8217;m now typing this message on my 16.04.
 But it requires 10-15 reboots on average and it&#8217;s gotten worse over time. I expect that eventually I won&#8217;t be able to boot Ubuntu at all if this trend continues.

Hardware specs:

All harddisks are sata.
1:120gb intel ssd
2x 500gb Seagate Hds
1x 2 TB WD HD
1x 3 TB Seagate HD.

Asrock P77 pro 3
Intel 3570K
8GB gskill DDR3
Nvidia geforce GTX750 Ti

(MB, CPU, GPU and RAM are 3 years old) The TB harddisks are both 1.5 years old. THe other harddisks about 3-5 years old.

---

### Post by arthur24 on 2016-06-07
I might have been a bit unclear (may be due to the fact that I typed on my phone)
 I had 14.04 installed.
 I erased the disk with 14.04 prior to installing 16.04.
16.04 is installed on a different harddisk because I expected harddisk issues in the first place. All harddisks except one are pretty new. I haven&#8217;t installed Ubuntu on the older harddisk ever and I have 5 harddisks in total.
 
 
 I&#8217;m very sure the error messages are not part of the POST.
 
 
 The computer actually boots from the live cd.  
 This is clear because  
 
 
 1: The CD drive starts spinning prior to the errors after the POST display.
 2: The error messages are also displayed when attempting to boot the installed 16.04 after the POST has been completed.
 
 
 When booting Ubuntu the loading bar is displayed for a short time but dissapears followed by the error messages. These are the same error messages when booting the live CD, after the CD drive becomes active.  
 
 
 However, to me the problem could be due to anything, and yes also the motherboard even although the errors are not part of the post.  
 
Occasionally Ubuntu does boot. I&#8217;m now typing this message on my 16.04.
 But it requires 10-15 reboots on average and it&#8217;s gotten worse over time. I expect that eventually I won&#8217;t be able to boot Ubuntu at all if this trend continues.

---

### Post by oldfred on 2016-06-07
Do you have asmedia ports?

 Some have issues with Asrock and its asmedia ports 

One user said even using DVD drive on asmedia port caused drive issues.

---

### Post by arthur24 on 2016-06-07
Do not actually know what asmedia ports are, but I looked it up and now I do.
According to the internet the Z77 has asmedia ports. 1 sata controller for up to 4x 3Gb's, and a asmedia controller for up to 2x 6 Gb's. (all 6 Sata ports are in use. 5 harddisks + the dvd drive)

The thing is, how do I know which of the 6 are the 2 asmedia connectors?
All sata ports look similar on the MB. Is there any way to tell?
Good chance that therein lies the problem. Either both hd's are connected to them, the dvd drive or vice versa.

---

### Post by oldfred on 2016-06-07
I do not see anything in your manual.
[http://asrock.pc.cdn.bitgravity.com/Manual/Z77%20Pro3.pdf](http://asrock.pc.cdn.bitgravity.com/Manual/Z77%20Pro3.pdf)

Do you have all drives in AHCI mode, not RAID nor IDE?

---

### Post by arthur24 on 2016-06-09
I got it fixed, finally.

The solution was quite simple. Apparently I forgot to set the harddisk priority in the BIOS and choose the harddisk with the Ubuntu partition as the first option.
Apparently Ubuntu did boot occasionally without changing this option, but these errors are now gone completely and I hope never to see them again.

---

