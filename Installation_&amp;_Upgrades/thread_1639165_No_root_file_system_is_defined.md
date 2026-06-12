---
title: "No root file system is defined"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by kinglogan420 on 2010-07-11
PLEASE HALP!!! 

i am trying to install the new version of ubuntu 10.04(desktop 32 bit) on my desktop and when i get to step 4 (prepare partitions) nothing shows up and if i click forward, i just get "no root file system is defined, please correct this from the partition... etc", i am currently "trying" 10.04 becuase i have no operating system on there right now, my windows 7 went corrupt so i deleted it. why cant i see my hard drive in gparted or anything to create partitions AND WHY CANT I INSTALL? 

please help.. desperate here

Thanks.
-Logan

---

### Post by maximumdoodoo on 2010-12-06
Did you ever resolve this issue?  While I am able to see the hard drive in gparted, I'm stuck with the same problem you're seeing during installation.

---

### Post by Quackers on 2010-12-06
Do you have an operating system installed on the disc already?

---

### Post by maximumdoodoo on 2010-12-06
The hd has been erased.  I'm attempting to install 10.10 via Live CD.  I am able to successfully create partitions, but the partitions are not recognized during installation.

---

### Post by Quackers on 2010-12-06
You should have started a new thread.
How are you making the partitions? With what program? The installer?

---

### Post by maximumdoodoo on 2010-12-06
New thread, continuing from [http://ubuntuforums.org/showthread.php?t=1528612](http://ubuntuforums.org/showthread.php?t=1528612)



I created partitions within gparted.

---

### Post by maximumdoodoo on 2010-12-06
[http://ubuntuforums.org/showthread.php?p=10207400#post10207400](http://ubuntuforums.org/showthread.php?p=10207400#post10207400)

---

### Post by sikander3786 on 2010-12-06
Check your Bios settings and switch your HDD mode to 'ahci' or 'compatible'. If that doesn't help, our mate **Quackers** are still there to help you :P

---

### Post by sikander3786 on 2010-12-06
> **maximumdoodoo said:**
> New thread, continuing from [http://ubuntuforums.org/showthread.php?t=1528612](http://ubuntuforums.org/showthread.php?t=1528612)



I created partitions within gparted.
As the issue was being addressed there, I don't feel there was an absolute need for a separate thread.

As now you have started it, I would suggest to remove the reference to the other one and edit above post and describe your exact problem here.

From what I've read there so far, this might be helpful.

[http://ubuntuforums.org/showpost.php?p=10207420&postcount=7](http://ubuntuforums.org/showpost.php?p=10207420&postcount=7)

---

### Post by Quackers on 2010-12-06
As Sikander says in the other thread which hopefully will appear in this thread shortly (Mr. Moderator :-)) check your bios settings - unless this hard drive has been recognised ok in your machine previously.

---

### Post by CharlesA on 2010-12-06
Please stick to one thread. It makes it less confusing.

Threads merged.

---

### Post by Quackers on 2010-12-06
Thanks CharlesA.
OP, if you delete all the partitions you have made with gparted does the installer see the unallocated space? Or nothing at all?

---

### Post by maximumdoodoo on 2010-12-06
Since I made a giant mess on my first post, I'll describe the issue in full.

Starting from a formatted hard drive, I am attempting to install 10.10 via the Live CD.  During installation, I keep getting stuck on Step 4 (Prepare partitions).  The window appears blank.  Upon attempting to proceed to the next step I get "no root file system is defined" error.

I am able to successfully create partitions with gparted.  Upon deleting all partitions, the installer is still unable to recognize the unallocated space.

Originally, the hard drive was set to RAID by default.  I have since changed it to  AHCI.  This makes no difference.

---

### Post by ronparent on 2010-12-06
Delete the raid meta data that remains on the drive despite the fact that it is no longer used as a raid!

ie sudo dmraid -E /dev/sda etc.

---

### Post by maximumdoodoo on 2010-12-06
Is it advisable to delete this meta deta before creating partitions?

---

### Post by Quackers on 2010-12-06
The command should be run on all discs that have been raided in the past.
I wouldn't think that it would matter whether any partitions are present. Maybe ronparent (the raid king :-) ) could confirm?

---

### Post by maximumdoodoo on 2010-12-06
I have now recreated the appropriate partitions.  Upon attempting the dmraid suggestion, I get the following error:

"ERROR: option missing/invalid option combination with -E"

I have checked fdisk -l, and both sda1 and sda2 are listed.  

Any ideas?

---

### Post by Quackers on 2010-12-06
Could you post a screenshot of the terminal screen as you run
```
sudo dmraid -E /dev/sda
```
please. Thanks.

---

### Post by maximumdoodoo on 2010-12-06
[IMG]http://i.imgur.com/1QK71.png[/IMG]

---

### Post by maximumdoodoo on 2010-12-06
Apologies for the insanely large image...

---

### Post by maximumdoodoo on 2010-12-06
Also, I realize I took a screenshot using /sda1 in the command.  /sda yields the same result.

---

### Post by Quackers on 2010-12-06
Do you just have the one hard drive? Also are any usb sticks plugged in?

---

### Post by maximumdoodoo on 2010-12-06
Just one hard drive.  No USB plugged in.

---

### Post by Quackers on 2010-12-06
I've just been reading about it.
I think you may need to try
```
sudo dmraid -rE /dev/sda
```
instead. (Notice the extra r)

---

### Post by ronparent on 2010-12-06
Quackers - how right you are. I blew that one!

---

### Post by Quackers on 2010-12-06
So did I ronparent! I just blindly copied it knowing it didn't feel right!

---

### Post by maximumdoodoo on 2010-12-06
You are a king amongst men.  I cannot thank you enough.  

Due to this entire experience (I'm on hour 18 so far), I am deathly afraid to say "problem solved" until the machine gets through the next installation step, but so far, it looks like this has been resolved.  

Again, thank you so much.

On a side note, this is totally irrelevant, but as I was typing this, the Golden Girls was on tv, and the theme song goes, as always, "thank you for being a frieeeeeeeeend".

---

### Post by Quackers on 2010-12-06
Nice one :-)
I'm off to bed now, it's 2 am here.
Nice one ronparent :-)
Goodnight all.

---

### Post by maximumdoodoo on 2010-12-06
Ok.... All is well.  10.10 is now fully installed.

---

### Post by ronparent on 2010-12-06
Congratulations - have fun.

---

### Post by jerry555 on 2010-12-21
Sorry for bumping, but i just wanted to thank Quackers! I installed Mint with no problems, but when i restarted the computer, it told me the BIOS was not installed, and it tried to boot, but nothing happened. I'm trying to install Ubuntu now, will edit this post when i am done.

---

### Post by sikander3786 on 2010-12-21
> **jerry555 said:**
> Sorry for bumping, but i just wanted to thank Quackers! I installed Mint with no problems, but when i restarted the computer, it told me the BIOS was not installed, and it tried to boot, but nothing happened. I'm trying to install Ubuntu now, will edit this post when i am done.
Strange to hear an error saying BIOS not installed. If Bios was not installed, you wouldn't be able to use your computer any longer ;-)

Bios is the small program which runs at boot and then hands over all the control to the Boot loader in the MBR of your HDD.

So I think the error was regarding Grub or Boot or something like that?

Let us know how your Ubuntu installation goes and feel free to ask if you need any type of help.

Good Luck!

---

### Post by jerry555 on 2010-12-21
It loads the BIOS, says the BIOS is FastTrack version 2.00.0.17. Then it is scanning for drives, and then it blinks "No array is defined!". i can press esc to continue booting, when i do that an error message comes saying "[NOTE!] The BIOS is not installed!" and it boots as if there wasnt an operating system. In the Ubuntu installation, it said something about a I/O error, so i guess it is a faulty drive? or maybe i made it faulty, after removing the RAID

oh, and i can get into the BIOS setup.

---

