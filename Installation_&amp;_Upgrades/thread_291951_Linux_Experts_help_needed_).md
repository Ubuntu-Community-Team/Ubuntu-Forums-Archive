---
title: "Linux Experts help needed :)"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by Ma$$imo on 2006-11-03
I am new to GNU/Linux and Ubuntu -- I have just been testing Ubuntu 6.10 on VMware from WinXp. 
I like it a LOT!!! I am about to install it on my ASUS L5 Laptop with Dualboot (WinXp + Ubuntu).

Now I&#8217;ve come across with some specific issues:
1. I installed Partition Magic 8, started it and saw that my HD (60Gb) is divided into recovery disk of 2Gb and a 58Gb Primary disk with NTFS file system. Is there a way to free up some space at the end of this disk (say 10Gb) to create a Linux partition there or I HAVE to format my HD and re-install WinXP as well.

2. Question: when I install Ubuntu on a computer with WinXp what OS will be then launched first by default. I guess WinXP? Then how should I manage to have GRUB launching when I turn on the PC? Through NT Loader?

3. When I turn on my laptop with Ubuntu LiveCD inserted into CD-drive it doesn&#8217;t load automatically. Pressing &#8216;Del&#8217; I get into &#8220;kinda BIOS&#8221; which doesn&#8217;t give a selection of drives to load except for A: which in fact is a FlashCard inserted into USB slot. :(
Maybe copy Super Grub Disk to USB?

---

### Post by tombeharrell on 2006-11-03
Your current partitioning is no problem. The ubuntu installer's partitioner will be able to resize your NTFS partition down to give you space for the ubuntu partition (and a swap partition). It's straight forward but read the prompts carefully so you don't destroy the Windows partition.

Ubuntu will install Grub and add the Windows to the end of the list, Ubuntu will be default. You can edit the grub menu later from Linux.

Not sure about your boot up sequence problem though, is there another page of the bios with boot up sequence? It's very unusual that you can't boot off CD.

---

### Post by mark_g on 2006-11-03
1. In partitionmagic, resize the ntfs disk, so you have 10gb of free space. Then you can create a new partition there (doesn't matter much which type, because ubuntu will convert it to ext3 during install). You may want to use a bit more space, so you can also have a swap partition if you don't have much RAM.

2. Grub will autodetect that you have Windows XP installed too and it'll prompt you a menu when you boot up your pc. I'm not sure, but I think Ubuntu is booted by default. However, you can easily edit /boot/grub/menu.lst to boot Windows XP by default. You won't need ntloader, because Grub is installed by default.

3. You'll have to change your boot order, so it'll first boot off the CD-ROM before the hard drive. How to change this depends on the type of BIOS software you have.

Let me know if you need more help.

---

### Post by Ma$$imo on 2006-11-03
Thank you *mark_g* and *tombeharrell*.

I will try that @home tonight and will drop a post on my progress!

If that is BIOS what I reach by holding 'Del' key while starting computer -> then I guess it has only one page and no drives selection ](*,) 
I know it is weird but.. i will place a screenshot of my BIOS later. How? Using my Casio Exilim Camera ;)

---

### Post by Ma$$imo on 2006-11-03
I managed to start BIOS on ASUS Laptop - I had to press not 'Del' but 'Esc' or 'F2'. There I changed the boot sequence and started Ubuntu from the burnt Live CD. Worked fine. I did not want to install it though prior to making a partition (or just unallocated space) for Ubuntu from Partition Magic.
But I could not resize my WinXP partition thru this program. I know there's omly 4 GB free, but still. It gives only an option to create a partition of 7.8 MB! :mad:  I am attaching the screenshot of what it shows.

[IMG]http://www.fost.ru/images/partitions.gif[/IMG]

BTW when I started Gparted from Ubuntu there was a possibility to resize WinXP partition, but I was afraid of doing that...
Q: Why can't I resize WinXP partition from within PM 8.0?
Q: Is it safe to do this thru Gparted?
Please help ASAP. ](*,)

---

### Post by rsambuca on 2006-11-04
Q1:  I have no idea why PM8.0 won't let you do that.  It has been a while since I used it, but I never had problems.

Q2:  I have used GParted a fair bit lately and have never had a problem.  I have backed up my data, but haven't had to use the backups yet!

Note:  I think you are running a little tight on disk space.  While ubuntu can certainly run on 4G, it doesn't give you much play room to add other stuff.  Also, if you take away all of your XP free space, I can almost guarantee you will have problems on that side as well.

You might want to consider a tighter linux distro.

---

### Post by Ma$$imo on 2006-11-04
> **rsambuca said:**
> 
Note:  I think you are running a little tight on disk space.  While ubuntu can certainly run on 4G, it doesn't give you much play room to add other stuff.  Also, if you take away all of your XP free space, I can almost guarantee you will have problems on that side as well.
I know, I know :-?  I will defenitely have to clean up the disk, erase some GB of mp3 and stuff -- i have them all burnt to CDs anyway. That's not a problem as I will have 10GB easily for Linux partition, when I'm done with that.
BUT: WHY DOESN'T PM LET ME RESIZE IT?? STRANGE! AND SAD! :-k
I will perhaps try backup some 'useless' :rolleyes:  data and try to resize with gparted! Wish me luck!

[SIZE="5"][B][COLOR="Red"]PROBLEM SOLVED:
[/COLOR][/B][/SIZE]
The lack of free space (if you can call 4GB free a "lack" :)) was the problem. When I freed up to 9 GB PM let me shrink WinXP partition by about 4.5 GB!!!
THANX EVERYONE WHO TRIED TO HELP! :wink:

---

### Post by rsambuca on 2006-11-04
Good stuff!  I ran ubuntu on a small (and very old) 6GB hard drive that I had lying around from an old machine.  I installed it as a slave drive for ubuntu.  After A while, I partitioned my main drive and now have split my 250GB HD into two, one for XP and one for linux.  (I have since reformatted the old 6GB Drive as FAT32 and use it to transfer files between the two operating systems - later found a driver for windows to read ext files).

The only think at present keeping me from wiping out XP completely is webcam/video conferencing issues.  Can't get it to work under linux yet, and our family uses it a lot to chat with family members across the pond.  Currently use Skype - which doesn't have video for the linux side - and Sightspeed, which has excellent video quality.  If I can ever get that to work, I'll be free of Windoze for good!

---

### Post by Ma$$imo on 2006-11-04
[COLOR="Red"][SIZE="4"]NTFS PARTITION !@#CKED UP![/SIZE][/COLOR]

I chose to resize NTFS partition by 4.5GB in the freaking Partition Magic as described above. Then the comp restarted and started a long-long process of resizing the partition. I even had time to go shopping.
At some certain moment I looked at the screen and saw the following:

```
Error 1518. File attribute does not fit.
Entire progress: 100%
Error 1518 while executing Batch.
Error 1518. File attribute does not fit.
Will now reboot.
Press any key to continue.
```

After that I made a lot of attempts to launch WinXP in vain! I get the usual Windows XP Loading screen and then some errors on the black screen and PC reboots. I cannot see what the mistakes are, they appear for about 0.2 seconds.
More to that I cannot install Ubuntu from the Live CD because Gparted gives an error when trying to resize. I cannot mount NTFS volume either. :(
Have I totally lost all the data in my NTFS partition. Wat to do now to recover it?
I couldn't see the contents of my NTFS partition since then with any program.


HOW GLAD I WAS WHEN I LAUNCHED FIREFOX and..... absolutely unexpected... the internet was working! And this is with having Motorola SB5100 cable modem connected thru [SIZE="3"]**USB**[/SIZE]! Of which I've read people were trying very hard to configure in Ubuntu, and I didnt make any configuration AT ALL!

So now the only salvation is ***your advice***...

p.s. at least now i have access to repositories and other stuff...

---

### Post by Ma$$imo on 2006-11-04
I don't believe noone knows what to do?? :-k

---

### Post by MWAAAHAAA on 2006-11-04
If your NTFS partition still exists you might try mounting it and see if the filesystem is still intact:

'mount -t ntfs /dev/hda2 /mnt'

This command should be run with root privileges and without the quotes. I am guessing from your partition table shown in the picture that the partition that your NTFS filesystem should reside is /dev/hda2. If this is not the case, substitute the actual device. Of course the directoy '/mnt' should exist.
If the mount is successfull you can try to list the contents:

'ls -a /mnt'

Again as root.

Oh yeah, next time, be a wise guy, and use the applications supplied by the Ubuntu installer ;)

---

### Post by Ma$$imo on 2006-11-05
Thanks!

Yeah. I guess I should have been wiser choosing from Win and Linux applications to make partitions. The latter is definitely more secure and stable no matter that it's free! :)

As I told I can only start Ubuntu from the Live CD but still I can create directories in 'filesystem' and the internet works!
I tried to mount NTFS partition using mounts, ntfsmount commands as well as adding lines to pmount.allow. I couldn't manage to mount the partition anyway. :(  and yes its /dev/hdc2. 
I also have a hidden 1.5GB partition with ASUS preinstalled stuff. I made it unhidden unselecting the respective flag from gParted. Now its labeled in Ubuntu as /dev/hdc1. But it's not mountable either although its a FAT32 one.

Now I tried to copy some NTFS rescue soft for DOS but its mostly demo and I couldn't start it from DOS.
There is one NTFS rescue program for Linux though: Testdisc. Trying to figure out how to start it now... ***Any ideas?***

I have one idea: If I fail to rescue the data from Dos and Linux I will erase the ASUS preinstalled partition of 1.5GB and install WinXp on it from which I'm sure I could reach data on the big NTFS partition that was broken.

---

### Post by Ma$$imo on 2006-11-05
I tried to mount the NTFS partition but here's what errors occur:
> [17180504.112000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17180504.516000] printk: 68 messages suppressed.
[17180504.516000] NTFS-fs error (device hdc2): load_system_files(): Failed to load $Bitmap.
[17180504.516000] NTFS-fs error (device hdc2): ntfs_fill_super(): Failed to load system files.


Does anyone know a good [COLOR="Red"]RESCUE PROGRAM[/COLOR] that is for [COLOR="Red"]LINUX (or DOS)[/COLOR] that could heal [COLOR="Red"]NTFS[/COLOR] partitions???

---

### Post by mark_g on 2006-11-05
Before resizing a partition, you best first defrag that partition. When I forget to do that myself, which I almost always do, then Partition Magic always just gives me an error, but it has never damaged my filesystem. 
I guess you've had some misfortune there, so I apologize for not telling you this earlier on. A solution to (hopefully) read your data from the disk would be to boot from a special Windows XP livecd. You can find instructions on making or obtaining such a cd on the web.

---

### Post by Ma$$imo on 2006-11-05
Thanks.
I dont really have time to look for a live winXP cd really. But...
Do you think WinXP installation on the small partition (which is readable now and has 1.6GB on it, and is FAT32) could be the salvation?

---

### Post by mark_g on 2006-11-05
Sure, might be even easier. Good luck.

---

### Post by rpkehoe on 2006-11-06
it sounds like you have corrupted your filesystem, no worries, I have done it before myself with partition magic.  First suggestion: Throw away partition magic, download a live cd of gparted (it will be your new best friend).  To fix your problem with windows, get you windows installation cd and chose repair, it will take you to the command prompt, you can then run chkdsk /f.  It will take awhile, but let it go.  When it is finished, reboot to your windows cd again in repair mode, and run chkdsk /f again.  If your main priority is getting windows back up first for your data, run fixmbr, which will overwrite grub.  Once you are happy with your windows installation, you can move on to ubuntu.  You may want to give windows so more space, it probably will not be happy with 4.5 gig.  Use the gparted live cd to resize your windows partition.  You will then need to reboot to your ubuntu live cd to reinstall grub. good luck

---

### Post by Ma$$imo on 2006-11-07
***rpkehoe***, thank you for your advice. I took the laptop with me to work and now I am running chkdsk. It says it is checking for errors and reparing...
The progress percentage didn't take long to reach 75%. But then, when I got back to the screen: I saw it stuck at 50% and it only got to 52% in the following 30 minutes! Is it OK that the process takes SO long?  :-k 

My laptop specs:
ASUS L5 / P4-3.0 HT / 512MB / 60GB

P.S. The HD activity LED is ON all the time and caps lock indicator also works...

[COLOR="Red"]**It took THREE HOURS! But at last I reboot and WinXP started, just like before. All the data is here and nothuing so far noticed to be missing!!! THANK YOU VERY MUCH,  [SIZE="5"]rpkehoe![/SIZE]  You are the MAN. I owe you a big good advice. I also thank all other people without whose advice I wouldn't get this far in comprehending Ubuntu :) **[/COLOR]

So here's what I did (in case someone has a similar trouble):
[LIST]
[*] ran WinXP Installation CD
[*] selected repair ('R' key)
[*] input "chkdsk /R" at the command line
[*] waited 3 hours until it's done
[*] rebooted the sytem
[/LIST]

Now I will transfer all my photos and music files to my work laptop using USB Flash and format my drive to make proper partitions for WinXP + Linux.

Last question in this thread: Which filesystem should I select for Win partition? FAT32 is 100% compatible with Linux form the box. Does it have any drawbacks?

---

### Post by rpkehoe on 2006-11-07
No problem, I have been there, glad you got your system back it.  My suggestion in the future is to never mess with a partition while it is active.  That why the gparted live cd is so great.  Good luck to you

---

### Post by Ma$$imo on 2006-11-07
My Ubuntu 6.10 installation hangs at 63%. I checked CD integrity and it showed: 1 checksum failed, when the bar was at about 30% checking. What does that mean - i won't be able to install using this very CD-R??

---

### Post by rpkehoe on 2006-11-07
You either have a bad download or a bad burn.  Either one is quite possible as the server have been very busy, it doesn't take much to corrupt the download.  You should be able to check the checksum on the iso you downloaded.  If that checks ok, then you need to reburn your disk, try it at a lower burn speed.

---

