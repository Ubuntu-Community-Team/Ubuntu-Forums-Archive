---
title: "Grub Loading Error 2 w/ Adaptec ASH-1233 UDMA controller"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by rkang on 2007-02-23
I use this controller card (based off the Sil0680 chip) to get 48-bit addressing on my older Shuttle SS51G to access a single 400GB drive.

The LiveCD recognized, partitioned, formatted, and installed on the drive without a hitch, which is why I was so surprised to get the error:

GRUB Loading stage1.5.

GRUB loading, please wait...

Error 2

during a boot from the drive.

Any help would be greatly appreciated.

---

### Post by Herman on 2007-02-23
Hello rkang,
Here is where you can look up what the Gnu Grub Manual has to say about Grub error 2, [Errors reported by the Stage 2]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors")

You could try running a filesystem check and see if that clears it. You can do that from the Ubuntu 'Desktop' LiveCD (on the unmounted filesystem), if you know the right commands. 
My suggestion is this one,```
sudo e2fsck -C0 -p -f -v /dev/hda2
```(Where /dev/hda2 is your Ubuntu partition, and you are using the ext3 filesystem).

Otherwise if you don't like using commands, the easiest way to run a filesystem check is to boot a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), click on the partition you want fixed, and select 'check' from the menu, and wait for a while. 

You might also try booting it from [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") or with a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and see if that will boot it for you. If that works then you will be able to easily fix it by editing your /boot/grub/menu.lst file.

If you would like more help with your specific problem you could run the Ubuntu Desktop Live CD and post here the output from the following command, ```
sudo fdisk -lu 
```And then [mount your Ubuntu hard disk installed operating system's]("http://users.bigpond.net.au/hermanzone/p10.htm") filesystem (partition) and get a copy of the /boot/grub/menu.lst file and post that here please. Then hopefully someone will be able to see something wrong and be able to help you better.

Regards, Herman :)
[URL="http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#2_"]
[/URL]

---

### Post by rkang on 2007-02-23
running e2fsck -c -p -f -v /dev/hdf1 does nothing at all... the system merely hangs.
ran Gparted LiveCD and ran file check- everything seems fine but still get the Grub Error 2.  One strange thing is I get a failure to unmount filesystems when rebooting out of GParted.


sudo fdisk ls:

Disk /dev/hdf:  500.0 GB 500088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

Device        Boot       Start               End            Blocks               Id  System
/dev/hdf1    *         63                 773834984     386917461         83  Linux
/dev/hdf2               773834935     781417664    3791340             5    Extended
/dev/hdf5               77385048       781417664    3791308+           82 Linux swap / Solaris


I then mounted hdf1 and edited menu.lst:

title      Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdf1 ro quiet
splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
initrd /boot/vmlinuz-2.6.17-10-generic root =/dev/hdf1 ro single
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot


Thanks again

---

### Post by Herman on 2007-02-23
> running e2fsck -c -p -f -v /dev/hdf1 does nothing at all... the system merely hangs. ran Gparted LiveCD and ran file check- everything seems fine but still get the Grub Error 2. Thank goodness for GParted LiveCD then.
I re-tested that command just to make sure it was correct. It works for me and it gives me a really cool 'progress bar' like: '|====>' moving from right to left across the page, until it meets a tumbling bar, '/' with a % readout after it. Then that disappears and my feedback is presented, like this,
> ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/hda2
                                                                               
  116487 inodes used (3.52%)
    1356 non-contiguous inodes (1.2%)
         # of inodes with ind/dind/tind blocks: 5307/245/0
 4720964 blocks used (71.65%)
       0 bad blocks
       0 large files

   84081 regular files
   13875 directories
    1225 character device files
    4547 block device files
       2 fifos
     468 links
   12746 symbolic links (11946 fast symbolic links)
       2 sockets
--------
  116946 files I think the only thing you might have done wrong was typing 'e2fsck -c ', the command begins with 'sudo e2fsck -C0...' (that's a large 'C' followed by a '0' (zero), but never mind. You got the job done with the GParted LiveCD which is really great, I use GParted LiveCD almost every day for all kinds of jobs, it's almost indispensable. :)

Now... thank you for your fdisk output and you menu.lst  boot-up entries.
I notice right away that your fdisk output shows your hard disk as /dev/hdf, which normally indicates hard disk number  6.  
Your menu.lst file boot-up commands have grub setting 'root' (hd0,0), which means your first hard drive, first partition is designated as the boot partition. That doesn't seem to match up. :confused:

Let's see if we can come up with an efficient way to find out whether this is okay for booting your particular computer or if the problem will be something else. I can think of several ways to test this.
One way, since you are usung the 'Desktop' Live/Install CD, is to boot your LiveCD, and open up a terminal again.
In Terminal, open a 'grub shell', with this command, 'sudo grub' ```
sudo grub
```Then after the grub>_ prompt, type 'geo', then press your tab key and the command 'geometry' will automatically be completed for you.
```
geometry (hd
```Then type '(hd', and press your tab key again for a list of your hard drives. If you had more than one it would be a list, but in you computer it might just complete to '(hd0,', which will confirm that grub sees your drive as the first hard disk. Then to see if grub sees your partitions on your first hard disk, press tab again and you should get a list of your partitions.
If grub doesn't see your hard disk as (hd0), it might see it as (hd5), (hard disk number 6 in grub's numbering scheme), then you might try editing your menu.lst entry accordingly.

Another approach to your problem is to try booting with a [Super Grub Disk.]("http://supergrub.forjamari.linex.org/")
You can try booting from SGD's menus, for a quick way to see if your computer will boot up. Try 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot  Gnu/Linux'
Or, 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot  Gnu/Linux Directly', and see if your computer will boot.

A more informative method would be to press 'c' from a Super Grub Disk menu to get a [Grub Command Line Interface.]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 You can use Grub's command line to interface to investigate your computer, as CLI grub provides useful feedback that might help you solve your problem. The link given above includes some handy tricks that should help you with that. If you can [boot Linux from CLI grub]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI"), then you can edit your menu.lst file with the same commands, so keep notes of what commands you try on a piece of paper, or in another computer.
Or, it might be your device.map files that needs editing, depending on what you find out.

Try those ideas and see if any of them help,
Regards, Herman :)

---

### Post by rkang on 2007-02-23
Hi Herman-
I ran the grub geometry command and it properly detected hd0.

Possible partitions are:
Partition num: 0, Filesystem is ext2fs, partition type 0x83
Partition num: 4, Filesystem type unknown, partition type 0x82

This seems consistent with hdf1 (ID 83) being the main partition and hdf5 (ID 82) being the swap partition.


using the Super Grub Disk 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux':
findf /boot/grub/menu.lst
Error 15: File not found

Booting 'trying /boot/grub/grub.conf'
findf /boot/grub/grub.conf
Error 15: file not found

Booting 'trying /grub/menu.lst'
findf /grub/menu.lst
Error 15: File not found

SGD has NOT done it


Using the SGD command: 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly':
Booting 'trying to find a unique root filesystem'
findf /boot/vmlinuz
Error 15: File not found
booting 'trying to find an separate root and boot filesystem'
findf /etc/fstab
set root_fs=/dev/hda1                                                                  //could this hda1 be an issue?
findf /vmlinuz
Error 15: File not found

I am investigating using the SGD CLI as of right now.
-grub geometry can only detect partition 0 (ID 83) on hd0.
-find /vmlinuz:  Error 15: file not found
-find /sbin/init:  Error 15: file not found
-null (hd0,0)/:  possible files are: lost+found var etc media cdrom bin boot dev home initrd lib mnt opt proc root sbin srv sys tmp usr vmlinuz initrd.img
-null(hd0,0/boot/):  unrecognized device string
-null(hd0,0)/boot/:  Error 2:  bad file or directory type.

there are no harddrives listed under null (hd0,0)/dev/.
So I can't find the kernel, can't find the root partition, and can't find the boot directory... perhaps the system didn't install correctly?

Thanks again

---

### Post by Herman on 2007-02-23
:-k Hmmm... It seems to me as if your new hard disk is not being properly read by either grub or fdisk. First you said it's a 400 GB hard disk, but according to fdisk it's 500 GB. Now it seems as if Grub can only partially read your hard disk. 
It claims it can't find the files,
>  -grub geometry can only detect partition 0 (ID 83) on hd0.
-find /vmlinuz:  Error 15: file not found
-find /sbin/init:  Error 15: file not found
 But yet it can tell us what files are there, > -null (hd0,0)/: possible files are: lost+found var etc media cdrom bin boot dev home initrd lib mnt opt proc root sbin srv sys tmp usr vmlinuz initrd.img Those are the files we are looking for, so grub can 'see' them but can't access them?

It could be a problem to do with disk geometry translation in the BIOS.
As an experiment, how about resizing the Ubuntu partition to a much smaller size, like 80 GB or at least within the 137 GB limit just to see if that helps. Probably it would be best to move the swap area too.  I understand you use the controller card to overcome that, but lets just see if that helps. If that does help, then we can resize the partition larger again until we have problems, then reduce it a little.

Regards, Herman :)

---

### Post by rkang on 2007-02-24
sorry Herman, I must have typed in the fdisk output incorrectly (I am not posting from the machine running LiveCD).
Fdisk correctly recognizes the drive as 400GB.

does this change your prognosis or should I go ahead and resize the partitions using Gparted?

again thanks for all your help.

---

### Post by Herman on 2007-02-24
That's okay, so it's a 400 GB hard drive, which is still a very large disk. 
I still think it would be worth trying to see if shrinking the partitions and moving the swap area towards the beginning of the disk as well would be worth a try to see if it helps any.
Regards, Herman :)

---

### Post by rkang on 2007-02-24
Success!
I did a clean re-install of Ubuntu 6.10 from the LiveCD with a 80GB ext3 and a 5GB swap and it booted fine into the OS.

I used GParted to create a secondary partition to capture the unused space and everything seems to be working well.
Thanks for all your help.

---

### Post by Herman on 2007-02-24
:) Wonderful!

But... I'm a little concerned that with your hard disk so large and large data partition and your BIOS and firmware possibly not being able to keep perfect track of files that far out (or *in* to be more correct), on such a large hard disk, you could lose data. So be careful there.

I'm not an expert on these matters by any means. But from the reading I have been able to do I think that the mathematics they use to translate between what they call 'fake disk geometry' to 'real disk geometry', can sometimes be a little bit out. (Or something like that anyway). Apparently there are a lot of complicated formulas and equations involved. 'algorythms?' I couldn't begin to explain it (really because I don't understand it myself), but this link might give you the idea, [Disk Geometry]("http://www.rwc.uc.edu/koehler/comath/42.html")   That first page is the only simple one, the pages it links to are more advanced.
So anyway, what I am basically trying to say is this, I think that the more of your very large hard disk you try to use, the more a small inaccuracy in a mathematical formulae will be magnified.  That's what I suspect the reason for your booting problem might have been.  So it looks like you will have to experiment a little to see where your firmware and BIOSes view of your hard disk starts to get a little fuzzy. Hopefully you will be able to safely use almost all of your disk. 
That's only my opinion. See how you go anyway, time will tell. 

I'm happy you have it booting, that's the most important thing. Congratulations and well done! :guitar:
Regards, Herman :)

---

### Post by rkang on 2007-02-25
Hi Herman- just thought you'd like to know when I mounted the remaining 300 GB partition, it only comes up as a 70GB drive.  So I guess the upper limit using this controller card is ~155GB.  So I guess I will go back to XP for the 400 GB drive and reinstall ubuntu on a 160GB drive I have now.

Thanks for all your help.

---

### Post by Herman on 2007-02-26
Hello rkang, I suppose that would be the wisest choice, thanks for the update. 
Regards, Herman :)

---

