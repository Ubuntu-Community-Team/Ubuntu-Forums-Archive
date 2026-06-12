---
title: "GParted problems"
date: 2023-04-08
forum: Installation &amp; Upgrades
---

### Post by dcredway on 2023-04-08
I have following problem using GParted in 18.04

Initially PC working in dual boot mode with Windows7 and two Ubuntu versions - 18.04 on sda6, which includes /home, and 22.04 on sda8 which at 14GB is running out of space.
sda5 is /home at 45GB but only 7GB used so far with 22.04.

To gain free space to extend sda8 I created sda9 of 17GB in sda5 and moved 7GB of sda5 to sda9.

Now I can only boot into Windows or 18.04 which is working correctly but "Files" Other Locations only shows Computer with no other partitions.  GParted displays sda partitions correctly.

My intention was to delete empty sda5, just 336MB, for free space to extend sda8 but unable to boot 22.04 has stopped me.

How should I proceed?

---

### Post by ajgreeny on 2023-04-08
Oh my goodness, you lost me in that explanation of your partitions, and I think this is one situation where an attached screenshot of the gparted window will help us all and remove the potential for a costly mistake and removal of data that's important to you.

Take a screenshot  save it to your disk then use the ***Reply to Thread*** button and click the paperclip icon in the toolbar, browse to the saved image and click the Upload button.

---

### Post by yancek on 2023-04-08
If 22.04 is on sda8 why did you create another partition (sda9) instead of simply enlarging sda8?  Did you have unallocated space after sda8 before making this change?
Post an image of GParted as suggested and the output of sudo fdisk -l to list partitions.  The fdisk output will show sectors which will be helpful

> To gain free space to extend sda8 I created sda9 of 17GB in sda5 and moved 7GB of sda5 to sda9.
 

Why?  You said sda5 had the most space available so why move data from it to another partition?

Are all 3 installs Legacy installs with an Extended and Logical partitions?  That would be the default for windows 7.

---

### Post by dcredway on 2023-04-09
Thanks for your responses.

 Attached are GParted .jpg currently and txt file of sudo fdisk -l.

Answer to your questions.  There was no free space to enlarge sda8  / 22.04.

sda5 was /home and was too large with only 7Gb used of 45GB.

sda9 would become /home and sda5 deleted for free space to extend sda8.

Maybe too simple??

---

### Post by yancek on 2023-04-09
>  Partition table entries are not in disk order

I'm not sure if you understand the concept of Extended and Logical partitions.  The quote above is from your fdisk output which shows sda3 as the Extended partition.  This partition does not and can not contain any data.  On a dos drive such as you have, you can only have 4 primary partitions and one of these can be used to created an Extended partition which can then contain a number of Logical partitions.  On Linux, Logical partitions start with 5 (sda5, sdb5, etc).  Your partitions are not in order beginning with 5 but are  sda8, sda5, sda9, sda6 and sda7.  This would be their location on the disk.  Since you did not do anything with sda8, the 22.04 install there should be no problem unless sda5 is the /home partition for 22.04.  You indicate it will not boot, what exactly happens, what error do you get? 

In your initial post you indicated your plan was to delete sda5 but your posted output still shows sda5.  Doing that would create problems because deleting a Logical partition changes the partition number.  sda8 would then become sda7, sda7 would become sda6, etc.  If you moved all the data from sda5 to sda9 and sda5 was the /home partition for 22.04, you need to change the /etc/fstab entry for that partition on 22.04

---

### Post by dcredway on 2023-04-11
Thanks yancek for your comments.

Yes, my intention was to delete sda5 after creating sda9 and moving /home data to sda9. But 22.04 not booting stopped me deleting sda5 for free space as indicated in initial question.

 Booting 22.04 still just hangs after Ubuntu flash screen then blank screen with just flashing cursor - might be because sda5 is not now /home??

"Files" Other Locations today shows "Computer" 18.04 with all other partitions including partition sda8 22.04 and its files.

How can I get free data to increase size of partition 8 22.04? 
 Depending on that answer sda5 could be restored and remain as /home.

Otherwise it could mean a fresh install even to full SSD of 22.04. I seldom use Windows7 these days having used Ubuntu for 95% of work since 8.04 LTS.

How do I restore SSD to initial state?

I would prefer to keep 18.04, even as no longer supported, and 22.04.

I appreciate at 90 your guidance.

GParted jpg clearly shows Extended Partition is Partition 3 of 100GB and has been since 2014 when SSD, Windows and Ubuntu were installed.
Currently running 18.04 from Partition 6.
So I do not understand "This partition does not and can not contain any data."

---

### Post by ajgreeny on 2023-04-11
An extended partition can contain only other partitions, not any files or data so your options may be to backup all the files and folders in your current /home partition and then delete all ext4 partitions and start again with with a reinstallation of your chosen version of Ubuntu, though you can forget 18.04 which is just about to lose any further support or upgrades.

Your partition arrangement on disk is so muddled that trying to continue without a restart is likely to end with more problems, and from what I understand from your posts, you have some partitions that are not used nor needed, eg, sda5, though I may be confused by your multipartition system.

---

### Post by yancek on 2023-04-11
If sda5 was originally /home for 22.04, and you moved all the contents of that partition to sda9, I would not expect it to boot and if it did I would not expect you to be able to log in.  You would need to change the entry in /etc/fstab for the /home partition from sda5 to sda9 if that is where you copied the data to.

>  How can I get free data to increase size of partition 8 22.04? 

If you look at the output of fdisk -l which you posted you will see the Extended partition (sda3) is Sectors 39270398 to 234440703.   sda8 is the first logical partition in the Exended partition beginning at sector 39270400 and ending at  sector  68569087.  The partition that is immediately after sda8 is sda5 beginning at sector 68569088.    The end sector for sda5 is 99289087 and the beginning sector for sda9 is 99291136.  So to add to sda8, you would delete sda5 and sda9 and would then be able to add  about 32GB to sda8.  You would need to do this from a 18.04.  Don't forget to copy the /home data from sda9 to another device before deleting it.   This may not seem logical but note in the output of fdisk that  Partition table entries are not in disk order.  That is why sda9 is next to sda5.

Major problem with doing this is that when you delete a logical partition (sda5, sda9) the other logical partitions will change number.  Deleting sda9 won't be a problem as it is the highest number but doing only that won't help as it is not contiguous with sda8.  If you delete sda5, the higher numbered partitions will each change to a lower number and that will present problems with booting and logging in.  You would need to modify your /etc/fstab file as well as Grub files to boot 

I would think that if 18.04 is entirely on sda6, you could boot it and make sure that sda5 and sda9 are not mounted and then delete them and extend sda8 into the new unallocated space.  Again, since you have apparently copied the /home directory to sda9, you would need to move that to some external device so you can copy it back later.  Then run sudo update-grub while still booted into 18.04.

Probably easier to reinstall 22.04.

---

### Post by dcredway on 2023-04-16
Now understand initial "Oh my goodness" ajgreeny and thanks yanek for detailed explainations.

Before deciding way forward just a couple of questions.

1.  Where does downloaded software reside, / or /home?

2.  Does /home only contain users data?

3.  If I delete current / (not accessable 22.04) on sda8 and /home on sda9
    can I created new / and /home partions using install without effecting 18.04
    partition?

4.  Will new update-grub then cater for change of 18.04 partition number?

Getting close to final decision!

---

### Post by yancek on 2023-04-16
If you are downloading software from the Ubuntu repositories, it will be installed somewhere on the / (filesystem) partition.  There is no specific location for all software.  Do you know the difference between / (symbol for the entire filesystem) and /root which is the root user directory and rarely contains much. 

/home contains user data but there are also configuration files for the user in that directory, it would not be in /home but in /homt/username for each user.

I would suggest that you boot the Ubuntu install USB and use GParted on the disk to first delete sda5, then select sda8 to enlarge it to include what had been sda5.  Check the partition numbers here.  If you understand my explanation above and you have not changed the disk layout/partitions since posting the fdisk output, you will see that sda8 and sda5 are contiguous.  If you delete sda5, sda8 will change to sda7 and sda9 will change to sda8. You can see this by looking at the Start/End sectors for each partition.  After including the unallocated space from the former sda5 partition, you will have a / (filesystem) partition of 28GB rather than 14GB.  Once you have completed the partition changes and you can see the changes in GParted, start the installer and make certain to select the manual (Something Else) install option and select what was formerly sda8 and should now be sda7 (since you deleted sda5 so the numbering changed).  sda7 should be selected for the filesystem with a mount point of / and sda8 should be for /home.  If you don't see these changes in the installer, reboot and check again.

If you are able to successfully install 22.04 to those partitions, it should run update-grub at the end of the installation.  Watch the screen to see this.   When you install 22.04, make sure you select the Legacy option.  If you don't have UEFI compatibility on this computer, it should do that automatically.

---

### Post by TheFu on 2023-04-16
Bloat in Ubuntu has grown tremendously since 18.04 (which was bloated compared to all earlier versions).  I miss the days of having a little 10G OS.  All the GUI stuff adds bloat.

[LIST]
[*]/ in 20.04 and later needs to be 35G, assuming a separate swap partition.  
[*]For a desktop, swap should be 4.1G.
[*]/home is for user files and configs.  The only programs that use that for libraries and executables would be manually installed without using any package manager.
[/LIST]

There are reasons to have a separate /var/ file system too, thanks to bloated snap packages and to prevent run-away logs.

---

### Post by dcredway on 2023-04-17
Thanks Yancek.  Will try your detailed instruction in next day or so.  Will let you know result.

---

### Post by dcredway on 2023-04-17
Thanks TheFu for your comments.

The 18.04 install was 32 bit and 22.04 install was 64 bit so much bigger install.

---

### Post by TheFu on 2023-04-17
> **dcredway said:**
> Thanks TheFu for your comments.

The 18.04 install was 32 bit and 22.04 install was 64 bit so much bigger install.

Err ... the difference between 32-bit and 64-bit installs isn't 2x.  It doesn't work that way.

---

### Post by dcredway on 2023-05-02
Latest situation

Followed partition instructions and screenshot is attached.

Installed to sda7 and all correct until grub update failed with fatal error.

Used live 22.04 to gain terminal access.

Followed final Ubuntu mag 'Revival' terminal instruction s with failure finally to display boot menu.

Tried to repeat above but attempt to mount sda7 failed - no such partition.

Is solution now to delete all sda3 logical partitions and start again with new partitions.

Only penalty is loss of 18.04 but retaining Windows 7.

Look forward to your advice.

---

### Post by yancek on 2023-05-02
> Followed partition instructions and screenshot is attached. 

Which 'partition instructions' are you referring to?  What is your reference to 'Ubuntu mag Revival' about?  Did you make notes in a text file of each exact step during the process so you could post here in case of failure?  If not, I would suggest you do that in the future.  How did you attempt to mount sda7?  Was this from the Ubuntu install USB?

You have the / filesystem on sda7 and /home on sda8 so is 18.04 on sda5?

Probably be simpler for you to just delete the logical and then Extended partitions and start over since 18.04 support ends this month.  Make sure you unmount the logical partitions before trying to delete them.

---

### Post by ajohnl on 2023-05-03
> **TheFu said:**
> Bloat in Ubuntu has grown tremendously since 18.04 (which was bloated compared to all earlier versions).  I miss the days of having a little 10G OS.  All the GUI stuff adds bloat.

[LIST]
[*]/ in 20.04 and later needs to be 35G, assuming a separate swap partition.
[*]For a desktop, swap should be 4.1G.
[*]/home is for user files and configs.  The only programs that use that for libraries and executables would be manually installed without using any package manager.
[/LIST]

There are reasons to have a separate /var/ file system too, thanks to bloated snap packages and to prevent run-away logs.
Swap is confusing in some ways. For instance if you install no swap as I have done but another distro the option to sleep when the machine is shut down needs to disappear. This article goes through it fairly well
[How Much Swap Should You Use in Linux? (itsfoss.com)]("https://itsfoss.com/swap-size/")
It explains what happens if loads of apps use swap but then mentions video editors. Those need ram otherwise they are reading from disk, writing to swap and then reading from disk yet again from swap. "Great idea"

Bloat would be off topic. Lets just say some aspects are down to modern ideas about using C++ aimed at increasing productivity ie produce stuff more quickly, It has it's complications. ;) Maybe a counter culture will crop up.

---

### Post by dcredway on 2023-05-04
Answers to your questions Jancek of May 3:

Which 'partition instructions' are you referring to?    Those of your response 2 weeks ago.

What is your reference to 'Ubuntu mag 'Revival' about?   UBUNTU USER mag of Spring 2017 in Discovery Installation section had 'Revival' instructions as follows:

  To revive and installed Ubuntu, boot up Live mode ....
  Be sure that the Live mode and the installed versions are the same architecture.
  Then, invoke a terminal and invoke following commands.
  Substitute for /dev/sda6 entry the specific partition in which the 
  root directory (/) of the installed Ubuntu is located.

$ sudo mount /dev/sda7 mnt           (22.04)
$ sudo mount -o bind /dev /mnt/dev
$ sudo mount -o bind /sys /mnt/sys
$ sudo mount -t proc /proc /mnt proc
$ sudo chroot /mnt
$ grub-mkconfig -o /boot/grub/grub.cfg
$ update-grub2              (Fatal error)
$ grub-install /dev/sda
$ exit
$ sudo boot


How did you attempt to mount sda7?  In Terminal $ sudo mount /dev/sda7 mnt     (22.04)

Was this from the Ubuntu install USB?  Yes

You have the / filesystem on sda7 and /home on sda8 so is 18.04 on sda5?  Yes

END OF ANSWERS

Any chance of edit to /boot/grub/grub.cfg  and/or  grub-install /dev/sda to complete installation?

If no can I delete logical partitions sda5, sda7 and sda8 plus sda6 Swap in sda3 Extended partition then create new logical partitions for / , /home , Swap partitions?

After fresh install to / would this retain Windows and dual boot?

---

### Post by yancek on 2023-05-04
>  How did you attempt to mount sda7?  In Terminal $ sudo mount /dev/sda7 mnt     (22.04)


If that is the actual command you used, it is not correct.  You left off the leading forward slash ( / ) on mount.  Also on the proc command. /mnt/proc. 

> sudo mount /dev/sda7 /mnt 

>  If no can I delete logical partitions sda5, sda7 and sda8 plus sda6 Swap  in sda3 Extended partition then create new logical partitions for / ,  /home , Swap partitions?

Yes.  Use the manual (Something Else) option because you are not using a default installation.  You need to create the partitions and format them and during the install, make sure you select the correct partition for / (the base filesystem) and /home

>  After fresh install to / would this retain Windows and dual boot? 		

Yes, it should as long as you do not make any changes to the windows primary partitions.  Grub should be installed during the system installation and updated to include the windows system.

---

### Post by dcredway on 2023-05-07
Thanks Jancek for seeing my errors of missing /

I have repeated "Revival" correct terminal instructions with following result:

grub-install: error: cannot find EFI directory
 
Below is copy of "Revival" terminal input/output.

First question is where and size of EFI partition/directory should be created?

Windows is not detected in listing but could be due BIOS setting of "Boot Mode Selection" being UFEI only now changed to UFEI and Legacy.

Second question relates to installing last year of 22.04 (with problem of UFEI partition) until running short of space this year. How could this happen?


ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt 
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -t proc /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-43-generic
Found initrd image: /boot/initrd.img-5.15.0-43-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
root@ubuntu:/# update-grub2
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-38-generic
Found initrd image: /boot/initrd.img-5.19.0-38-generic
Found linux image: /boot/vmlinuz-5.19.0-35-generic
Found initrd image: /boot/initrd.img-5.19.0-35-generic
Found linux image: /boot/vmlinuz-5.15.0-43-generic
Found initrd image: /boot/initrd.img-5.15.0-43-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
root@ubuntu:/# grub-install /dev/sda
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
root@ubuntu:/#

---

### Post by dcredway on 2023-05-07
Second question relates to installing last year of 22.04 (with NO SIGN of UFEI partition) until running short of space this year. How could  this happen?

---

### Post by yancek on 2023-05-07
>  Second  question relates to installing last year of 22.04 (with NO SIGN of UFEI  partition) until running short of space this year. How could  this  happen? 		 	  	 		5 Hours Ago
 		

I'm not sure what you mean by that.  Your GParted and fdisk output you posted earlier do not show an EFI partition and you are using an MBR/dos drive and your install of windows 7 and Ubuntu 18.04 are in Legacy/CSM mode.  If you install 22.04 in EFI mode, you will not be able to boot windows 7 from Grub.

In your last post you show the output of trying to install Grub in EFI mode and you get an error saying it could not find an EFI directory.  That's because (according to earlier posts) you do not have one.  If you want to keep windows 7 and 18.04 installed in Legacy mode, you need to boot and install 22.04 in Legacy/CSM mode also.  Did you notice the WARNING message in update-grub?  Os prober is disabled by default and doesn't detect other systems so you need to enable that before updating Grub.  You can do this by adding the line below to the /etc/default/grub file using sudo and a text editor:   GRUB_DISABLE_OS_PROBER=false

---

### Post by dcredway on 2023-05-15
It is clear now Jancek from your last post of my problems caused in BIOS of Legacy and EFI modes.  The install of 22.04.1 last year used Legacy mode.

But install of 22.04.2 this year can only be in EFI mode thereby preventing retention of Windows 7 and 18.04.

Thanks for ways around via Terminal but USB Live boot 22.04.1 also needed.  Terminal and I are strangers especially sed text file editor.

So to get out of your way I decided to abandon Windows 7 and 18.04 and have installed 22.04.1 on full 120GB SSD.  Then updated to 22.04.2 on-line.

Your help plus others at Ask Ubuntu have increased my Linux knowledge.  Thanks.

---

