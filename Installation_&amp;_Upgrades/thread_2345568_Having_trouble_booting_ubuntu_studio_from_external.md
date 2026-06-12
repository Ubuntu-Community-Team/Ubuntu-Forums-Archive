---
title: "Having trouble booting ubuntu studio from external hhd."
date: 2016-12-05
forum: Installation &amp; Upgrades
---

### Post by mcmiste2 on 2016-12-05
I'm having trouble booting ubuntu from an external hhd. First off I guess specs. Computer is lenovo t530 thinkpad. External hhd is seagate expansion desk (3tb). In the t530 there are 2 drives. 1 500gb hhd and 1 16gb ssd. Windows 7 installed on 500gb drive. Lenovo recovery stuff is on the ssd. 

Here's what I've done: created Bootable usb memory stick. I can boot the live usb/cd from that and mess with ubuntu live. I've then ran the installer from the desk top of ubuntu live. Created 2 partitions on ext. Drive. Both ext4. Mounted and formatted one (roughly 11gb) for the Linux install and one roughly 9gb ( for swap. And changed it to swap). Now here I've tried 2 things. First I tried to install bootloader on the partition that I installed linux on. Later to find out that's not correct. So then I just installed bootloader on the actual device. Gparted lists drives and partitions as follows : sda (windows drive) sdb (external drive with partitions sdb, sdb1,sdb2,sdb3.) And sdc (ssd). So I installed bootloader on sdb. Everything seems to install fine. When I go into bios I can see the ext drive in boot priority and can change priority. But when ext drive is first it just boots to black screen with a blinking cursor. Windows still boots fine if it's first. And the memory's tick boots fine if it's first. Guess I'll stop there and hope for some advice. Thanks.

---

### Post by karl96 on 2016-12-05
Can you switch to TTY4 from the blinking cursor with Ctrl + Alt + F4? (try press a few times, or change the f key). It should drop you into a shell if i'm right.

---

### Post by mcmiste2 on 2016-12-05
First thanks for the response. I will try that asap 8n a few hours after work. 5hrs probably.

---

### Post by yancek on 2016-12-05
It would be useful if you indicated which version of windows you have installed.  Windows 8 and newer use UEFI and the methods for booting are different and the possible solutions will of course be different.

---

### Post by mcmiste2 on 2016-12-05
Ok. So I just tried cntrl+alt+f1thru f12. Nothing happens. Also I did indicate what windows. It's 7. I'd also like to note the laptop has both usb 2.0and usb 3.0. And it's plugged into a docking station that has usb 2.0's. I've tried connecting the ext via all those and get the same no boot situation.

---

### Post by mcmiste2 on 2016-12-06
Update on what I've done. I have another pc that I tried to install via. This pc has one 500gb hhd inside with windows 7 on it and another external drive (1tb) with other data on it that I need to keep. 

So I booted ubuntu live via my live-usb stick. Created 2 partitions on external drive via gparted. One 10gb for ubuntu and one 8gb for swap. Set the 10gb partition to / . Set 8gb to swap. Choose "something else" and formatted 10gb to ext4. Also swap is ext4. Oh I forgot to mention on this install and the previous one on the other pc/external hhd I choose to not install updates or the extra media/mp3 stuff. It just takes a long time atm. Also made sure bootloader was installed on device (not partition) of external drive. Interestingly this install went through about 2x as fast as the other. Probably cause there is no Internet turned on atm. So everything looks like it installed fine.

Restarted and set ext drive to boot first, internal drive 2nd and usb-stick third. Still won't boot from ext drive. What is wierd though is when booting it hangs on blinking cursor for a couple minutes and completely skips windows boot and goes straight to usb-stick. At a loss here.

---

### Post by mcmiste2 on 2016-12-07
Another update : I got ahold of another hhd. It's a 320gb sat connected drive. Installed it in the "other" pc(not the lenovo). Disconnected original hhd that has windows 7 installed and disconnected external hhd. Went through ubuntu installation. Everything good there. Ubuntu successfully boots from this drive. Although I still have no wifi on this machine. Just not being detected at the moment ( obviously this is another separate issue. I'll work on this later). So there is some reason when ever I install ubuntu to external USB hhd's it won't boot. Any suggestions appreciated.

---

### Post by oldfred on 2016-12-07
With gpt which is required for any drive over 2TiB, you have to have either the ESP - efi system partition for UEFI boot or the bios_grub partition for BIOS boot.

Even before I go my first UEFI system, I converted to using gpt on all new or totally reformatted drives. and in 2012 when Windows converted to UEFI and all new systems were UEFI, I started adding the ESP as first partition and then a bios_grub to boot my current BIOS based systems.

For grub to install correctly to the protective MBR on your gpt drive, you need to add a bios_grub partition. It must be unformatted and only needs to be 1 or 2MB. With gparted you use the bios_grub flag. If using gdisk it is code ef02. I might suggest adding an ESP if you think drive may be later used with a newer UEFI system. But ESP should be first or nearer beginning of drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by mcmiste2 on 2016-12-08
> **oldfred said:**
> With gpt which is required for any drive over 2TiB, you have to have either the ESP - efi system partition for UEFI boot or the bios_grub partition for BIOS boot.

Even before I go my first UEFI system, I converted to using gpt on all new or totally reformatted drives. and in 2012 when Windows converted to UEFI and all new systems were UEFI, I started adding the ESP as first partition and then a bios_grub to boot my current BIOS based systems.

For grub to install correctly to the protective MBR on your gpt drive, you need to add a bios_grub partition. It must be unformatted and only needs to be 1 or 2MB. With gparted you use the bios_grub flag. If using gdisk it is code ef02. I might suggest adding an ESP if you think drive may be later used with a newer UEFI system. But ESP should be first or nearer beginning of drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

Thanks for all that info. I did some searching to find out what partition schemes my external and internal drives were. Looks like the external is gpt and the internal is mbr. I followed your steps on creating /boot_grub, /home, swap and ubuntu(where the os is) partitions and I wasn't paying attention to where I installed the bootloader. Later, as it was installing on the ext hhd I realized I put the bootloader on the drive with windows. I was freaking out through the whole install. Didn't want to wreck the windows installation. But after it was done installing I rebooted and it still won't boot from the ext drive but..... I get a grub menu now if I boot from the windows drive. And it boots ubuntu! And windows too!

---

### Post by oldfred on 2016-12-08
If grub2's boot loader is in MBR of internal drive, then you can only boot internal drive with external connected.
Best to install grub to external and install a Windows boot loader to internal.

Best to have Windows repair disk. You can only make minor repairs to Windows from Linux.  But one of the repairs is to install a Windows type (not official one) Windows boot loader. You can use Boot-repair's advanced mode and choose operating system and drive to install boot loader into.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But grub remembers the specific drive you installed boot loader. And on major update will reinstall to that drive. You want to change that setting to external drive.
       
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Be sure to fix install of grub to external and make sure that boots before installing Windows boot loader to sda.

---

### Post by mcmiste2 on 2016-12-09
[COLOR=#000000]"If grub2's boot loader is in MBR of internal drive, then you can only boot internal drive with external connected.[/COLOR]
[COLOR=#000000]Best to install grub to external and install a Windows boot loader to internal."
Ya I was suspicious of that possibly happening. 

Im going to attempt to reinstall grub2 on the external drive but before I do I want to make sure I have everything in boot-repair set up correctly.

First off boot-repair and the "disks" application in ubuntu list my drives as sda(external where ubuntu is installed) and sdb(internal where windows is installed) and sdc(ssd with lenovo recovery stuff on it).
I want to install grub on sda, correct? also would you recommend checking "place grub in all disks (except usb disks without os)? on this screen [/COLOR][IMG]http://pix.toile-libre.org/upload/original/1335263804.png[/IMG] or just "place grub into: ( and select sda)?[COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2016-12-09
You do not want grub in all disks. I do not like that option in Boot-Repair and it seems to be one of Boot-Repairs standard settings. That puts grub everywhere. If you have multiple drives, often best to have different boot loaders in each drive. But some do not know which drive in BIOS is set as default so copying grub everywhere probably makes it work for more.

You want the Windows boot loader in the Windows drive.
You want to check/tick the external drive for Ubuntu and then it knows to install grub to external drive.

If you can boot into Ubuntu.
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

