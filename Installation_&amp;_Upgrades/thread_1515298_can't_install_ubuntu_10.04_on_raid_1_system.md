---
title: "can't install ubuntu 10.04 on raid 1 system"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by kennyssp on 2010-06-22
Hi. I tried to install new ubuntu on Intel raid 1 system but it said that:
> The ext4 file system creation in partition #1 of Serial ATA RAID isw_chibcceegh_Volume0 (mirror) failed.


My config is:

P5Q Pro
2x500 GB Seagate HDD
Intel Raid 1
Boot ubuntu from USB Drive (Wonder does this cause the problem?)

---

### Post by xombiemp on 2010-06-23
I'm getting the same error as well trying to install 10.04 server.  I have 2 500gb Western Digitals in sata raid 1.  Is this a bug in Ubuntu or is there a fix for this?

P.S.  I'm installing using a live cd.

---

### Post by ronparent on 2010-06-23
This seems to be a current glitch in trying to install 10.04, desktop or server, to a raid drive. The best advise seems to be to use the alternate CD. If your more adventuresome you might try partitioning before you try to install. Note however that gparted from the 10.04 live cd 1) will not be able to see the raid 2) if you chose to partition manually through a terminal, you have to partition using the symbolic link for the array ( ie /dev/mapper/isw_chibcceegh_Volume0) 3) the same applies if you use the live cd from an earlier version. Also if the earlier version is 9.04 or earlier you will have to install dmraid to the live cd session to access the raid array.

I have installed 10.04 to a pre-partitioned raid0 with no problems from the live cd. If you want to boot from the raid in step 8 you also have to hit the 'Advanced' box and enter your array (ie /dev/mapper/isw_chibcceegh_Volume0) as the location for grub2 to write the grub MBR. Post if you need more.

---

### Post by konradson on 2010-06-23
usually RAID utilities in PC mainborards are only for Windows. I mean that they only work with Windows. I've seen this even in Sun Fire 2100 servers, with SATA controllers.
 
You have a choice, install the OS in one disk and do a software RAID, with metadispositives.
 
Good Luck.

---

### Post by ronparent on 2010-06-23
If a system is going to share data on a raid with both windows and ubuntu (or any Linux distro) you are limited to using dmraid. Dmraid serves the same purpose as a driver for a MB raid chipset. A software raid is usable only in linux.

---

### Post by kennyssp on 2010-06-29
Can you tell more specific? I'll use hiren boot cd to partition RAID 0 array first or use what programs/command in ubuntu CD? I want to do it so bad


> **ronparent said:**
> This seems to be a current glitch in trying to install 10.04, desktop or server, to a raid drive. The best advise seems to be to use the alternate CD. If your more adventuresome you might try partitioning before you try to install. Note however that gparted from the 10.04 live cd 1) will not be able to see the raid 2) if you chose to partition manually through a terminal, you have to partition using the symbolic link for the array ( ie /dev/mapper/isw_chibcceegh_Volume0) 3) the same applies if you use the live cd from an earlier version. Also if the earlier version is 9.04 or earlier you will have to install dmraid to the live cd session to access the raid array.

I have installed 10.04 to a pre-partitioned raid0 with no problems from the live cd. If you want to boot from the raid in step 8 you also have to hit the 'Advanced' box and enter your array (ie /dev/mapper/isw_chibcceegh_Volume0) as the location for grub2 to write the grub MBR. Post if you need more.

---

### Post by ronparent on 2010-06-30
Each Ubuntu release has had it own quirks with regards to installing on a raid. The 10.04 desktop release does come with dmraid which allows you to access your raid (apparently '/dev/mapper/isw_chibcceegh_Volume0'). The quirks are 1)that gparted run from 10.04 will not work on a raid partition and the partitioning step of the installation will fail 2) that the installer will try to install the grub boot loader to /dev/sda and that if this is one of your raid drives, that will fail.

The workarounds I have used are to:

 1) pre-format (ext2, ext3 or ext4, it doesn't matter) the target partition with an earlier version of Ubuntu, either installed or live cd. The catch is that you must have dmraid installed or install it. This can be done to a live cd session if you have internet capability - gparted will not see the raid or its partitions unless the raid drives are activated by dmraid.

To install dmraid in a terminal - Code:

> sudo apt-get install dmraid

To activate the raid - Code:

> sudo dmraid -ay

You now can start gparted (System>Administration>Gparted or Partition Disks depending on the version your running from) and select an unallocated space to create your target sized as you want it - or resize an existing partition to give you unallocated space in which to create your partition in. You will also have to create a swap partition if there is not already one present. We probably don't have to address it here, but if you already have two or more partitions on this array, you should create additional partitions in an extended partition (you are currently limited to four total primary partitions including an extended partition on any drive). Note the name of this partition. Once your pre-formated partitions is created on the raid you can boot into your 10.04 live cd. 

At this point you pick the desktop icon to start the installation of 10.04. When you reach step 4 of 7 you will pick the option to manually specify the partition you have previously formatted to install to. When step 5 of 8 appears, select your partition and click 'change' at the bottom of the window. In the box select the format from the drop box choices (probably ext3 or ext4, same as what you previously formated). Do **NOT** check to format. In the next drop down select '/' - the mount point you file system is to be installed to.

 2) To hopefully handle the 2nd quirk, at step 8 of 8 you will click on the box labeled 'Advanced'. At this point you should be able to select the top array name (the name representing the entire array, not one of the partitions) from a drop box. After this you have done everything you can do. You can click next and you system will be setup on the chosen partition. I have just run into the problem in Mint where this was not adequate. The installer still tried to install to sda and resulted in a 'fatal failure'. If this happens don't despair - it can still be fixed. Just continue to install without the boot loader. I will have to research the specific steps and get back to you on this if we have to address it.

As you can tell, raid in Ubuntu is not for the faint hearted or under informed. It is doable. You will have to do some learning along the way. If you are going to try and stick with it, I or others will be able to help along the way.

---

### Post by my_2_cents on 2010-06-30
@ronparent;

Have you heard of anyone having success installing 10.04 on a RAID1 Windows 7 system using wubi.exe? Think the alternate distribution iso might work? wubi seems pretty simple, but there might be a way I haven't yet found to tell it to do optional things like load a raid driver.

---

### Post by kennyssp on 2010-06-30
thank ronparent so much, you're the best. I'm trying to install it, follow your instruction. if having any prob, I will informs you and others soon.

> **ronparent said:**
> Each Ubuntu release has had it own quirks with regards to installing on a raid. The 10.04 desktop release does come with dmraid which allows you to access your raid (apparently '/dev/mapper/isw_chibcceegh_Volume0'). The quirks are 1)that gparted run from 10.04 will not work on a raid partition and the partitioning step of the installation will fail 2) that the installer will try to install the grub boot loader to /dev/sda and that if this is one of your raid drives, that will fail. 

The workarounds I have used are to:

 1) pre-format (ext2, ext3 or ext4, it doesn't matter) the target partition with an earlier version of Ubuntu, either installed or live cd. The catch is that you must have dmraid installed or install it. This can be done to a live cd session if you have internet capability - gparted will not see the raid or its partitions unless the raid drives are activated by dmraid.

To install dmraid in a terminal - Code:



To activate the raid - Code:



You now can start gparted (System>Administration>Gparted or Partition Disks depending on the version your running from) and select an unallocated space to create your target sized as you want it - or resize an existing partition to give you unallocated space in which to create your partition in. You will also have to create a swap partition if there is not already one present. We probably don't have to address it here, but if you already have two or more partitions on this array, you should create additional partitions in an extended partition (you are currently limited to four total primary partitions including an extended partition on any drive). Note the name of this partition. Once your pre-formated partitions is created on the raid you can boot into your 10.04 live cd. 

At this point you pick the desktop icon to start the installation of 10.04. When you reach step 4 of 7 you will pick the option to manually specify the partition you have previously formatted to install to. When step 5 of 8 appears, select your partition and click 'change' at the bottom of the window. In the box select the format from the drop box choices (probably ext3 or ext4, same as what you previously formated). Do **NOT** check to format. In the next drop down select '/' - the mount point you file system is to be installed to.

 2) To hopefully handle the 2nd quirk, at step 8 of 8 you will click on the box labeled 'Advanced'. At this point you should be able to select the top array name (the name representing the entire array, not one of the partitions) from a drop box. After this you have done everything you can do. You can click next and you system will be setup on the chosen partition. I have just run into the problem in Mint where this was not adequate. The installer still tried to install to sda and resulted in a 'fatal failure'. If this happens don't despair - it can still be fixed. Just continue to install without the boot loader. I will have to research the specific steps and get back to you on this if we have to address it.

As you can tell, raid in Ubuntu is not for the faint hearted or under informed. It is doable. You will have to do some learning along the way. If you are going to try and stick with it, I or others will be able to help along the way.

---

### Post by kennyssp on 2010-06-30
okie here comes the problem. Step8, I click on Advanced, then chose 1st option (there are 3 options, **/dev/mapper/isw_ebeafbadaj_Volume0 Linux device-mapper (mirror) (500.1BG)**, **dev/mapper/isw_ebeafbadaj_Volume01**, **dev/mapper/isw_ebeafbadaj_Volume0-1**). after that, it installed perfectly until reboot...nothing happened then :(. It seems no boot loader or MBR not found.

---

### Post by Yompa on 2010-06-30
Ronparent is right. 

A few weeks ago I took a slightly different approach installing 10.04 on fake-raid (BIOS-raid) together with a Win7 partition. A separate boot CD also came in handy. [Super Grub Disk]("http://www.supergrubdisk.org/") or similar was needed.

I'm fairly new with Linux myself, I didn't take notes and it was a few weeks ago I did this so I hope you understand if I'm not perfectly clear on all the details.

Like everyone else I found out 10.04 failed on formating the raid partitions. Everyone suggested soft raid, a better alternative but in this case I had an existing Win on fake-raid I didn't want to touch.

After a lot of Google and hours of reading posts from frustrated people with the same problems I used a 9.10 Live CD to create and format the Linux partitions. 

If you haven't created the needed partitions manually before the minimalist can use: A Linux swap partition (2 x RAM size is a good suggestion) and one ext partition for all the rest.

Then I used the regular 10.04 Desktop install CD. At partitioning I used the already existing swap and the existing ext-partition became root (/). The installation went well but grub2 failed to install, again the raid issue. Some parts of 10.04 clearly didn't recognize the raid. The installation was kind enough to allow me to continue without grub2.

At this point I had a 10.04 on fake raid with no means of booting it except via an extra boot CD. Once I had my new 10.04 booted (boot CD help) I tried [installing grub2 manually]("https://help.ubuntu.com/community/Grub2") from the shell. 

When using "sudo grub-install" people recommended adding --recheck if the raid device or disk wasn't recognized. That did absolutely nothing for me. Grub refused to see the raid until I tried "sudo update-grub". Suddenly the raid was visible and I could install the grub boot loader.

Everything works like a charm. 10.04 and Win on fake-raid using Grub2.

Summary:
Partition and format using a tool CD (9.10 worked)
Install 10.04, use existing partitions, don't format, ignore failed grub install
Boot system with tool CD
Perform a premature update-grub command.
Install grub to raid manually

In retrospect you can probably use Super Grub Disk to install a legacy boot directly skipping some of my steps.

---

### Post by stelamethew on 2010-07-01
Mainly RAID work only with windows. I have seen this in SunFire2100 servers. Currently I installed 10.04 with partitioned raid0 from cd, If you want to boot raid in step 8, this option includes in Advanced box.

---

### Post by ronparent on 2010-07-01
Check your bios boot options. You can have the MBR installed correctly but it isn't the one selected to boot. It does appear that the first option you checked above is correct.

In my bios, the raid array is one of the listed boot options. To boot the array (where you have the MBR you are trying to boot to) I had to move it up to be first in the list. In my bios it was found under Advance Options>Hard Disk Boot Order. The specific terminology and how the bios options are presented vary by hardware maker, bios maker, whim of the sytem designer, etc., so you have to interpret what is presented in your bios to some degree. Keep me posted. It sound like you are on the right tack.

ps kennyssp: I didn't see the two above posts when I replied, but you are still on track. Both posts are correct. Also, you may want to read this if we need to fix the grub: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html)

---

### Post by masgeeks on 2010-07-24
Hi... I thought I'd add my experience.  I solve my RAID1 install issues after some head scratching.  Was installing on machine with two TB HD's, 64 bit server ver of 10.04.

Mine was two part - I had to go into the BIOS and change not the order of boot devices, but instead had to tell it to only look at CD drive and nothing else.  The machine is a DELL and came equipped with hardware RAID, and even though there was NO RAID ARRAY present, and I had obliterated the disks, I still had issues when using the Ubuntu CD to do my partitioning and setup my RAID1 array.

Once changing the BIOS I was then able to install using partition disks during Ubuntu server install and set up my RAID1 without having to fight with it - so problem one solved.  However, when it would continue to install, after formatting, I started getting warnings about package corruption errors.  Blew my mind, I had used the same CD hours before to install on another box, 64 bit server install, and had used it during the past week for several other machines without issue.  I even ran a check disk function on the media which showed it was fine.  So, I figured I still had hard disk issues with the current machine.  

Whelp - NO.  I *got smart* and tried the install again but this time put the media in the OTHER CD drive on the machine.  

Life became good, lol...

After the install completed, then I went back into the BIOS and changed my settings back the way they were so on boot up it would look for more than just the CD drive, of course.

Life became REALLY good at that point... happy 64 bit server, happy RAID1 array, happy me...  :)

---

### Post by mclad on 2010-08-09
I'm having a similar problem. Desktop CD already recognised drives (dmraid -ay told me this), gparted /dev/mapper/via_bfidghddbd enabled me to setup ext4 and linux-swap logical partition.
 
I then ran the ubiquity graphical installer which failed on step 3 or 4 I think with error message:
ubi-partman failed with exit code 10
 
ignoring this error and at step 7 choosing the **advanced** option and selecting /dev/mapper/via_bfidghddbd for my root install, spits me straight back out to step 5 for some reason.
 
So i tried the **alternate CD (amd64)**
This detected my SATA RAID configs and asks to activate them, I choose yes. AFter this the next message box is **"[!!] Partition disks**. This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings" etc... BUT there are no partition shown and the only two options are (1) Undo changes to partitions or (2) Finish paritioning and write changes to disk
 
Neither of these get me anywhere. Selecting finish partitioning tells me "No root file system is defined, please fix from partitioning menu" and returns to the previous menu.
 
Undo changes to partitions gets me to a blue screen (!!) which I have to control-C to get back to the partition disks menu (with undo or finish options only again).
This time I choose to <Go Back> which again gets me a blue screen.
 
Frustrating...

---

### Post by ronparent on 2010-08-10
The situation has gotten easier.

I've learned thatthe basic problem is that gparted, as distributed, will not recognize raid or raid partitions. To get around this, I have booted to a live cd and installing from there. _Before_ you start the install use the synaptics pakage manager to install kpartx for the session. After this the install should proceed normally. You may and will probably get a 'fatal error' on the grub install - this is fixable. Keep us advised of how you make out. Good luck.

---

### Post by watling on 2010-08-21
I'm new to this site and new to Linux. I've registered on the site in the hope of getting help with my installation problem and to get to know more about Linux.
I too have been unsuccessfully trying to install Ubuntu 64-bit server to a bare metal Fujitsu Primergy TX100 S1 server which I have bought specifically for the purpose, being blissfully unaware that the process is frought with difficulties. It is a relief however to find that the problems are not down to my doing anything silly.
The server mothererboard is equipped with an hardware RAID controller which allows me to configure a RAID1 set which is then detected by the installation CD which goes on to ask me if I want to activate it. On activation the partitioning screen then displays but no SATA Raid drive is listed.
So I'll be following this thread with interest, hoping that you more knowledgable types can come up with a solution. I'm already impressed with ronparent's contributions!

---

### Post by mganapa on 2011-01-05
I am having the same issue. However there are a few minor differences. 

[LIST]
[*]I am trying to install Ubuntu 10.10 Server x64
[*]The installation detects the raid 1 arrays and prompts me if SATA raid drivers have to be loaded. If I answer yes, it loads dmraid and takes me to a screen where I only have three options: Configure iSCSI drives, undo changes to partition and write partition changes to disk. The issue is that no partitions are actually created and I cannot create them manually either.
[*]If I chose not to load the dmraid then I see the individual disks and no raid 1 arrays.
[/LIST]
I tried to use the advanced configuration but the issue persists. 

What I am trying to achieve is this:

[LIST]
[*]4 drives on two raid 1 (Hardware) configuration.
[*]On the two raid 1 arrays, create an LVM with two volumes.
[*]Create my partitions under the two LVM volumes.
[/LIST]
My system is a [supermicro 6014H-T server]("http://www.supermicro.com/products/system/1U/6014/SYS-6014H-T.cfm") and it does have support for hardware raid 0, 1 & JBOD built in using a marvel 4 port SATA controller. It also has an ICH5R SATA 2 port controller which I am not using. All the HDDs are matching 1.5 TB Seagate drives.

---

### Post by mganapa on 2011-01-07
As an update to my previous post, I decided to dump the fake raid (raid configuration using Adaptech HostRAID) and do a software raid instead. When I try t create a RAID array (0, 1, 5, 6 or 10) during Ubuntu installation I am encountering a problem. The partition manager does not set the bootable flag to on while creating the /boot or / partitions on any of my 4 1.5 TB drives. This is using Ubuntu 10.10. After reasearching a lot, I found out that 9.04 version was more reliable in creating software raid during installation. This was indeed the fact. I was able to set up RAID 5 using all of my 4 disks and install Ubuntu system (9.04) on it. When I rebooted the machine, it comes on and does not show the grub loading screen at all. Instead I see a blinking cursor. What could be the proble?

---

