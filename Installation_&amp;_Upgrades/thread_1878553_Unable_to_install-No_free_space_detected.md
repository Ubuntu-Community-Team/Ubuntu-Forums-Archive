---
title: "Unable to install-No free space detected?"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by oooryan on 2011-11-10
Alright so I decided to install Ubuntu after discovering its amazingness recently.  Seeing what it can do I was super excited that it was free!  But I am having trouble installing it...I know there is something I have to do but I don't know what...

So pretty much I'm using an old system from like 4-5 years ago. I breathed new life into it with a new motherboard and small SSD harddrive (60gb).  It still runs a single core processor but it still runs windows 7 64 bit very well. eI downloaded the Ubuntu iso and made a boot disk DVD..restarted and loaded the Ubuntu installation.  When I get to the second step, I has an X beside at least 4.5 GB free.  Before this I shrank the partition Windows 7 was in from using the whole drive (except the 100 mb for the backup partition) to having 18 GB of unallocated space.  So I was confused by it wasn't recognizing it.  I did the "test Ubuntu out" and the gparted tool recognized two things.  A drive I suspect is the windows backup and OS partitions combined and unallocated space.  Both have readings that are not correct at all (the unallocated reads at like 1.3 Gib and the other drive reads at around 2.3 Gib.  The one drive also has an error icon and when i click on it it shows all these errors. I downloaded Parted magic and made a boot dvd (took forever to install) and it didn't recognize and drives at all after a long scan...When I go into windows it shows the drives exactly how they are....whats going on??  I'm hoping it doesn't have anything to do with the SSD because SSD+Ubuntu would just be the ultimate media center...any information you need I will gladly provide it for anyone who can help me out.  I really would like to experience this operating system :D

---

### Post by darkod on 2011-11-10
Boot the ubuntu cd into live mode (Try Ubuntu option), open terminal and post the result of:

sudo fdisk -l (small L)

That will show your disk partitions.

Another question, have you ever used this disk in raid?

---

### Post by oooryan on 2011-11-10
hey alright I'll do that when I get home later... I'm just at work now...and the raid thing... No in guessing not because it's a new drive and is connected to the Sata ports in the motherboard

---

### Post by Mark Phelps on 2011-11-10
If Win7 still runs OK, then when you start it next, go into the Disk Management utility, look at the "drives" (what Windows calls partitions) and confirm that they are NOT Dynamic Disks.

Win7 will work fine with these, but I believe that the Linux utilities will not, including the Installer.

---

### Post by oooryan on 2011-11-10
Okay Im going to try that when i get home in like 30 min...ill also post that partition thing....if this doesn't work out I think i might just wipe the drive and start from the beginning (ssd's install FAST)  but I would install Ubuntu first just so there is no issue...would i be able to install windows 7 second?

---

### Post by oooryan on 2011-11-10
Thanks so much for the help guys, I love the community here...its super helpful...especially for beginners like me :D

---

### Post by darkod on 2011-11-10
> **oooryan said:**
> Okay Im going to try that when i get home in like 30 min...ill also post that partition thing....if this doesn't work out I think i might just wipe the drive and start from the beginning (ssd's install FAST)  but I would install Ubuntu first just so there is no issue...would i be able to install windows 7 second?

Yes, you can install win7 second. But there are few things to consider. In that case I would:

1. First boot with the ubuntu cd in live mode (Try Ubuntu), open Gparted and create one primary ntfs partition at the beginning of the disk, with the size you want to allocate to win7.
2. Then reboot again with the ubuntu cd and start the install. You can use either one of the auto guided methods or do your own manual partitioning (which I always prefer).
3. After a while when you are ready to install win7, note that it will delete the grub2 bootloader and win7 will bot directly without offering option to boot ubuntu (windows can't see linux OSs). But don't panic, and there is no need to reinstall ubuntu again.
4. Just boot with the ubuntu cd again in live mode, open terminal and execute:

sudo mount /dev/sda? /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That will reinstall grub2 to the MBR of the disk. In the first command /dev/sda? is your ubuntu root partition, depends whether it will be /dev/sda5, /dev/sda2, etc, depending how you do the install.

5. Once ubuntu is booted up, it still doesn't know about win7, to discover it run in terminal:

sudo update-grub

And that should be it.

---

### Post by oooryan on 2011-11-10
Sweet, thanks a lot for your help!!! :D  That was exactly what I needed to know if i decide to start over anew....wow im learning so much about computers just from installing ubuntu

---

### Post by oooryan on 2011-11-10
Alright...so when I got home, I couldn't even load ubuntu from the dvd anymore..so i just rebooted and loaded parted magic from a usb and did a internal secure erase...my drive is clear and all that boots when i reboot is the pcie gigabit ethernet card thats in it (could that affect anything?)...so i boot ubuntu from a usb and go into the "try it on this computer" again and run gparted.  it takes a long time to scan the first thing...nothing...then another long scan in the next thing is nothing...then it scans the usb and displays it..when i try ti install it still doesn;t allow me and has an x beside at least 4.5 GB of space....I really don't know what to do, I don't want to install windows....

---

### Post by oooryan on 2011-11-10
okayy WHAT? I am so confused.....i explored my motherboard and saw that the smart monitoring was disabled i don;t know if that did anything, I also took out the pcie card....so i go into ubunu live and attempt and install..MAGICALLY it showed that I had space...i was excited...so i exited the installer and proceeded to the gparted tool to partition the drive for a future windows install like darkod instructed...when i open the tool, it shows the USB drive only...so i went okay whatever ill just install it and worry about windows later...but now all of a sudden it says it shows that i don;t have at least 4.5 GB of memory in the installer..what did i do? what happened? I feel like there was a glimmer of light!

---

### Post by oooryan on 2011-11-10
okay so i went into the disk utility in ubuntu and it sees the SSD...it shows unknown for the volumes and when I try to format it i get this

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sda, scheme=0
ped_device_get() failed

---

### Post by oooryan on 2011-11-10
oh yah here is the fdisk report

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          48     7831551     3915752    b  W95 FAT32


it doesn;t look like it detects the ssd...do i have to mount it manually?

---

### Post by oooryan on 2011-11-10
maybe this can help too...i looked at the sata ports on my mother board (there are four)  and each one has its own name..they are Sata 1 (0.0) Sata 2 (0.1) Sata 3 (1.0) and Sata 4 (1.1)...if the identifying number for these four different ports is at the end of /dev/sda(insert number here)...is there a conflict between the first and second ports because of the same first number?  I'm not computer expert, im just trying to give the best description of whats going on here...

---

### Post by oooryan on 2011-11-11
okay i somehow got past the second step...random it detected free space when i rebooted and i clicked continue...There are no devices listed and i cant click on new partition table or add...pretty much anything except quit back and install now...the device for boot loader is incorrect and displays the usb...which i obviously don't want to install too and doesn;t show anything else..aahh this is frustrating...why did it allow me to to get to the install point randomly(well not randomly, i just didn't open gparted as soon as ubuntu loaded and that somehow had this same result when i tested it twice)...did it think i was going to install it on the usb? cause there isn't even enough space on it...

please anyone??

---

### Post by oooryan on 2011-11-11
This might help as well...when i load ubuntu live i get all these errors at first but it still loads

---

### Post by oooryan on 2011-11-11
BUMP!

Okay this is just getting worse and worse...I can't even format my ssd anymore in parted magic...im going to try again but i have been trying to install this for the last three days going into super late into the night and no success...before i was unable to format...i was able to load ubuntu 10.04 and my ssd was located in gparted...so i made a new partition for windows and exited..then went into install ubuntu...everything was going will...i was able to set my name and locaion and stuff and when i got to the manual partition I created a primary ext4 / partition and a logical swap partition...then went to the next step...it started installing for a while then when it got to copying files it stalled on 32 percent....then after about 10 minutes an error came up saying it was unable to copy files...disk read only....


btw in parted magic i have to disconnect then connect the power to the ssd so that it can read it (maybe bios does something to it?) could that be of some importance in this overall ubuntu not installing problem??

---

### Post by oooryan on 2011-11-11
AHHHHH now ubuntu wont even loaddddddd from live usb....it has all these time out: killing 's/sbin/modprobe -bv pci....time out: killing 's/sbin/modprobe -bv usb...over and over again omg this is a nightmare...it stoppped after a few minutes and now it has the what looks like a cheap version of the splash screen ive seen in the last few days...it shows Ubuntu 11.10 in a different font and my keyboard isn't working so i can't even press down to check the background....

why is know one responding! does no one even know wtf is going on with my computer???

---

### Post by oooryan on 2011-11-11
Unbelievable!!!

Throughout all these errors and multiple drive erases...and being scared to death my ssd was toast...windows 7 is still able to be installed...it reads the drive and shows the right space....but its late now and i have to be up early again...i really hope this can be fixed because i would really like to use ubuntu....is there a place I can call for support or is it pretty much the community helping the community kind of deal...

---

### Post by darkod on 2011-11-11
You SSD seems not to be detected properly. I usually start using the sata ports from the first (or marked 0 sometimes), to the last. It doesn't really make a difference.
What does make a difference, is the settings in BIOS. Go into the BIOS and make sure there is no RAID enabled, the SATA mode should usually be AHCI.
Note that if it's IDE and you change it to AHCI with win7 already installed, it will stop booting. It's better to use it in AHCI (and faster) but win7 doesn't boot if you switch it and it's already installed.

fdisk command should ALWAYS see the disk, no mount is needed for that.

So your first task is to make the disk "visible", I guess the install will go smooth after that.

---

### Post by oooryan on 2011-11-11
When I go into bios there is no achi option ... Just IDE and raid and it's been in IDE this whole time...now I am having triuble just doing a live boot from USB... Could it be the us ? Cause it worked before... But when I formatted it I did a quick format in fat32 Would that be a problem?

---

### Post by oooryan on 2011-11-11
okay im trying to run ubuntu live 10.10 with usb and its not going smooth....when its starts the usb boot....it takes way longer than it did before to load ubuntu (it was less that 30 seconds to load from usb)...and now it takes  alot longer and shows all these errors that didn;t happen when i first started booting with the usb...now its at the splash screen with Ubuntu 10.10 in a really cheap looking font....when i was first started trying the installs the splash screen showed ubuntu in a nicer graphic and didn't have the version number beside it (that was 11.10)...but if you read above...after the usb errprs starting..when i booted 11.10 from usb the splash screen was that cheap looking one....is it booting in some kind of safe mode or something?  I'm going to wait to see if ubuntu loads and if not im going to try partition magic again via usb..and if that doesnt work then with the live cd....and if that doesn't work i have no idea how to partition


my abosolute last resort is to just install windows 7 again since it has no problem at all...i just don't want to have to do that...but i might try and install ubuntu 10.10 through windows (wubi) because there was an error with i installed 11.10 through windows which started this whole chain of steps to try and install ubuntu externally....

---

### Post by darkod on 2011-11-11
The usb stick loading longer should not have anything to do with the SSD. You can do the following test: turn off the computer and disconnect the sata power cable from the SSD. Try to boot with the usb to see how it goes, faster or not.

If your board has no AHCI option that will make the SSD run slower. But it should still work in IDE mode. The same applies for mechanical HDDs too, AHCI mode is faster.

Something looks really strange, maybe a hardware issue. Has this SSD been used in raid earlier? Usually raid data is left on the disk which windows doesn't mind but ubuntu does. To prevent overwriting a working raid array ubuntu will usually not install on a disk with raid meta data.

You can try deleting meta data from a terminal in live mode with:

sudo dmraid -E -r /dev/sda (if your SSD is /dev/sda)

Do NOT use this if you are running raid, but you didn't mention it so far. This might be a reason the installer not seeing the disk properly.

Otherwise, opening Gparted in live mode should always be able to format the disk deleting all the data (good and bad) on it.

---

### Post by oooryan on 2011-11-11
OH I forgot to mention one thing...the SSD is refurbished so maybe it had some raid data on it if it was used with raid before...but I formatted it in parted magic...would it still be there? and i will try and format it in a terminal is i can get live mode running somehow...thanks a lot for you help!!! :)...i didn't even know my board wasn't capable of AHCI...so theres no way to get it on my board (its a hardware thing?) cause faster would always be better and if ahci is better that ide i want ahci lol

why isn't ubuntu able to work with raid? or it can but you have to do a lot of manual stuff?this really does seem like the only logical reason why ive been having problems...but the usb thing is hanging in the back of my mind...ahhh i hope this works!!

---

### Post by oooryan on 2011-11-11
also i dont know if this might be a problem either but for the display i am not commecting to the vga port on the motherboard...its a ati graphics card in a pcie slot with hdmi...could that have any impact?

---

### Post by oooryan on 2011-11-12
okay new update...so weird thing is i think it is the ssd...because i can boot parted magic with no problem and super fast with it is disconnected..and when i connect it ni partedmagic..it doesn't see it in in the erase disk program...how can i format it otherwise?

---

### Post by oooryan on 2011-11-12
Alright I found the solution...and the problem...but basically its the SSD...so i loaded and regular hdd and it works fine...its installing now and im excited to finally use it....a little bummed that I can;t use the SSD...but I will return it and get a brand new one and try once more...it wont be the same brand..im think of the intel ssd 40gb...if anyone knows any expereince with that ssd let me no...if not I can probably get a new corsair f60 because the ssd has a manufacturers warranty

---

### Post by darkod on 2011-11-12
Well, it seems you located your problem. Just to answer your previous question, the raid meta data doesn't get deleted with formatting (usually). That's why running the dmraid command can get rid of it.
Ubuntu installer ignores disks that have raid meta data I think to protect you from installing on the wrong disk, over you raid array. Imagine if by mistake you destroy your data.

---

