---
title: "Disk /dev/sdb doesn't contain a valid partition table"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2012-09-07
Hi! 

I just got a new desktop computer, and wanted to make it a dual boot. 

I have been running Ubuntu for years on an old computer. **But I am still a novice especially with the technical stuff. **

Anyway...    

The new computer came with a 2 TB hard drive with Windows 7 installed. 

I added a second 2 TB hard drive to install Ubuntu on (WD)     

The new hard drive was not formatted.

 I did not format it because:


[LIST=1]
[*]I did not want to format with windows and then have a mess when I installed Ubuntu over it.
[*] I figured if I used Wubi to install Ubuntu, it would find the blank drive and format and install properly.
[/LIST]

I was concerned because I was not seeing my HD when looking in Nautilus.

 I used "System Monitor" to see how much space was used on the Ubuntu drive.   Looking under File Systems I did not see it.

You can see the attached file System_Monitor.png   

So I ran the command:   sudo fdisk -l

Here is the output:

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7329376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000  1611192319   781404160    7  HPFS/NTFS/exFAT
/dev/sda4      1611192366  3907024064  1147915849+   7  HPFS/NTFS/exFAT
Partition 4 does not start on physical sector boundary.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table



 I looked at nautilus and took a screen shot  [attached] Screenshot - nautilus - 10:13:23 AM.png  


So here are my questions:  


[LIST=1]
[*]Do I need to re-install using the ISO files burned to a dvd which I did yesterday?
[*]If so do I first need to create a valid partition table on the WD (sdb)
[*] If I need to do that, how do I do that?
[*] Can I create a a valid partition table, and then move the entire Ubuntu  installation over to the new drive "/dev/sdb" without having to  re-install?
[/LIST]

I did find : [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)  But I don't understand about partitions, mounting points etc. I'm not a technical person.  Any help you can give me will be greatly appreciated. 

Thanks!

---

### Post by marinara on 2012-09-07
Don't use wubi.

use the manual partitioner to install ubuntu to the second drive, you will need to create 2 partitions, one for / and 1 for swap.
you will be installing boot sector to the first hard drive

---

### Post by oldfred on 2012-09-07
wubi is a version of Ubuntu that runs inside a NTFS windows partition and uses Windows boot loader. It is intended for those who are not sure they will like Ubuntu and do not want to repartition. It can then easily be uninstalled and you have all your space back. It is not intended for long term installs, but as an extended test over using just the liveCD to test your system.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is not normally installed to a separate partition although I have seen a few do that. Most that have space for added partitions just do a fully partitioned install.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

There are now two partitioning schemes. MBR(msdos) and gpt(GUID). MBR is the standard that everyone knows and has been used since hard drives were added to PCs in the 1980s. MBR has a limit of 2.2TB so you can still use MBR on your 2TB drive. MBR also has a 4 primary partition limit, but Linux will work from logical partitions and with MBR one and only one of the 4 primary can become an extended partition which can hold many logical partitions. Since Ubuntu works in logicals, the primaries often are used by Windows and the logicals then by Ubuntu.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

I do not like huge system partitions or the partition Windows system files and programs are installed into and the same for Ubuntu. Better to separate systems from data.

For the Total space you want for Ubuntu - my standard suggestion:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3) format
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

In your case I might only use one or two primary at the beginning of the drive, say 100GB NTFS for shared data, 30GB for Ubuntu's / (root) or system partition. I would then make the entire rest of the drive as the extended partition but only use part now and then in the future when you have a better idea of what you may want you can change. The make logical partition of  a /home of 100GB and swap of 2GB or the size of RAM. That leaves most of drive as currently unused unless you have specific plans now for it.

---

### Post by LaughingHorse on 2012-09-07
Thanks oldfred & marinara,

oldfred, if my understanding is correct, I should download and install GParted and pre-partition the unformatted hd (sdb), then use Wubi to uninstall the Ubuntu installation, and re-install using the install disc (ISO) files i burned yesterday.

Is my understanding correct?

Will Ubuntu format sdb when I do the install?

Yeah, I know my questions sound dumb. Even to me. But the only dumb question is the unasked one.

Thanks!

---

### Post by marinara on 2012-09-07
no, delete the existing wubi ubuntu.  I donno how so i can't tell you.
then use the desktop cd to install to  the new drive

---

### Post by darkod on 2012-09-07
You don't use wubi to uninstall it. You boot windows, go into Control Panel - Programs and uninstall wubi (called ubuntu in there) like any other program.

After that boot with the cd and install like oldfred suggested. I suggest you create first the / partition at the start of the disk as he suggested, that's better on large disks like 2TB.

---

### Post by oldfred on 2012-09-07
Also on the install menu are several choices. With two drives do not use any of the automatic or side by side installs, but choose something else. That is the only way you get to choose where to install the grub2 boot loader. You want to leave the Windows drive totally as is. And have grub2's boot loader on the new drive which will probably be sdb. You then set BIOS to boot from sdb drive and grub will give you a menu to boot either system.

You do not have to download gparted separately. Sometimes I do just to have the very newest version (and another bootable liveCD/USB). 

Gparted is included in the Ubuntu liveCD and is all you really need to partition. You essentially get the same partition screens as part of the manual install, but that does not include the capability to create the NTFS partitions as Ubuntu will not install to NTFS. If partitions are created in advance, then from the Ubuntu install you select the partition, choose the format (ext4) and choose what to use it as like / (root) or /home. If swap was created in advance as swap it should automatically find it.

When you create partitions in advance you do have to keep track of which is which. I have created several new partitions and then installed to the wrong one. Fortunately it did not have any data. :)

---

### Post by LaughingHorse on 2012-09-07
Thank You Everyone for your help!

oldfred, I read the info at all the links and got extremely confused. (If I do X what are the ramifications) So here is what I did so far.

I opened GParted
I set a Table on /dev/sdb
I then started to partition the drive

(Primary) New Partition #1      NTFS 100 GiB
(Primary) New Partition #2      ext4 30 Gib (for Ubuntu Root)
(Extended) New Partition #3   Extended 1.69 TB
(Logical) New Partition #4       Linux Swap 16 Gib (My Computer has 16 GB RAM)
(Logical) New Partition #5       ext 4 (My Home)

Now I have a few questions. Please bear with me.

1. Does this look right?
2. Windows 7 is installed on sda, so how do I make a directory for GRUB?
3. Will the extended partition be used for file storage? I have a lot of data I am bringing over. Movies, music, heavy graphics. And I do't want to run out of space because i allocated too little to a partition. I also don't want to waste space b allocating more than I will ever need.

I do use Ubuntu Studio both graphic and recording (Audio).

4. I know from when I was going to install Ubuntu on my computer, I selected the installation where I could choose the drive. I selected sdb and then was told by the installation disc I did not have a root.

Do I select "Journal 4" as the choice while letting the system know New Partition #2 will be the Root?

Or do I use something different?

5. How will the installation know to put my own home packages into New Partition #5?

And finally, how do I install GRUB and where should it be installed?

Thank You Again for your help and patience.

I'm totally befuddled here.

---

### Post by oldfred on 2012-09-07
Grub2 it made up of many parts most are inside the / (root) partition. But when we say install grub we really just mean the install of the grub2 boot loader to the MBR. The MBR is the very first sector on every hard drive. Windows has its boot loader in the very first sector of the Windows drive and we do not want to over write that (relatively easy to repair but best not to have to fix.).

If you want to share most of your data with Windows only make /home partition in the extended partition 100GB also. Then you can use the rest of the drive for one or more NTFS partitions. If you want to eliminate the first NTFS 100GB partition and make the one's in the extended larger that is ok also. 

Under manual install or Something else you have to tell the installer which partition is which. So you select sda2 and choose / and ext4. Also sda6 (?) for /home and ext4. Also on that screen at the bottom is the combo box on which drive to install "grub" to or grub2's boot loader.

This shows creating the partitions as part of the install. If partitions already exist, just click on partition and then choose /, /home and swap. See screenshot with drive choice combo box at the bottom and be sure to choose your second drive.
Install to external drive 11.04. Also any second drive. (Installer still about the same.)
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

### Post by LaughingHorse on 2012-09-07
oldfred,

Thank you for your help so far (hint hint)  ;)

When I had it installed on my windows disc using Wubi Grub was working and my wireless connection was working.

With the new installation neither are working.

**When I rebooted, Grub did not show up.** The system immediately went into windows.

So what I did was hit the Delete key on a reboot to get me into the BIOS.
From there I checked the graphic boot sequence, and the WD drive I just installed 12.04 on did not appear.

However, thanks to the link in the previous article you gave me, I was able to check and do a manual boot sequence. From there I saw the Western Digital drive (at least I think it was), because it had the option to start Ubuntu 12,04 generic

So now I have to boot that way. Any ideas how to get Grub working properly? When I installed I did choose for it to be installed on the WD drive, the same one that Ubuntu is installed on.

**The Second problem is my wireless modem will not connect.**
I keep getting a message "Wireless Connection Disconnected"

Again, it was working when I had 12.04 installed on the same drive as windows using Wubi, so I know it is not a problem with the modem.

Any ideas?

Thank you in advance for your time. It is truly appreciated.

---

### Post by oldfred on 2012-09-07
I do not know about wireless modems. Did you have a Ehternet connection to download a new driver. The liveCD often does not have all the versions of wireless.

You can down load this into Ubuntu if you can boot it, download it into your liveCD or download it as a liveCD of its own. Then run the BootInfo report and post the link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by LaughingHorse on 2012-09-08
When I first ran the install modem, I was using my wireless connection.
After installing Ubuntu from the installation disc on the newly partitioned HD my wireless connection is lost.

This morning I tried using my install cd and booting from it.
This time there was no wireless as well. It just keeps giving me a message it is disconnecting me.

I'm wondering... Since I have no data on the installation, would it maybe be a good idea to just either reinstall over the installation, or use GParted to make a new table which will as I understand it remove everything on the drive.

Or is there a better way to remove the current install and start over fresh?

Thanks!

---

### Post by darkod on 2012-09-08
If it doesn't work in live mode, probably it won't work when installed too. You will probably just be wasting time and complicating things if you decide to do a fresh install.

What is this modem you are talking about? Usually the wi-fi is a built in wireless card. Are you using some kind of wi-fi usb adapter or usb 3g mobile modem?

Can't you connect the machine by cable so that you get internet going, and then install what ever you need to make your wi-fi work? Usually you would need internet to sort out the wi-fi drivers etc.

---

### Post by LaughingHorse on 2012-09-08
darkod,  

My WIFI card was working from the install cd. 

I don't know the model number, but it is an actual card in a slot, with it's own antenna.  Not that M$ software nonsense.

I don't want to start downloading all sorts of stuff to make it work, because it _was _working _no_ _problem_ using the install cd.  

Once I installed Ubuntu 12.04 on the new HD, my WIFI card stopped working.

I can go into windows and it works perfectly. 

This morning I tried using the install CD to test and see if the WIFI card would work from the install disc like it did before (when I installed 12.04 on the windows disc using Wubi, and then uninstalled it before installing 12.04 on my new hd [sdb].

Now it will not work. So putting together the Grub problem, the WIFI problem, anda new problem as I was updating with java (Oracle's version... you don't need to say anything :p ) Add to i, I have no data on my current install I have nothing to lose by wiping the disc clean and starting over.

It may end up solving all my problems. Worst case, I will be in the same place (minus the Oracle java problem)

In the mean time I am going to download "Boot Repair" as oldfred suggested, I will run it do the  'Create BootInfo' report  and post the link so we can all learn form this and help our knowledge.

This is the first time I have had problems like this. I've been running Ubuntu since 2008. I never learned all the commands and lower level stuff, just learned how to use the applications, and can do all sorts of wonderful stuff with them ;)

---

### Post by LaughingHorse on 2012-09-08
Boot Repair Link:
[http://paste.ubuntu.com/1192806/](http://paste.ubuntu.com/1192806/)

---

### Post by darkod on 2012-09-08
I'm no expert on wi-fi networking. Working once with the live cd and then not working again makes little sense since the cd is the same and nothing can be saved or modified on it since it's a CD-R.

Sometimes it has happened if the wi-fi has been disabled with the switch on the laptop or similar, that it doesn't come on as it should. But I forgot the commands how to check that.

You can always try reinstalling if you think it will help, I was just having in mind that you said you are not familiar with partitioning etc, the more times you reinstall, more chances things to go wrong and maybe even lose your windows if things get real messy.

Another question, the wi-fi doesn't even connect to the network, right? Or it connects but you have no internet?

If it connects but there is no internet it might be problem with the dns server it's using.

---

### Post by LaughingHorse on 2012-09-08
darkod,

"I'm no expert on wi-fi networking" Me neither.

"Working once with the live cd and then not working again makes little  sense since the cd is the same and nothing can be saved or modified on  it since it's a CD-R." 
That is what is driving me sane ;)

The WiFi will not connect now only with Ubuntu (it does not matter if it is from the install cd, or from the installed hdd [sdb] )

I will guess it connects for just a fraction of a second and then disconnects. As I keep getting the message "Disconnected from Internet" after I see it searching.

Any suggestions on what I should do to wipe the current install off so I can do it fresh?

If I use GParted to make a new table it gives me a message I will delete everything on the drive. No problem as that is what I want to do. But will it really delete or is there something else I need to do that will work more efficiently? Graphical works best for me.

---

### Post by oldfred on 2012-09-08
If you like the partitioning you have you can just reinstall. Part of the manual reinstall is to reformat. If you want to revise partitioning then use gparted & that will erase partitions.

With liveCD did you have Ethernet hard wire connected at some time? As it will also download added drivers.

Always best to have Ethernet connected for initial install. The install CD just does not have enough room for all the versions of wireless drivers, but does have most of the Ethernet wired drivers.

---

### Post by LaughingHorse on 2012-09-08
oldfred

Install: I used the WiFi connection for the install.
This time I will use the ethernet.
Hopefully that will make a difference.

Any idea why Grub disappeared on my first install??
When I did the install I told the installer to install it on sdb. I did not see a space to specify the directory, but I did make the Root partition and let the installer know where it was.

RE Partitions:

I just followed what was on the link you gave me regarding size and type. That link made everything very clear. But I saw he only had one primary drive of 258 mb for the boot. Maybe I'll make that a GB as I have so much space on the drive, or would that be wasting space?

I'm thinking I should add a partition for NTFS.

If I have 16 GB RAM should I make the swap 32 GB? Or should I make it more?

Also, if I make a separate partition for data, when I would save data, would it be as easy as it is without that separate partition? Or do I have to find it first?

In other words let's say the partition for my data is called "Stuff" and it is on "sdb 5"
When I am going to save a document, would I go to Stuff/filefolder/filename?

Or is it more complicated than that?

Thanks!

I really appreciate your and darkod's help. Without both of you, I would be even more bald than I am now.

---

### Post by oldfred on 2012-09-08
When you install grub2's boot loader, you just want to install to sdb not to any partition like sdb1. You then have to set BIOS to boot from sdb first.

Swap only needs to be the same size as RAM if you want to hibernate. Ubuntu boots fast enough for me that I never would hibernate. The old rule of 2X RAM was back when you had 256K or 512K  of RAM. Many of us suggest 2GB of swap just to have some. But with hard drives as large as they are you can have more. Swap is only used when you run out of space in RAM and I have 4GB and almost never use swap. If editing Videos then you may need lots of RAM and then swap also. With 16GB of RAM it will be difficult to load enough programs at once to fill RAM. (It will fill RAM anyway as it uses it as cache, but that is not the same as using all of it for active programs.)

With data partitions there are several ways to use them. With Nautilus and auto mounting it will be in /media/stuff with default ownership & permissions. But it is better to create a permanent mount point. After you get it installed we can walk thru that. A bit of editing of fstab, but it will help to have actual partition's UUIDs.

---

### Post by LaughingHorse on 2012-09-08
Thanks oldfred :KS,

I'm going in. Wish me luck everything works right this time.

I do some editing on some video's I post on YouTube, so I guess adding 32 gig for a swap file will be a good way to go.

---

### Post by LaughingHorse on 2012-09-08
oldfred,

I did the new install.
First I used GParted and wiped off the partitions.
Turned off the computer waited about 1/2 hr.
Then I made a tree, and then did a fresh install.

The system still is not finding Grub

So I downloaded Boot-Repair and ran a test.

Here are the results.
[http://paste.ubuntu.com/1193802/](http://paste.ubuntu.com/1193802/)

Also, when I used the Delete to disrupt the boot sequence and then went to F8 to select the drive to start, I selected the WD drive [sdb]

I started reading the top and noticed it is GNU Grub 1.99 I don't know why I ended up with that one. I was not able to get the entire info as it loaded the Ubuntu system.

Anyway, that is all the info I have at present.

oldfred,  I'm looking forward to your help in getting Grub working.

---

### Post by oldfred on 2012-09-08
If you are gettting the grub menu it is booting thru grub, but then has another issue.

What video card do you have? Did you choose to install with the proprietary drivers option?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by LaughingHorse on 2012-09-08
To make this so you know what I see happening...

When I turn on my computer, it does not go to Grub. It immediately boots to windows.

So when I turn on my computer, or restart my computer, I have to press Delete to get into the Bios (my computer is an ASUS Essention [desktop] CM6780.

When I get into the BIOS (I believe it is UEFI but am not 100% positive) my WD [sdb] is **not** showing.
So I press the [F8] key and my WD drive appears as a choice along with the other drive (Seagate loaded with windows), and the cd/dvd player.

So I click on the sdb drive and I get a Grub screen. However, the screen is not crisp. it looks more like a recovery low res screen.

At the top of the Grub menu it says: Grub Gnu Version 1.99-21 Ubuntu 3.1

I click on the Ubuntu menu item and Ubuntu 12.04 loads.

So I don't end up with a black screen, or blank screen. Either the computer boots up windows, or I have to go into the BIOS and manually find sdb and manually boot up from Grub.


I'm not sure about the video card I have.

What is the hardware command I can run to see all my components.

I seriously doubt it is the video card, as again Ubuntu including Grub worked perfectly when I installed using Wubi.

Wireless worked
Grub worked

And I now have another problem 
"waiting for apt-get to exit"

So now I can't even download packages or update my system. It is a known bug as i found out when I was doing research on it.

I tried using 
[http://ubuntuforums.org/showthread.php?t=1838092&highlight=waiting+for+apt-get+to+exit](http://ubuntuforums.org/showthread.php?t=1838092&highlight=waiting+for+apt-get+to+exit)

And got:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This may be a stupid question but...

If I once again wiped the hard drive, then did a Wubi install on the sdb, then after doing that install could I then do an install of the root from the install cd on sdb ?


**EDIT**

I fixed the problem of not being able to download packages and update my system. Seems there was a problem installing the Restricted Extras using terminal. It got stuck in the EULA for M$ fonts. And I did not realize I needed to tab though to reach the "OK". So I just closed the terminal getting the message from terminal that all processes woudl stop or end.  They didn't end. They kept trying to start up no matter how I tried.

SO I went back to terminal trying something, and tabbed through to the OK. SO that part now works.

---

### Post by darkod on 2012-09-09
Go into BIOS and set sdb to be first booting option before sda. That way the computer will boot from it automatically without going into bios on every boot. Your grub2 is there and that's the disk that needs to boot first. There must be an option in bios that says in what order are the HDDs booted. Just set sdb first and save the settings.

So, I think you said ubuntu can boot when you use sdb to boot. Does everything work now after you fixed the apt problem? Or not?

---

### Post by LaughingHorse on 2012-09-09
darkod,

I can use sdb to boot, but the Bios does not recognize sdb, only if I get into a separate part of the boot sequence, [F8]. But that part is not adjustable - meaning I can not set which drive to boot from if that makes sense.

Unfortunately I can not do a screen capture to give you a graphic.

But the problem is still there.

---

### Post by oldfred on 2012-09-09
Some BIOS have the choice of drive as a sub menu under the settings for devices like hard drive, CD/DVD, etc and others have it as a totally different menu entry sometimes on a different page.

---

### Post by darkod on 2012-09-09
Most recent BIOSes from the last 3-4 years have two different types of settings about the boot.

One is boot device, like CD-ROM, HDD, USN, etc.

Then another list is only the hdd boot order so that in knows which hdd is your first choice when you have more than one.

Which is your case exactly. You need to locate this.

Alternatively, if there is no such option in the BIOS, you need to decide whether you want to install grub2 on the MBR of sda, since you say you can boot only from sda.

Currently you have windows bootloader there which can't recognize linux so it's booting windows directly.

---

### Post by LaughingHorse on 2012-09-09
Ok,  here are some more details.

As I re-started my computer, I hit the Delete key to go into BIOS.

So far what I have seen is a graphical interface for the bios. It shows me what the BIOS (seems to) have found, and then I can use my mouse to move those in the sequence I want for booting.

Unfortunately, sdb does not show up on the graphical interface. (I did take some pictures and can post them if you think it will help to make ti clearer.

The only place I have seen SDB (listed as it's serial number (as the Seagate [SDA] is) is when I select the [F8] key to start up from BIOS.

I then went into the "Advanced" setting

In Advanced it shows:

Boot Option #1
SATA SM: ATAPI BD E DH12E

Boot Option #2
SATA PM: ST2000DL 003-9V166     (which is by SDA)

Interesting is when I plug in my WD external drive (I only use that for storage and back-up) That WD drive shows up in the graphical front of the BIOS, and it shows up in the Advanced.

I believe the Western Digital has NTFS format. *My SDB has no NTFS format partition. Could that be the reason it is not showing up?*

Further...
I clicked on Boot Option #1 and Boot Option #2  (in advanced) and my only choices were
SATA SM: ATAPI BD E DH12E
SATA PM: ST2000DL 003-9V166

I clicked on Hard Drive BBS Priorities

And then clicked on Boot Option #1 and it shows 
SATA SM: ATAPI BD
SATA PM: ST20...  (My SDA)
And interestingly it shows 
My SDB!
There is also a choice "Disabled"

I think we are making progress here. I don't know why the BIOS is not really "Officially" recognizing my SDB. I'm tempted to add a partition on my SDB and make it NTFS just to see.

EDIT

Looking at the link below I saw 
[COLOR=Red]Warning: extended partition does not start at a cylinder boundary. [/COLOR][COLOR=Red]DOS and Linux will interpret the contents differently.[/COLOR]

That was below
"blkid"And at the bottom of the report

"/boot detected. Please check the options. Partition outside the disk detected. 
=================== 

Final advice in case of recommended repair Please do not forget to make your BIOS boot on sdb (2000GB) disk!

 =================== 

Default settings Recommended-Repair This setting would reinstall the grub2 of sdb6 into the MBR of sdb, using the following options:        sdb1/boot, Additional repair would be performed: unhide-bootmenu-10s "

---

### Post by LaughingHorse on 2012-09-09
If I use GParted to create a partition you can see how my HD (SDB) is partitioned from the link 
[http://paste.ubuntu.com/1193802/](http://paste.ubuntu.com/1193802/)

So if I used GParted and added a Logical partition in the biggest partition which is now ext4 format, would that corrupt any data I have on that partition?

---

### Post by oldfred on 2012-09-09
Since you do not directly write to an extended partition, but only the the logical partitions inside the extended, then the warning on extended partitions does not matter. And it only matters on new 4K or SSD drives and is not really important on older drives.

I have seen the Partition outside of disk error, but it looks like an extraneous error. Not sure if from BootInfo, script or parted, but I think it is just a bug.

Some BIOS need a boot flag, but you have one. You should not need a NTFS partition. 

I think your BIOS is showing drive. But sometimes it is not intuitively obvious how the move the second entry to be the first in the drive order. Perhaps manual has info. Sometimes arrow keys, sometimes spacebar or tab move things around.

---

### Post by LaughingHorse on 2012-09-09
I may be able to move the SDB to the first drive,  I'm concerned I might end up bricking my new computer.

What really bothers me is it is not showing up in the BIOS graphical area, but my external WD drive does show up in the graphical area when it is plugged in.

---

### Post by oldfred on 2012-09-09
You should always be able to get to BIOS to change things back if that is a concern.

---

### Post by LaughingHorse on 2012-09-10
oldfred and darkod,

Thank You Very Much! If they had a smily that was bowing, I would put it in. Your help was just what I needed!

What was that saying "No guts no glory" 

Well, I went deep into the BIOS, because of you darkod. I started looking around, and saw where i might be able to change it. But I didn't want to brick my computer. I posted that and with oldfred's reassurance I would change it back if I failed and would not brick the computer... I tried it.

It worked!

For others who have the same problem Here are the steps i took:


[LIST=1]
[*]I went into the **BIOS **as my **computer **was **booting**.
[*]From there I went into the [B]"Advanced" setting.
[/B]
[*]From there I found a link called **"Hard Drive BBS Priorities" **and I clicked on it
[*]Once I was in **"Hard Drive BBS Priorities"** I  clicked on **Boot Option #1 **
[*]I **saw **my SDB drive (it is listed by the manufacturer and S/N so I **selected it**.
[/LIST]
I then **saved** my **new** **selections** and **re-booted**. Grub came up! \\:D/

---

### Post by oldfred on 2012-09-10
Glad you got it working and thanks for update on details how.

---

### Post by LaughingHorse on 2012-09-10
My pleasure!

Hopefully someone with the same problem will read this and be able to solve it. Or at least you can point them to this thread when you reply to their request for help.

I tried to lay out the steps I took to be very clear, so even a neophyte like myself can follow them ;)

---

