---
title: "too Feisty to install!!"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2007-08-06
Specs: P965 Neo mobo, 2x 1024MB OCZ XDDR, NVidia GF 7600GS, Seagate Barracuda 7200.10 250GB HDD.

After toiling to get a working Live CD of Feisty (Thanks merlinus for the recommendation of InfraRecorder), I got feisty up and running, even surprising myself that it can now find the HDD that has been so elusive (see my previous troubles: [http://ubuntuforums.org/showthread.php?t=518071](http://ubuntuforums.org/showthread.php?t=518071)). I had to go through the install process 3 times, the first hanging up somewhere after 72% when I wasn't paying attention, the second when I restarted and made the mistake of leaving the room, and the third which appeared successful. 

I removed the Live CD after install and restarted, noticing everything to look as expected, and then....

"GRUB loading, please wait.....
Error 21"


and it freezes. I've searched the forums and see no mention of this error, unless I'm not searching correctly. Once again I turn to the Ubuntu Gods to shed some light on this problem, pray tell what to do next?!

---

### Post by merlinus on 2007-08-06
Boot from live cd, go to a terminal and post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by joe.turion64x2 on 2007-08-06
I am afraid your problems with the hard disk are not over yet:
> Error 21 means :
"
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.
"
[https://launchpad.net/ubuntu/+source/grub/+bug/8978](https://launchpad.net/ubuntu/+source/grub/+bug/8978)

Joe.

---

### Post by sp0nge on 2007-08-06
upon your advice, the terminal returns:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14972   120262558+  83  Linux
/dev/sda2           29043       30401    10916167+   5  Extended
/dev/sda3   *       14973       29042   113017275   83  Linux
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris
/dev/sda6           29043       29644     4835502   82  Linux swap / Solaris

Partition table entries are not in disk order

Might this have anything to do with my changing the partitioning options on the third try? Rather than selecting the second option to use the whole HDD, I selected the first option of a guided partition.

---

### Post by Pumalite on 2007-08-06
Follow these guidelines: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by merlinus on 2007-08-06
Hey Pumalite -- here we go again with a partition table that does not match the blocks.

:)

He also has two swap partitions.

:mrgreen:

My advice -- start over and partition the entire disk.

-merlin

---

### Post by sp0nge on 2007-08-06
Just to see what would happen, I tried to install again. This time I partitioned the entire disk. Surprisingly, we had forward progress as the install was successful. Or so I thought. Upon rebooting, I still get Error 21. 

I just don't understand how I can use the drive in windows (before I started formatting everything) and Feisty can see the hard drive when I try to install... but GRUB 1.5 seems to loose his way!

---

### Post by merlinus on 2007-08-06
Once again, run and post results of:

```

sudo fdisk -l

```-merlin

---

### Post by sp0nge on 2007-08-06
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

---

### Post by merlinus on 2007-08-06
This is lots better than before! 

Try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```Substitute results from find for (hdx,x).  I would expect (hd0,0).

-merlin

---

### Post by sp0nge on 2007-08-06
You presumed correctly, hd0..

upon setup (hd0) it returned:

Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by merlinus on 2007-08-07
Did you restart?  If not, do so and report back.

-merlin

---

### Post by sp0nge on 2007-08-07
Still with the Error 21. :(

---

### Post by sp0nge on 2007-08-07
My brain is trying to pop out of my head! I've been working on this for 2 days straight now and feel like I've made little progress in spite of the few small victories. 

I'm going to get a little shut eye until this problem rattles around in my head long enough to bring me back to the office.

Please don't hold back, I'll be here in a couple hours to scour for more possible solutions. If you come across something that might help, lay it on me! I'm up for anything at this point!

Thanks for all your help so far, Merlinus. You've helped educate me if nothing else.

---

### Post by merlinus on 2007-08-07
I suggest downloading and burning SuperGrub to see if it will boot ubuntu.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If you need more instructions on how to use it:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Pumalite on 2007-08-07
> **merlinus said:**
> Hey Pumalite -- here we go again with a partition table that does not match the blocks.

:)
He also has two swap partitions.

:mrgreen:

My advice -- start over and partition the entire disk.

-merlin

Hey Merlin, one day I'm going to learn to read the post before answering it. Cheers.

---

### Post by sp0nge on 2007-08-07
Perhaps you can help me figure a way to burn sgd while running my Live CD? I only have one optical drive. I'm going to try to reboot and see if there is anything left of my windows partition (highly unlikely).

---

### Post by sp0nge on 2007-08-07
As I suspected, I only got Error 21 upon booting to the HDD. All I Have is this live CD unless I load windows again (ACK!) 

I tried to burn sgd but when my system looked back at the live CD to find a  blank, it hung up.

---

### Post by merlinus on 2007-08-07
Use a friend's computer to burn SuperGrub.

-merlin

---

### Post by sp0nge on 2007-08-08
Ok, so what am I missing??!!??

I made it to another maching to download and burn sgd. I first downloaded sgd_0[1].9598.iso.bz2 and burned the image again using InfraRecorder. That was no help, after burning the disk wouldn't boot and when I looked at it through windows explorer, it was blank!!

I went back to download sgd_curent.iso, repeated the process, and found still a blank disk!?

---

### Post by logos34 on 2007-08-08
did you unzip/extract it first?  It's a .bz2 archive.  Right-click on it>extract here (not sure if windows can do .bz2 format--might need to use 7-zip).

---

### Post by sp0nge on 2007-08-08
In repeating the process from the beginning once more, I thought I had progress. I Downloaded sgd_0.9588.iso once more and went to burn the image. It hung for about 10 minutes then displayed failure messages. 56 gets 0 fills, the disk is still empty.

---

### Post by sp0nge on 2007-08-08
No, Logos, I did not. In looking, I see .ISO, .ISO.BZ2, ,ISO.GZ, .IMG, and .IMG.GZ files!! Why do I not see a .ZIP file?

---

### Post by sp0nge on 2007-08-08
In reading more on the website, it directs me to download the .ISO since I'm on a windows machine at the moment. Each time I do so, I start to burn the image in InfraRecorder. It starts, then the status says "waiting for reader process to fill input buffer" where it hangs before telling me the following:

"Input/output error. send opc: scsi sendcmd: retryable error."
"OPC failed"
"fifo had 56 puts 0 gets"
"fifo was 0 times empty and 0 times full, min fill was 100"

---

### Post by logos34 on 2007-08-08
i don't see a zip file either...have you tried this one:
[http://download.forjamari.linex.org/supergrub/SuperGrubDiskCdromENGLISH/0.9550/](http://download.forjamari.linex.org/supergrub/SuperGrubDiskCdromENGLISH/0.9550/)

---

### Post by logos34 on 2007-08-08
Or try a different burning program--Alex Feinman's IsoRecorder is well-regarded:
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

not sure what else to suggest

---

### Post by sp0nge on 2007-08-08
Thanks again for the help, I feel like you're leading me in the right direction~ it's so close I can taste it. 

I downloaded the .ISO you led me to, and tried to install it with InfraRecorder. Still I got the error messages, so I installed IsoRecorder and followed the direction. It seemed like it would work, then I've gotten an error each of the 4 times I've tried to burn the image~ something about the drive interface couldn't be initiated to close the disk. 

Could be something wrong with the disk which means I need to find another machine to get this done correctly. 


I'll check back for any more input available, please don't hold back. I'll post again once I get to another machine to try the burn.

---

### Post by logos34 on 2007-08-08
well, if you're having trouble no matter what image burning application you use, and you've tried different cd's (ruling out faulty media), then it may be the cd burner which also seems to be having trouble reading the sgd iso disk you downloaded and burned on a different machine.  Maybe it's merely the lens which is dirty.  Or maybe it's kaput.

---

### Post by sp0nge on 2007-08-08
My thoughts exactly. Rather than waiting until I have s friend home from work, I ran and stole the kid's machine from his room. I brought it into the office and hooked 'er up thinking that if something were wrong with my buddy's machine, I should certainly be able to get around it on another machine. 

I installed InfraRecorder, and get the same "Input/Output error"!~

I installed IsoRecorder, and get the same "Interface can't be initialized to close the disk"

to make it worse, what ever is being written to the disks simple "kill" them to the point they're unusable!

At least now I know it's not my buddy's PC, but I'm totally at a loss! This makes day 4 with no end in sight. Could it be that I've found (or even worse, BUILT) a michine that won't run ubuntu?

---

### Post by sp0nge on 2007-08-08
I REFUSE TO GIVE UP!!!!!!!!!

On to the next post, hopefully to spark more ideas in us all- I just don't understand!

[http://ubuntuforums.org/showthread.php?p=3154763#post3154763](http://ubuntuforums.org/showthread.php?p=3154763#post3154763)

---

### Post by psusi on 2007-08-08
Sounds like either your burners are broken or you have some messed up software installed on both computers.

---

### Post by sp0nge on 2007-08-08
Both burners are confirmed to be working and the InfraRecorder software worked perfectly to burn the ISO of feisty.

---

### Post by psusi on 2007-08-08
So you can burn the feisty iso but not the super grub disk?  That is messed up...

---

### Post by sp0nge on 2007-08-08
agreed.

I intend to go to another house this evening and try again, any other ideas or suggestions?

---

### Post by warnec on 2007-12-04
I don't know if it would help you, but if i were you i would try **Alcohol 120%**
[www.alcohol-soft.com/](www.alcohol-soft.com/)
And use trial version to burn .iso . The difference between this program and others is that it is specially designed to burn pirated games and such stuff, so it has got many tools to correct errors and such (which appears as a consequence of breaking copy protenction, lol). Just try it.

---

### Post by Pumalite on 2007-12-04
You can also try ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Download and install.
Go to Mode>ISO>Burn

---

### Post by warnec on 2007-12-04
> **Pumalite said:**
> You can also try ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Download and install.
Go to Mode>ISO>Burn
I second that. It is very well-known and reliable program.

---

