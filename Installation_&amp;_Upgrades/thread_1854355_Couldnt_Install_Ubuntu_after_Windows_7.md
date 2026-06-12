---
title: "Couldnt Install Ubuntu after Windows 7"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by Amajed on 2011-10-04
Hi

I've been trying to install Ubuntu on my system all day long .. without success .

Infos:
4x SSD Vertex 2 60GB on RAID 0 (intel ICH10R Controller) Total of 223.59GB in the system count
this set has 2 partitions
first partition is 60GB for Windows 7 64Bit (Installed and working fine)
Second Partition is 143GB
There's a Free allocated space of 20GB (was intending on installing Ubuntu in it)

also I have 2x Seagate 1TB HDD for my personal files (will never touch these at all)


so , what I'm trying to do is that I have a Win 7 64bit on my first partition the 60GB (cant be touched)
and Ubuntu 64bit my the free 20GB space
I'll leave the 2nd partition the 143GB for my Programs/Games so it cant pe touched too


I've downloaded Ubuntu 11.04 64Bit on my 4GB USB key
its working just fine . I can see the Live OS and I can use the install menu just fine


so , when I go to the install menu there are 3 options:
1- install ubuntu Alongside with Windows 7
2- Install Ubuntu over Windows 7 (removes the Windows 7)
3- somthing else

a Pic:
[http://www.psychocats.net/ubuntu/images/installingnatty06.png](http://www.psychocats.net/ubuntu/images/installingnatty06.png)

I tried the first and the 3rd options

the 1st options installs just fine , at the end when I was asked to restart , after the reboot I get a massage says:
error: no such device: (long number here).
grub rescue>

I dont know what that is . no idea at all

so I used my USB Windows install to run CMD and then I fixed the boot manager
now my windows 7 is fine

I again tried to install ubuntu but this time with the 3rd option (something else)
I found my Free 20GB space . and created a "root /" partition with Ext4 Format
then I selected it and clicked on install , massage was asking me about Swap area but I pressed Continue (I got 12GB Memory so I thought it should be more than enough)

after finishing the install and reboot , the same massage appears and I had to fix the Boot manager for the windows



I tried to search for a soulotion before posting here , but nothing helped

also theres a strange thing

after my last attempt it I tried again to install ubuntu from the same option (Something Else)
and I was suprised that the partition that I created on the Free 20GB Space was deleted
How did that partition Deleted ?




TL;DR:
error: no such device: (long number here).
grub rescue>

every time I install ubuntu 64Bit after Windows 7 64Bit

---

### Post by sanderd17 on 2011-10-04
Can you give us the output of the boot info script? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Run the scrip from the live OS.

---

### Post by Amajed on 2011-10-04
Thank you :)

the result:
boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sde...
Computing Partition Table of /dev/sdf...
Computing Partition Table of /dev/sdg...
Computing Partition Table of /dev/mapper/isw_deidfccjbe_Stripe...
Searching sde1 for information... 
Searching sdf1 for information... 
Searching sdg1 for information... 
Searching isw_deidfccjbe_Stripe1 for information... 
Searching isw_deidfccjbe_Stripe2 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".




This result is just after I installed Ubuntu on the Free 20GB Space (still havnt fixed the Boot manager for  Win7)

---

### Post by sanderd17 on 2011-10-04
I need your help on this. You have way too many hard drives for easy understanding.

Some linux terms: sd stands for solid disk (aka hard disk). This can be an SSD, a regular HDD or a USB stick. They are numbered alphabetically. So normal computers have and sda, some also have a second hard disk called sdb.

Those hard disks contain partitions. The partitions are numbered with real numbers. So if the first hard disk has 3 partitions, they are probably called sda1, sda2 and sda3. They don't have to follow each other. If in that configuration sda2 would be deleted and a new partition would come in it's place, that would be partition sda4. So you would have sda1, sda4 and sda3.

Now I have to understand what drive is what.

I believe sde and sdf are your two 1TB HDDs. And sdg is a 4GB drive, probably your USB stick.

So sda, sdb, sdc and sdd are the drives in RAID0. The RAID0 device is also seen as a drive. Namely as the drive "mapper/isw_deidfccjbe_Stripe".

isw_deidfccjbe_Stripe indeed has two partitions (regularly numbered), so one partition should contain Windows and another one should contain Linux. But I see that both partitions are formatted as ntfs. The first one does contain Windows boot files, but the second one doesnt.

Linux can't be installed to an NTFS partition. Linux can read and write NTFS partitions, but you need a superior* native Linux partition as root and boot partition *(superior on features like user rights and symbolic links). 

If you know you formatted it as NTFS, install it again and format it as EXT4 (currently the best supported native Linux filesystem available).

Now back on top of your file. Grub looks for the UUID 73a9c1d0-94d8-402e-a960-69c1b3e7bba4 (this should also be the number you see in your error message). But I can't find any drive with that UUID, in fact, it should be the UUID of the partition isw_deidfccjbe_Stripe2. So if you formatted that partition right, you can change the UUID.

---

### Post by Bluesan on 2011-10-04
Take some guidance on dual booting from here:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Amajed on 2011-10-04
> **sanderd17 said:**
> I need your help on this. You have way too many hard drives for easy understanding.

Some linux terms: sd stands for solid disk (aka hard disk). This can be an SSD, a regular HDD or a USB stick. They are numbered alphabetically. So normal computers have and sda, some also have a second hard disk called sdb.

Those hard disks contain partitions. The partitions are numbered with real numbers. So if the first hard disk has 3 partitions, they are probably called sda1, sda2 and sda3. They don't have to follow each other. If in that configuration sda2 would be deleted and a new partition would come in it's place, that would be partition sda4. So you would have sda1, sda4 and sda3.

Now I have to understand what drive is what.

I believe sde and sdf are your two 1TB HDDs. And sdg is a 4GB drive, probably your USB stick.

So sda, sdb, sdc and sdd are the drives in RAID0. The RAID0 device is also seen as a drive. Namely as the drive "mapper/isw_deidfccjbe_Stripe".

isw_deidfccjbe_Stripe indeed has two partitions (regularly numbered), so one partition should contain Windows and another one should contain Linux. But I see that both partitions are formatted as ntfs. The first one does contain Windows boot files, but the second one doesnt.

Linux can't be installed to an NTFS partition. Linux can read and write NTFS partitions, but you need a superior* native Linux partition as root and boot partition *(superior on features like user rights and symbolic links). 

If you know you formatted it as NTFS, install it again and format it as EXT4 (currently the best supported native Linux filesystem available).

Now back on top of your file. Grub looks for the UUID 73a9c1d0-94d8-402e-a960-69c1b3e7bba4 (this should also be the number you see in your error message). But I can't find any drive with that UUID, in fact, it should be the UUID of the partition isw_deidfccjbe_Stripe2. So if you formatted that partition right, you can change the UUID.
Thank you very much , now I understand what those litters mean .

back to the problem, I mentioned that I used EXT4 as the format type of the partition that I installed Ubuntu in it. also I have mentioned that after I get the Error message it seems that the partition that I created is gone and deleted for some reason , this is why u were not able to see it in the result.txt file.

in my RAID0 set there are 2 partitions . first one for Win 7 and second one for my Programs/Games (Both are NTFS) and I left 20GB Free space so I can create a partition (as EXT4 root/) for Ubuntu. and this is the one that has been deleted every time I install Ubuntu in it. I think this is my problem , why is this partition been deleted ? it should stay as it is even if theres a problem in the boot system or w/e .
> **Bluesan said:**
> Take some guidance on dual booting from here:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Natty#Dual-Booting_Windows_and_Ubuntu)
I've read it , but nothing helped . it seems like I'm doing the right thing . but also have problem .
thank you

---

### Post by sanderd17 on 2011-10-04
> **Amajed said:**
> Thank you very much , now I understand what those litters mean .

back to the problem, I mentioned that I used EXT4 as the format type of the partition that I installed Ubuntu in it. also I have mentioned that after I get the Error message it seems that the partition that I created is gone and deleted for some reason , this is why u were not able to see it in the result.txt file.

in my RAID0 set there are 2 partitions . first one for Win 7 and second one for my Programs/Games (Both are NTFS) and I left 20GB Free space so I can create a partition (as EXT4 root/) for Ubuntu. and this is the one that has been deleted every time I install Ubuntu in it. I think this is my problem , why is this partition been deleted ? it should stay as it is even if theres a problem in the boot system or w/e .



Can you launch gparted on the Live OS, create a new ext4 partition on that 20GB empty place and reboot? Check if that partition is removed or not.

Both the installer and Gparted use the parted library to change partitions. So they should have the same results.

---

### Post by Amajed on 2011-10-04
Sorry for been late , and thank you for your assists.

I Created the partition as EXT4 from the GParted in the Live OS then reboot and logged in to the Live OS again and the Partition was removed and I have my Free Space back again

I thought I should mention that I'm using Ubuntu 11.04 Desktop 64bit downloaded from ubuntu.com

also I thought I should remind you again that the Raid is a RAID 0 (Stripe) on Controller Intel ICH10R and the board is an X58 Chipset


so what else can I try ?


and thanks again :)



I would like to add one thing , I tried to burn an image to CD and try a new install from it . but unfortunately I get the same error and the Partition has been deleted or removed.

at least now I'm sure that my USB Key is OK , need to focus on the Deleted partition thing . why I cant keep the Created partition after I reboot ? this is what seem to be the problem.

---

### Post by Amajed on 2011-10-04
Sorry for bumping this but I really loved the Live OS and I desperately wants to install the system so I can enjoy it more.

Please help me out


Sorry , and Thank you

---

### Post by sanderd17 on 2011-10-04
> **Amajed said:**
> Sorry for bumping this but I really loved the Live OS and I desperately wants to install the system so I can enjoy it more.

Please help me out


Sorry , and Thank you

You bumped a bit early, I was just a few hours in a lesson. Bumping every 24 hours is considered as polite.

Anyway, your RAID controller is indeed the problem. The partition isn't created.

I now assume you have a backup (you should always have one), because I don't know how dangerous it is.

Could you change make a file on the windows RAID0 partition? Just a random file, than reboot and see if it's still there. Just to check if you can write to the disk.

It seems that Ubuntu isn't able to execute all commands like it should. I never worked with real RAID (only with software RAID), so I will be handed over to googling.

---

### Post by Amajed on 2011-10-04
Yeah sorry about the bumping , thread was already in the second page and I was too excited to solve this and start using Ubuntu. sorry again

about the back up , Win7 is a new fresh install , and games/programs are already backed up so I wont be sad if something goes wrong , but I prefer not losing Win7 cause its a pain in the butt installing programs/games and updates . not to mention the tweaks . but sure I can screw as hard as I could go full with it.


So , sorry I didn't really get what you've just asked me , u want me to make a file on Windows 7 Partition ? and see if its still there ? do you mean by Live OS then go to the Win7 partition and create a file ?

if that what you mean then sure , I'll be back in a min or so.


Thank you very much , I really appreciate that :)

---

### Post by sanderd17 on 2011-10-04
It looks like Ubuntu is not able to edit your RAID hard disks.

So I ask you to create a file on one of those partions with the live OS, and afterwards check if it's still there (with your windows installation or with the live OS).

---

### Post by Amajed on 2011-10-04
OK I've Created an empty file and named it "mytesting" and restarted the system . logged in to Live OS and the file still there , then I logged in to Win7 and the file is still there too.

what do you think ?

---

### Post by sanderd17 on 2011-10-04
So you just can't edit partitions.

I got to googling, and found this: [http://ubuntuforums.org/showthread.php?t=1351580](http://ubuntuforums.org/showthread.php?t=1351580)

This thread suggests you should use the alternate installer (a text-based installation method, not a live CD).

And maybe you first have to create a new device.

I'm going to bed now. It was a late day, and I'm kinda tired.

---

### Post by Amajed on 2011-10-04
Thank you.
I've read it carefully , I downloaded Ubuntu 11.04 Alternate 64bit and burned it to a CD
started the instillation and it did asked me about activating the Raid and I've chosen Yes.
I created a Partition in the Free Space as EXT4 and Root / also Flagged as Bootable.

in the end of the install process and after rebooting the system the same error came and I've checked if the partition is still there , but too bad its not . I guess this method wont work.


I'm starting to think of shrink one of my 1TB HDD (both not on the Raid set but both are on ICH10R Controller) and use a 20GB of space for Ubuntu. I really don't want to touch those Hard Drives but its worth it.


I'll be doing it tomorrow , I'll go to bed now . if you have any suggestions about what I'm going to do please tell me ;)



Good night and have a nice dreams.

---

### Post by Amajed on 2011-10-04
Couldn't wait , so I defragmented one of my 1TB HDD and made a 20GB Free space in it by Shrinking it.
I started the Install . Created a Partition as EXT4 Root/ , but for the  installation device for boot loader I for some reason have chosen Win7  Partition , in the middle of the install process it gave me an error  massage saying that it couldn't install the boot loader in that  partition and I have to chose another one . for some reason I could not  chose any of the list (clicking OK wont do anything at all) so I just  restarted my system.

after that I check if the partition is still there . and FINALLY its  there , it seems the problem wont happen if I install ubuntu on a none  Raid drive (Too bad :()

this time I'll sleep for sure . tomorrow I'll start the installition  again and see how it goes . in the mean time please tell me which  partition I should select for the installation device for boot loader.



Thanks again ;)

---

### Post by oldfred on 2011-10-04
You do not install grub2's boot loader to the partition but to the MBR of the drive you installed to. Then in BIOS set to boot that drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Amajed on 2011-10-05
> **oldfred said:**
> You do not install grub2's boot loader to the partition but to the MBR of the drive you installed to. Then in BIOS set to boot that drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")
If I isntalled the boot loader to the MBR of the drive and set the boot to that drive will I be able to use my Win7 normally ? or I should be changing the boot order every time I have to log in to the other OS ?

I want a boot menu where it ask you which OS you want to boot in to.

so what is the right choice here ?


and thank you very much ;)

---

### Post by sanderd17 on 2011-10-05
Windows is not able to see Linux OS.

So you need to boot first to a drive on which the MBR points to Grub. It doesn't really matter where the MBR of Linux is, but that should be set as primary drive in your BIOS. Than Grub starts and lets you choose the OS to boot.

---

### Post by Amajed on 2011-10-05
OK , I think I got it now , I'll go try it and see if its works. I still want to install Ubuntu in a RAID0 set tho :/ good thing that I can use the RAID0 for installing files and such.


Thank you very much , will get back when I finish the instillation .

---

### Post by Amajed on 2011-10-05
Finally the system is working , everything seem to be alright . somehow its not as fast as Windows 7 but maybe because of the RAID0 set in my Win7 , wish I could install Ubuntu on the RAID0 but I guess I'll stay like this for a while till I figure it out.


nothing seem to bother me ,other than games compatibility , they seem to not work like they should be even if the game has a Linux installer already . I guess its normal since most companys care for Windows not Linux .


anyway thanks a lot guys .. been very helpful and I've learned many things.


Thank you and have a nice day ;)

---

### Post by sanderd17 on 2011-10-05
I'm sorry that I couldn't help you to the end.

I guess 4 SSDs in RAID0 vs a HDD makes some difference in speed ;)

---

### Post by PayPaul on 2011-10-11
> **sanderd17 said:**
> 
Some linux terms: sd stands for solid disk (aka hard disk). This can be an SSD, a regular HDD or a USB stick. They are numbered alphabetically. So normal computers have and sda, some also have a second hard disk called sdb.

Those hard disks contain partitions. The partitions are numbered with real numbers. So if the first hard disk has 3 partitions, they are probably called sda1, sda2 and sda3. They don't have to follow each other. If in that configuration sda2 would be deleted and a new partition would come in it's place, that would be partition sda4. So you would have sda1, sda4 and sda3.



I have a similar problem mostly to do with understanding where my drives are and which ones are named what. From your explanation above I finally understand how Gparted sees my drives and partitions. What I've gathered from looking at the devices in that program is that my Window7 partition is labeled sde3. That's really weird as it is the first partition or C drive of the main HD which has 3 partitions in it. I have a Wubi install currently of Ubuntu. Why would Ubuntu/Wubi give the main drive an sde designation? Could this also explain my current busybox, drop to a shell boot problem? Wouldn't it be better if Windows7 and my Wubi install be seen on a drive labeled sda not sde?

---

