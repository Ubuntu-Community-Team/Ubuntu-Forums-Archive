---
title: "prepare partition problem"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by tonefetish12 on 2010-05-08
Hi all,

I'm trying to set up a dual boot system with Windows 7 64 bit and Ubuntu 10.04. I have the windows 7 os set up am now trying to set up the Ubuntu os. Everything is going fine until I get to the Prepare Partition screen; the problem is that my hard drive does not show up; there are no options for me to click, all the buttons such as new partition table, add, change, delete, revert are gray, but I could click on quit, back, and forward (though this doesn't help me advance in my install). 

Some people in other threads talked about having grayed hard drive options, I don't have this, it's just blank. The hard drive is a 1.5TB WD Caviar Green SATA hard drive if that helps any. I have checked multiple other forums on this similar issue so I'll address the common concerns that people mentioned by stating that my hard drive is not set to raid, it is set to IDE and my write protection is turned off. 

In case it helps, I am running a intel i7, 4 gb ram, and (in case bios instructions are needed) I have ASUS p7h57d-v evo mother board. Also Windows 7 is running fine one it, there are no issues with the ram as I've tested it due to other problems I was having before.

Thank you in advance for any help you may be able to give.

---

### Post by jbrown96 on 2010-05-08
What does ```
sudo fdisk -l
``` tell you

---

### Post by tonefetish12 on 2010-05-09
Sorry, but I'm not sure where am I supposed to enter this code. Can you give me a more detailed step by step of what to do?

Thank you

---

### Post by srs5694 on 2010-05-09
Chances are very good that you've got the same problem described in [this thread.](http://ubuntuforums.org/showthread.php?t=1477371) Try following the directions in my first post (#2) and check the end point of your extended partition. If it falls after the final partition of the disk (specified near the start of the "fdisk -lu" output), you can correct the problem as described in my second post (#5); but you'll need to do the arithmetic to find the appropriate extended partition length for your own system. If you need more help, post the output of "fdisk -lu" here.

---

### Post by darkod on 2010-05-09
Also look at my post #4 here if it helps:
[http://ubuntuforums.org/showthread.php?t=1467871](http://ubuntuforums.org/showthread.php?t=1467871)

---

### Post by tonefetish12 on 2010-05-09
this is what I got with the sudo fdisk -1

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Andrew>sudo fdisk -l
'sudo' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\Andrew>

---

### Post by darkod on 2010-05-09
> **tonefetish12 said:**
> this is what I got with the sudo fdisk -1

Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Andrew>sudo fdisk -l
'sudo' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\Andrew>

It's a linux command, you need to use it in ubuntu. Boot with the ubuntu cd selecting Try Ubuntu. That will load a so called live desktop, ubuntu running from the cd (no changes to your hard disk).
Go in Applications-Accessories and open Terminal. There execute:

sudo fdisk -l (small L)

---

### Post by tonefetish12 on 2010-05-09
Thank you very much for your help and patience. I'll give this a shot and let you know what I get.

---

### Post by tonefetish12 on 2010-05-09
ubuntu@ubuntu:~$ sudo fdisk -1  
 fdisk: invalid option -- '1'  
 

 Usage:  
  fdisk [options] <disk>    change partition table  
  fdisk [options] -l <disk> list partition table(s)  
  fdisk -s <partition>      give partition size(s) in blocks  
 

 Options:  
  -b <size>                 sector size (512, 1024, 2048 or 4096)  
  -c                        switch off DOS-compatible mode  
  -h                        print help  
  -u <size>                 give sizes in sectors instead of cylinders  
  -v                        print version  
  -C <number>               specify the number of cylinders  
  -H <number>               specify the number of heads  
  -S <number>               specify the number of sectors per track 



This is what I ended up getting. Does this help any?

---

### Post by darkod on 2010-05-09
> **darkod said:**
> 
sudo fdisk -l (small L)

Not -1 (number one)

---

### Post by tonefetish12 on 2010-05-09
ubuntu@ubuntu:~$ sudo fdisk -l  
 ubuntu@ubuntu:~$ sudo fdisk l
 

 Unable to open l


I used lower case L instead of one both with and with out dash. with dash nothing happened so I tried with out  as well and nothing. I'm sure I'm probably still doing something wrong, but I dont know what. Sorry to make this difficult.

---

### Post by darkod on 2010-05-09
> **tonefetish12 said:**
> ubuntu@ubuntu:~$ sudo fdisk -l  
 ubuntu@ubuntu:~$ sudo fdisk l
 

 Unable to open l


I used lower case L instead of one both with and with out dash. with dash nothing happened so I tried with out  as well and nothing. I'm sure I'm probably still doing something wrong, but I dont know what. Sorry to make this difficult.

The first one was correct but if it didn't show you data about your hdd I don't know right now what happened.

---

### Post by srs5694 on 2010-05-09
If "sudo fdisk -l" is returning nothing, then it sounds like your disk isn't being detected. Try this to verify it: "ls /dev/[sh]d?". If you get no output, then your disk isn't being detected. A system with one disk will probably produce "/dev/sda" as output, but there are other possibilities.

Note that disk detection isn't normally an issue of the disk per se; it's a matter of the disk *controller,* which is normally part of the motherboard. A quick Google suggests that your board uses the Intel H57 chipset, and more Googling turned up a couple of problem reports for that chipset with Ubuntu. I don't know if that means there are limitations in the Linux kernel itself or that it's Ubuntu-specific kernel configuration issues. If the latter, you might have more luck with another distribution (Fedora, OpenSUSE, Debian, etc.). If the H57 chipset just has poor Linux drivers at this point, then you've got fewer options. The best of these is probably to buy a plug-in SATA card and use it to handle the disk. Another might be to track down new/experimental drivers and use them; but installing Ubuntu like that would be quite a pain.

I advise you to do more research, though. Try Googling "Linux Intel H57" or some other variant of that. Unfortunately, you'll get a lot of noise in such searches, since this type of search tends to turn up a lot of Windows-centric product reviews on sites that have unrelated "Linux" links. You should get a few relevant hits, though.

---

### Post by srs5694 on 2010-05-09
Another thought: It's conceivable that adjusting BIOS options related to the hard disk will help. Such changes may require you to re-install Windows, though.

---

### Post by tonefetish12 on 2010-05-09
it came back as no such file or directory. I'm not sure if this helps with anything, but a friend of mine let me borrow a 40 pin connecting hard drive and I tried installing ubuntu on this. It worked out, however I need to return the hard drive. Does this tell you anything more about the problem or not really? Thanks again to both of you for all your help. I greatly appreciate it.

---

### Post by srs5694 on 2010-05-10
It sounds like you just don't have working SATA drivers for your motherboard, so my previous comments hold: You'll need to try another distribution, use a plug-in SATA controller card, or learn to upgrade your kernel manually. None of these solutions is guaranteed to work.

There is, however, one slim chance for an easier solution: Try plugging your disk into different SATA ports on your motherboards. Some motherboards have two SATA controllers: One handles a certain number of disks (say, 4 of them) and the other handles additional disks (say, 2 more). Sometimes one controller is supported but not the other, so switching from one connector to another may fix the problem. If this works, chances are Windows will break, although it may be able to repair itself when it reboots.

---

### Post by Grench on 2010-05-11
OK - I'm seeing the same issue and I think you guys are going in the wrong direction.

Machine:  Compaq Evo P4 with an IBM Deskstar 20GB drive.

Scenarios:
10.04 installer from CD boot.
10.04 installer from Live CD desktop.

Outcome:  Step 4 of 8 Prepare Partitions - Nothing is listed.  New Partition Table, Add, Change, Delete and Revert are all grayed out.  Quit, Back and Forward are 'normal'.  Forward fails (no root file system is defined.)

NOW the weird part.  If I open the terminal and sudo su then do #gparted I can edit the partitions on the drive without complaint.

The issue is in the installer - not the partitioner.

I am in the process of trying to install from CD due to 8.04 to 10.04 migration failing spectacularly on this machine.  

It's twin on the other side of the table (I have two of these dinosaurs) did 8.04 to 10.04 fairly uneventfully.  The twin machine also will partition properly.

So, it appears that the partitioner in the installer is having issues with particular HDDs that gparted can handle.

I hope this helps.

I'll be trying to get a clean 8.04 install back on this machine tomorrow night.  Too late tonight to try.  I thought that the HDD branding difference might be important though.

---

### Post by darkod on 2010-05-11
> **Grench said:**
> OK - I'm seeing the same issue and I think you guys are going in the wrong direction.

Machine:  Compaq Evo P4 with an IBM Deskstar 20GB drive.

Scenarios:
10.04 installer from CD boot.
10.04 installer from Live CD desktop.

Outcome:  Step 4 of 8 Prepare Partitions - Nothing is listed.  New Partition Table, Add, Change, Delete and Revert are all grayed out.  Quit, Back and Forward are 'normal'.  Forward fails (no root file system is defined.)

NOW the weird part.  If I open the terminal and sudo su then do #gparted I can edit the partitions on the drive without complaint.

The issue is in the installer - not the partitioner.

I am in the process of trying to install from CD due to 8.04 to 10.04 migration failing spectacularly on this machine.  

It's twin on the other side of the table (I have two of these dinosaurs) did 8.04 to 10.04 fairly uneventfully.  The twin machine also will partition properly.

So, it appears that the partitioner in the installer is having issues with particular HDDs that gparted can handle.

I hope this helps.

I'll be trying to get a clean 8.04 install back on this machine tomorrow night.  Too late tonight to try.  I thought that the HDD branding difference might be important though.

In the OP case, fdisk doesn't show any drive at all, while in your case it's not shown only in the partitioner.

There is another possibility for your problem. Starting from 9.10 if a hdd has RAID settings on it, the partitioner is somehow "ignoring" it. I guess the ubuntu team decided to be too helpful and the partitioner is considering such disks as part of raid array and ignoring them for individual setup. In my personal opinion, that's going too far, but a lot of people these days want more and more things done for them automatically by the OS.

Back to the issue. You can easily check if this is your problem. Load the 10.04 in live mode, and in terminal do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending which disk it is)

If it asks you are you sure to remove settings, this was the issue. Just remove them, and it's solved. Additionally you can remove the whole dmraid package:

sudo apt-get remove dmraid

Of course, all of the above assumes you're [COLOR=Red]NOT USING RAID[/COLOR], otherwise doing that will [COLOR=Red]DESTROY[/COLOR] your array.

This "issue" started with 9.10, you would be able to install earlier version without this fix.

---

### Post by Grench on 2010-05-11
> **darkod said:**
> In the OP case, fdisk doesn't show any drive at all, while in your case it's not shown only in the partitioner.
Actually, the issue as described by the OP is 100% the same.  From what I can tell the OP wouldn't know how to open terminal, sudo and gparted from the live CD.  No offense to them.  What this revealed to me was:
1.  The hardware in the machine was responding properly.
2.  Ubuntu 10.04 CAN partition this drive
The fact that the installer dead ends here, does not recognize the partitions (even if set to and formatted as ext4 and swap via gparted) and is failing.

> **darkod said:**
> There is another possibility for your problem. Starting from 9.10 if a hdd has RAID settings on it, the partitioner is somehow "ignoring" it. I guess the ubuntu team decided to be too helpful and the partitioner is considering such disks as part of raid array and ignoring them for individual setup. In my personal opinion, that's going too far, but a lot of people these days want more and more things done for them automatically by the OS.

Back to the issue. You can easily check if this is your problem. Load the 10.04 in live mode, and in terminal do:

sudo dmraid -r -E /dev/sda (or /dev/sdb, etc, depending which disk it is)

If it asks you are you sure to remove settings, this was the issue. Just remove them, and it's solved. Additionally you can remove the whole dmraid package:

sudo apt-get remove dmraid

Of course, all of the above assumes you're [COLOR=Red]NOT USING RAID[/COLOR], otherwise doing that will [COLOR=Red]DESTROY[/COLOR] your array.

This "issue" started with 9.10, you would be able to install earlier version without this fix.

RAID?  On an ancient Compaq EVO?  There is only one IDE HDD in this box.  No room for more.  No RAID on it and the drive has been re-partitioned with the 10.04 gparted to 20GB ext4 and ~4GB as swap.

There is no RAID adapter, there is only 1 HDD, it is partitioned by a 10.4 utility - and the installer still can't see the thing.

Someone PM'd me that they were having the same issue on a 60GB Deskstar drive - is this issue due to the Deskstar (OLD Hitachi) hardware?

---

### Post by darkod on 2010-05-11
> **Grench said:**
> 
Someone PM'd me that they were having the same issue on a 60GB Deskstar drive - is this issue due to the Deskstar (OLD Hitachi) hardware?

Possibly. In most cases we are talking about newer disks so the raid settings would be my first idea.

It doesn't necessarily have to be used by you, it's enough that the disk has raid settings remains from before. I've seen this issue and people puzzled because they have never set it up in a raid.

I would still check whether

sudo dmraid -r -E /dev/sda

reports existing settings or not. And the chance of it being "too old" is still there.

---

### Post by tonefetish12 on 2010-05-11
Thank you all so much for all your help and collaboration. I know it was suggested before that perhaps I should plug into a different SATA port, and I did ... I plugged it into the one right next to it on the front of the motherboard. The motherboard has a total of 8 sata ports on it, but six of those face perpendicular to the plane of the motherboard and I neglected to try plugging into one of these until today. Guess what ... IT WORKED !!!!! Sorry for being such a tough person to help, but as I said, I greatly appreciate all of the help and feedback you all gave. It's nice to know that there's a community of people to help you out when you need it.

---

### Post by srs5694 on 2010-05-11
> **Grench said:**
> Actually, the issue as described by the OP is 100% the same.  From what I can tell the OP wouldn't know how to open terminal, sudo and gparted from the live CD.  No offense to them.

The OP was perfectly able to do this, with a bit of advice. See posts #11 and #15 for proof.

> What this revealed to me was:
1.  The hardware in the machine was responding properly.
2.  Ubuntu 10.04 CAN partition this drive

Again, see posts #11 and #15. The drive was *not* being detected -- "ls /dev/[sh]d?" returned no results, which indicates that Linux was not detecting or configuring the drive! What's more, the final successful solution (post #21) of plugging the drive into a different SATA port on the motherboard further substantiates the hypothesis that Linux just wasn't able to see the drive via one motherboard disk controller, but it did work on another one.

Your own problem appears to be very different, although some of the symptoms are the same. Old RAID data could be an issue if the disk had been used in another computer that employed RAID in the past, although I'm not going to suggest that this is certain. There are other conditions that can give GParted fits, too, such as a logical partition that ends after the disk does. (This particular problem ordinarily causes problems for the text-mode parted program, though, so it seems an unlikely cause in your case.)

It's unclear to me if you're commenting on the issues generally or if you need help. If the latter, I suggest you post the output of "sudo fdisk -l", or perhaps even the full output of the [Boot Info Script.](https://sourceforge.net/projects/bootinfoscript/) These tools will provide vital diagnostic information about your disk and its partitions. If you post the output, please enclose it between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string; that will improve legibility.

---

### Post by Grench on 2010-05-12
OK, so here is what I did last night.

Tried again with the 10.04 media - no go.  Same issue at step 4.

Tried again with the 8.04 media - no problem.  Step 4 went as expected and the full system installed perfectly.

Since I had a fresh install of 8.04 I thought I would try the online upgrade to 10.04.  It died after 2 hours after registering a failure/exit in one of the installation programs.

Tonight's plan:
1.  Try again with the 10.04 install disk - I don't think it will work, but it's worth a shot - maybe it will detect the previous installation/upgrade.
2.  Do the 8.04 install again tonight
3.  Update all 8.04 packages - I skipped this last night and went straight to the 10.04 upgrade.
4.  Try the 10.04 upgrade again.

Does anyone have an alternative suggestion rather than the above steps?

What my experimentation has shown - there is a substantial difference between the 10.04 and the 8.04 installers in step 4.  gparted has no issues seeing the drive.  8.04's step 4 has no issues seeing the drive.  10.04's step 4 acts like there is no drive.

This is one of my kid's machines - it isn't mission critical, but he would like to have it working again.

I am posting up an ongoing issue that I am having with 1 of 2 nearly identical machines.  The only difference I can see between them is a Deskstar vs Seagate HDD.  Both machines have been running Ubuntu for the last 4 years.

I will try to run the "sudo fdisk -l" from the live CD and post up the results.

I have never had to do this:
"the full output of the Boot Info Script"
Where would I find the output from that script when booting from the Live CD?  Or should I do this after I re-load 8.04 on it again - if so, fine, but I'll still need to know where to find the output file.

Thank you.

---

### Post by Grench on 2010-05-12
> **tonefetish12 said:**
> Thank you all so much for all your help and collaboration. I know it was suggested before that perhaps I should plug into a different SATA port, and I did ... I plugged it into the one right next to it on the front of the motherboard. The motherboard has a total of 8 sata ports on it, but six of those face perpendicular to the plane of the motherboard and I neglected to try plugging into one of these until today. Guess what ... IT WORKED !!!!! Sorry for being such a tough person to help, but as I said, I greatly appreciate all of the help and feedback you all gave. It's nice to know that there's a community of people to help you out when you need it.

8 SATA ports?  Wow - what kind of motherboard is it?

I'm glad you got this sorted out - it turns out you and I had different problems - I hope you don't mind if I continue my tale of woe on the end of your thread here.

Congrats!

---

### Post by darkod on 2010-05-12
> **Grench said:**
> 
I have never had to do this:
"the full output of the Boot Info Script"
Where would I find the output from that script when booting from the Live CD?  Or should I do this after I re-load 8.04 on it again - if so, fine, but I'll still need to know where to find the output file.
Thank you.

Boot the live mode, download the script, for example from my signature, and depends where it is the execution command will be different of course. For example if you move the script to the desktop (perhaps it will download there by default), execute with:

sudo bash ~/Desktop/boot_info_script*.sh

The results.txt file will be on the desktop. It's always the same folder where the script is. Only the execution command will be different depending where it is.

When posting the content of the file it's much better to manual wrap it in CODE tags at beginning and end ([/code] at end) for easier readability. There is a lot of text.
You can also do the [code] wrapping if you select the text you want and hitting the # button in the toolbar above when creating your post. It will insert the tags automatically.

---

### Post by Grench on 2010-05-16
OK, I thought I should fill in the blanks on this.

Since I had already installed 8.04 on the machine and tried (failed) the upgrade to 10.04 once, any RAID settings that may have existed were probably wiped by that.

I was able at that point to do a straight install of 10.04 onto the machine with automatic settings on step 4.

So, the drive may have had RAID settings on it from some past life - installing 8.04 seems to have taken care of those or whatever the flaky bit was with it.

The 10.04 installer - If it is going to have issues like this when encountering a RAID drive - is there any chance it can actually say so rather than just giving a blank screen and a firm stop to the install?

Anyway, I have the Compaq Evo working - mostly.  Sound didn't work until I changed the sound output to -anything but the default-.  There is something wonky going on with SuperTuxCart where it's causing the display to panic into vertical white bars whenever it goes to the cart/character selector screen - but that is a topic for another thread.

Thank you for your assistance.

---

