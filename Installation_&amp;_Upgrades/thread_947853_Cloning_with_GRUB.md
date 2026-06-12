---
title: "Cloning with GRUB"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by aajax on 2008-10-14
I've been using Debian for some time now.  However, Sarge is the latest version I've used and I am now trying to adopt Ubuntu.  I have considerable need to clone.  By this I mean move systems (boot/root partitions) around.  The technique involves creating an image, which also provides backup/restore capability, using a program such as ghost and then restoring it to either a different drive or different partition on the same drive.  This, of course, has the effect of making the new partition unbootable.  The simple solution involved booting from a rescue disk using the root= boot parameter and then updating the LILO configuration file and rerunning LILO after which the new partition boots fine.  I'm thinking I need to do something similar with Ubuntu but cannot find necessary documentation on how this is done when using GRUB.

---

### Post by caljohnsmith on 2008-10-14
I think the Grub command that comes closest to what you are looking for is "update-grub". But if you are moving partitions around, you will most likely have to manually modify your Grub's /boot/grub/menu.lst. The main thing will be getting the "root (hdX,Y)" lines and UUIDs correct in the menu.lst for your OS entries. If you want some help with that, let me know. :)

---

### Post by aajax on 2008-10-15
Thanks for the advice regarding update-grub.  I'll check it out but you bring up something else that has confounded me.  In my quest to try and find out how this UUID (for partitions ?) stuff works I think I was able to learn that it is not required on the commands/directives that appear in menu.lst and fstab.  However, I am curious and would like to understand.  Possibly it makes life better when cloning.  The basic questions are -

- How is this UUID computed?
- What component performs the computation?
- How is one to find the correct values?

Any help on the above would be appreciated.

---

### Post by caljohnsmith on 2008-10-15
> **aajax said:**
> Thanks for the advice regarding update-grub.  I'll check it out but you bring up something else that has confounded me.  In my quest to try and find out how this UUID (for partitions ?) stuff works I think I was able to learn that it is not required on the commands/directives that appear in menu.lst and fstab.  However, I am curious and would like to understand.  Possibly it makes life better when cloning.  The basic questions are -

- How is this UUID computed?
- What component performs the computation?
- How is one to find the correct values?

Any help on the above would be appreciated.
Truthfully I don't know how the UUID is actually computed, I've never delved into the technical details of it before. Usually the important point is that if you change the size of your partitions, the partition UUID will change; but if you clone the partition, it will be exactly the same and have the same UUID. You can easily find the UUIDs for all partitions on all drives with:
```
sudo blkid
```
If you clone a partition, it is recommended that you change the UUID of a cloned partition so it doesn't get confused with the original partition on the other drive; to do that you can use:
```
sudo tune2fs -U random /dev/sda1
```
And replace sda1 with the partition in question. That's about the extent of my knowledge of UUIDs. :)

---

### Post by ByteJuggler on 2008-10-15
Just to add to what's being said:  UUID's make partitioning/booting etc more robust in the face of accidental drive mapping changes (e.g. /dev/sdb becoming /dev/sdc due to a new Sata or USB disk being plugged in or whatever) which would break fstab and bootup if conventional drive identifiers were used.  

The problem with cloning a partition is that you clone the UUID with it, so if you keep both the original and the clone oneline at the same time and boot, you could run into throuble since there would then all of a sudden be 2 partiitons with the same supposedly univerally unique identifiers... I've actually not tried to see what would happen but logic dictates that you'll probably boot successfully without actually knowing which partitions the system ended up picking, which is in any case a bad situation to be in.

Now, this situation can be avoided by the advice given by the previous poster, but then, as you yourself said, you need to update the places where the old UUID was used and rerun "grub" to rewrite the boot loader on the cloned disk. (As an aside/alternate suggestion: It may be easier to save the original UUID's and just replace them temporarily to prevent boot problems on the clone drive, then restore them when you need to use the clone, thus avoiding having to mess with updating grub or fstab or uuid's etc.)

---

### Post by aajax on 2008-10-16
Well just for the record I went and found the man page for the update-grub command.  After reading it I deduced that it wasn't going to replace (rewrite) the boot sector, which is what I thought needed to be fixed.  However, I did find something called the Super GRUB Disk ( [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) ), which turned out to be useful.  Unfortunately, the documentation is a bit lacking and it was somewhat of an ordeal for someone new to GRUB to figure out how to use it.  However, it seems that GRUB supports a command line (shell) for executing commands manually.  This is what I did -

- Boot the Super GRUB Disk.  I used a CD but I think you can put it on other media as well.
- From the resulting menu enter the option that presents the command prompt.
- Enter the command “root (hd0, 2)”, which I think has the affect to specifying the drive (0 – first seen by the BIOS when booting) and partition (2 – the third one on the drive) that contains the /boot/grub directory of interest.  If I'm not mistaken the really good part of this is that GRUB can find this directory in many different file systems.
- Enter the command “setup (hd0, 2)”, which I think has the affect of writing the GRUB stage 1 on the the boot sector of the specified partition.  I'm thinking this involves figuring out the absolute address of the stage 2 file (or in some cases the stage 1_5 file) and combining that with the contents of the stage 1 file. 

Bottom line is that whether or not I properly understand how it works the above did solve my problem.  Something like this has to be done whenever you clone a Linux partition that you want to boot from.

In the case of GRUB, I think the above only has the affect of allowing the stage 2 to be loaded.  Then, I think, the stage 2 is able to find the menu.lst file using conventional file system access methods.  Therefore, in the general case the menu.lst file may also need to be updated.  In my current scenario this was not necessary because I was actually dealing with a newly built/installed system that was transferred from another drive (with different geometry) and I opted to make the partition configuration (i.e., device assignment) on the new (target) drive the same as what had existed on the old (source) drive.

Note:  It might be worth pointing out that the Ubuntu installer failed to figure out the correct drive assignment for booting.  As it happens I had instructed the BIOS to boot from the 2nd hard drive.  It seems that the BIOS makes it appear as though the 2nd drive is the 1st during the boot process but the installer didn't know about this.  Therefore, the installer constructed the boot loader for drive 2 but this didn't work because the boot loader sees drive 2 as drive 1.  The work around for this problem was simply to use the feature that GRUB provides to edit values before commands are executed.  In my case this meant changing the command “root (hd1, 2)” to “root (hd0, 2)” during the boot process.  Once the system is booted in is easy to go and edit menu.lst to refer to 1st drive rather then the 2nd one.

However, the problem that remains, which I didn't experience this time, but which should normally arise when cloning is that the contents of /etc/fstab also need to be updated and this should be done before booting from the new (cloned) partition.  On DEBIAN I was able to produce rescue diskettes that could be used to boot a very minimal system.  However, there was enough capability to mount the new partition and edit the /etc/fstab file.  It looks to me like the Ubuntu installation CDs actually cause a much more capable system to be run without using any hard disks.  If so this should provide an even better rescue disk.  This brings us to the matter of how UUID might be used.  I notice that the “blkid” command prints out a list that seems to show all of the partitions on the computer.  Some of them that are for other operating systems are also included along with UUIDs.  For example, I always put a small (less than 30MB) primary partition on every disk drive.  Typically I use this partition for running a boot manager.  Since I'm pretty sure that DOS does not store a UUID in the FAT file system, I have to suspect that this Linux method of handling UUID does not depend on storing these values on the file system itself.   Consequently, I'm still curious about the properties of these UUIDs and how it is intended that they be maintained.  I plan to conduct a cloning experiment just to see what happens to the UUID.

Sorry about being so verbose but thought the above might be helpful to anyone who subsequently references this thread.

---

### Post by ByteJuggler on 2008-10-16
> **aajax said:**
> Since I'm pretty sure that DOS does not store a UUID in the FAT file system, I have to suspect that this Linux method of handling UUID does not depend on storing these values on the file system itself.   Consequently, I'm still curious about the properties of these UUIDs and how it is intended that they be maintained.  I plan to conduct a cloning experiment just to see what happens to the UUID.

Well, you're right about DOS and UUID's, but that implies nothing about EXT2/3 and its handling of UUID's.  Anyway, I don't know if the system perhaps generates a fake UUID from the volume label/ID for DOS partitions for completeness sake (it would make some sense to do so), but I do know the UUID is stored in the filesystem somewhere for EXT2/3 partitions.   

Cheers.

Edit: [This thread]("http://ubuntuforums.org/archive/index.php/t-479047.html") is quite relevant and covers the same ground as this one, but in more detail.

---

### Post by aajax on 2008-10-17
Please HELP!

As a result of the discussions herein I set about trying to update the UUID associated with my /root filesystem, which is on device=/dev/sdb2.  Following is console output and file contents.  My remarks are delineated by << ... >>.

<< Prior to what is shown below the basic objective was to run the tune2fs command with the intent of updating/changing the UUID.  More specifically -

sudo tune2fs -U random /dev/sdb2

However, as you can see in the following it is difficult to tell what effect that command has had.  This is primarily attributed to the fact that the value of the UUID seems to differ depending on how it is displayed.  Furthermore, the value displayed by the vol_id command and shown below is the same value that was displayed (by the vol_id command) prior to making any attempt to change the UUID, whereas the value shown by the blkid & tune2fs command is different than what was shown before running the command to change it. This leaves me very confused and asking how is one to know what is the real/correct UUID for this file system. >>

ajax@Tester:/boot/grub$ sudo vol_id --uuid /dev/sdb2
235c1600-faf6-1d00-0000-000002000000
ajax@Tester:/boot/grub$ sudo blkid /dev/sdb2
/dev/sdb2: SEC_TYPE="ext2" TYPE="ext3" UUID="a889bbec-d1ac-49ad-9b92-7953a9a2dec2" 
ajax@Tester:/boot/grub$ sudo tune2fs -l /dev/sdb2
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          a889bbec-d1ac-49ad-9b92-7953a9a2dec2
<< a bunch of lines thought to be insignificant were removed >>
ajax@Tester:/boot/grub$ 
<< What follows immediately is the content of the file=/etc/fstab, which I updated as shown where I chose the value displayed on 2 of the 3 previous commands for the UUID.  The commented value is what was displayed prior to attempting the change by the blkid & tune2fs method of display. >>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
#UUID=7cb02ee4-4579-4a79-b291-d8e507f1e2b7 /               ext3    relatime,errors=remount-ro 0       1
UUID=a889bbec-d1ac-49ad-9b92-7953a9a2dec2 /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
<< Following instructions provided in the thread ([Here]("http://ubuntuforums.org/archive/index.php/t-479047.html")) I removed the file /boot/grub/menu.lst and ran update-grub, which produced a new version of the file /boot/grub/menu.lst.  A relevant portion of that file is shown below.  An obvious consequence of this is the /etc/fstab and /boot/grub/menu.lst contains different values for the UUID as a result of running update-grub and I don't see any way to ascertain which, if any, is correct. >>
<< lines omitted from the front of /boot/grub/menu.lst >>
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=235c1600-faf6-1d00-0000-000002000000 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
<< lines omitted from the back of /boot/grub/menu.lst >>

---

### Post by caljohnsmith on 2008-10-17
For one thing, did you reboot? For instance, if you just use "sudo blkid", it just dumps its cache stored in /etc/blkid.tab, which is not going to be instantly updated after you change the UUID of a partition. You can force blkid to look for the current UUIDs and not just print out its cache file by doing:
```
sudo blkid -c /dev/null
```
But still, there may be other processes that have files in /proc that still use the old UUID or something like that; so bottom line is, after changing the UUID, I would reboot and then check everything.

---

### Post by aajax on 2008-10-19
Well getting it to boot into the correct partition is the goal but that's the reason I'm changing the UUID.  Therefore, I think I've learned that there is some preparation required before rebooting.  My understanding at present is that at a minimum you need to -

1.) Update /etc/fstab - ultimately the goal is to replace the old UUID with the new one but to do that you need to know what value to use.
2.) Update /boot/grub/menu.lst with the correct UUID, which is used both in the kopt argument of the Automagic Kernel List as well as the kernel statement/s.  I think the kopt only matters when update-grub gets run but the others have immediate affect on how the system will boot the next time.

The basic dilemma is that you need to know what the correct UUID is in order to prepare to boot.  Something I thought should be possible was to temporarily change fstab and menu.lst so that the used the device (e.g. /dev/sdb2) rather than UUID technique.  However, in my current experiment things turned real bad.  I seem to have gotten into a situation where no matter which partition I boot I boot the same file system and I haven't figured out how to reliably determine which one it is.  For example, I have 2 partition at /dev/sdb2 and /dev/sdb3.  I seem to be able to boot either one.  In that, when I execute mount -l the output shows the file system I thought I booted as root (/).  Then I mount the other one on /mnt.  This seems to work fine.  But when I try and update a file (e.g., /mnt/etc/fstab) the update takes affect in both (i.e., /etc/fstab as well as /mnt/etc/fstab).  The same thing happens no matter which partition I think I booted.  I have to conclude that some how or another only one (? which one) of the 2 partitions is being found regardless of whether I reference /dev/sdb2 or /dev/sdb3 which I suspect is an outcome of having at one point in time had both partitions which used the same UUID.  Unfortunately 
both partitions should be nearly identical because one has been restored from the image of the other.    

At this point I've decided that it is a real bad idea to ever allow more than one partition with a given UUID to be created on the same drive.  Possibly this idea should be extended to be the same computer but I haven't tried anything beyond the same drive.  I have it in mind to make sure and update the UUID on the an operational partition as soon as any backup (image) is created with the idea that this prevents the possibility of ever restoring a partition that duplicates the UUID of another partition.  However, another idea is that if hurts don't do it and UUIDs are really hurting me right now.  I generally want to go with the trend when new things come along but right now I'm seeing no benefit and lots of problems with this UUID stuff.  The problem with this idea is that I fear that it conflicts with the proper use of the package management and system updating procedures and methods.

---

