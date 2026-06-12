---
title: "Dual boot problem"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by frank392 on 2006-12-30
Hi I have a dual boot with windows, and as usually windows broke and i need to re install it but I have Ubuntu in the same computer, with GRUB as the boot loader, haw can I save my UBUNTU installation, GRUB. In suse linux that was very easy you have the option to install Grub in a Floppy. is there a way to do that on UBUNTU?
thank you very much :confused:

---

### Post by pandu.rs on 2006-12-30
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by bulldog on 2006-12-30
Installing GRUB again is not hard to do.
If you want GRUB on a floppy to boot.I suggest you read this,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr

---

### Post by mhenriday on 2006-12-30
**Pandu.rs**, **bulldog**, if I'm lucky you may well have put forward the solution to my problem as well as to that of **frank392**. As I've explained elsewhere on this forum, I managed to wipe out all my **Windows** files when installing **Ubuntu 6.06** (since upgraded to **6.10**) from a shipit CD. I'd like to reinstall **Windows** and some apps, mainly so that I can retrieve some lost files from my **Mozy** backup. I've got a 160GB WD hard disc on an upgraded Pentium III machine with approx 500 MHz clock speed and 512 MB RAM. I had hoped to be able to use **QTParted** (v0.4.5) to partition the disc and then reinstall XP, but as I've mentioned on another thread, I can't get the programme to work. Is it possible to boot my computer from my **6.06** CD and manually partition my hard disc using the instructions provided in the *Restore GRUB* tutorial to which **pandu.rs** linked, _without wiping out my **Ubuntu 6.10** files_ ? Here are the instructions :

[INDENT] 1.  Boot your computer with Ubuntu CD.
   2. Go through the install process until you reach "[!!!] Disk Partition."
   3. Select Manually Partition.
   4. Mount the appropriate linux parti[ti]ons:
      /
      /boot
      swap
      DO NOT FORMAT THEM
   5. Finish the manual partitioning.
   6. Select "Yes" when it asks you to save the changes.
   7. It will give you errors saying that "The system couldn't install ....." after that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu.
   8. Jump to "Install GRUB."
   9. Once it is finished, simply restart your computer.[/INDENT]

If I remember correctly, it was in attempting to mount the Linux partitions that I failed ; I couldn't get the computer to accept three separate partitions for «/», «/boot», and «swap», so I was forced to go back and choose automatic installation, which proceeded to write over the existing **Windows** files. If, indeed, it is possible to partition the hard disc using the above procedure, I should be very grateful for help with respect to how to manually partition the disc, so that I don't make the same mistake as last time, and end up again in square one ! And if I do succeed in partitioning the disc, do you have any suggestions as to how to make sure that **Windows XP** and **Office** get installed in the right (empty) partition ?...

Henri

---

### Post by bulldog on 2006-12-30
I would make the suggestion to download the Gparted live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It's only 30MB,burn it to a disk and boot from it.
It gives you a nice partitioner with a GUI which is rather easy to use.

You have a 160GB drive and I presume your windows will be the main used OS.
Some partition suggestions.

Create a primary 20GB NTFS for windows 
Create a primary 60GB NTFS for data and programs
Create a primary 10GB ext3 for the /  (root) partition
Create an extended partition of the remaining space.
In the extended create a logical 10GB ext3 for /home
In the extended create a logical 1GB as swap format as swap
In the remaining space [about 60GB] create a logical for /data.

You can play with the amount of GB's of course,to alter them to your needs.

Now install windows first on the first primary,office is no problem,you can install it in the windows partition or use the NTFS data partition.

Install ubuntu next and when you come to the partitioner choose manual partitioning {you already have done the partitioning.}
Mount your 10GB as / and reformat
Mount your swap as swap and reformat
Mount your /home as /home and reformat
Mount your /data as /data and reformat
Be sure the NTFS partitions are **un-checked** so they won't be formatted as well.
Apply, and resume the installation.
At the end will GRUB be installed so you can boot windows and ubuntu from the GRUB menu.

I think this should do :D ,hope this can help you.

---

### Post by junk269 on 2006-12-30
bulldog i tryd setting up vms for ubuntu knoppix you no the stuff i wanted to play with first i messed it up an im on an _old stinkpad_a22m slow an old thats me can you help me i want to go through an redo the laptop 2k then vms of christian ubuntu ubuntu types then freespire/linspire if i get that far ill have maxed this laptop im guessing but i am soooo lost this is new to me an i really want to figure this stuff out like my wireless card working that would be reallly nice lol so can you help?
or no anybody who can????:confused: ](*,) ugh windows bites

---

### Post by mhenriday on 2006-12-31
Thanks, **bulldog**, for the detailed instructions ! I have a couple of additional questions before attempting, *mutatis mutandi*, to follow them. Firstly, can I use the procedure you outlined above if I download to a USB stick according to the information provided [here]("http://gparted.sourceforge.net/liveusb.php") ? For example, does the USB download tell me how to create «a fat16 partition on the usb stick and make sure it's flagged "boot"» and will my **Ubuntu 6.10** terminal accept a command like «syslinux -s /dev/sda1» ?...

As a matter of fact, I had intended to continue using **Ubuntu** rather than **Windows** as my default OS even after a successful installation of the latter ; how should I modify the partitioning instructions given above to allow for this ? What I should like to have is a GRUB notice when I boot my computer that allows me to choose the OS to be used in a particular session. Am I correct in assuming that the procedure outline will provide this ?...

Thanks again for all your help in this matter !...

Henri

---

### Post by bulldog on 2006-12-31
It should be no problem installing this on a USB stick.
The formatting and put the boot able flag you have to do with a partitioner,like gparted before you can copy the files to it.
You can do this in ubuntu or windows if you like.

If you install ubuntu you install GRUB as well,because ubuntu won't be boot able without it.
Your windows entry and all Os's for that matter will be set up by GRUB as well,or you can add them manually.

It's possible to put GRUB on a boot floppy if you prefer to do so,you can find info about that over here,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

To use ubuntu as a main OS and keep windows as backup OS you have to do nothing at all.
Just take a look at the space I set for windows /data and if that's to much you can make it ext3 or resize the partititions as you like.
You know best what capacity you'll need for windows and ubuntu,I made just an example,which you're free to change.
Just keep in mind to set windows on the first primary to avoid problems with booting,where ubuntu is installed don't matter,it will boot if GRUB is set properly.

---

### Post by mhenriday on 2006-12-31
**Bulldog**, unless I've misunderstood completely, I shouldn't have to download **GParted** to anything, as a version of **0.2.5** was included on the shipit disc for **Ubuntu 6.06** I installed on my computer, and which (**0.2.5-1.1ubuntu11**) I retain on my present **6.10** setup. (I don't know whether there would be any point in updating to the latest version, **0.3.3**, nor, in that case, utter novice that I am, am I quite sure how to do so.)

When the programme is opened , the following information about my system is shown on the main screen :
[INDENT]Partition                File system     Mounting point      Size          Used          Unused      Flags

/dev/hda1       [lock] [square] ext 3         /            147.61 GiB     8.14 GiB   139.47 GiB  boot
/dev/hda2              [square] extended                       1.44 GiB     ---               ---
/dev/hda5              [square] linux-swap                     1.44 GiB     ---               ---[/INDENT]

My assumption was that I could use the resize/move widget and the partition tool to rename and divide the sectors presently found under ext 3, so as to accommodate two **NTFS** partitions for the **XP** OS, applications, and data files, leaving plenty of room for my present **Ubuntu ** system, which would be denominated as primary. To my surprise, however, I could not remove the lock on the /hda1 partition ; when I right-clicked on the partition and clicked on «unmount», I received a message to the effect that the partition could not be unmounted from the point «/», presumably because other partitions are also mounted from this point. It was suggested that I unmount them manually. But no mounting point is given for the other two partitions mentioned above, and in these cases the unmounting option is either disabled (for «extended») or unavailable (for «linux swap») !...

I then turned to the **GParted FAQ** for help and found the following :
[INDENT]...

5 : Why are some menuitems disabled?
[INDENT]1. The partition is mounted and modifying a mounted partition is DANGEROUS. Just unmount the partition or in case of swap, disable it.(use swapoff)

2. At startup gparted decides which operations on which filesystems are supported. For instance, to create an ext3 filesystem gparted needs mkfs.ext3. If this cannot be found on your system, the creation of an ext3 filesystem is not possible and therefore disabled in gparted. The same goes for copy, resize etc..[/INDENT]
...[/INDENT]

Unfortunately, given my inexperience with and lack of knowledge concerning **Linux** systems, I didn't find the above very helpful. Where do I go from here ? As I said, what I should like to do is set up a few more partitions to accommodate **Windows XP** and other **Windows** files, to be accessed via **GRUB**, while maintaining **Ubuntu** as my primary OS. I am convinced that this is possible ;I just wonder if I can obtain an explanation that is both simple and detailed enough for me to succeed in following it....

Henri

---

### Post by bulldog on 2006-12-31
Well now you found out why I suggested the live cd.
Also the build in partitioner is a little harder to use and understand,so you can easily been mistaken.

If you boot the gparted live cd there's no hdd mounted,so you can rearrange and repartition without the unmounting trouble.

---

### Post by mhenriday on 2007-01-01
> **bulldog said:**
> Well now you found out why I suggested the live cd.

...

Well, **bulldog**, I took your advice, downloaded the **GParted** live CD, and burned it to a RW disc. The disc now contains an **isolinux** directory with 7 files totalling 5.9 MB, and a **gparted** file, marked with what I interpret as an «unreadable» emblem, some 22.3 MB in size. I've scanned for viruses, but not found any....

Where do I go from here ? As noted above, I've got well over 130 GiB of space left on /dev/hda1, mounted as ext 3, plus 1.44 GiB on each of /dev/hda2 (extended) and /dev/hda5 (linux-swap). What I should like to do is partition /dev/hda1 further, creating, as you suggested, one NTFS partition of about 20 GiB (about the size of my so-called C disc when I was using **Windows**) for **Windows XP** programmes, and another of about 50 GiB for data and applications. Most importantly, I want to do this _without losing the **Ubuntu** programmes, applications, and data that I already have_. Can I simply turn off my computer, turn it on again, insert my **GParted** live CD, and then reboot from the latter ? Will my present Ubuntu programmes be recognised and survive the process (avoid being overwritten) ? And in that case, after partitioning my hard disc as explained above, will it be possible without any major difficulty to install **XP** and **Office** in the desired partitions directly from CDs ?...

If I go into unnecessary detail in the above, this is due to my lack of familiarity with the manner in which the hard disc is partitioned in **Ubuntu**, and the nervousness resulting therefrom. Usually I manage to be more succinct. But as I say, I don't wish to lose the programmes and data I now possess. Hope you won't mind helping me a bit further down the rocky road to a successful dual-boot machine !...

Henri

---

### Post by bulldog on 2007-01-01
You have to boot from the gparted live cd,but I have to warn you,a cd-rw isn't a very good idea to use,but give it a try.

You can partition and resize as you like,if you will do something what's not aloud you will notice.
If you're disk is at your desire hit the apply and it will be done.

About your data,I can never give you a guarantee,you are the one who execute the program so you should be careful not to touch your ubuntu data,and be sure your windows partition is the first primary.
Make a note of all the partitions on your disk when you're done so you can look back to what you've created and their names like hda1,hda2 and so on and what's on it.

---

### Post by mhenriday on 2007-01-05
Well, **bulldog**, I finally managed to screw my courage up to the point where I was able to insert my **GParted** live CD (by the way, why isn't a cd-rw to be recommended ?) into my CD slot, turn off, and then re-boot my computer. And wonder of wonders, after answering a series of queries about which language I preferred, type of keyboard set-up I have (wasn't sure which of the two types of Swedish keyboard I should choose, so I chose the first alternative), and the «depth» of my ancient Mac monitor (again, not being sure, I chose the one marked by default), about my set-up on my screen, and was able to reconfigure  /dev/hda1. The set-up now looks as follows :

 Partition  File system    Mounting point         Size          Used           Free          Flag
/dev/hda1    ext3*                /                      20.00 GiB     6.28 GiB**   13.72 GiB     boot
/dev/hda3    ntfs***                                     25.00 GiB   65.23 MiB    24.94 GiB
/dev/hda4    ntfs***                                     60.00 GiB   66.32 MiB    59.94 GiB
not allocated****                                         42.60 GiB      --              --
/dev/hda2   extended*                                   1.44 GiB
/dev/hda5   linux-swap*                                 1.44 GiB

* Locked

** Originally, the this partition had a total capacity of 147+ GiB, 8+ GiB of which were used, 139+ GiB free. I have no idea what has happened to the nearly 2 GiB of data that were originally represented as being used, hitherto I haven't noticed anything missing.

*** A warning triangle is shown here, which when clicked reveals the following text : «Unable to read contents of this file system- For this reason, certain actions may not be available. Did you install the correct plug-in module for this file system ?» Is this do to the fact that I've not yet installed anything in the two file systems concerned ?

**** Left over from the original /dev/hda1 partition.

As I see it, I've come pretty close to your original recommendations, save in one respect only - the unallocated partition which takes up as much as 42 GiB of my hard disc and which in its present configuration is useless. I've tried to used the **Gparted** programme I have installed on my computer to include this space as a logical partiton under /dev/hda2, but can't unlock the latter.  Should I re-boot from the **GParted** live CD (I'm still reluctant to do this, for fear that my data will disappear, despite my positive experience the one time I tried it) and try to do this there ?...

The next question is, can I use the partitioning described above to download **Windows XP** and **Office** ? If so, should I install **XP** to the 25 GiB /dev/hda3 partition, and **Office** to the 60 GiB /dev/hda4 partition ? Any tips on how to make sure that **Windows** doesn't simply write over everything during the installation process ?

And finally, will I be able to use **GRUB** to determine to which of the two OS I wish to boot during start-up ? Does the fact that (in this case) both **Ubuntu** and **Windows** have been downloaded to _primary_ partitions - /dev/hda1 and /dev/hda2, resp - make any difference here ? And if I don't intervene, will **GRUB** boot by default to **Ubuntu** (which is what I desire), as this partition come first numerically ?  Anything else special to watch for ?...

Thanks a lot for all the help I've hitherto received from you and from other forum readers with this problem, which like almost all others is simple if one knows what to do, but otherwise quite perplexing !

Henri

PS : I found **bodhi.zazen**'s guide, «[*Partitioning basics*]("http://ubuntuforums.org/showthread.php?t=282018&")» very helpful for my understanding of the naming conventions used in both **Unix** and **Windows** machines. It's been about forty years since I did **&#22352;&#31109;** in a temple in the snow country of western Japan - perhaps I should do it more often !...

---

### Post by bulldog on 2007-01-05
As I discribed,it's not recommendable to put windows on the second partition,it will give you a head ache to boot windows,without altering the boot.ini file.

To change your partitions and use the unallocated space your disk should be unmounted,and to avoid errors,I recommend using the gparted live cd.

If it was me,I should re partition the disk again.
Make the first two primary's NTFS for windows and windows data.
You can make one more primary for ubuntu / (root 10GB) but it's not necessary to have it on a primary though.
Make from **all** the free space left,an extended partition,and create logical partitions till the space is consumed,I leave it at your imagination how many you want to have :D  

When you install windows you will be asked on which partition it should be,**choose the first primary for windows**and install it.

Then install ubuntu and mount all the partitions you have made for it,if this isn't possible,be sure to mount / ,swap and your /home as the minimum,the rest can we add later in the fstab file.

Installing programs [office] in windows later on,is no problem,windows can't write to a ext3 file system by default and the install of any application in windows should be smooth.

---

### Post by mhenriday on 2007-01-05
OK, **bulldog**, I get your point - to modify my partitions I'm going to have to make use of my **GParted** live CD again. This I'm willing to try, even if I'm still worried about losing data from my present **Ubuntu** set-up. And I can also try, as you suggest, to make /dev/hda1 (~ 20 GiB) and /dev/hda3 (60 Gib) into NTFS partitions, leaving /dev/hda4 for an ext 3 partition for **Ubuntu** (do you really think that 10 GiB suffices ?) The remaining space I can then use to create an extended /dev/hda2 partition, which can then be split up into a small /dev/hda5 linux-swap (1.44 GiB) subpartition and a large (> 55 GiB if I can get away with 10 GiB for /dev/hda4) extended /dev/hda6 subpartition, respectively. But what I _don't_ want to do is to install **Windows** and then install **Ubuntu** ; the whole point of the exercise is to re-install **Windows**, _while preserving my existing **Ubuntu** programmes and data intact !_ What I'm after, in other words, is to _first_ move my existing files from /dev/hda1 to a new /dev/hda4, without modifying their content. Is this possible, or am I dreaming ? If this can be done, then I can try to reconfigure the remaining partitions according to the above sketch. How then am I to proceed in order to mount /dev/hda4 to root («/») ? How do I then mount /dev/hda2 and the subpartitions /dev/hda5 and /dev/hda6 ?...

If I succeed in the above, I intend to insert my **XP** disc and try to install the OS to the first primary partition (/dev/hda1). Should I then attempt to install **Office** to /dev/hda3 ? Will I even here be met with a prompt which asks me where I want to install the application ?...

_If_ everything works as desired, and I succeed in all of the above, the question then becomes : What happens when I switch on my computer ? Will I get a **GRUB** prompt which allows me to choose which of the two OS I wish to use on my screen ? As I mentioned above, I should like to create a dual-boot set-up in which **GRUB** boots to **Ubuntu** by default, but where I can intervene to choose Windows when I need to have access to that system....

Well, it has taken some time, but with your help I feel that I'm nearing the goal ! In Swedish we say «*skam den som ger sig !*»...

Many thanks

Henri

---

### Post by bulldog on 2007-01-05
All you want is possible! But fooling around with not backed up data is always a certain risk.

You can install windows on the first primary with no problem.
I think you have a misunderstanding in how office is installed.
This will not happen by booting the cd,but if you are boot into windows,you pop in the office cd and install it.
The default install is in C:\ but you can change this in the partition you want,just read carefully when you install the application.

If you have installed windows your boot loader [GRUB] will be over written,but that's an easy one to repair with the ubuntu live cd.

But be careful with your data when you go and partition the drive again.

Good luck.

---

### Post by mhenriday on 2007-01-06
One step forward, two steps back ! I managed to move the 42.60 GiB unallocated portion of the hard disc to the a new partition, /dev/hda6 ext 2, under /dev/hda2 extended. On the other hand, I failed in my attempt to decrease the sizes of /dev/hda1 ext 3 and dev/hda3 ntfs to 15 and 20 GiB, respectively ; when I tried to do so, two unallocated partitions measuring 5 GiB were created, and I found myself unable to move them, as I had hoped, to /dev/hda6. Nor was I able to move the 25 GiB NTFS partition to /dev/hda1. My present set-up thus looks like this :

[INDENT]Partition File system Mounting point Size Used Free Flag
/dev/hda1 ext3* / 20.00 GiB 6.45 GiB 13.55 GiB boot
/dev/hda3 ntfs** 25.00 GiB --- ---
/dev/hda4 ntfs** 60.00 GiB --- ---
/dev/hda2 extended* 44.04 GiB
[INDENT]/dev/hda6 42.60 GiB 732.88 MiB 41.88 GiB[/INDENT] 
/dev/hda5 linux-swap* 1.44 GiB

* Locked

** A warning triangle is shown here, which when clicked reveals the following text : «Unable to read contents of this file system- For this reason, certain actions may not be available. Did you install the correct plug-in module for this file system ?» Is this do to the fact that I've not yet installed anything in the two file systems concerned ?[/INDENT]

But the real problem is that I'm beginning to think I've misunderstood you all along ! What I now think you've been talking about is a three-stage rocket ; first, partitioning the hard disc using the **GParted** live CD, then installing **Windows XP**, and finally, re-installing **Ubuntu** from a CD, which in my case would mean first installing version **6.06** and then downloading and installing the upgrade to **6.10**. Am I correct in understanding that this is what you are suggesting that I do ? That would mean wiping out all the partitions I presently have installed ; can I use the delete button on the **GParted** tool bar to do this, or do you have another suggestion ? In that case, what happens to the 6.45 GiB of data that I presently have installed in the /dev/hda1 ext 3 partition ? Do they simply, and unretrievably disappear ? As I have mentioned previously, I had hoped to be able to preserve these data and simply repartition the disc and then download the **Windows** OS to a new, dedicated NTFS partition, but from what you say it looks like this is not possible. So can it go !...

I suppose one possibility would be to see if I can borrow an external hard disc, transfer the present contents of /dev/hda1 to this disc, then use the **GParted** live CD to wipe out all the partitions and information on my hard disc and re-partition it according to your instructions, install **XP** to the new /dev/hda1, and finally re-install my **Ubuntu** files and data from the external hard disc on which they had been stored. Is this procedure feasible ?

I haven't given up yet !...

Henri

PS :Forgot to mention that ever since re-booting my computer with my **GParted** live CD, I've been getting the following message every time I start it :

[INDENT]**Internal Error**
failed to initialise HAL ![/INDENT]

Is this failure to initialise the hardware abstract layer upon starting, something I can or should attempt to correct ? If so, how ?...

---

### Post by bulldog on 2007-01-06
As I see it you can backup your data to an external drive,wipe out all partitions and start from scratch [the easy way].
Or move your data on your hdd using the ubuntu cd.

Explanation,format the hda6 partition to ext3 and copy your data to it using the ubuntu live cd.
Then format hda1 to NTFS
Format hda3 to ext3

It then looks like,

hda1 20GB NTFS [windows]
hda3 25GB ext3  [ubuntu]
hda4 60GB NTFS [windows data]
hda2 44GB Extended partition
hda5 1,44GB swap
hda6 42.60 GiB [ubuntu data] [732.88 MiB 41.88 GiB you have to explain this  to me it make no sense at all]

And yes,I meant backup your data and begin from scratch with the three step rocket :D 
I never should do with my data what you're doing,the risk of losing it is to big.

The HAL error I don't know,it can be a faulty gparted cd [you used a cd-rw]maybe this has to do something with it,but I can't explain.
I should use a new cd-r,they cost hardly nothing now a days.

---

### Post by mhenriday on 2007-01-07
**Bulldog**, thanks a lot for all your help ! The only means I have of repaying you is to post an blow-by-blow account of my (mis)adventures here on the thread, so that others can learn from them. Here goes : I followed your instructions and copied my data from hda1 to hda6 ext 3, after which I deleted the original hda1, and then re-formatted the resulting unallocated space to a new hda1 ntfs, which was then automatically flagged as boot and locked. The other partitions were more or less as you list them above, save that hda3 was created as a 25 GiB ntfs partition, and hda4 as a 60 GiB ext 2....

I then tried to install **Windows XP** from a hard disc, but received **GRUB** error message 19 and was unable to boot the computer. I then attempted to make some further modifications in order to be able to do so, in the course of which I received error messages 17 and 22 when trying to reboot. At this point I decided I had come as far as I could just then in my quest for a dual boot, and decided to restore an all-**Ubuntu** set-up, at least for the present. After copying my files back and forth several times, I ended up with the following configuration :
[INDENT]Partition File system Mounting point Size Used Free Flag
/dev/hda1 ext3* / 25.00 GiB 6.62 GiB 18.39 GiB boot
/dev/hda3 ext2 20.00 GiB 367.30 MiB 19.64 GiB
/dev/hda4 ext2 60.00 GiB 1016 MiB 59.01 GiB
/dev/hda2 extended* 44.04 GiB

[INDENT]/dev/hda6 42.60 GiB --- ---

/dev/hda5 linux-swap* 1.44 GiB[/INDENT]

* Locked[/INDENT]

which I was able to use to re-boot my machine. As far as I can see, I have not lost any data despite the extensive process of partitioning and re-partitioning to which I've subjected the machine. I do not know what, e g, the 367.30 MiB of files represented as used in hda3 represent, but my experience is that these mystery files disappear and do not return if I delete the partitions in question and then open a new one in the unallocated space. I am no longer receiving that annoying message about a failure to initialise HAL. As to my choice of a RW disc, I fear this led to a misunderstanding on your part - the RW disc to which I chose to copy **GParted** live was not used but _new_ ; the reason I chose it rather than a read-only disc is that I assume that the quality of the former is somewhat better....

I don't know why I was unable to boot my computer from a **Windows CD** after making the changes first described - the only real difference between my configuration and that you suggested was that I designated hda3 as an ntfs partition for **Windows** data and hda 4 as an ext 2 for **Ubuntu** data (i e, the opposite of the configurations you suggested) ; as both were empty, I find it hard to believe that this was the cause of my problems. I should have thought that the only essential thing was how the boot partition, /dev/hda1, was configured - but obviously, I have a lot to learn !...

Well, I'm back to square 1, or, as the phrase goes, equally confused, but at a higher level. In any event, at the cost of several hours of work and some worry - had I irretrievably lost my data or not ? - I've gained some experience in using **GParted** ! My present understanding is that what you were suggesting that I do was to move all my Ubuntu files and data to /dev/hda6, install **XP** from a CD to /dev/hda1, and then re-install **Ubuntu 6.06** from a CD to /dev/hda3, after which - I'm guessing here - I could copy my earlier **6.10** files from hda6 to hda3, thus updating my system. Is this assumption correct ? In any event, if in reading the above, you can see where I went wrong, I'd appreciate you giving me a heads up (in some detail, as otherwise it's too easy for me to miss something essential)....

Thanks again for bearing with me so far !...

Henri

---

### Post by bulldog on 2007-01-07
The only thing I can suggest to you is to use the ext3 file system rather than ext2.
Why windows won't install on your primary NTFS partition is beyond me.
But as you said,no data loss and you learned a lot about partitioning.

If you have more questions,just put them on the forum and we have a look at them.

---

### Post by mhenriday on 2007-01-07
> **bulldog said:**
> The only thing I can suggest to you is to use the ext3 file system rather than ext2.
...

If you have more questions,just put them on the forum and we have a look at them.

I e, use the ext3 file system for the /dev/hda3 partition for the **Ubuntu 6.06** installation after I have installed Windows to /dev/hda1 ntfs ? Just what is the difference between the ext 2 and ext3 systems ? And in case of a new attempt to set up a dual-boot machine, should I, as I have done previously, first move my present **Ubuntu** data to /dev/hda6 extended ? And in the event that, despite the odds, I do succeed in installing **Windows XP** and **Ubuntu 6.06**, can I use the data on /dev/hda6 extended to upgrade back to my present **Ubuntu** set-up ? What is the procedure to be followed - or will **Ubuntu** _automatically_ run in the present **6.10** version upon booting ?...

As you see, I do always seem to have more questions to ask - thanks for your kindness in answering the ones I've posed heretofore !...

Henri

---

### Post by mhenriday on 2007-01-14
> **bulldog said:**
> ...

If you have more questions,just put them on the forum and we have a look at them.

Well, **bulldog**, as for some reason I've not as yet been able to understand, my various attempts to install a dual-boot system on my present set-up have failed, I intend to try something new. In return for some work I've done, I'm going to be receiving an external hard disc - a **Packard Bell Store&Save** with 400 GB capacity, 8MB cache, and a USB 2.0 connexion. Would it be possible to run **Windows XP** from such a device on my computer, so that it would be unnecessary to perform any adjustments to my present internal hard disc ? If so, I should be grateful for any tips you could give on how to configure my present set-up so that both **Ubuntu 6.10** and **Windows XP** become available to me when the machine is started. I presume that this would require re-loading **GRUB** to allow me to choose between which of the two hard discs is to be booted - is this correct ? If so, I should appreciate detailed instructions on how to do this as well. Or am I way off base here, and the configuration I have in mind impossible ?...

Thanks for your help !...

Henri

---

### Post by bulldog on 2007-01-14
Don't know if windows will run from a USB drive,never tried it.:D 
But I can't understand why you can't make a dual boot system with just one internal disk.
It should be easy to do if you make it not too hard for yourself.
When you have your new USB disk backup all your data to it and wipe out all the partitions on your internal disk.

Make a note how you want to divide the space on your 'old' disk and format it.
Be sure your first partition is NTFS for windows.

Install windows to this partition.
Then install Ubuntu and GRUB on their partitions.
And you have a dual boot system :D 
Now you can copy your data from the external drive back to the internal if you wish,or leave it where it is [I do]

Just keep things simple and it will work.

---

### Post by mhenriday on 2007-01-15
> **bulldog said:**
> ...

Make a note how you want to divide the space on your 'old' disk and format it.
Be sure your first partition is NTFS for windows.

Should be no problem....

> Install windows to this partition.
Then install Ubuntu and GRUB on their partitions.

Again a few questions : can I here make use of the **GRUB** that comes with the **Ubuntu 6.06** live CD, or do I need to make a copy (CD or floppy ?) of the drive from the **GRUB** website and use it under the installation process (and in that case, _before_ or _after_ installing **Ubuntu**) ? Will **Ubuntu** _automatically_ install in the hda3 partition if the latter is marked as ext3 and hda1 and hda4 are both marked as ntfs ? If not, what do I need to do to see to it that the **Ubuntu** CD doesn't once again repartition the whole hard disc, thereby wiping out **Windows** ? And where should the boot flag go - on hda1 ntfs, eller on hda3 ext3 (what I want the computer to do is boot to **Ubuntu** by default, but leave me the option to boot to **Windows** by choosing that path in **GRUB**....

> And you have a dual boot system :D

That would indeed be splendid !...
 
> Now you can copy your data from the external drive back to the internal if you wish,or leave it where it is [I do]

I e, copy my **Ubuntu** data from the externa hard disc to hda6 ext 2 (if I so choose) with the help of the **Gparted** live CD ?... 

> Just keep things simple and it will work.

Do my best !...

Henri

---

