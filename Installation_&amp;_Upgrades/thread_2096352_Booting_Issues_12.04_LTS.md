---
title: "Booting Issues 12.04 LTS"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by wisersun on 2012-12-19
I have recently encountered an issue when booting from GRUB. As far as I know, I did nothing to spark the issue. :/ I didn't update/upgrade anything and I have had little to no problems with Linux on this machine. I have been running Ubuntu on this laptop for quite a while now and nothing out-of-the-ordinary (like this) ever happened. 
     The problem: I shut down my computer regularly (by selecting the "shut down" option) and closed the lid (after shutdown was complete). I came back later and turned it on. It started up like normal by taking me to the Toshiba start screen, then it took me to a purple GRUB menu with options:
[I] Ubuntu, with linux 3.22.0-35-generic
 Ubuntu, with linux 3.22.0-35-generic recovery[/I]
      and two other options about memtest. I chose the first thinking nothing was wrong. I waited and nothing happened for about a minute. I restarted it and chose the second option (the recovery). Same result. I restarted the computer, chose the first option, set it down, and started researching the issue on my PC. I came across many articles that didn't really relate to my problem or that i didn't understand. Then, my computer jutted out lines of script. At the end i received this message: **Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)** or something like that. I waited longer but now all that was happening was my caps-lock key was flashing and the terminal-like underscore was continuously flashing as well. (the underscore that appears when it is waiting for a command) I waited over an hour and that is ALL that went on. Please help.
     I still do not understand the issue or the steps needed to fix this. I have a minimal knowledge about this and would like things to be explained without expert terminology or with understood steps. In other words, if you would be so kind as to "spell it out" for me, that would be appreciated. All help and efforts are greatly appreciated! Thank you for your time and consideration!

---

### Post by wisersun on 2012-12-19
If any specs are required, please feel free to ask. Thank you.

---

### Post by oldfred on 2012-12-20
How did you shut down? That often causes more issues.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

    
Then we may be back to your original issue. Was it just running fsck in the background? It usually runs fsck every 40 or 60 reboots, but displays that it is running, but it can take a few minutes if ext4 and a lot longer if ext3.

---

### Post by wisersun on 2012-12-20
I thank you greatly for responding! I shut it down by clicking the Ubuntu symbol in the top-right and selecting shutdown. To me, it seemed to shutdown normally. I understood maybe half of what you said but I understand the REISUB thing now. Thanks for that info! I'm sure it will come in handy when it freezes, but 
THATS THE THING: my computer was acting NORMAL, it didn't freeze this time or anything. There was no FORCE shutdown. Then i restarted it and well... Anyways, I would be glad to follow instructions if I knew what they meant... I understand the Livecd but then i continue reading and it looks like this: *"LPALELFPELF now  hjfdshfjhs to your system and kkjkgjf so that it properly reboots :) this should solve it"* I hope this gave ANY insight whatsoever to what my problems are. Thanks again for replying! 

EDIT: clueless about: fsck, ext4, ext3, that whole sentence..., the # steps: "#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)" -- do WHAT from livecd?

EDIT: it still hasn't rebooted, I never successfully booted the system yet: i am still always getting grub screen, then selecting an option, then letting it run, then getting **Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**

---

### Post by oldfred on 2012-12-20
Can you boot liveCD/DVD/flash drive?

If so from terminal run these:

sudo fdisk -lu
sudo parted -l

Best to copy & paste commands into terminal. the l are el, not 1 or cap i. And sometimes spaces do not look like spaces.

---

### Post by wisersun on 2012-12-20
Thanks! I'll try it and see what happens.

---

### Post by wisersun on 2013-01-06
Sorry for my very late reply, but these last weeks have been devastating. My son just came back from the hospital yesterday after being in about a week and my father-in-law passed away three days before that. I just managed to get to the store and get some writable disks today. I just burned the LiveCd and am just about ready to boot. I will post some updates as soon as i get that working (or not).

---

### Post by wisersun on 2013-01-14
input: sudo fdisk -lu
output: Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bc819

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   606713855   303355904   83  Linux
/dev/sda2       606715902   625141759     9212929    5  Extended
/dev/sda5       606715904   625141759     9212928   82  Linux swap / Solaris
input: sudo parted -l
output: Model: ATA WDC WD3200BEVS-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  311GB  311GB   primary   ext4            boot
 2      311GB   320GB  9434MB  extended
 5      311GB   320GB  9434MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           
(for clarification)**input= the command i entered output=the information received**
     ***Read the next post about the actual booting from the disk***

---

### Post by wisersun on 2013-01-14
Booting from the disk: I did _NOT_ re-install Ubuntu..... I simply booted from the disk and chose "try ubuntu," instead of installing it. Please tell me if I need to install it. If so, then is there any way to do so ***WITHOUT*** losing all files? I suspect not, however, my lack of knowledge in this area isn't by any standard exceptional, for someone who works with computers. I would love help and suggestions and, as always, anything is always appreciated.


Thank you so much.

---

### Post by wisersun on 2013-01-14
Hello, I am wondering if we can just forget what has been said in the past and focus on the issue. I started this thread to fix my problem not get here and say "Nevermind guys, I think i'll just screw it and completely WASTE you time!" I am back telling you that I am ready to fix it, and I am wondering if you are willing to help.... :)

---

### Post by oldfred on 2013-01-15
Sorry to hear about your son & father-in-law. Hope your son is doing better.

Have you tried e2fsck as suggested in post #3? I would try that before reinstalling.

You have just a / (root) and swap partitions on drive. Error message is because CD is oversize and it reports that as an error.

---

### Post by wisersun on 2013-01-18
Btw, I am no longer planning to re-install. (That was just an idea that flashed through my head and i decided to post, however, at that time, i wasn't thinking.... ;) ) Again, if i could get a link or details/step, that would be amazing!

---

### Post by wisersun on 2013-01-18
Oops! Sorry! I was waiting for a reply and then i saw "page 1 of 2". Now I saw your post. Thanks you for describing my problem. On a sidenote, thank you for your condolences regarding my family. Nice to know that people feel for you :) .  Anyways, do you have a link or could you describe the way to swap partitions? (or whatever else in necessary to fix it?) If you don't mind, that would be great. Thank you greatly!!!

---

### Post by oldfred on 2013-01-18
Did you run the commands on e2fsck as posted in #3. Just use sda1 not the sdb1 I used in the example.

---

### Post by wisersun on 2013-01-19
Where should i run the commands from? As far as i know I cannot run them while using the disk because that only temporally saves everything... (RAM if i am not mistaken...) so where exactly do i run those commands from?

To clarify: I am supposed to run these commands?:
sudo e2fsck -C0 -p -f -v /dev/sda1
then
sudo e2fsck -f -y -v /dev/sda1

Please confirm. Thanks as always!
**EDIT** Just ran the first command from the terminal(from try ubuntu) and this is what i got:

Error reading block 2621542 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

---

### Post by wisersun on 2013-01-19
Tried the same command in the same circumstances but without -p 
input:  sudo e2fsck -C0  -f -v /dev/sda1
and so i got this:

e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Error reading block 2621542 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? 
I wasn't sure weather to continue or not ( y then enter) so i just aborted (control+c, ^C)
after aborting i got this:
/dev/sda1: e2fsck canceled.                                                    

/dev/sda1: ********** WARNING: Filesystem still has errors **********

---

### Post by wisersun on 2013-01-19
Went back and read post #3.... 

#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

i DID have an error.... sooooo.... trying that command. (but with sda1)
since that command automatically answers.... when  force rewrite cam eup it said yes.... does that mean that i will lose data? (if it's rewriting whatever it's rewriting?)

EDIT: Oh well, I guess whatever happens happens.... I will just leave it to run (while i supervise, of course) and will check back in about 15 mins.... Any idea whether i will lose my data or not?


EDIT: It finished!!! Moment of truth!!! Fist bump if it works... :P

---

### Post by oldfred on 2013-01-19
Seems like a lot of errors, but still hopeful.

---

### Post by wisersun on 2013-01-19
Hmmm... not sure where to go from here. I took out the CD and rebooted. It still takes me to the purple GRUB screen. (see post #1) Not sure which option to select.... or what to do... or how long to wait. My question now is what do i do from here? Any more commands or suggestions? :) Still hopeful as well.
EDIT: Btw, booting from CD still works perfecly...

---

### Post by oldfred on 2013-01-19
If you hold shift key down from BIOS until menu, do you get menu? then maybe try recovery mode? May be a video issue?

---

### Post by wisersun on 2013-01-19
BIOS menu, no.... i don't have to do anything but reboot and the grub menu comes up... no shift-holding or anything... Will try recovery mode... Be back soon! What do you refer to when you say "video problem?"

---

### Post by wisersun on 2013-01-19
Tried recovery mode... seems not to work. What now? Didn't you say something before about swapping partitions?

---

### Post by oldfred on 2013-01-19
Nothing to swap.

Lets try Boot-Repair. If you can get to grub menu, and have already run a filecheck, Boot-Repair will probably not fix anything, But it tries to mount all partitions and shows some useful info. From your LiveCD install Boot-Repair.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by wisersun on 2013-01-23
Accidentally had links disabled, didn't know that was possible.... thanks! Will get on that ASAP. Posting the results when done. 

Just finished this is the URL i got:
[http://paste.ubuntu.com/15644768](http://paste.ubuntu.com/15644768)

---

### Post by oldfred on 2013-01-24
LInk does not work. Rerun BootInfo and create new link.

---

### Post by wisersun on 2013-01-28
[http://paste.ubuntu.com/1583827/](http://paste.ubuntu.com/1583827/)

Try this one... just copied and pasted, try it please :) . As always, I appreciate the help. I am starting to feel like we are getting somewhere! So there you have it; thanks for everything!

EDIT: Just checked to see if the like works, it does... MY GOSH, thats a lot of info to sift through... I am starting to look through it right now, to see if i can spot something...

---

### Post by oldfred on 2013-01-28
I do not see anything wrong.

But we have seen issues with some combinations of BIOS and maybe a grub issue. What mode is drive in? It should be LBA, large, or AHCI but not IDE.
If boot files are beyond 100GB systems just may not boot. Boot-Repair often suggests a separate /boot partition. I normally suggest making / (root) smaller. I use 25GB for root normally.
You can test by shrinking / with gparted from liveCD to under 100GB. You then can use rest of drive as a data partition or /home.

You may be able to boot with supergrub.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
    
Then run this to update grub.
       sudo dpkg-reconfigure grub-pc
    
You also have a lot of kernels. May be time to houseclean. I prefer synaptic.
       Determine your current kernel:
uname -a
uname -r
In synaptic or software center search for linux-image to choose to purge old ones  or completely remove.
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by wisersun on 2013-02-06
Not able to open synaptic... tried gksudo synaptic, but that didn't work. If you could tell me how to open synaptic (while using the livecd) that would be great. I'm pretty sure i can follow the rest of the steps from there..... (they're pretty self-explanatory). As for what you posted about super grub and before, I'm  quite lost on that regard... tried that super grub command in terminal, and it asked me to check if the kernel script looked alright, i clicked ok and then it did some things and stopped.... Again, as for BEFORE super grub, didn't try that and I am not sure how to. IF you could maybe explain that AND give me some directions as to how to start synaptic, that would be great!!!

---

### Post by oldfred on 2013-02-06
You have to be inside your install with a gui to run synaptic. That was for after you repaired booting and then you could houseclean old kernels.

Did you check BIOS settings and have you tried shrinking / (root) ?
Supergrub is another repair ISO. You have to download it and install to a CD or Flash drive and boot from that. It has a version of grub and scans for a bootable system(s). If you have a working kernel and just a broken grub, Supergrub should boot it.
Instructions on Supergrub site. It has one simple small version that just boots. Another for repairing grub legacy (which is now mostly obsolete) and a version for grub2 repair.

---

### Post by wisersun on 2013-02-09
Could you please walk me through shrinking root (and maybe checking BIOS settings if still necessary)?  Looking into Supergrub right now..... which one do you suggest i get? The one that just boots, just it JUST boot or does it ALSO fix grub? Thanks so much!!!

---

### Post by oldfred on 2013-02-09
You should be able to use a liveCD or flash in live mode and load gparted. You usually have to click on swap and right click swap-off to unmount it  as liveCD's use swap to speed things up a bit. Then edit / (root).

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    
I cannot give specific instructions on BIOS as each vendor's is different. I had to take camera shots of mine as it reset everything back to defaults when I upgraded it and it took awhile to get the settings back that I wanted. Now I have documentation.

---

### Post by wisersun on 2013-02-25
Hello OldFred. It seems like this is going to be my last post on this subject. Earlier today, I re-installed 12.04 LTS on the same machine. When it finally booted up (after installing) I used it for about 30 seconds when a box came up alerting me about my hard disk. I clicked explore and read the details and it said Hard Disk failure imminent. SO I think we found the problem here. I will go buy a new disk and install that. This is a relatively old computer, so I was expecting this anyways. Now that I realize what needs to be done, I am somewhat relieved. :D  This is not a hard fix for me and it's an operation that I have done many-a-time before. marking this as solved because there is nothing left to say. Thank you for all your help and expertise on the subject. I greatly appreciate your timely help. ( Before I got an answer here, I posted on ASk Ubuntu. They still haven't responded. However, my loyalties lie to this site because the other pales in comparison. I should've known that I wouldn't get an answer there. ;)) So, once again, thanks for your time and effort.

---

### Post by oldfred on 2013-02-26
You are welcome. 

I guess we should have also looked at Disk Utility as it will show Smart Status of a hard drive. It has lots of detail but all I know is if it is green drive is ok for now. 

I tend to demote my main drive after a few years to backup duty. I usually need more space (but now drives are so large that is not an issue for me anymore) and just do not trust drives to last even with guarantees.

---

### Post by wisersun on 2013-02-26
Yes, i suppose we should have. My SMART status says Failure imminent, and only a few measures are green. Like I said, this machine is relatively old and the hard disk was bound to fail sometime. Oh well, good things don't last forever. Going to best buy tomorrow, or perhaps i will order one from Amazon. Nevertheless, at least I know what needs to be done!

---

