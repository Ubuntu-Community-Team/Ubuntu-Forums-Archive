---
title: "problem installing on internal drive."
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by hungryghost on 2011-12-19
Hello everyone, I wasn't  sure whether to post in absolute beginners as thats what I am, so please  bear this in mind when you answer, thanks!

     I have been  interested in ubuntu and linux for a while now; the reason being that  whenever I have used opensource windows software it has been superior to  commercial versions; also an article by science fiction writer Neal  Stephenson "in the beginning was the command line" made Linux sound  cool.(Using the metaphor of cars, Windows were cheap, fairly reliable  station wagons, Macs were expensively sleek sports cars, and Linux boxes  were free tanks!) I liked the idea of it, so recently I decided to take  the plunge.

      I downloaded the live CD  ISO of the latest  distribution (oneric ocelot? 11.10 I think?) It runs off the disc fine,  if a little slow. My laptop is an old packard bell notebook, easynote  K5305, running XP with about 40gb hard drive. The wireless wasn't  working, (firmware missing) but I reckoned i could sort that out later  on. (It is a broadcom card b4318 and from what I've read I should be  able to get it working)

     So I decided to install. I wanted to  keep windows at least at first (mainly for iTunes as I have an iPhone) I  therefore decided on a dual boot. I had about 16Gb of spare space on  the internal drive which I thought would be enough, as I have a 500gb  external HD (buffalo ministation NTFS) for storage.

      I  wanted to install on the internal HD rather than the external as my  laptop only has low speed USB 1.0, so I thought there might be speed  issues with running OS from external HD. My windows installation has no  problem playing movies from it, but I thought it would be better to have  it internal.

       Since wireless wasn't working in Ubuntu  I  was able to tether the laptop to my iPhone and use my 3G internet  connection. This worked fine while running from disk.
       
I  clicked "Install Ubuntu" after a short while a list of 3 requirements  came up with ticks next to them, 4.something Gb of free space, power  supply and internet connection, I selected "Next".The next screen as I  expected gave three options:
                     Install Alongside current windows installation

                     Install over current windows installation(wipe disk)

                      Something else (manual partition)

     As I wanted dual boot, I selected the first.


     This is where things departed from the script.

       The next screen gave me the option to adjust how much partition to  allow for the installation, BUT it was showing only my external 500gb  hard drive. There WAS a select drive button but only the external hard  drive (E:)was given as an option. No C:

       Ok, strange, I  thought, maybe I need to disconnect the external drive. So, I quit,  booted back into windows and dismounted and disconnected it. Tried above  steps again.

      This time, when I came to the select installation screen there were only two options:

               Install over current windows installation (wipe disk)

               Something else (manual partition)

(I can't remember exact terms used but this was the general drift!)

                Hmmmm. I was hoping not to have to do it manually, I want the user  friendly default install. Ok, maybe I CAN put it on the external drive.  At this point I am thinking that perhaps there is not enough contiguous  space on C: despite my defragmenting it all day.

             So,  I try again with the external drive connected and select the first  option, and then choose the smallest partition it will allow, which is  34Gb. This seems strange, but with slight misgivings I press onward. I  go through all the other stuff and wait about 2 hours for it to finish  installing. I assume the long time is cos of a)slower internet  connection (i had ticked boxes asking to update and install proprietry  software during install) and b) slow 1.0 writing to hard drive.

           After a long wait it announces "Successful Install, please reboot to log in."

           With baited breath I do so.

          When the computer comes back on instead of a boot menu I get an error message: 

         "error device not found e4d543ef68c...(long hex string)
GRUB RESCUE>"

       (it might have been "file not found"- stupidly I didn't write it down)


        After googling this I realised that there was a LOT to learn about this  grub prompt business (it might be very simple but it looked   complicated) and the night was wearing on; my Mrs was getting annoyed at  me being hunched over the computer so I decided to call it a day for  now.
  
       I ran the Windows recovery console, did FIXMBR and  FIXBOOT, and booted back into windows. Sure enough my external E: drive  had 34Gb missing. So Ubuntu HAD been installed on it; and presumably  some thing had been done to the bootloader because my windows boot had  been replaced with the GRUB one (I think)

       I was wondering  if the problem is that my BIOS cannot boot off an external hard drive?  But surely the boot program must have been installed on C:?

       Anyway,I realised I was out of my depth (in an inch of water)  and so  using Easeus that I downloaded I reformatted the Ubuntu partition to  NTFS and merged it with E: returning myself nicely to square one.


       My questions therefore are:

       Why would it not let me install alongside windows on internal drive C:?

        If this is not possible what is the correct way to install it on E:?


I  will be very grateful if anyone can help me get a dual boot running on  my machine, please be aware that I need fairly basic level instructions.

---

### Post by oldfred on 2011-12-19
Some of the issues that may prevent install to your internal are that you have used all 4 primary partitions, that Windows needs a chkdsk (even if XP boots), that at some point you set RAID on in BIOS (probably not on a older portable). If portable only has USB 1.0 it probably is not bootable. Grub auto installs to sda or usually the internal drive as that is usually the boot drive. If BIOS gives option to boot USB devices it will show it or show it as another hard drive that it can boot. One time boot key if you have it (f12 on my system) also will show it.

From liveCD terminal post this (you can just copy & paste.
```

sudo fdisk -lu
```I prefer to partition in advance with gparted from liveCD and then use manual install (Something else) to choose the / (root) partition. If swap has been set up already it will find it automatically. If you had more room, I might also suggest a separate /home but if most of your user data in elsewhere you can easily backup /home if you want to reinstall.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Gparted would not show my sda drive and took forever to show the other drives. I ran chkdsk on sda1, my XP NTFS drive. Then gparted showed the sda drive. Also xP booted a bit faster 3-4 minutes instead of 5 minutes.

---

### Post by hungryghost on 2011-12-20
OK, thanks for taking the time to answer. I'm not sure I understand everything, I think i need more detailled instructions how to manually install on C:, but I imagine I can find them online.

        As far as the issues preventing the automatic install on C:

       I had ran CHKDSK f/ regularly, and immeadiately before the install.

       My C: drive only has the one partition (ie is not split into partitions) with my windows installation on it.

       I don't think RAID is set on my BIOS (although don't know what that means!)

       There is no option to boot from USB device in my BIOS menu.

       So does this mean I cannot install ubuntu to the external drive? Because it cannot be booted from? 

       What will:
sudo fdisk -lu                                     do?    Is it like CHKDSK?

       So if I am to install it on C: I need to create 3 additional partitions on it? About 10GB for main OS then 2GB for home and 2GB for swap. And its better to do this before starting the install using Gparted, rather than using "something else"  to do the partitioning as well as manually install?

      This is a total of at least 14GB. Since I have only 16GB free on my C: drive I am worried this will be cutting it a bit fine. Could it be this lack of room that caused the installation proccess not to allow me to install alongside windows automatically.?It seems strange that the menu only suggests that you need 4.4 GB.  I guess it is out of date.

      I could probably make more space by deleting or moving some windows programs to E:


        I don't think it will detect swap, as the installation was on E: and as I say I have reformatted and merged the partition so I could start again from scratch.


        Anyway thanks once again for your help.

       I think what I need now is  detailed instructions on how to manually install Ubuntu to the 16GB of free space I have on my C: drive.  I get what you have told me but I don't quite understand how to do some of your instructions. 

       ie: I know how to create a 10GB partition and format it to ext4 (i think!) but not sure what you mean by mountpoint,  what else do I need to do?

      If you or anyone else could give me a few more pointers I would be very grateful. 
I wish I knew more about this stuff, but I'm eager to learn.

---

### Post by hungryghost on 2011-12-20
Sorry I'm being really stupid today. I'm meant to type that command in and post the result arent I? Bear with me I will do so later. Don't give up on me!

---

### Post by darkod on 2011-12-20
Manually installing (using the Something Else in the latest version) should always be the best way. That gives you most control.

First, if you are running only ONE internal hdd (and only in this case), make sure you have no raid meta data left over. If there is, the ubuntu installer will ignore the disk. This might be the reason it didn't report it.

Boot with the ubuntu cd in Try Ubuntu live mode, and in terminal execute:
sudo dmraid -E -r /dev/sda

If that asks you to remove the meta data, it means it was there.

Second, you need to make unpartitioned space for ubuntu on your int hdd. Since XP doesn't have a built in tool for this, you can either use some windows software or again the ubuntu cd in live mode and using Gparted. With Gparted shrink the partition as much as you want (but it can't shrink more than the free space you have on it). DO NOT proceed to install ubuntu right away. Boot XP and run the chkdsk again and reboot few times.

Third, once XP is happy, boot with the ubuntu cd and now start the install. If you decide to use the manual way, the partitioning goes like this:

partition for root /, create as ext4, logical, mount point /
partition for /home, ext4, logical, mount point /home
partition for swap, swap area, logical, doesn't have mount point

That's it. When considering the partition sizes take into account that you need some more space for /home than the 2GB you stated earlier. It will work with 2GB but you have to be aware that the total you can store in your Home folder will be 2GB of course.

---

### Post by hungryghost on 2011-12-20
Ok thanks, I get it now I think. I will try this. I have burned a Gparted live cd from ISO. I assume I can use this. So I can shrink the windows partition down as much as possible; do I need to leave it a bit of wiggle room? I will report back when I have tried these things

---

### Post by oldfred on 2011-12-20
Windows likes lots of wiggle room. NTFS partitions work best with 30% free space, start to slow at 20% free and at 10% you just about cannot do much. Of course Linux type partitions need some free space and it actually hides 5% to help prevent you from running out and causing issues.

If using only 16GB, do not create the separate /home, just leave it inside / and create just / & swap.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Herman's guides are very complete, some thing too much for a beginner, but if you want to know details his site it the one to review. Install process is essentially the same across versions with only minor differences in screen presentation. The main new difference is which gui is the one you end up wanting.
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by hungryghost on 2011-12-20
Ok thanks again...I will have a look at those;I think I'm going to definately have to clear some space. Is it woth me looking into xubuntu I believe that is a smaller version? In the mean time here are the results of sudo fdisk -lu:Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x968d968d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78124094    39062016    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000d98e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976771556   488385747    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 

    thanks once again for your time and patience in assisting a beginner.

---

### Post by hungryghost on 2011-12-20
The results of @sudo dmraid -E -r /dev/sda were as follows:


no raid disks and with names: "/dev/sda"



    I guess this means that wasnt the problem? Still at least thats eliminated.

---

### Post by hungryghost on 2011-12-20
Ok so I was beginning to think this was a non starter. 16 GB didn't really seem enough and that was leaving windows with nothing to spare. I was thinking about it and I was sure I had more space on C: a few months ago. I was in the shower and wondering if I had the balls just to commit fully to Ubuntu and wipe windows altogether.... But then I thought of iTunes. I know you can get your iPhone to work with Ubuntu but it looks like a pain. Then it struck me... Every time I sync my Phone it backs up it's contents....
Sure enough when I checked there it was: iTunes media folder hogging 8 Gb on my hard drive! 

Fantastic. I've moved it over to E: now I have 20 GB to give to Ubuntu and can leave 4Gb for windows to breathe in. I'll have another crack at installation when I get chance.

---

### Post by darkod on 2011-12-20
> **hungryghost said:**
> Ok so I was beginning to think this was a non starter. 16 GB didn't really seem enough and that was leaving windows with nothing to spare. I was thinking about it and I was sure I had more space on C: a few months ago. I was in the shower and wondering if I had the balls just to commit fully to Ubuntu and wipe windows altogether.... But then I thought of iTunes. I know you can get your iPhone to work with Ubuntu but it looks like a pain. Then it struck me... Every time I sync my Phone it backs up it's contents....
Sure enough when I checked there it was: iTunes media folder hogging 8 Gb on my hard drive! 

Fantastic. I've moved it over to E: now I have 20 GB to give to Ubuntu and can leave 4Gb for windows to breathe in. I'll have another crack at installation when I get chance.

Seems like you found a big piece of the puzzle. :)

---

### Post by hungryghost on 2011-12-20
Yes it looks like it. I'm very pleased.


        So now I've got more space, I think, having learned a little more about it, I will try and go for the manual partition. What would you (and anyone else) recommend to maximise performance of both OS, given the extra space I have:
  
     For windows partition (windows is now using 16GB I am thinking 4GB free space?)

      For root/ (10-12GB?)
      For /home (3-4GB?)
      For swap (3-4GB?)


     Does this sound about right?

      Also the recommended procedure is to shrink windows partition to desired size using Gparted. Then run Chkdsk again. Then run the Ubuntu install and select something else to partition and install?

---

### Post by oldfred on 2011-12-20
I would still keep /home inside / (root). You do not have enough space and whether you will use more for programs or for user data is not known yet. So if both are in one partition you share the unused space. You still should backup /home as it has all your data and user configuration files.

---

### Post by hungryghost on 2011-12-21
Ok thanks oldfred, those hermann guides are exactly what I was looking for; not just instructions but explaining to me what's going on. I'm going to educate myself a bit before going any further!

---

### Post by hungryghost on 2011-12-21
Ok; I think I'm ready to go. Im glad it turned out this way as Ive learned  more about partitioning and filesystem than i would have had the autioinstall gone to plan. 
        Everything i have read suggests a swap area of 2GB. i only have 512 MB RAM; is there any benefit to increasing swap area further? My current plan is 
          17GB Windows(primary)(12+5 free NTFS)

           17GB /(logical ext4)

            2GB swap (logical ext4)
     
              One more question: since I have a 500gb Ntfs external drive I don't think I need to leave a shared Ntfs partition on internal drive?

---

### Post by darkod on 2011-12-21
> **hungryghost said:**
> One more question: since I have a 500gb Ntfs external drive I don't think I need to leave a shared Ntfs partition on internal drive?

It's up to you. If you have that disk connected all the time, both windows and ubuntu will be able to access it so no need to have a shared partition on the internal disk.

PS. Have in mind that transfer rate is slower for ext hdd compared to int hdd.

---

### Post by hungryghost on 2011-12-21
Excellent; that's what I thought. Access is slightly slow but it hasn't been a problem. I was worried it wouldn't be able to play video from it but its been fine with XP. So can Ubuntu write to NTFS or just read?

---

### Post by darkod on 2011-12-21
> **hungryghost said:**
> Excellent; that's what I thought. Access is slightly slow but it hasn't been a problem. I was worried it wouldn't be able to play video from it but its been fine with XP. So can Ubuntu write to NTFS or just read?

Read and write, no problem.

---

### Post by hungryghost on 2011-12-21
Ok when I go into Gparted there is an exclamation mark in a red circle next to dev/sda1 and it will not let me drag the right edge to resize it. What does this mean please and how can I fix it.? There also seems to be 7MB of unallocated space on the drive, is this relevant?
     Thanks in advance, this is driving me mad now!

       Also in the rsize/move window it says Free space preceding 1 (in red), free space following 6MB (in black)

(edit:ok it was only red cos it was highlighted!)

---

### Post by hungryghost on 2011-12-21
ok.....it says my HD has over 53 bad sectors!!!!! And cannot be resized! This is dissapointing news! Is ther any remedy?




........i think I'm screwed aren't I?

---

### Post by hungryghost on 2011-12-21
Ha take that Gparted...I just used Easeus to resize my windows partition and then created / root and swap using Gparted. Hopefully I'm on my way....should be going to bed but I need to do this!

---

### Post by hungryghost on 2011-12-22
Alas....the installation proceeded fine to 'ready when you are', then afterwards hung up at 'configuring target system'. Guess its those bad sectors taking their revenge! Gonna try again now without downloading updates and third party software.  If this fails I might have to look at a new C: drive.
Its an old notebook laptop and when I first got it it was crashing all the time. I fixed that with BIOS update and reinstall Windows,but it still kept shutting down at random. Eventually realised it was overheating; got one of those cooling fan platforms and its been fine since.
      I reckon  that may have caused damage to C: !

---

### Post by hungryghost on 2011-12-22
Ok thanks both of you for your time and patient help. Ubuntu 11.10 is now running a dual boot on my laptop. Next project: install updates and get wireless working.

---

