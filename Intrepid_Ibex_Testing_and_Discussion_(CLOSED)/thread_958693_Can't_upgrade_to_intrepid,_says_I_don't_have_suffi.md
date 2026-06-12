---
title: "Can't upgrade to intrepid, says I don't have sufficient space"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2008-10-25
Hi,

I have just tried to upgrade to the Intrepid RC after running the "command update-manager -d" and I go all the way to the step of setting new software channels when the upgrade process stops and a box comes up saying: 

"Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 138M free space on disk '/boot'. Please free at least an additional 134M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I tried "sudo apt-get clean" and tried deleting some files in /boot that I think were old kernels.  I went through the upgrade process again and it stopped in the same place as before.  Could you guide me as to what I should do to fix this and get through the entire upgrade process?

As an aside, I have at least 50 GB of free space, so I don't know why it would state that I don't have enough free disk space.

---

### Post by kansasnoob on 2008-10-25
Try running:

```
sudo apt-get -f install
```

and see if it gives you an auto-remove output.

It would be interesting to see a screen shot from gparted.

---

### Post by bcasanov on 2008-10-25
It did give me an auto-remove output and I took care of that.  I don't know about gparted.  I looked for gparted in Synaptic and I did not get any results.  How would I get gparted?

---

### Post by caro on 2008-10-25
I had the same issue.  Do you see a lot of old versions of the linux kernel if you look in /boot?  That was my problem.  If you do, go to Synaptic, search for linux-image-2.6 and remove all the linux-image.2.6*generic EXCEPT for the latest one (the one you are using).  This will free up a lot of space.

You can also go to Applications > System Tools > System Cleaner and remove the old kernel packages.

---

### Post by bcasanov on 2008-10-25
I tried what you suggested above, but I still came up short.  The update manager now says that I need to free an additional 8244 kb of space.  I looked up gparted and installed it, and here I have posted a screenshot of it, as requested by kansasnoob

---

### Post by bcasanov on 2008-10-25
I was having trouble upgrading to Ubuntu Intrepid, as detailed in this thread, [http://ubuntuforums.org/showthread.php?t=958693](http://ubuntuforums.org/showthread.php?t=958693) and I resized my /boot partition through a live CD, after removing what I believe were old kernel files that went like: initrd.img-2.6.24-19-generic and initrd.img-2.6.24-19-generic.bak.  I left only the kernel version 2.6.24-21.  After resizing the /boot partition to over 2 GB, and taking all the unallocated space away, I decided to boot up to my computer, and I found out that I could not.  The screen only showed the text Grub and that's it.  I don't really know what I did that could have caused it.  Perhaps I deleted the wrong kernel?  I would like your help to get my computer to be able to boot again.  

As a side note, I am on the live CD right now and do have all my files alright in / on the main partition.

---

### Post by bcasanov on 2008-10-25
When I went into the /boot folder of the / partition, I found that it was empty!  And the /boot partition had all the files in it.  Is this supposed to happen?  Is this why I can't boot to my desktop?  I tried copying the files in /boot partition to the /boot in the / partition, but I was told that I don't have the permission to do so.  How can I get the necessary permission?

---

### Post by bcasanov on 2008-10-25
Please, I need urgent help with this.

---

### Post by caro on 2008-10-25
did you download 8.10?  if so, the kernel for intrepid is 2.6.26-7.  here is the output of "ls /boot" from my laptop:

abi-2.6.27-7-generic         
memtest86+.bin
config-2.6.27-7-generic      
System.map-2.6.27-7-generic
grub                         
vmcoreinfo-2.6.27-7-generic
initrd.img-2.6.27-7-generic  
vmlinuz-2.6.27-7-generic
lost+found


did you use synaptic to delete your old files?  i wouldn't try to delete kernel files from the cli.  synaptic will remove the dependent packages too.  

i've never tried resizing my partition so if that is the problem i won't be much help.  

you do have the live CD, so you could backup all your data and do a fresh install.

---

### Post by bcasanov on 2008-10-25
Actually, I did not get to upgrade to Intrepid, so I cannot have Intrepid's kernel version.

---

### Post by caro on 2008-10-25
when you boot up do you have the option to go to the grub menu?  if so, can you select a version of the kernel to boot with?  or can you repair packages?

---

### Post by kansasnoob on 2008-10-26
Sorry to just disappear!

You have a separate boot partition and it's nearly used up. Each time there's a kernel update Grub updates as well so it's just used up.

It's actually rather odd to see a separate boot partition, but that's OK. It may be that way for a good reason - some are described here:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

Since you have 2 GB of free space just ahead of that partition (sda3) the first thing I would try is booting any Ubuntu Live CD and using Gparted (Partition Editor) to expand that partition (sda3) to the left.

The way "cylinders" are rounded Gparted may or may not allow you to use the entire 2 GB, but you're currently only at 196 MB, 500 MB to 1 GB would be enough to live with for quite a while!

So, the next thing is ........ have you ever used Gparted to do any partitioning?

As I said it MUST be done with a live CD!

If you're unsure please ask for more help.

---

### Post by forumache on 2008-10-26
Please give us the output of the following commands:

df -h /boot

(this will show the free disk space in the partition where /boot is, displayed in a "human" form)

ls -lh /boot
(this will list files in /boot with some details)

---

### Post by bcasanov on 2008-10-26
No, I don't really know how to go to the Grub menu.  All I am shown is a message that says something like this:

Booting from hard disk...
GRUB 

Next to GRUB is a flashing cursor, and that's about it.  It does not display any list or options.

---

### Post by bcasanov on 2008-10-26
What key combination is available to access a Grub menu?

---

### Post by caljohnsmith on 2008-10-26
If you do:
```
gksudo nautilus
```
That will run the file browser as root user so that you can copy your entire /boot folder over to your new partition. Then you'll need to reinstall Grub to the MBR (Master Boot Record) and point Grub to the new boot partition for its boot files. So once you've copied over the /boot folder, how about posting:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by bcasanov on 2008-10-26
Thank you for your quick reply!  

Actually, I found that the /boot folder in the main / partition was empty, but that the /boot partition had the files.  I copied and pasted the files in the /boot partition over to the /boot folder in the main partition.  Here is the result of the "sudo fdisk -lu" command:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda3   *      160650     4771304     2305327+  83  Linux
/dev/sda4         4771305   156296384    75762540    f  W95 Ext'd (LBA)
/dev/sda5         4771368     7357769     1293201   82  Linux swap / Solaris
/dev/sda6         7357833   156296384    74469276   83  Linux

---

### Post by caljohnsmith on 2008-10-26
Well if you copied the boot files from your /boot partition back to your main partition, I must ask, what exactly are you ultimately trying to accomplish? :) Do you want a boot partition, or do you want your boot files back in your main Ubuntu partition? And if you want a boot partition, is there any special reason why? Were you getting Grub errors maybe, and if so, what were they?

---

### Post by bcasanov on 2008-10-26
What I really want is to get the boot files from the main partition and to boot from the main partition.  I don't really know why I have a boot partition, but I guess my computer came with it.  The /boot partition was already there when I went to Gparted and checked.  I have a Dell Inspiron 1420N that came with a Dell Recovery Partition that I decided I didn't really need and I deleted it, and later committed the resulting unallocated space to the /boot partition because I didn't know how to allocate it to the / partition.   What I really would like is to have only the main / partition to boot from.

---

### Post by caljohnsmith on 2008-10-26
Well, I would first reinstall Grub to the MBR to point to your main partition sda6 for its boot files, and confirm that your computer can boot correctly; your HDD is only 80 GB, and there are some older BIOSes that can't access anything on a HDD past 8.5 GB, so there's maybe a small possibility that the 8.5 GB BIOS limitation is why your computer came with a /boot partition at the beginning of the HDD. So before deleting your /boot partition, I would recommend confirming that you can boot from your main partition by doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then go ahead and reboot, and when you get the Grub menu (hopefully), select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hd0,2)", press "e" to edit it, change it to "root (hd0,5)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Let me know if you can get that far. :)

---

### Post by bcasanov on 2008-10-26
Wow, the commands actually worked!  I rebooted and got the Grub menu, but it went too fast for me to see what it said, but at least, it booted into the desktop.  How do I pause Grub enough to let me see what it says, or do I just enter "e" at the first moment I see Grub and just wait and see what happens?

---

### Post by bcasanov on 2008-10-26
I moved/resized the /boot partition to the left so that there is no longer any unallocated space left, and now the /boot partition is a little over 2 GB in size.  However, after restarting. I had trouble booting to my desktop, as detailed here: [http://ubuntuforums.org/showthread.php?p=6036673#post6036673](http://ubuntuforums.org/showthread.php?p=6036673#post6036673)

What I really want is to get rid of the /boot partition and only have the / main partition as the only ext3 partition from which I boot.  I don't want a separate /boot partition where the free space is rather limited compared to a main / partition.

---

### Post by caljohnsmith on 2008-10-26
> **bcasanov said:**
> Wow, the commands actually worked!  I rebooted and got the Grub menu, but it went too fast for me to see what it said, but at least, it booted into the desktop.  How do I pause Grub enough to let me see what it says, or do I just enter "e" at the first moment I see Grub and just wait and see what happens?
Well, the bottom line is that I don't think you should have any problem getting rid of your /boot partition if you want to. The only problem is that your swap space comes right after the /boot partition, so you won't be able to simply expand your main Ubuntu partition sda6 to take up the free space from the /boot partition. I suppose though that if you delete the /boot partition, you could move both the swap partition and the main Ubuntu partition towards the front of the drive so that you would end up claiming the extra space with the Ubuntu partition.

I would make sure all your important files are backed up first, and then if you boot your Live CD (don't do this from Ubuntu on your HDD), you can use Ubuntu's partition editor gparted to make the changes:
```
gksudo gparted
```
Let me know how that goes, or what you decide to do, and we can work from there.

---

### Post by Torgas Prim on 2008-10-26
The reason for the boot partition is for the recovery options and recovery partition on all Dells.
<---Dell Lvl2 Tech a year ago....
If you have a catastrophic failure in your OS and are unable to boot, you can invoke the Restore to factory defaults option which is what your computer was like the day it shipped to you.
It reformats your main drive and reinstalls everything as when you opened the box the first time. You lose your saved data, but at least you have a running OS in about 15 minutes again, so back up your data before doing this.

---

### Post by bcasanov on 2008-10-26
This is what my partitions look like.  Should I also delete the fat16 partition along with the /boot partition?

---

### Post by caljohnsmith on 2008-10-26
That sda1 FAT partition is only 80 MB and is labeled as your Dell Recovery partition, so that must be the Dell Recovery Partition that you mentioned earlier about deleting? It doesn't look like it got completely deleted. So if you don't want it any more, sure, you can certainly delete it. :)

---

### Post by bcasanov on 2008-10-26
Well, now I deleted both partitions, and the screenshot I took is the result.  Gparted won't let me move or resize sda4 partition to fill the resulting unallocated space, and shows that sda4 and sda5 are locked and I can't move/resize them.  When I go to move/resize the sda6 partition, the left arrow won't move any further left.  How can I get the unallocated space into the ext3 partition?

---

### Post by GuitarRocker2562 on 2008-10-26
You can't because your / partition is an extended partition. Do you have an external HDD?

---

### Post by bcasanov on 2008-10-26
I don't have an external HDD.

---

### Post by GuitarRocker2562 on 2008-10-26
Hmm... Well, the only way to get you partiton table the way you want it would be to back up your entire / drive. Or at least your /home folder. Then, nuke your Ubuntu install, manage your partitions with a GParted LiveCD, and install Ubuntu again. Oh and as far as your system not booting, the /boot partition UUID probably changed. Does it begin to boot, or do you get an error at GRUB?

---

### Post by kansasnoob on 2008-10-26
Please go back to this thread:

[http://ubuntuforums.org/showthread.php?t=958785&page=2](http://ubuntuforums.org/showthread.php?t=958785&page=2)

---

### Post by caljohnsmith on 2008-10-26
Since your swap partition sda5 and Ubuntu partition sda6 are logical partitions inside of the sda4 extended partition container, you would want to try and resize the sda4 partition to the left first. I'm not sure why it shows the partitions and locked though; one thing you can try is right-click the swap partition and choose "swapoff" to make sure the Ubuntu Live CD doesn't use it. That will probably also unlock the sda4 partition. Let me know if that works.

---

### Post by kansasnoob on 2008-10-26
Caljohnsmith,

We have two se3ts of instruction going here:

[http://ubuntuforums.org/showthread.php?p=6037078&posted=1#post6037078](http://ubuntuforums.org/showthread.php?p=6037078&posted=1#post6037078)

---

### Post by kansasnoob on 2008-10-26
Bcasanov,

If I'm following properly and your system is now bootable there is no need to reinstall. A few thoughts though:

(1)Since you're planning to upgrade to 8.10 there is at least a small possibility of the upgrade NOT working and leaving you with a broken OS, so it's always a good idea to back up anything you don't want to lose.

(2)The reason sda4 and sda5 are locked is because swap is "on". By clicking on sda5 and clicking "swapoff" you'll then be able to move/resize sda4 and sda5.

(3)Once you resize or move swap you'll need to fiddle with uuid's to get swap to work properly and get usplash to work properly.

---

### Post by kansasnoob on 2008-10-26
So, I'll check back from time to time if you decide to resize/move swap this is basically what you need to know about the uuid thing:

Read all of Coffeecat's posts here:

[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

I thought he did an excellent job explaining it.

I kept a sample of commands and some notes here:

> lance@lance-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs"
/dev/sda5: UUID="3f6a93da-cbc0-4203-92ce-42ff70394f0a" TYPE="ext3"
/dev/sda6: TYPE="swap" UUID="5b397135-2a82-4933-aefd-00d7ff23b413"
/dev/sda7: UUID="cb8d8925-8059-46bc-8312-9ce5f42afa91" SEC_TYPE="ext2" TYPE="ext3"
gksudo gedit /etc/fstab
gksudo gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u
1 - Run 'sudo blkid -c /dev/null' (no quotes) from a terminal. Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.
2 - Check that the UUID for the swap partition in /etc/initramfs-tools/conf.d/resume is the same as the UUID you got from blkid. Edit the file if necessary.
3 - Run 'sudo update-initramfs -u' from a terminal (again, no quotes).
4 - Reboot.
5 - Enjoy usplash.

Always create a simple backup of these files before editing! And remember to "save" changes, then click File > Quit!

Clear as mud:confused:

If you're unsure please ask more questions.

---

### Post by bcasanov on 2008-10-26
Sorry that I took so long to respond.  I followed the instruction to have swap unlocked, and then resized/moved the partitions so that there was no longer any unallocated space left.  The process is still taking me more than a few hours.  I only have planned one extended partition, sda4, with sda5 increased to about 2 GB, and sda6 increased by one GB. I will go to the next step concerning the UUIDs once the partition resize/move process is complete.

---

### Post by bcasanov on 2008-10-26
Alright, now the partition process has completed.  Here is a screenshot of how my partitions look like.

---

### Post by bcasanov on 2008-10-26
Before trying the UUID thing to get swap to work, I checked to see if I could boot to my desktop.  I have run into a snag in that I cannot boot to my desktop again.  After the Grub menu appears, I get an error: 

Error 22:  No such partition.  Press any key to continue.

Following the instructions a few posts above: 

Once I got the Grub menu, I selected the first Ubuntu entry, pressed "e" to edit it, selected the line that says "root (hd0,2)", press "e" to edit it, changed it to "root (hd0,5)", pressed return to save the change, then press "b" to boot.  However, I still could not boot to the desktop.

The result of "sudo fdisk -lu" is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4              63   156296384    78148161    f  W95 Ext'd (LBA)
/dev/sda5             126     4289354     2144614+  82  Linux swap / Solaris
/dev/sda6         4289418   156296384    76003483+  83  Linux
 

What do I do now?

---

### Post by caljohnsmith on 2008-10-26
You could not boot Ubuntu I think because not only did the "root" line change, but also the "kernel" line still uses the old UUID. Next time on start up, edit the Ubuntu entry again, use "root (hd0,5)", and then change the kernel line to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=[COLOR="Red"]/dev/sda6[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
That should be enough to boot into Ubuntu, and then you can follow Kansasnoob's instruction about getting all your UUIDs in order.

---

### Post by bcasanov on 2008-10-26
I tried what you suggested, but I got another error:

Error 15: File not found.  Press any key to continue.

Perhaps the number in the root (hd,x) entry should be another number?

As an aside, I found an entry in my Grub menu that may have to do with the Dell Factory Restore.  It said something like Restore to Factory Default.  It is listed as root (hd, 1).   Should I delete this entry in my Grub menu, since I already deleted the Dell Recovery Partition?

---

### Post by caljohnsmith on 2008-10-26
OK, I realized that you're not going to be able to boot into Ubuntu until you at least edit your fstab so that it has the correct UUID for the new partition, and of course the swap UUID needs to be updated to; so you might as well take care of all of it from the Live CD. Begin by booting your Live CD and doing:
```

sudo mount /dev/sda6 /mnt
sudo blkid -c /dev/null
gksudo gedit /mnt/etc/fstab
```
And using the results of the blkid command above, change the UUID in your fstab that has a mount point of "/" to the UUID of your new sda6 partition. Also correct the UUID for the swap partition in your fstab. Next open up your menu.lst:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And make sure all the Ubuntu entries look similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,5)[/COLOR]
kernel		[COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		[COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.24-19-generic
quiet
```
So in addition to using (hd0,5), you will probably also have to add /boot in front of the lines for kernel and initrd; and lastly change the UUID to the sda6 UUID. Also make sure your "#groot" line is:
```
# groot=(hd0,5)
```
And also change your "#kopt" line in menu.lst to use the new UUID for the sda6 partition:
```
# kopt=root=UUID=[COLOR="Blue"]<new UUID goes here>[/COLOR] ro
```
Next open:
```
gksudo gedit /mnt/etc/initramfs-tools/conf.d/resume
```
And change the UUID in that file to your swap partition UUID. After that reboot, and you should be able to boot into Ubuntu, but you most likely won't get a splash screen. To correct that, once you get into Ubuntu, just do:
```
sudo update-initramfs -u
```
And you should be all set if I didn't forget anything else. Let me know how it goes.

---

### Post by bcasanov on 2008-10-26
Oh my goodness, it worked, caljohnsmith!  Thank you!  Thank you so very much for your kind and patient help, all of you!  This is what is so wonderful about the Ubuntu community.  I will be sure to share the solution to this problem with others in case they have a similar problem to mine.  Again, I appreciate all of your warm and helpful support.  You are what makes this community so inspiring and so much better and richer than MS phone support.  I'll be sure to mark this thread as solved.

---

### Post by bapoumba on 2008-10-27
Threads merged.

---

### Post by caljohnsmith on 2008-10-27
> **bcasanov said:**
> Oh my goodness, it worked, caljohnsmith!  Thank you!  Thank you so very much for your kind and patient help, all of you!  This is what is so wonderful about the Ubuntu community.  I will be sure to share the solution to this problem with others in case they have a similar problem to mine.  Again, I appreciate all of your warm and helpful support.  You are what makes this community so inspiring and so much better and richer than MS phone support.  I'll be sure to mark this thread as solved.
You're certainly welcome, glad you've got it all working now. Just a small request though: please only start one thread per subject, as it makes it really difficult for members to efficiently help you when you have two threads going on the same subject. Anyway, cheers and have fun Ubuntu-ing. :)

bapoumba: Thanks much for merging the threads. :)

---

