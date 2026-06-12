---
title: "Installing Ubuntu 17.10 on an external drive"
date: 2018-01-28
forum: Installation &amp; Upgrades
---

### Post by michael239 on 2018-01-28
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I would like to install Ubuntu 17.10 on an external USB drive, a brand new 1 Tb WD Elements. I tried to follow the &#8216;how to&#8217; advice one can find in this forum and even a YouTube video, but only got to &#8216;No root system is defined&#8217; in the &#8216;Something else&#8217; setup screen. I don&#8217;t want to do anything wrong, hence this thread.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]The WD Elements drive came pre-formatted in NTFS. I thought perhaps this caused the problem, so I created a 1 Gb partition and formatted it as ext4 and the rest of the disk a Fat32.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]When I run install / &#8216;Something else&#8217; again, the external drive identifies as /dev/sdf and I can choose /dev/sdf1 (that&#8217;s the one with the ext4 format) as &#8216;device for boot loader installation&#8217;. But I still get the &#8216;No root file system&#8217; error.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]How do I proceed now? What do I have to do in the &#8217;partitioning menu&#8217;?[/SIZE][/FONT][/COLOR]



[/LEFT]

---

### Post by Impavidus on 2018-01-28
You have to select the partition where you want to install Ubuntu, make sure it's ext4 (unless you want something different and know what you're doing) and set its mount point to /. That defines your root file system. And 1 GB isn't enough, make it somewhere between 15 and 30 GB if you have a separate partition for /home or data (recommended). Else just use the entire drive.

As for the device for boot loader installation: bios or uefi? I'm still on an older bios computer and in that case you'd install the boot loader to /dev/sdf, not /dev/sdf1. Someone else can tell you about uefi.

---

### Post by sudodus on 2018-01-28
I agree with the advice by Impavidus, particularly if the internal drive is soldered to the motherboard (and not possible to remove).

It will be easier to install Ubuntu into an external drive, if you can remove the internal drive.

The following link and links from it might help,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by oldfred on 2018-01-28
I now recommend gpt partitioning whether system is UEFI or BIOS.
And then later you can convert from UEFI to BIOS or vice versa.
The only reason to have MBR(msdos) is if you want  to boot Windows in BIOS mode and you cannot do that from an external drive anyway.

        Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt 



 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by michael239 on 2018-01-28
Hi and thanks for the quick replies.
It seems there is a lot to read and learn before I will get any further ... :cool:
Please bear with me ....

---

### Post by michael239 on 2018-01-29
I have tried to follow oldfred&#8217;s recommendations, but still getting nowhere. All Ubuntu gurus please bear in mind I&#8217;m just an humble user. So GPT, MBR, UEFI, :confused: don&#8217;t mean much to me.

 What I have done so far :
 - Deleted the FAT32 partition and made the whole drive GPT &#8211; EXT4
 - Tried to define the root file system both with Gparted and from within the install programme but without success. That doesn&#8217;t seem to be possible.

 However, I did notice something : When the disk is mounted, it indicates it&#8217;s mount point as */media/ubuntu/_*

 So I suppose the key-step would be to get this Mount Point right.

---

### Post by sudodus on 2018-01-29
Maybe you can try my link in post #3 with a more cook-book-like approach.

---

### Post by oldfred on 2018-01-29
You cannot define the / (root) partition with gparted. You can in gparted create an ext4 partition.
Then using Something Else change button on partitioning screen will be format, type like / (root), and format option. 
You then can add or set up other partitions on that screen.

---

### Post by michael239 on 2018-01-31
Hi guys,
Sending you this message from my iPad, as my desktop connection is temporarily out of order.
My internet provider is replacing the cable network in our neighbourhood. Work should be finished by tomorrow.

---

### Post by mastablasta on 2018-01-31
if you are still suck post the screenshot where you are stuck. you need to create ext4 partition with mountpoint "/"

---

### Post by michael239 on 2018-02-02
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]As I wrote in #6, I did try to define the root file system ( / ) but the installer just won&#8217;t allow it.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I tried everything oldfred suggested. No success.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]So here is a screenshot of what the installer shows after choosing &#8220;something else&#8221;[/SIZE][/FONT][/COLOR]
[/LEFT]
[IMG]file:///media/michel/USB%201/Install-01.png[/IMG]
                        [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]/dev/sda and it&#8217;s partitions where my actual operating system is located.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]/dev/sdf : the external drive I want to install 17.10 to. This drive has already 2 partitions, one of them /sdf2 where I want 17.10 to be installed. But as you can see, the installer doesn&#8217;t show these partitions.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]However, /sdf1 and /sdf2 do show up in the list &#8216;Device for boot loader installation&#8217;, alongside /sdf WD Elements (but I cannot take a screenshot from that list) and in the 'partitions line' on top.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Now, when I click on /dev/sdf (here highlighted orange), I cannot edit it. It wants to create a new partitions table. And when I try that, the highlight just jumps to /dev/sda.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Choosing /sdf2 as &#8216;Device for boot loader installation&#8217; doesn&#8217;t work either.[/SIZE][/FONT][/COLOR]
[/LEFT]

---

### Post by Impavidus on 2018-02-02
There's something present below /dev/sdf. I see a part of a checkbox. Have you difficulty scrolling down? The mouse wheel or selecting one of the partitions and pressing arrow down key a couple of times may work. Or maybe you can make the window a bit larger.

---

### Post by elton27 on 2018-02-02
I do not know why you can not. For me it has become just a new word of technology, after the built-in. I notice the difference, I have such a device Dell DW316[SIZE=1], [/SIZE]the specifications are here [https://www.bestadvisor.com/best-external-cddvd-drives](https://www.bestadvisor.com/best-external-cddvd-drives) If earlier I needed to do back up and after the upgrade was just a loss of the DVD driver, now when working with back up or image, the process has become stable and there are no bugs and failures when writing.

---

### Post by michael239 on 2018-02-02
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]You were right Impavidus, there is indeed something below /dev/sdf. Only, I didn’t spot it. I’m (still) not used to Ubuntu’s narrow right vertical scroll bar.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]/dev/sdf1 and /dev/sdf2 are there, but also 2 small ‘free spaces’ (how? I didn’t create them).[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]But clicking on sdf2 still not offered an option to set it as root. However, I accidentally clicked on a ‘free space’ and there it shows the option.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]What would be next? Delete the partitions, create a ‘large’ free space and use that as root?
[/SIZE][/FONT][/COLOR]
[/LEFT]

---

### Post by oldfred on 2018-02-02
You should be able to be on sdf2 and click the change button and get the same screens you show for formatting (again) and making it /.
Also if BIOS install be sure to choose sdf as location of  boot loader (grub).

While FAT32 is ok for smaller partitions, it is not recommended for large partitions. It cannot store files over 4GB and has no journal for recovery when corrupted.
If you want a format you can share with Windows use NTFS.

Did you change drive to gpt? If not you should be ok. If you did you need either bios_grub or ESP partitions.

---

### Post by michael239 on 2018-02-04
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]The never ending story? Thanks Oldfred, I finally got 17.10 installed on the external HD. So that should be it? Unfortunately : no.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Rebooted the computer and first changed boot order in bios to first USB, second CD ROM, third Hard Disk. Computer just ignores the external USB-FDD and continues to boot 16.04 on the computer&#8217;s Hard Disk.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I started experimenting a little before posting this reply, trying to find a solution, but all that follows gets the same result : no booting from the USB drive.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]- Erased /dev/sdf1 & 2 &#8211; reformatted entire USB-drive as ext4 root &#8211; installed 17.10[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]- Installed 17.10 on an USB flash drive[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I even disabled the CD ROM and Hard Disk boot options in BIOS, but the computer boots from the hard disk anyway.[/SIZE][/FONT][/COLOR]
[/LEFT]

---

### Post by oldfred on 2018-02-04
It must have been 10 years ago I did my first full build and wanted to boot flash drive. I tried every USB setting, it had many and expecting USB -HDD or other to work. I knew flash drive was good as it booted on another system.

But it turned out that it was another hard drive entry. My system has a tiny down arrow and opened up hard drive choices. That only happened when I had a flash drive plugged in. And flash drive had to be bootable, not a data drive or only internal hard drive was shown.

---

### Post by michael239 on 2018-02-05
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I did some more testing with BIOS , the external drive and the USB flash drive, but to no avail.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I was already planning to do as Oldfred, i.e. testing the USB flash and HD on one of a friend&#8217;s machines. If they boot there, at least I&#8217;ll know they are valid bootables.[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Then I&#8217;m going to contact my computer&#8217;s vendor. Perhaps they hold the solution. It&#8217;s a Shuttle AMD Glamor.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]This can take some time. Do we leave this thread open? Because the problem has not been solved, has it?[/SIZE][/FONT][/COLOR]
[/LEFT]

---

### Post by oldfred on 2018-02-05
Is this an older shuttle?
Or BIOS only?

How much RAM? If 2GB or less, one of the lightweight Ubuntu flavor may be better.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Also some had nVidia, so you may need nomodeset boot parameter once you get it to start booting.
       
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by michael239 on 2018-02-06
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Oh dear! Seems like I have a lot to check and read. Most of it all new stuff for me.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]The Shuttle would be some 5 years, so it will perhaps be considered relatively &#8216;old&#8217;. As it was build from a barebone I will have to find out what hardware and RAM the vendor did put in. I remember specifying I wanted lots of memory, so it will most probably exceed 2 GB. It has not have any memory issues.[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] 
 [/LEFT]

---

### Post by michael239 on 2018-02-12
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]No, I&#8217;m not dead (yet). Unfortunately things have gotten from bad to worse over the past 5 days.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]1) I went to my friend to test the USB Flash drive. It turned out that both of his machines, desktop and laptop, are &#8216;company&#8217; items and his employer&#8217;s IT team have their BIOS password protected. No way to change the boot order to USB first.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]2) To the shop where I bought the computer? Well, the building is still there. The shop isn&#8217;t.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]3) I set out to find my computer&#8217;s configuration. Found some &#8216;terminal commands&#8217; that reveal what Oldfred mentioned :[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]RAM = 4 GB[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Graphic card = Radeon 3000, therefore nomodeset not needed.[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]4) Then I thought of another way to test USB boot-ability. I used Start-up Disk Creator with a brand new 16 GB USB-drive. It just doesn&#8217;t want to boot.[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] 
 [/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Once more : back to square one.[/SIZE][/FONT][/COLOR][/LEFT]

---

