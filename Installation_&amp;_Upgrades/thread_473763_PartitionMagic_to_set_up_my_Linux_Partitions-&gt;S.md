---
title: "PartitionMagic to set up my Linux Partitions-&gt;Something went horribly wrong"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Tr0janV0dka on 2007-06-14
Ok, so I got PartitionMagic 8 and to cut a long story short, I can no longer get into Windows. That's the first part of my problem, which is fixable via Linux. Now, my second problem with Kubuntu 7.04 is that I can't get access to my NTFS partitions while running a Live CD (access to the Windows partition will allow me to fix PartitionMagic's "issues"), but I can't resize my partitions while using a Live CD, it just doesn't let me! I've already tried logging on as root (doesn't work anyway, tells me I can't log on as root!) and various other power users, giving the ubuntu account total system/root access, mounting the ntfs partitions so that even the lowest account can use them and I still can't get any flipping access to the ntfs partitions!!!

I've tried pretty much everything I can think of/find. If worst comes to worst, Windows is gonna get the drop kick (along with fracking Norton PartitionMagic, I don't think I'll ever touch that thing again) and get a re-install. Luckily all my games/goodies are on the 2nd NTFS partition (after the 1st, which is Windows), so there's a small loss.

Also, hello everybody! I gave up with Ubuntu after 3 hours trying to fix the bloody partitions at a LAN Party (kept on re-assigning themselves LOL), but I've come back bloodied and ready for a fight!

---

### Post by Herman on 2007-06-14
> I can no longer get into Windows. That's the first part of my problem, which is fixable via Linux.Hello Tr0janV0dka,
What do you mean exactly when you say 'can't "get into" Windows? Do you mean Windows doesn't boot anymore? Or you can't access the partition? (Like, mount it read/write?).
If you just mean you can't boot Windows anymore, then I am just guessing maybe you are implying that Partition Magic has suddenly changed your partition numbers. 
I am just guessing since you didn't provide much real information.
If that is the case, then you would need to be able to edit boot.ini with the correct (current) partition numbers in order to boot Windows. Unfortunately the catch22 is you would normally need to boot Windows to edit boot.ini, but you can't boot Windows so you can't edit boot.ini.
If you had Windows with the FAT32 file system, boot.ini is a hidden, 'system', read-only file, but if you relaxed the security attributes for the boot.ini file before hand from within Windows like it explains in this page, [WinGrub Page]("http://users.bigpond.net.au/hermanzone/p9.html"), you would be able to access and edit it from your Ubuntu Live CD.
The best way to boot Windows in those circumstances if that's your problem is to use a Super NTLDR Disk. Download the .iso file from this page "[http://tinyempire.com/notes/ntldr]("http://tinyempire.com/notes/ntldrismissing.htm") by Miles Comer ",  and find the CD file and download it, (it is only a very small download), make a CD from it.  Read that web page to learn how to use it (it's easy). That should help you boot Windows if that's what you want.

> Now, my second problem with Kubuntu 7.04 is that I can't get access to my NTFS partitions while running a Live CD (access to the Windows partition will allow me to fix PartitionMagic's "issues"), but I can't resize my partitions while using a Live CD, it just doesn't let me! I've already tried logging on as root (doesn't work anyway, tells me I can't log on as root!) and various other power users, giving the ubuntu account total system/root access, mounting the ntfs partitions so that even the lowest account can use them and I still can't get any flipping access to the ntfs partitions!!!You should be able to use Gnome partition editror in the Ubuntu Live CD by going 'System'--'Admistration'-->'Gnome Partition Editor', and you should be abel to reszie any partition with that, although I can't imagine how that will possibly solve your partition numbering problem, if I'm guessing right about what your problem really is.
Maybe you really mean you want to write to your boot.ini file. Normally Ubuntu does not try to write to any NTFS file system, however Ubuntu is quite capable of doing so these days. Here's ubuntugeek's how to for that, this is for a hard disk installed Ubuntu operating system, **[Windows [B]NTFS** Partitions **Read**/**write** support made easy in Ubuntu **...**]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")[/B]
I have tried that out and it works perfectly for me. I don't use NTFS for anything, I don't like NTFS, but I had to use it for testing how to recover someone's system with TestDisk one time.
If you really want to be able to mount an NTFS file system read/write from a Ubuntu LiveCD, you can make a USB persistent /home for your Ubuntu Live CD by following the advice in the following .pdf file (download), [SIZE=-2]**[PDF]**[/SIZE] **[Untitled]("http://www.oreilly.com/catalog/ubuntuhks/chapter/hack03.pdf"), **and then after that follow ubuntugeeks, great tutoral on mounting NTFS partitions read/write that I just gave you trhe link for above and it should work for the LiveCD. I haven't tested that myself yet but I think it should work.
boot.ini is a hidden, 'system', read-only file, but if you relaxed the security attributes for the boot.ini file before hand from within Windows like it explains in this page, [WinGrub Page]("http://users.bigpond.net.au/hermanzone/p9.html"), you would be able to access and edit it from your Ubuntu Live CD then.

Finally, you should use only 'Parted based partitioners to do any disk partitioning work. If you want to have the best and the most user freindly disk partitioning software in the world, download [GParted -- LiveCD]("http://gparted.sourceforge.net/") and burn that to disk and boot it. You'll be glad you did.
Regards, Herman :D

---

### Post by Cam1223 on 2007-06-14
had the same problem when i tried to resize my ntfs partition in partition magic what a POS!!! whats weird is that when i try to boot windows it starts loading, hits a blue screen and restarts. i cant see the partition on ubuntu even tho its in fstab but i can see it on an old knoppix 3.3 live cd. but i dont get LAN connection on the 3.3 to back up my stuff as im gona reinstall everything anyway. i tried to remount in ubuntu but it says i have to unmount and mount again which i dont kno how to do.

---

### Post by Herman on 2007-06-14
Hello Cam1223, :D
> had the same problem when i tried to resize my ntfs partition in partition magic what a POS!!! whats weird is that when i try to boot windows it starts loading, hits a blue screen and restarts. What error messages do you see?

If the file system is still okay and your partition table is still okay you should be able to boot with either an NTLDR CD as linked to in my earlier post in this thread or make yourself a Microsoft Windows Xp boot floppy disk, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/"). The floppy disk has its own boot.ini and there are no file permisson prblems with it in the floppy disk. Since the floppy disk is FAT32, it's easy to mount it and edit the boot.ini in the floppy disk from Ubuntu or the Ubuntu Live CD. [                          Mount a floppy disk]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_floppy_disk")

I don't know anything about Partition Magic, only what I have read about it in the following links, 
[PartitionMagic - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&ct=res&cd=5&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FPartitionMagic&ei=dcVxRpWrN5aQigG6vZ3lCA&usg=AFQjCNF4rR7AQclky9YfuBhMU1HUTc9hDQ&sig2=zMnWw2FFc6R1fFrfIERxvA")

[Partitioning Tools ( And which ones not to use )]("http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html") 

[FONT=Arial][SIZE=2][Partition    Magic may write "28 96 C4 17" to an HDD's 1st Track]("http://www.geocities.com/thestarman3/asm/mbr/2896C417.htm")[/SIZE][/FONT] 
 I am under the impression that another one of the problems with it is that it tries to renumber people's hard disks into numerical sequence for some reason. I suspect that might be what's causing the issues in this thread.
Often when we see the feedback from fdisk -l we see the message " Partition table entries are not in disk order" Hard disks don't need to be in disk order for Linux, and renumbering  them to force them to be in disk order could be the problem. Partition numbers 1 to 4 can be allocated to Primary partitions or a Logical partition, and they can be in any order in the partition table. Any of these can be an 'extended' partition, which can contain 'logical partitions'. Logical partition numbers always begin numbering from 5 and count upwards from there. So you could have partition 1, partition 2, then partition 3 could be the extended. There might typically be no partition4, as that number is skipped if you don't make all four primary partitions. Then your logical partitions could start counting from 5 upwards. There is no need for partitions to be listed in disk order for Linux. I understand Partition Magic is a great partitioning tool for Windows users though, or so I read. Many people love it and have used it for partitioning for Linux without any problems too. I don't know why though when good Linux partitions are provided  for free that are compatible with Linux.

>   i cant see the partition on ubuntu even tho its in fstab but i can see it on an old knoppix 3.3 live cd. but i dont get LAN connection on the 3.3 to back up my stuff as im gona reinstall everything anyway. i tried to remount in ubuntu but it says i have to unmount and mount again which i dont kno how to do.What output do you get after you enter 'sudo fdisk -lu' in a terminal? :D ```
sudo fdisk -lu
```Have you tried mounting your Windows XP filesystem and you can't mount it? Or can you mount it but you don't see any files? Here is a link to my how-to on mounting, [            Mounting Windows FAT32 or NTFS filesystems]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop")

I can help you with a file rescue too if you need to do that. :D 
You can do it with your Ubuntu Live CD or Knoppix. 
Since you mentioned Knoppix, here are my breif notes on LAN file rescue with Knoppix,
1. Insert Knoppix CD and restart computer, follow prompts to start Knoppix
2. Click the penguin icon, lower left corner of monitor 
  (a) Network/Internet,   card configuration
  (b) Choose DHCP
3. Find the right icon on the desktop for the partition required (hoover 
   them with mouse pointer to find the right one).
4. Right-Click it and click 'mount'
5. Click on it to open it and navigate to your files to be rescued.
6. Click the 'house' icon to open another file browser window.
   (a) type in the location for the other computer on your LAN
   (b) click the 'GO' button over to the right of the location bar
7. The home directory or shared file in the other computer should appear.
8. Move (drag 'n drop) all your files to be rescued
9. Click the 'K' button and log out, shut down.

Let me know if you would like more exact help. I can give more specific help if you post your output from 'sudo fdisk -lu' here.

Regards, Herman :)

---

### Post by Cam1223 on 2007-06-14
> What error messages do you see?
it flashes by too fast. right after the WinXP with the scrolling bar it flashes blue with like 2 lines maybe but i cant read it and it restarts

> I don't know why though when good Linux partitions are provided for free that are compatible with Linux.
yea i know qtparted and such are great but they whouldent resize the ntfs partition, which is a good thing considering what happend..

that specific knoppix dosent detect my ethernet card, im in it now (on the other computer) backing up some files, when its done i'll see about that sudo fdisk -lu hopefully i can get it to mount cuz this is gona take forever with a 20gb usb drive

---

### Post by Cam1223 on 2007-06-14
oh and the reason i havent made a boot disk for XP is that i have one of thoes HDTVs that dont display CLI or BIOS screens which is really a pain when something goes wrong.

---

### Post by Herman on 2007-06-14
> yea i know qtparted and such are great but they whouldent resize the ntfs partition, which is a good thing considering what happend.. QTParted is a good 'Parted based partitioner, but it didn't have much development for a while, so it seems a little behind, but should be improving now,  _[FONT=Arial][SIZE=2][QtParted - Wikipedia, the free encyclopedia]("http://www.google.com.au/url?sa=t&ct=res&cd=4&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FQtParted&ei=XNpxRubzMIS4iwGvqanlCA&usg=AFQjCNHWU7uIonypXNdWwpGW46h41UrAGA&sig2=BO-Hj31e-CETzglAs09_lw")[/SIZE][/FONT]_[FONT=Arial][SIZE=2]   |   [/SIZE][/FONT][U][FONT=Arial][QtParted homepage]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fqtparted.sourceforge.net%2F&ei=XNpxRubzMIS4iwGvqanlCA&usg=AFQjCNFKzC_wNGo4cRCUUi1PxkRSSpxV8Q&sig2=YBFfUe-jYx8Scxvl8_ekEw")

[/FONT][/U][FONT=Arial]I used to use QTParted sometimes too, until I heard about [/FONT][GParted -- LiveCD]("http://gparted.sourceforge.net/"). GParted LiveCD can do about everything I can imagine or would want. It can safely do everything with NTFS partitions. [Features]("http://gparted.sourceforge.net/features.php")
GParted LicveCD is free and it's only a small download. 

The Ubuntu installer uses a special version of GParted called Gnome Partition Editor, which can also safely resize any NTFS partition. That's already included for free as part of the Ubuntu Live CD's Graphical installer. :D

The 'Alternate' CD's installer, 'Partman', has also been able to safely resize NTFS partitions for ages now, ever since Ubuntu 'Breezy' I believe. I have not heard of anyone having any problems with it for years now. :D

If any of those do refuse to touch any partition, it is probably because they have detected a problem with it that was left there by someother partitioner you may have used before, (a boobytrap in your partition table), and if they touch anything it might be dangerous, so sometimes they do bale up. Most of the time though, any of the 'Parted based partitioners to do all you need, and very reliably too I might add :D. 
There are no partitioning software makers who don't recommend the user make a backup first before using their program though. ;)

Regards, Herman :D

---

### Post by Herman on 2007-06-14
> oh and the reason i havent made a boot disk for XP is that i have one of thoes HDTVs that dont display CLI or BIOS screens which is really a pain when something goes wrong. That could be a problem, hmmm ... :confused:


---

### Post by Herman on 2007-06-14
Maybe tell me more about that and how you manage? 
Do you mean you can't see anything until the GUI (Xserver) Starts?
How did you install Ubuntu then? And do you not even see the Grub Menu?

---

### Post by Cam1223 on 2007-06-14
well i see the Board screen when the computer starts then it goes blank until it says ubuntu with the loading thing or windows with the loading thing. nope cant see the GRUB i jus know ubuntu is first and XP is at the bottom. so the only thing i see is ubuntu loading screen and the xserver. i had to transfer the tower to my other computer and connect it to a regular CRT when i installed it. basicly if its not 640 800 or 1024 at 60Hz i wont see it. I remember i installed ubuntu but when i went to boot it the xserver whouldent start so i had to connect the CRT to fix the xorg.conf cuz i couldent see the CLI. Iv got a card with svideo out which is the only way i have to see everything but it looks like crap and its an MX4000 PCI. my integrated card is better LOL i need a new card with component connections

---

### Post by Cam1223 on 2007-06-14
heres the output of sudo fdisk -lu

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 10.0 GB, 10005037568 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541089 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    18603269     9301603+  83  Linux
/dev/hdb2        18603270    19535039      465885    f  W95 Ext'd (LBA)
/dev/hdb5        18603333    19535039      465853+  82  Linux swap / Solaris

```

---

### Post by Cam1223 on 2007-06-15
intresting i jus followed ur page
> [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
and when i try to add the partion again heres what happens
```
cam@IceWolf:~$ sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
idk but that dosent sound good.....
its supposed to be mounted in ubuntu as u can see in the post before this but i dont see the files. how is knoppix mounting it that i can see all the files automaticly?

---

### Post by Tr0janV0dka on 2007-06-15
Ok, sorry about my poor description about the situation.

As I said before, I used (tried and failed) to resize my 2nd partition to make room for some Linux action. This didn't work and I faced a screen similar to CHKDSK. It says press any key to continues (doesn't work) and it pretty much sits there until you reboot it. Anywhos, I found a disc lying around that had a bootable partition magic 8 on it (Bart FTW!) and I managed to resize my 2nd partition in this boot utility to make room for Linux. I installed Linux and did a bit more research on this Partition Magic 8. It's using a file called xmnt2002.exe found in the system32 folder. Now what I could do is change the name of the file/move it somewhere and see if that fixes it, but I've stumbled upon a dozen problems with doing this. I hunt down a thingo/app for Linux that allows writing to an NTFS partition (can't rename anything within NTFS right now - says it can't delete files), but the bloody thing won't compile! I've installed Fuse along with god knows how many other tiny applications and it still wont install/compile. I'm pretty p***ed right now, because I've been trying to fix it for almost 8 hours now.

I'll read up more on your first post. ;)

---

### Post by Herman on 2007-06-15
Cam 1223,
Okay, thanks, at least I can tell by that that your partition table looks okay, at least as far as fdisk is telling us. :D

That is interesting that that mount command didn't work because I can't see anything wrong with that command. It should work. 
As far as I can see it's the same command everyone else uses. 

Knoppix does mount disk partitions automatically, it is designed to do that. I would imagine it just automatically runs a scritp or two to do that. You can make your own script in Ubuntu to do that too, here, [Making a script for mounting your other filesystems instantly]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script"), maybe Knoppix uses a script like that and it runs on bootup or something. Ubuntu could easily do that too but I guess the developers don't think it's important for what Ubuntu is mainly meant to be used for. :D Anyway, it isn't very much work to make our own and just run it whenever we want to.

---

### Post by Cam1223 on 2007-06-15
its mounted i jus cant see the files

```
cam@IceWolf:~$ blkid/dev/hda1: TYPE="ntfs" 
/dev/hdb1: UUID="d775cb41-de3b-4297-9d90-3e48cbc06335" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="5541a25d-2bd8-49ce-93e1-31237dc4104d" TYPE="swap" 

```

whats UUID for? n how come the ntfs dosent have it, maybe thats the problem?

---

### Post by Herman on 2007-06-15
> whats UUID for? n how come the ntfs dosent have it, maybe thats the problem? That's part of the information usually written at the head of the file system to identify your exact file system. So maybe Partition Magic has corrupted your NTFS a little bit? It's probably worth investigating more...
Or maybe just run a copy of [GParted -- LiveCD]("http://gparted.sourceforge.net/") and right-click on the partition and click 'check' and see if that helps. No guarantees that'll work, especailly when some other program has already been used on it, but it might be worth a try. :D

---

### Post by Cam1223 on 2007-06-15
i have Gparted on ubuntu, but it dosent have the ability to check NTFS. is the live cd diffrent?? and does tha live cd have some GUI that i could see on my screen? or else im going to have to leave it till tommorow

yea tomorrow sounds good :)
lol damm that partion magic, too much magic not enough partioning!!! j/k its great on windows not so much for linux i guess

---

### Post by Herman on 2007-06-15
Yes, GParted in it's own Live CD is different, and yes, it does have a nice GUI that you should be able to see on your screen. 
The Ubuntu version of GParted is called 'Gnome Partition Editor', and it's great for installing Ubuntu with and a few other partitioning jobs, however, it's based on an older version of GParted.
[GParted -- LiveCD]("http://gparted.sourceforge.net/") is far more advanced and can do lots more things including file system checking and resizing Linux partitions from the start point of the partition too, which is important if you like Ubuntu and you want to increase the amount of disk space for Ubuntu. I imagine it's a lot of work to integrate a newer version of GParted into the installer though. Other linux distros still use the older version too. You need the GParted LiveCD to have the latest version.
Regards, Herman :D

---

### Post by Herman on 2007-06-15
Hello Tr0janV0dka,
Let me know how you get along. The information I posted earlier should help you mount your Windows partition and write to it. I don't really understand how it might help to change the name of a file Partition Magic is using in Windows though. 

 What I thought you would want to do is edit boot.ini in Windows to adjust for the new partition number, (if I'm guessing right and that's what your problem is).
The easiest way to do that would be to go to this page, [http://tinyempire.com/notes/ntldr]("http://tinyempire.com/notes/ntldrismissing.htm") by Miles Comer and read 'How to fix: NTLDR is missing, press any key to restart', and download yourself a copy of Miles Comer's Super                                                 **NTLDR Disk, **burn one of those to a CD, or make a floppy disk out of it. Read that web page by Miles Comer, that should help you boot Windows sooner or later if you keep trying.

Good luck and kepp me informaed of your progres, even if you decide to do it your own way, that's okay. :D

Regards, Herman

---

### Post by Tr0janV0dka on 2007-06-15
Well... I didn't follow any of your advice so far, not that I have anything against you very helpful people, but I've been trying my own methods.

I tried to make a MS-DOS boot disk, but it was a very old floppy and it didn't work, BUT it made my computer boot into Windows when I faced the stupid message I was getting (the message I couldn't get past).

The 1st problem I encountered was no internet (Xfire worked like a charm, so did receiving emails, IE refused to work at all!) and the 2nd was mysterious HDD usage. The 3rd was Windows automatically checking consistency of the disk (CHKDSK) every time I boot up.

I solved all 3 problems at once. I ran cmd.exe, typed in **chkdsk /f** which made the computer boot up and do a hard drive scan. The scan finished, computer rebooted and it wanted to do another scan. The 2nd scan finished and I finally got into Windows on the 3rd boot. IE was working properly, the strange HDD usage was gone and after searching a bit for a way to disable automatic CHKDSK, I found the fix.

Run CMD.exe, type in **chkntfs /x C:**
Note: Where C: is, you can also add other drives via spaces if I'm not wrong. This command excludes the drives listed from being automatically scanned.

Edit: IE is still slow at loading pages (yes, I have been capped down to 64K, but on Linux, page loading was much faster than it currently is). I'll probably back up all my goodies and reformat soon. Windows gets broken far too easily. If I never investigated Linux, I would have a formated C: drive right now with a fresh install of Windows XP on it!

---

### Post by Herman on 2007-06-15
Okay, good. It sounds like you're doing fine without much help! :D
You'll find that once you install Ubuntu, you won't have much more trouble in Windwos anymore if you use Ubuntu for all your internet purposes or as much as you can.
I used to spend a lot of my computer time running scans for this and that and the other thing in Windows, and monitoring intrusion attempts at my firewall and worrying, worrying, worrying. 
With Ubuntu, you'll find all your anti adware scans in Windows will come up empty all of a sudden if you don't use Windows on the internet except maybe for updates and trusted sites. Actually, it will soon seem like a waste of time even bothering to run them. :D
After a while, you'll probably only need Windows for a few programs, (like games maybe), and then maybe you'll be like many of us here, you won't need it for anything much at all. :D

---

### Post by Cam1223 on 2007-06-15
Well Herman I downloaded Gparted and booted it up and it refuses to boot after seeing like 10 errors like WDCxxxxxx could not initilize (my hdd) and bad superblock, read write error. and more bad sounding errors. everytime i boot it, it goes a little furthur in the configuration and then stops. Im just going to copy my stuff in knoppix and reformatt everything. oh by the way i tried with Knoppix 4.0 and it said the same thing as ubuntu when i tried to mount the drive.  Knoppix 3.3 must be a little diffrent

---

### Post by Cam1223 on 2007-06-15
i figured out how to get ubuntu to see the bad ntfs partition. i had to run ```
ntfsfix /dev/hda1 
```
and then i could mount it by force with 
```
 mount -t ntfs-3g /dev/hda1 /media/Cizzle -o force
```

hopefully i can copy this now and reinstall everything...

---

