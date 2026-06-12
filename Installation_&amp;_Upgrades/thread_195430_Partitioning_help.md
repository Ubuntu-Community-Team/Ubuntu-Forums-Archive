---
title: "Partitioning help"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by hedonistic.heathen on 2006-06-12
I am trying to install dapper on my dell laptop so that I can dual boot XP - I have a 100GB hd and here is what the 'Prepare partitions' screen reads when I reach that point:

/dev/sda1   fat16   7/39MB --> i.e. 7MB used out of 39MB total
/dev/sda2   ntfs   32/87GB
unallocated               8MB
/dev/sda3   fat32    4/5GB
unallocated               8MB

I resize the windows partition to make room for the new ubuntu partition and I create a an ext3 partition for the ubuntu install, but when I try to create a swap partition I get an error that says I can't have more than 4 primary partitions...

I vaugely understand that a fat32 partition allows files to be shared between the  two OS's, I don't know what a fat16 filesystem type is, I don't have a clue why they're both on my HD, and I assume that my problem has something to do with those two partitions.

So, can anyone tell me what the best way to resolve this is?  BTW, I don't even know how to check what's on the fat16 and fat32 partitions, but I did install GIMP and the associated GTK environment (I don't really know what that is) and I have a feeling that maybe that has something to do with it...or I could be completely off base there.




Also, if anyone would care to elaborate on the best way to set up a partition to avoid future headaches...For instance I've read that the best thing to do is to shrink the windows partition down to its 'used' value, allow 6GB for the ubuntu install, and partition the rest as fat32 so that files can be shared between the two.  I also read that there are problems with fat32 and to just make a /home - shared ext3 partition in place of the fat32.  BTW, I don't really understand how to make a /home partition and a /root partition...should the /home - shared partition be an extended partition?  I'm pretty confused by that whole thing...

I would really like to make the transition to using Linux as my primary OS, and I realize that it will take some time to become familiar with the system, but for now I just want to get my laptop to the point where it can dual boot XP and dapper in a stable fashion and has an efficient and logically partitioned hard drive. 

Thanks in advance for any help.

---

### Post by kb3hkg on 2006-06-12
ok, one thing at a time:

1. Is this an internal hard drive? Usually it would come up as hda not sda

2. fat16 is an older version of fat from back in the days of DOS, it is mainly used now for hidden recovery partitions and usb thumb drives

3. for filesharing between the two fat32 works, if you want you can do the seperate ext3 /home partition but it is not necessary. It is easier to just make the one / partition for linux

4. for you to make room for ubuntu it looks like it would be easiest to shrink your ntfs partition with windows. If you are going to do this you will want to defragment that drive partition first or data will be lost. I recommend you still leave room in ntfs though for any possible expansion if you use windows further.

5. Yes, fat32 can sometimes have issues but for the most part it works fine especially for sharing files between the OS's

6. Multiple partitions either for /home or a fat32 area really all come down to what you feel comfortable with and what your preference is.

If you have further questions go right ahead and ask.

---

### Post by pyromithrandir on 2006-06-12
Wow, there are quite a lot of questions there, I'll try to get you started.
First off, you can't have more than 4 primary partitions. What you can do, though, is make one of your 4 primary partitions an extended partition, and then have logical partitions contained in the extended partition. :)

Fat32 is read/write natively under both windows and linux, so if you want to transfer files between, or be able to access files from, both OSs this is the easiest fs to use.
Fat16 is kinda like Fat32, but it's a little different. They're closely related, and both get called vfat by linux.

I see you have an NTFS parition. Linux and NTFS don't really get along well, just so you know. You can read it, but writing to it can get tricky.

---

### Post by brucenduane on 2006-06-13
Hello hedonistic.heathen,

A suggested partitioning scheme:
backup you information on the drive  especially the data on /dev/sda3.
use the dapper partitioner during installation.

delete the /sda3 partition.
resize the sda2 ntfs from 87Gb down to say 50Gb
you now have:
/dev/sda1  fat16  7/39MB
/dev/sda2  ntfs  32/~50GB

Add new Primary partition (sda3) and size ~1Gig   type linux swap.
Add next Extented partition (sda4) and size is the rest of the disk.
Add new Secondary partition (sda5) and size is ~6 GB type ext3 for Dapper  with mount point "/"  without quotes.  This is "root".
Add new Secondary partition (sda6) and size is rest of disk, type VFAT for Dapper home with mounting point "/home"  again without the quotes.  This is the home directory which you can exchange with Win$doze.  This will give you about 40 GB for you home directory.

The first partition is the windows D: drive for system recovery.
The second partition is the window C: drive.

Use "Grub" as your boot loader, which will be an option during the install.
Have the partitioner change the booting partition to sda5 where Dapper linux gets installed.  The grub menu will be in sda5  /boot/grub/menu.lst   Dapper will build a proper menu automatically to allow dual booting to windows.

Have fun and enjoy Linux!!!
-Bruce.

---

### Post by hedonistic.heathen on 2006-06-13
Thanks for the responses guys.

I'm not sure why the partitions are labeled as sda...It is an internal hard drive - a laptop though, not sure if that makes any difference...


Bruce, thanks especially, your reply makes great sense, helps out alot, and uses the partitioning scheme which I initially had in mind, but wasn't able to figure out the details of. One question though...

I have no idea how to back up the /dev/sda3 (fat32) partition...I don't even know how to view what resides on the partition.  Like I said above, I'm not even sure how the partition got there.  

I'm familiar with windows explorer, but as far as I can tell there's only the one C:\ drive...how do I find the data that resides on the fat32 partition so that I can back it up?


As far as everything else on the primary windows partition, I have the vast majority of my important files synchronized with my desktop PC, so that should be alright.  Oh, and I just defragged the hard drive before I started this whole process.

---

### Post by kb3hkg on 2006-06-13
That partition is probably a restore disk placed there by the computers manufacturer, they purposefully setup these partitions to not be visible in windows.

---

### Post by hedonistic.heathen on 2006-06-13
There are two partitions on my drive that I don't know the contents of though...the first is the smaller (<1GB) fat16 partition (which, if I understand Bruce's reply correctly, is likely the system restore partition) which I believe I should not delete...

If you are correct and the larger (~5GB) fat32 partition does contain system restore information and is hidden, then what are the consequences of deleting that partition?  Because, as I understand it, I have to delete either the fat16 or the fat32 partition...

---

### Post by kb3hkg on 2006-06-13
boot from a live cd and see what is contained in the fat32 partition, it may be obvious to you what it is then, if not then give us a general idea of what kinds of files are there.

---

### Post by hedonistic.heathen on 2006-06-13
I don't know my way around in ubuntu or linux at all for that matter, especially from the command line, so I'm not really sure how to 'look' at those partitions.  It's something I want to learn, but I don't have huge blocks of time to devote to doing so.  Getting my laptop to the point where it will dual boot a linux OS with XP will give me more opportunities to work through some of the tutorials with a functional linux OS at my hands.  That being said...


I see the three partitions in the 'disk manager' but no information is available (partition 2 is listed as Win NTFS and partitions 1 and 3 are listed as Win Virtual FAT - thought they were fat16 and fat32 though? - probably over my head at this point...).

Looking in 'Computer - File Browser' I see five icons listed:  CD/DVD Drive, 87.1 GB Volume:/tmp/disks-conf-sda2, Dell Restore, DellUtility, and Filesystem.  I can't access (ERR - Unable to mount the selected volume) the sda2, Dell Restore, or Dell Utility icons.



I'm assuming that /dev/sda1 (fat16) partition is represented by the Dell Restore icon and the /dev/sda3 (fat32) icon is represented by the Dell Utility icon - it may be vice versa though, I'm not sure how to tell.  Assuming that /dev/sda3 contains some type of Dell Utility files, I'm still unsure of what the consequences of deleting those would be (and why they would need to be placed in their own fat32 partition anyhow).  I uninstalled nearly all of the junk software that was included when I bought the laptop, but was always unsure if it was smart to delete all of the Dell related software, so I left most of it.

My wireless card is built in and is controlled by a Dell program I believe, and for all I know those files may be located in the fat32 partition, so I am hesitant to write the files on the fat32 partition off as useless and I still don't have a clue as to how to approach backing the fat32 partition up.  - (as a note, I am unable to connect to the internet wirelessly using the ubuntu live CD)


Thanks again for helping out.

---

### Post by kb3hkg on 2006-06-13
Ok, well unknowingly you just gave me lots of useful information so here goes...

Those drives are only useful if you plan to restore your laptop to how it was when you got it, or send it back to dell to have them do it, if you don't plan on doing either you are good to go and delete them. I have a dell as well and have done this. You should be able to see their contents in linux but it isn't necessary.

The VFat that you saw as partition type is just how linux handles both fat16 and fat32 drives, linux doesn't differentiate.

As for the wireless card. You have a Dell you have a Broadcom card, these are a pain to get working in linux just search the forum for it and you'll understand what I mean, I personally got a dlink pcmcia card and it has worked great, broadcom wasn't worth the effort.

If it will make you feel better you can try mounting the fat drives and backing them up onto cd's but the utilities should have come on a cd from dell as well and the restore I consider mostly useless.

---

### Post by kb3hkg on 2006-06-13
If you need a quick tutorial on mounting drives I can give that to you as well, and possibly what programs to use to backup the data on them too.

---

### Post by hedonistic.heathen on 2006-06-14
I didn't think things through when I ordered the laptop and I chose the default option to recieve no backup CDs.  So I probably need to keep the restore partition (which is probably the smaller fat16 partition, right?) incase I need to wipe the windows drive and reinstall XP.

I'd like to think it was alright to just delete the fat32 partiton (probably the dellutil stuff) without fussing with mounting it and backing up the data...I've never used and will never use any of the Dell 'help' related software that was put on there and I'm thinking that I'd be alright to just delete it and that XP will still function normally without it...I'd just really like to avoid messing up XP since I blundered and didn't get it on CD (trying to restore it from the dell restore utiity would probably turn into another headache)...

Since you have a Dell yourself, if you can say with some amount of confidence that its probably alright to delete the DellUtil partition then that's what I'll do...If you have hesitations then yes, I'd appreciate it if you could give me a quick rundown of how to mount and back up that partition (I wasn't aware that I could do that off of a live CD though)


Another thought I have is how can I be sure that the fat32 partition is actually the Dell Utility stuff and not the restore stuff?  

And as far as the broadcom thing goes, I don't like to hear that, but I guess I'll start dealing with that when I get dapper fully installed as a functioning internet connection is one of the first things I'd like to get working.

---

### Post by kb3hkg on 2006-06-14
You had mentioned the drives being labeled with DellRestore and DellUtil, that is the easiest way to tell which is which, but I am almost definite the fat32 would be the Util section. I have no worries about deleting that, I however had the cd's including one for XP. It is up to yo how safe you feel deleting those paritions without other cd's. Any Dell software or drivers you can download from their site though so I doubt the Util deletion will matter, the Rstore is up to you.

Sorry about the Broadcom, oddly enough Dell atleast used to allow you to choose RedHat as your OS, but if you ask them for linux drivers Dell claims they don't exist. Don't know how that is supposed to work.

As far as mounting and backing up the data on these drives goes, I have never done it with ubuntu live cd but I have with other live distro's. It works by you opening a cd burner application first, it is then loaded into the virtual filesystem used by the live cd in memory. at this point you can remove the live cd and insert a disk to b burned. For the fat32 partition you will either need quite a few cd's or 1 or 2 dvd's if you can burn them.

to mount these drives you will first need to make folders for them, so do the following commands from a terminal:

sudo mkdir /media/restore
sudo mkdir /media/util

then to mount the drives do the following commands:

sudo mount /dev/sda1 /media/restore -t vfat -o iocharset=utf8,umask=000
sudo mount /dev/sda3 /media/util -t vfat -o iocharset=utf8,umask=000

from there just open up the cd burner program and go for it. I believe the live cd comes with Gnome Baker for this. if not it is possible to run synaptic and tempoararily install it to the virtual filesystem.

---

### Post by rcarring on 2006-06-14
I would be extremely loathe to delete any of the partitions if you don't have back nup cds. Dell are notorious for not helping users who trash or reinstall their system and then need things like dvd decoders for xp to play cds.

Try vmplayer and create your vm using the tools on [http://www.easyvmx.com](http://www.easyvmx.com)

It's not an elegant solution but the safest.

----

Should you have already started backing up and deleting drives then hope it goes okay.

---

### Post by kb3hkg on 2006-06-14
You might be best off if you just leave them because that is true about Dell. Is it really necessary for you to get rid of them or can you just use the space freed by shrinking ntfs, and just have slightly smaller partitions then you had wanted?

---

### Post by rcarring on 2006-06-14
That was the same idea I had originally, except I don't know if the installer is sophisticated enough to do the following tasks:

a) identify current partition schema
b) allow resize of ntfs from 87GB to 50GB
c) create new extended partition in freespace
d) create ext3 format / partition say 36GB
e) create ext5 format swap partition say 1GB
f) correctly identify all partitions
g) correctly write menu.lst so that each are bootable -- this is probably the deal breaker as I bet the hidden dell partition will not boot after grub is installed.
h) allow booting to xp

Now, if XP becomes unbootable then he is in a hard place.

Dell will give him restore cds but they will charge him a fortune, especially for XP

---

### Post by kb3hkg on 2006-06-14
I believe it should still work as long as there aren't an attempted more then 4 bootable partitions

---

### Post by rcarring on 2006-06-14
I have posted a link to a page that may help the user create a backup and reinstall cd for XP.

Here is the link: [http://www.nu2.nu/bootcd/wxp/](http://www.nu2.nu/bootcd/wxp/)

---

### Post by hedonistic.heathen on 2006-06-14
I'm slightly confused now...

Currently I have the three partitions.  During the partitioning portion of the Dapper installation I am able to shrink the windows (ntfs) partition down and I am then able to create (or rather preview what it would look like in the installation interface) a new ext3 partition in the unused space, but when I try to add the swap partition I get an error - I assume this is because all three partitions currently on my computer including the fat16 and fat32 partitions are listed as bootable, hence the new ext3 partition makes the fourth bootable partition and the install process will not allow me to add another partition since there are already four...

I don't have a problem keeping the fat16 and fat32 partitions so long as I am able to get dapper and a boot loader functioning correctly...


So, rcarring, you say:

a) identify current partition schema [COLOR="Lime"]--> does this[/COLOR]
b) allow resize of ntfs from 87GB to 50GB [COLOR="Lime"]--> does this[/COLOR]
c) create new extended partition in freespace [COLOR="Lime"]--> does this[/COLOR]
d) create ext3 format / partition say 36GB [COLOR="Red"]--> here I begin to get lost[/COLOR]
e) create ext5 format swap partition say 1GB
f) correctly identify all partitions
g) correctly write menu.lst so that each are bootable -- this is probably the deal breaker as I bet the hidden dell partition will not boot after grub is installed.
h) allow booting to xp


So, should steps (d) and (e) be carried out as secondary partitions (I'm not sure that's the correct term, but I don't have the installer in front of me at the moment) nested within the primary ext3 partition?

If need be I can see about following some of your recommendations for accessing and backing up the fat32 partition and acquiring an XP backup when I get home later today, but I feel like maybe I'm missing a simple concept here, like I said, I don't mind keeping all of the current partitions, shrinking the windows partition, and adding the necessary partitions/sub partitions for dapper and the boot loader  - It's just that the installer won't let me do that (maybe I'm doing something incorrectly or maybe the two dell partitions are at fault).

---

