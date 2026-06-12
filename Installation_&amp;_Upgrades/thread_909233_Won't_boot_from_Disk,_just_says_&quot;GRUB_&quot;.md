---
title: "Won't boot from Disk, just says &quot;GRUB_&quot;"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Buckeyes69 on 2008-09-03
I have a Toshiba (M35-S456) laptop with 2GB of Ram.

I installed ubuntu with no problems.  When I boot... there is just a black screen with the word "Grub_".  None of the keys work...they just beep.

If I load with the Live CD and select "boot from hard disk" it boots up and works perfectly (wireless card & graphics).  Take out the CD and reboot, same problem it doesn't boot from hard disk.

I went into terminal and made sure the flag for the main partition said /boot. 

Most of the answers I searched gave some sort of command prompt...mine just stops at the word GRUB_ and no keys work.  Is this part of the natural boot process?  Do I need to wait it out?

---

### Post by louieb on 2008-09-03
Sounds like things did not go right when GRUB was installed. Its easy to fix with the Ubuntu Live CD.  [IDBS Restore Grub w/LiveCD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")   based on this thread [How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck") 

They show how to use the **grub>** prompt to fix this type of boot problem.
 
In your case you could just use the live CD to boot the hard drive install  and follow the instructions.   

Post back if you have questions. Good Luck.

---

### Post by Buckeyes69 on 2008-09-06
followed those instructions, it appeared to install...but still isn't working.

I ran GPARTED and it shows the following devices:

/dev/scd0 (172.57 MiB) unallocated (no flags)

/dev/sda1 ext3 (mount point /) 71.45 GiB  2.86 GiB used This is flagged as the boot

/deb/sda2  extended  ---
/dev/sda5  linux-swap  ---

During install...I selected "Guided" use whole drive...or whatever that options was. I'm not trying to dual boot or keep windows...appreciate any pointers

---

### Post by caljohnsmith on 2008-09-06
When you did the "find /boot/grub/stage1" command in grub, what did it return? And did Grub say it successfully installed after you did the "setup (hd0)" command? Also, please post the output of:
```
sudo fdisk -lu
```

---

### Post by Buckeyes69 on 2008-09-06
Additional Info
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7e3f7e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris
brian@Toshiba:~$

---

### Post by Buckeyes69 on 2008-09-06
grub> find /boot/grub/stage1
 (hd0,0)

grub>

On reboot it just says "GRUB_" (flashing cursor)..I hit space, esc and enter with no results.  eventually the keys just beep

---

### Post by Buckeyes69 on 2008-09-06
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

---

### Post by Buckeyes69 on 2008-09-06
read in another forum that an install on a Toshiba laptop (like mine) that has express media player (like mine) has had some issues.  The Express media player is installed in the first 15 sectors...deleting this can solve the issue.  However, I don;t have windows installed anymore.  Could this be the unallocated space that is showing up?  What if I partition that and rename it?  Is having unallocated space normal? I don't use the express media player, but I'm not sure how to delete it.

---

### Post by caljohnsmith on 2008-09-07
> **Buckeyes69 said:**
> read in another forum that an install on a Toshiba laptop (like mine) that has express media player (like mine) has had some issues.  The Express media player is installed in the first 15 sectors...deleting this can solve the issue.  However, I don;t have windows installed anymore.  Could this be the unallocated space that is showing up?  What if I partition that and rename it?  Is having unallocated space normal? I don't use the express media player, but I'm not sure how to delete it.
When you say the express media player is installed to the first 15 sectors, do you mean the first 15 sectors of the HDD or of the partition? 

Also, sometimes Grub can seemingly install OK but return errors later if your partition table is somehow messed up. It would be worth checking it at this point I think. Do you have internet access from your Ubuntu Live CD? If you do, try the following from the Live CD:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by Buckeyes69 on 2008-09-07
This is what I got (not sure about which sectors).  I assumed that when I installed ubuntu using the entire disk it would wipe everything.

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1  9326 254 63  149838192
 2 E extended              9327   0  1  9728 254 63    6458130
 5 L Linux Swap            9327   1  1  9728 254 63    6458067


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

---

### Post by caljohnsmith on 2008-09-07
OK, that's good, looks like your partition table must be OK. I'm wondering if you have some sort of hardware issue at this point, or maybe BIOS related. Before you installed Ubuntu, did you previously have a working version of Windows on that HDD? 

Also, please do the following command:
```
sudo dd if=/dev/sda bs=512 count=20 | gzip -c > ~/Desktop/sda.bin.gz
```
That will create "sda.bin.gz" on your desktop, and if you will attach it to your next post (click the paperclip icon in your message), I can take a look at it and see if the Grub stage1_5 file did indeed get embedded. That will help us figure out if the first sectors of your HDD have stuff related to media direct or to Grub.

---

### Post by Buckeyes69 on 2008-09-07
Yes and no on the windows. I had windows xp proffessional installed...but I could never get the wireless adaptor working.  All the drivers on the toshiba website didn;t work (blue screen of death)...which is why I went Ubuntu.  I spent hours installing toshiba drivers that windows didn't have (sound, video, ethernet)...I installed Ubuntu and it ALL worked, right from the start.  Down to the advanced features of the touch pad and the wireless that I'm using now.  

When I boot from CD and select boot from hard drive everything boots fine.  Does that use Grub from the CD to boot the HD?

---

### Post by caljohnsmith on 2008-09-07
Your sda MBR looks perfectly fine from what I can tell, which would make sense since I missed that you previously mentioned you could boot your HDD from the CD. I think there's a strong chance the problem is with your BIOS settings. Try tweaking some of your HDD settings in BIOS, but make sure you write down the original settings so you can change them back. If you need help with it, post which HDD settings you have in BIOS, and we can go from there.

---

### Post by listener on 2008-09-07
Did you say which version of Ubuntu?  I installed Intrepid Alpha 4 Sep 01 build, on my other box, and it gave the same type problems with grub.  This happened three installs, and I finally had to use a bootable ISO (burn to cd) called "Super Grub Disk".  You might try that.  It will install grub properly after finding your Ubuntu location and boot files, and has a menu.  Sounds like your problem is only with the installation/operation of grub.

My checksum was fine.

---

### Post by Buckeyes69 on 2008-09-07
I tried the Supergrub disk as a bootable ISO.  Repaired the grub install with no success.

I installed version 8.04 from a bootable CD.  As for the BIOS, It is Phoenix Bio 1.5.  There really aren't very many options available.  It lets me select the boot order (CD first then hard drive).  Is there a way to access more advanced settings?

---

### Post by listener on 2008-09-07
Is the Express Media Player, something in the computer's BIOS?  Not from either OS?  As in, it will work without booting an OS?

That may need to be gotten rid of, if it is at the very beginning of the hard drive.  I would have suggestions as to how, but they'd possibly make things a lot worse. 

good luck

---

### Post by meierfra. on 2008-09-07
I suggest to  install Grub without the stage1.5 files. This can be done fairly easily with SuperGrub:  [http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

Or you can use Lilo instead of Grub: [Herman's Lilo Page]("http://users.bigpond.net.au/hermanzone/p4.html")

---

### Post by caljohnsmith on 2008-09-07
> **meierfra. said:**
> I suggest to  install Grub without the stage1.5 files. This can be done fairly easily with SuperGrub:  [http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

Or you can use Lilo instead of Grub: [Herman's Lilo Page]("http://users.bigpond.net.au/hermanzone/p4.html")
Just for my own understanding, meierfra, I'm just wondering how will installing Grub in the MBR without the stage1_5 file help? Buckeyes69 did mention that he can boot his HDD fine from the CD, but he just can't boot the HDD directly on start up. Maybe I'm interpreting this wrong, but wouldn't that mean his embedded stage1_5 file must be OK since he can at least boot his HDD from his CD? Do you think this kind of behavior could be caused by a BIOS issue?

---

### Post by meierfra. on 2008-09-07
> Maybe I'm interpreting this wrong, but wouldn't that mean his embedded stage1_5 file must be OK since he can at least boot his HDD from his CD?

You are probably right. But since the stage1.5 files are known to cause problems with the Express Media player, I  think one should see what happens if Grub is installed without the stage1.5 files.

---

### Post by Buckeyes69 on 2008-09-07
The express media player was supposed to play DVD's & CD's without booting the OS.

I tried Supergrub disk and a reinstall of Grub without 1.5 files.  This did not work.  I then tried to install lilo, since it said some things about not installing in the same locations.  I got the following message when I tried to configure lilo:

 WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device                           &#9474; 
 &#9474; UUID=997ed345-fa50-4ef3-9d99-17d89938eb3e as the root filesystem device.  &#9474; 
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474; 
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474; 
 &#9474; as a RAID array) which this simple configuration program does not         &#9474; 
 &#9474; handle.                                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.                        

to my laymens eye, this sounds like the media player is in fact written to the first section.  I don;t use it.  Is there some way I can remove it completely.

---

### Post by Buckeyes69 on 2008-09-07
nevermind...the power of reading just a little further.

---

### Post by Buckeyes69 on 2008-09-07
OK, finally some success.  I installed lilo and rebooted.  The screen shows the splash page and then "Loading Lin_2.6.24img0....."  it hung there for quite a while...just as I was about to reboot, some more text followed and the boot process completed...yeh!.

To dispell the notion that beggers can't be choosers.  Knowing that this works, can I go back to Grub or find some way to expedite this boot process?

---

### Post by Endolith on 2009-02-13
I got the same problem last night out of the blue.  This is a brand new hard drive that I installed 3 weeks ago.  I cloned my old drive and then reorganized the partitions on the new one.  I [had some problems with the partitioning, but fixed them]("http://ubuntuforums.org/showthread.php?t=1054064&page=2") and considered myself finished with that stuff.  It's been working fine for two weeks.

I can't think of anything that I've done since the last reboot that would have affected the MBR or partition table.  Possibly installing [SeaTools]("http://www.seagate.com/www/en-us/support/downloads/seatools/") and running the drive self test?  That's all I can think of.

Does the unresponsive **[FONT=Courier New]GRUB_[/FONT]** prompt mean that it can't get beyond stage 1?

> The MBR contains GRUB stage 1. Given the small size of the MBR, Stage 1 does little more than load the next stage of GRUB (which may reside physically elsewhere on the disk). Stage 1 can either load Stage 2 directly, or it can load stage 1.5: GRUB Stage 1.5 is located in the first 30 kilobytes of hard disk immediately following the MBR. Stage 1.5 loads Stage 2.I'm not sure if mine has a stage 1.5 or not.  How does that work?

I was too frustrated to really dig into it late last night, but I did boot into System Rescue CD and run GParted, and it saw all my partitions fine.

---

### Post by caljohnsmith on 2009-02-13
Hi Endolith, sorry to hear you are having booting problems now. In order to get a clearer picture of your new setup as far as booting is concerned, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Endolith on 2009-02-13
It says "No boot loader is installed in the MBR of /dev/sda"

I have no idea why that would happen.  I can just re-install grub to it, but I'll backup the MBR first to see if I can figure out what happened?

---

### Post by Endolith on 2009-02-13
I re-installed GRUB and I'm back in.  It looks like something changed the first three bytes of the disk to zeros? (00 00 00 00 -> EB 48 90 00 fixed it, and the first three bytes [are apparently a jump instruction]("http://www.geocities.com/thestarman3/asm/mbr/GRUB.htm").)  I ran SeaTools in every way that I ran it the other day and it hasn't changed the MBR, so I have no idea what did.  Should I be worried?

---

### Post by addisor on 2009-07-29
I have 9.04 and an XP dual boot, been running 2 days. was using XP and restarted to get back to Jaunty and stuck at GRUB 1.5 flashing and restarting the loop. Put in the live CD and run the script you suggested. can you advise any suggestions. not tried anything yet. i've attached the script results

---

### Post by Endolith on 2009-07-29
> **addisor said:**
> I have 9.04 and an XP dual boot, been running 2 days. was using XP and restarted to get back to Jaunty and stuck at GRUB 1.5 flashing and restarting the loop. Put in the live CD and run the script you suggested. can you advise any suggestions. not tried anything yet. i've attached the script results

It looks like your MBR is broken?  "Unknown MBR on /dev/sda"

This article is good for learning GRUB:

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

To re-install GRUB to the MBR, you do something like this:

```
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

```

---

### Post by addisor on 2009-07-29
got this 
      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Tried (hd,04) and it worked, now for a reboot

grub>

---

### Post by Endolith on 2009-07-29
Well you can't just copy that and expect it to work.  You need to figure out which hard drive you're booting from, which partition has GRUB on it, etc.

---

### Post by addisor on 2009-07-29
All sorted, thanks for your help, i had (hd0,4)

---

### Post by Endolith on 2009-07-29
> **addisor said:**
> All sorted, thanks for your help, i had (hd0,4)

Great!  Now try to figure out why it happened.  Run that script again and see what the changes were to your MBR.  If it's a random error, you should check your hard drive for errors and you might need to replace it.

---

### Post by addisor on 2009-07-29
I ran the script again and can't really tell what I am looking for. I've attached the results, in case an error is evident.

---

### Post by Endolith on 2009-07-29
> **addisor said:**
> I ran the script again and can't really tell what I am looking for. I've attached the results, in case an error is evident.

Oh, I guess it doesn't dump the MBR if it knows what it is.  I'm not sure where in that script is the command for dumping the MBR, but this should work:

```
sudo dd if=/dev/sda of=mbr.bin bs=512 count=1
```

Always be careful with the dd command and make sure you've thought through what it does first, since it can easily destroy your hard drive.

---

### Post by addisor on 2009-08-07
sorry for late reply, been busy. Can you just explain what that command will do? i'm expecting it to dump MRB to file for reading?


just tried it and got

1+0 records in
1+0 records out
512bytes (512 B) copied, 7.0679e-05 s, 7.2 MB/s

---

### Post by Endolith on 2009-08-07
> **addisor said:**
>  just tried it and got

1+0 records in
1+0 records out
512bytes (512 B) copied, 7.0679e-05 s, 7.2 MB/s

Yes, that's what it does.  Now post the .bin file so we can look at what changed.  You can also view it in a hex editor like Bless.

---

### Post by jadhav333 on 2009-08-12
May I bring any of you all's (experts) attention to a similar problem of mine.. at this link.. 

**[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1235484[/COLOR]**

I have updated my fdisk & Boot script info there.. 
**Pls help me resolve it..**
Thanks

---

