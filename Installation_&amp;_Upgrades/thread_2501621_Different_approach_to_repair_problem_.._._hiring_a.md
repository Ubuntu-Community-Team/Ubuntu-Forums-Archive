---
title: "Different approach to repair problem .. . hiring a technician?"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by rudy5 on 2024-10-15
Hi all. Some of you may have seen my threads asking for help in migrating a broken 18.04 installation onto a fresh install on the same computer, but saving my data. (The upgrade path is irreparably broken.) Many thanks to the posters who have offered suggestions &c.

But after a month of thrashing about, I'm no further ahead, & am reaching the point of admitting to myself that I'm way out of my depth here, & lack the knowledge and skills to do this myself. 

When my plumbing goes, or when I need electrical work done, I hire a plumber or an electrician, they do the repair, and I pay them. 

Is there anybody with sufficient knowledge of Ubuntu linux, and the Dell XPS-13,  living within ca. 150km of Vancouver, B.C., to undertake this task for me?

---

### Post by Tadaen_Sylvermane on 2024-10-15
Forgive me but can you not just boot a live image, copy the home directory to an external then just install over the top of it?
Trying to fix something like that is a chore, even for someone experienced in it. Once it gets out of support + whatever other non recommended changes a person makes can create a mess. Just copy the home directories and reinstall.
Then learn from it, and don't do it again lol.

---

### Post by oldfred on 2024-10-15
We have seen a variety of users who went to a computer store that really only knew Windows & manage to delete all data and not do a correct install.

Still always best to have good backups. Many posts in forums on backups.

If you do not format / (root) and /home partitions (if separate) then it should keep all your data. Back up still required just in case.
Configuration files will change to new defaults if you edited anything in /etc. I edit grub, but save copy into /home so backed up.

Benefits of a release-upgrade (over clean install) by guiverc, but I prefer clean install & restore from backup
[https://ubuntuforums.org/showthread.php?t=2501145](https://ubuntuforums.org/showthread.php?t=2501145)
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)
[https://ubuntuforums.org/showthread.php?t=2496620](https://ubuntuforums.org/showthread.php?t=2496620)
[https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

---

### Post by rudy5 on 2024-10-16
Tadaen: No forgiveness required. And it's good to read that even experienced hands find this a chore! I've migrated between Linux systems in the past (been a continuous user since 2005) but I am by no means experienced, and this time the experience has been a raging nightmare.

What you are suggesting is what I've been trying to do. I hope you can stick with me / this for a few days, & help me navigate the various rabbit holes that I'm being sent down.

In order to copy my home folder to an external drive, I need a formatted USB drive. I have a 32gb drive here, formatted for Windows, so the first step is to re-format it for FAT --- correct? Because my Linux machine can't seem to mount the NTFS formatting.

Into the USB port with the drive. Using the GUI file manager, I select the drive for formatting, select ERASE, go. Result:

-Error formatting volume. 
Error erasing device: Error writing 1048576 bytes to /dev/sdb1: input/output error (udisks-error-quark,0)

I don't understand why the drive doesn't simply format (I can format a 4gb drive and a 16gb drive but that's not big enough to hold my 30.9gb of data.  But I can't parse this error message. Why can't linux erase the target drive? what are the 1048576 bytes it is unable to write? How do I understand this input/output error (udisks-error-quark,0)? 

So that's my first big question. Could you give me some advice on formatting this 32gb USB drive --- what format should I choose, what options when I'm formatting? Terminal command line alternative is welcome!

Then the next question I have is --- from the command line, what command would you enter to copy the entire /home folder and its contents onto my external drive, labelled Oc24data? I need help with the syntax!

cp -prv /home /media/rudy/Oc24data     
isn't doing it.

Should the "/home" argument be followed by /* ?

Should the target argument by /dev/ instead of /media/? do I need to put my account user name into this string? Do I need to specify the volume name? Do I need to specify /* so that all the files are copied?

If you can provide clear instructions about this, I might be able to move forward!

When you say "boot a live image". I've booted this 18.04 machine from my live-image USB drive with 22.04. With this live image USB in one port, do I need to put the target drive into the other USB port, and then use 22.04's copy tools to copy my home directory from this hard drive to the second, target USB drive?

I should just be able to copy /home to the USB drive from terminal, no?

And when you say "copy the home directory to an external then just install over the top of it", I'm confused by "then just install over the top of it" --- too many pronouns! Let's say I've got my copy of /home on the usb drive. Let's say I've finally been able to pave over this 18.04 yeeeesh and installed a fresh instance of 22.04 (on a Dell XPS-13 9360). Is my next step to copy my old /home folder from the USB drive where I've copied it, back onto the hard drive with its fresh installation of 22.04?

What is the terminal command that will copy my saved /home folder from the USB drive onto my hard drive with the new install of 22.04 on it?

---

### Post by rudy5 on 2024-10-16
Hi oldfred, you've kindly tried to dis-confuse my confusion over on another thread. Believe me, I would like to be able to successfully migrate my data to a new install WITHOUT hiring some Windows / Mac repair dude who once read an article about Linux and figures he can handle this .. .

When you say "backups", is there a backup utility built into (or that I can still download & install) that will back up all my data to an external drive, and allow me to restore that data to a *different* linux installation? How would this differ from a straight copy of /home which is then  copied back over the top of the /home directory of the new install?

I'm perfectly happy to accept the configuration determined by the fresh 22.04 install. I *DO NOT WANT* my old configuration --- it's been kicking up a blizzard of un-met dependencies &c. type of errors, & this is what has me trapped in this can't-upgrade-until-you-update-but-you-can't-update-because-broken-dependencies death loop. I want a FRESH install, that doesn't even know I ever had linux installed before, and I want to copy my current data *ONLY*, but *NOT* my SETTINGS, which seem eff'd.  

I only use a tiny handful of extremely vanilla applications, which I want to install fresh: Libre Office, Thunderbird (saving my old profile & history, if possible), Firefox (don't care about history). That's it.

The release upgrade path is closed to me. I've read the forum posts you point to. The repairs of the broken 18.04 that are suggested are far, far beyond my capabilities. I tried some of the suggestions, frustration has been the only result. I don't want to rescue my 18.04. I want to pave it over with 22.04, and copy my existing data --- e-mail history, word processor files, spreadsheets --- onto the hard drive with the new OS. 

I hope that I have been able to clearly state my needs & questions.

---

### Post by oldfred on 2024-10-16
Why are you using another Windows format FAT32? If also has limits on file size (4GB max) and no journal. 
NTFS may not work if Windows sets hibernation flag.
Windows formats do not support Linux ownership & permissions, best to use ext4.
30.9GB of data may be a bit too large for a 32GB flash drive as after partitioning & formatting it often is about 29GB usable.

If flash drive used with Windows or as an installer it may have partition table issues. Often a dd to zero out the partition table sector at beginning of drive may be required for partition tools to see drive.
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) 
Note this effectively erases entire drive, sometimes after reboot drive order changes, so always double check that correct drive is specified.
sudo dd if="/dev/zero" of="/dev/sdX" bs=4M count=32 #(X being the block device of the USB drive)
sudo fdisk -lu
sudo parted -l

I prefer rsync, but cp should work. 
[https://ubuntuforums.org/showthread.php?t=2465035&page=2](https://ubuntuforums.org/showthread.php?t=2465035&page=2)
# a simple rsync backup script:
rsync -avz  $HOME /mnt/backup/

---

### Post by rudy5 on 2024-10-17
Hi oldfred, there's a language gap, but you're providing some interesting suggestions for other rabbit holes to go down before I give up on this.

FAT32 because that was the formatting option that was suggested as Linux OS compatible by the operating system I'm using, which is Ubuntu 18.04. Thanks for letting me know that this is now a deprecated format; I'm lucky that my 4gb and 16gb drives formated as FAT32 work!! You see why I want to leave this 18.04 install behind? 

I wlll look for the ext4 formatting option the next time I try this, which will possibly be on a 64gb external drive that I'll have to find time to pick up this week. However, your post does not explain why this OS which can format a 4 and a 6 can't handle a 32.

I cannot understand "If flash drive used with Windows or as an installer it may have partition table issues." I'm not installing Ubuntu over a Windows OS; I'm working on an older 18,04 Ubuntu install. Where does Windows come into this? Two years ago we formatted a Dell Optiplex using a boot drive, is this now deprecated? Should we be doing the fresh install from the current OS instead? I am already aware that installing a fresh OS erases the data underneath.

I've read through the your linked post about rsync. It appears to be about creating manual backups for your data (and a bunch of it is, literally, "Greek to me"!). I guess that's an option, if I can't use cp to make a copy of my home directory. I'll do some experimenting with rsync next week to see if that might help towards a solution. Rsync is however seven pages in my Linux manual, way more complex than cp, & it will take some time to learn it. When all I want to do is make a copy of my home folder to an external USB drive!

Let's say I've used rsync to backup my complete home folder to an external drive, and it's time to "restore" it to the new 22.04 OS that I've installed. What is the command / structure that will restore my home folder data from the external drive to my new home folder?

---

### Post by yancek on 2024-10-17
>  FAT32 because that was the formatting option that was suggested as Linux OS compatible by the operating system I'm using

FAT32 is recommended to use when creating a bootable usb on which to put a LInux iso to use as a 'live' system and/or installer.  If you are copying data from a partition with a Linux filesystem, copy it TOO a partition with a Linux filesystem.  The default for Ubuntu has been ext4 for years.  You can get that information for your partitions with the command below:

```
lsblk -f
```

If your /home partition is ext4, then create a partition on which you wish to back it up as ext4.

>  Should the "/home" argument be followed by /*

Yes.

---

### Post by oldfred on 2024-10-17
FAT32 is intended for smaller partitions. It still is used for the ESP - efi system partition. As that is used by all UEFI based systems. FAT32 then is also required for the live installer, so it can boot in UEFI mode. 
Microsoft for some reason has a .wim file in its ISO that is too large for FAT32, so it cannot be directly copied into a FAT32 drive for required UEFI install. The Windows install tool splits the .wim file. Some other work arounds also exist.

But any other Windows format is not recommended unless also running Windows as chkdsk & defrag are periodically required and can only be done from Windows. Linux cannot fix any or maybe only a few Windows issues.

---

### Post by TheFu on 2024-10-17
Just buy a 2TB external USB HDD. They should be $40 and provide more than enough room.  When you are all done, you'll have storage for weekly backups for at least a year.

Oh, and use native Linux file systems, not MS-Windows file systems - so don't use FAT32, exFAT, NTFS.  Choose ext4 if you don't have a specific reason to choose any other file system for use on Linux.

---

### Post by rudy5 on 2024-11-05
I've been in sick bay, and have had to take a break from this.
Back this morning, & spent about 30-40 minutes studying this thread & making notes. 
The first step (and I'm still on it!) is copying the contents of my /home folder to an external drive. Previously I lacked a big enough flash drive (32gb not enough), and anyway it was formatted wrong. So, I went out and purchased a couple of 64gb flash drives.
Stuck the first one into a USB port, and proceeded with a quick format to the desired ext4 format.
Started copying .. . but ran out of room! After copying an unknown part of my /home contents, the command returned a string of error messages all ending in "No space left on device."
My diagnosis is that I probably should have emptied the trash before proceeding. So, I decided to go back and start again.
Easiest way to delete whatever did end up on the flash drive is a quick re-format. So I opened the GUI, selected my external drive, & initiated the same formatting command that I had ten minutes earlier, WITH ONE FATAL? DIFFERENCE: I selected the "check for bad sectors" option. The formatting screen disappeared, and so did the GUI listing of the drive I was formatting.
It's been 45 minutes. The flash drive is a bit warm, but I have no indication of any activity by this computer. Safe to say it's failed?
I don't have a lot of faith in this GUI either. Can I just use the terminal to format my external drive? Will this do the trick?

$sudo mkfs -ctv ext4 /dev/sdb1 

Please advise if this command from terminal will give me a 64gb ext4 format flash drive.

---

### Post by rudy5 on 2024-11-05
Because, here's what happens when I enter

$ sudo mkfs -ctv ext4 /dev/sdb1

.. . generates .. .

mke2fs 1.44.1 (24-Mar-2018)
mkfs.ext2: invalid blocks 'ext4' on device 'mkfs'

So, obviously not the correct command. Could someone please advise? I can't make a formatted 64gb flash drive from this computer (Ubuntu 18.04).

Meanwhile, I gotta do some work. In a while I'll be driving across town where I can have a look at these two 64gb drives on another Linux (22.04) install, & see if that might offer some clues.

---

### Post by oldfred on 2024-11-05
My system on reboot makes flash drive as sda, so internal drive then is temporarily sdb.
Post this:
sudo parted -l

I typically prefer to use gparted to create partitions, so I can also confirm which drive is which.

---

### Post by rudy5 on 2024-11-05
Hi again Oldfred,
Disaster. After giving up on being able to format my 64gb drives as ext4, I packed them up, & tried to reboot the Dell with 18.04 .. . nothing. Nothing. Just the Dell logo, and a black screen. A couple of re-power-ups, same result.
I put my 22.04 install drive in the USB port, & re-booted .. . but 22.04 thinks my hard drive is virgin, no data. ***?
This means that until further notice, I don't actually have a computer at home; just this work one (with Ubuntu 22.04).
Is there any special command that I need to execute, is my data there but for some reason I can't see it from the Ubuntu 22.04 flash drive?
Anyway, for my next trick, I'm going to try to format these 64gb flash drives (ext4 format) from this 22.04 installation. Wish me luck.

---

### Post by rudy5 on 2024-11-05
Here's what happens when I re-start:
Dell logo. Disappears. Single line of text at top of screen:

UBUNTU: Clean, 496642/6553600 files, 25954163/26208768 blocks

.. .  and that's it. Nothing further happens.

How should I understand this?

---

### Post by rudy5 on 2024-11-05
PS --- This (work) Dell desktop / Ubuntu 22.04 can't see the 64gb thumb drives *at all*.

---

### Post by oldfred on 2024-11-05
Ubuntu: Clean is just a message saying it sees partition and has no reported issues.

UEFI or BIOS boot.
Can you get grub menu?
If only one install, menu does not automatically appear unless you change grub settings.
But if UEFI you can press escape, just after Dell logo & before grub menu normally appears. Timing may require several tries.
If BIOS, you hold shift key from Dell logo until grub menu appears.
And then can you boot recovery mode, or second entry in grub menu?

---

### Post by rudy5 on 2024-11-05
PS --- This (work) Dell desktop / Ubuntu 22.04 can't see the 64gb thumb drives *at all*.

---

### Post by rudy5 on 2024-11-05
I now have three flash drives -- a 32gb, and two brand new 64gb --- that I tried to format as ext4, *think* I formatted as ext4 --- certainly intended that --- and even tried to copy my home folder (= only 16 gigs, so I don't know why it wants 32gb space, and even "runs out of disk space" on a 64gb drive).
But I can't access / read this drive now either on my home Dell XPS13 / 18.04 (which now may be no more), nor here on this Dell Optiplex / 22.04 system. 
The Mac across the room can see the drives, but recognizes that it's a format it doesn't support.
The Windows machine across the room can see the drives, but recognizes that it's a format it doesn't support.
The Linus machines can't even get that far.
??

---

### Post by TheFu on 2024-11-05
You've been asked to run some commands and post the results here.  Until that happens, we are guessing and you don't want anyone, including yourself, guessing which partition has which data when you are running format/mkfs commands.  I fear the worst has happened due to a mistake.

So, boot from a flash drive and run those 2, requested, commands, then post the output back there and use the Advanced editor to post it all inside forum code tags.

What are the commands?  
```
  lsblk -f
  sudo parted -l

```

I used forum code tags (#) is the button to post those commands.  If your post doesn't look like that and make all the columns line up like they do in your terminal, then please fix it.

Is there a reason you keep trying to use flash storage for backups?  That's a terrible idea.  Spend the $40 and get a cheap, external, USB 2TB HDD that spins and is USB3.  You'll need to set it up with ext4, but after that, you'll have plenty of room for backups and probably won't need to replace it for 8+ yrs.

---

### Post by rudy5 on 2024-11-07
Hi TheFu, thanks for your reply, and patience --- I have only limited pockets of time to devote to this.<br><br>I cannot see anything about forum code tags (#) on my screen here.<br><br>Two parts: lsblk -f, and sudo parted -l. I shall deal with each in separate replies. The lsblk -f discussion:<br><br>From terminal, I ran lsblk -f on the 64gb external drive, which responded:<br>sdb1 = vfat<br><br>I switched back to the GUI file manager, selected the 64gb drive (which was visible under the manufacturer's designation, LEXAR 64GB. I launched the formatting utility, selected quick format to ext4, &amp; started formatting. After a few moments, the utility displayed the info that my re-named flash drive (Nv_5_24) was now formatted for ext4.<br><br>From terminal, I ran the following command:<br>$ sudo cp -prv /home/* /media/Nv_5_24/home<br>The terminal display indicated that files were indeed being copied over; but then a series of lines ended with the message "no space left on device".<br><br>When next I tried to use the GUI, and the ls command from terminal, I was not able to see the 64gb drive at all.<br><br>I repeated the same sequence, with a second 64gb flash drive, which I named Nv_6_24. Running the cp command as above, yielded the same set of error messages ("no space left on device"). <br><br>At this point, everything goes black. By which, I mean, my display. I powered down / up, This yielded the line at the top left:<br><br>UBUNTU: Clean, 496642/6553600 files, 25954163/26208768 blocks<br><br>I next booted from the Ubuntu 22.04 install drive I had prepared, and launched the file manager. It was not able to detect any files in the home drive. (But which home drive was it looking, the clean one on the flash drive, or my hard drive? Stay tooned!)<br><br>Before I proceed to the listed command &amp;c., activated Dell's UEFI boot screen, and selected Ubuntu/Linux 4.15.0-173-generic (recovery mode). This resulted in the UBUNTU: Clean &amp;c. message &amp; screen.<br><br>Still from the Recovery menu, I selected, one after the other, three boot sequences: <br>clean - returned the error messages I've been getting from running, apt-get fix, clean, &amp;c., previously: unmet dependencies, and the advice (previously and repeatedly attempted) to run fix-broken-dependencies.<br>dpkg - returned "Not enough free disk space."<br>grub - not sure what it did, no error messages at least so I'm guessing that simply executed the boot sequence; because the result (black screen) was the same.<br>I have reached my limit today, &amp; will return tomorrow to tell the story of the listed command. I hope in the meantime I can learn how to post stuff in those white boxes you all seem to be using.<br><br><br>

---

### Post by rudy5 on 2024-11-07
(Don't understand what just happened there. Try again .. .)

Hi TheFu, thanks for your reply, and patience --- I have only limited pockets of time to devote to this.

I cannot see anything about forum code tags (#) on my screen here.

Two parts: lsblk -f, and sudo parted -l. I shall deal with each in separate replies. The lsblk -f discussion:

From terminal, I ran lsblk -f on the 64gb external drive, which responded:
sdb1 = vfat

I  switched back to the GUI file manager, selected the 64gb drive (which  was visible under the manufacturer's designation, LEXAR 64GB. I launched  the formatting utility, selected quick format to ext4, & started  formatting. After a few moments, the utility displayed the info that my  re-named flash drive (Nv_5_24) was now formatted for ext4.

From terminal, I ran the following command:
$ sudo cp -prv /home/* /media/Nv_5_24/home
The  terminal display indicated that files were indeed being copied over;  but then a series of lines ended with the message "no space left on  device".

When next I tried to use the GUI, and the ls command from terminal, I was not able to see the 64gb drive at all.

I  repeated the same sequence, with a second 64gb flash drive, which I  named Nv_6_24. Running the cp command as above, yielded the same set of  error messages ("no space left on device"). 

At this point, everything goes black. By which, I mean, my display. I powered down / up, This yielded the line at the top left:

UBUNTU: Clean, 496642/6553600 files, 25954163/26208768 blocks

I  next booted from the Ubuntu 22.04 install drive I had prepared, and  launched the file manager. It was not able to detect any files in the  home drive. (But which home drive was it looking, the clean one on the  flash drive, or my hard drive? Stay tooned!)

Before I proceed to  the listed command &c., activated Dell's UEFI boot screen, and  selected Ubuntu/Linux 4.15.0-173-generic (recovery mode). This resulted  in the UBUNTU: Clean &c. message & screen.

Still from the Recovery menu, I selected, one after the other, three boot sequences: 
clean  - returned the error messages I've been getting from running, apt-get  fix, clean, &c., previously: unmet dependencies, and the advice  (previously and repeatedly attempted) to run fix-broken-dependencies.
dpkg - returned "Not enough free disk space."
grub  - not sure what it did, no error messages at least so I'm guessing that  simply executed the boot sequence; because the result (black screen)  was the same.
I have reached my limit today, & will return  tomorrow to tell the story of the listed command. I hope in the meantime  I can learn how to post stuff in those white boxes you all seem to be  using.

---

### Post by oldfred on 2024-11-07
Screen shots of code tags.
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

if you get no space left on drive, then you have more data than the size of the partition you are copying into.
Click on your flash drive to mount it & the partition you are copying from if not mounted & run this;
If not mounted it will not show use:
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

---

### Post by rudy5 on 2024-11-13
I'm back --- dealing with not just this, but also a kidney stone, which is causing me to miss some work / time.

Thanks for the tip about ```
 code tags 
```, I'll use these the next time I post here.

Meanwhile, I have encountered ANOTHER problem with my computer / setup: my computer won't power down at all now. ?!?

The computer has been running since I booked off sick on the 7th of November. The power button has no effect.

I can unplug the power source, but then there's the battery. What's a good way to deal with this --- unplug, let the battery run down, re-connect to power & insert my boot drive? (Which is what I've been working on since the boot-up failed on November 6.)

A clarification on the backup medium. "if you get no space left on drive, then you have more data than the size of the partition you are copying into," you say; but here's the thing. I have no more than 26gb of data on this drive that I'm trying to copy --- probably closer to 16gb, after I removed three instances of the Ubuntu 22.04 ISO that I'd placed in the trash (which the cp command was apparently also trying to copy onto my storage medium). 

The data could not be copied onto the storage drive ("not enough free disk space") whether I was trying to copy onto a 32gb drive, or a 64gb drive. I do have a 2tb drive now, for what it's worth. Wonder if I'll ever be able to use it on this laptop. The problem isn't the capacity of the media, but something else.

Here's another queer thing about this. I haven't mentioned the fact that I bought this laptop from Dell WITH UBUNTU 16.04 PRE-INSTALLED. Now, this model doesn't even show up on the Canonical site as a supported model. Hundreds and hundreds of Dell models supported, yes, but not the one I purchased with Ubuntu already installed. Could there be a hardware problem (too)?

---

### Post by rudy5 on 2024-11-13
After some trial and error, I was able to get the on-off switch to respond (!).

After even more trial and error, I was able to launch the flash drive with Ubuntu 22.04, by selecting a boot-up option I'd never selected (or even seen?) before: UEFI: Generic Flash Disk 8.07, Partiion 2. Ubuntu 22.04 loaded. From terminal, I entered

```
sudo parted l
```

and this is what I got:

```
Model: ATA SK hynix SC380 (scsi)
Disk /dev/sda: 128gb
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk flags:

Number    Start    End    Size    File system    Name            Flags
1    1049kB    525MB    524MB    fat32    EFI system partion    boot,esp
2     525MB    3747MB    3221MB    fat32    Basic data partition        msftdata
3    3747MB    111GB    107GB    ext4
4    111GB    128GB    16.9GB    linux-swap(v1)                         swap

Model: Generic Flash Disk (scsi)
Disk  /dev/sdb: 17.7GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number    Start    End    Size    File system    Name    Flags
1    32.8kB    5032MB    5032MB                   ISO9660    hidden, msftdata
2    5032MB    5037MB    5155kB                  Appended2    boot, esp
3    5037MB    5038MB      307kB                  Gap1           hidden, msftdata 
```

I *know* there's something there. The purple Ubuntu load screen with the row of bubbles loads at start-up, and re-appears when I shut down.

---

### Post by yancek on 2024-11-13
You mentioned in several of your previous posts that you had an were using to try to copy data to 64GB flash drives.  Where are they?  The parted output you posted shows a 17.7GB drive and a 128GB drive.  Is the 128GB drive the one you are booting from?  Are you using different drives now to copy to? parted shows the partitions and their sizes but it does not show data.  You can mount each partition and then run df -h to see how much data is there, what % of the partition is used.  If you have other drives you are trying to copy to you haven't posted any information on them.

---

### Post by TheFu on 2024-11-13
A **week ago**, I asked for 2 commands to be run.  Didn't think that was hard at all to run them and copy/paste the output back here.  Guess it is.  
All the storage devices should be at least connected to the PC, if not mounted (which would be better).

---

### Post by rudy5 on 2024-11-14
Hi, yancek.

The 64gb flash drives I was unsuccessfully trying to copy my data onto are sitting on my actual, legacy molecule-format desktop here. They are not at the moment plugged into either of the two USB drives on the laptop.

I booted from an Ubuntu 22.04 install disk, stored on a 16gb flash drive. (I earlier described this Ubuntu 22.04 install disk as being a 32gb drive, but this was incorrect.) It was from this flash drive / Ubuntu 22.04 instance that I ran parted -l from.

Can you help me parse the information returned? I'm guessing the disk it found at sda is my 128gb hard drive. Can you tell me what information lines 1, 2, 3, and 4 are telling me? 

Disk /dev/sdb would appear to be that flash drive.

Perhaps my next move in this diagnostic adventure would be to buy a USB hub, and connect all these devices to the laptop?

---

### Post by rudy5 on 2024-11-14
Hi TheFu,

Sorry I was late with my homework. Hard to do from a hospital bed : / . I did run the commands suggested, and posted the results in this thread, admittedly not right away. And yes, it *has* been hard. 

This saga began (in 2022!) with my inability to either update or upgrade my installation of 18.04. None of the fixes suggested by the error messages (apt-get update, upgrade, fix, clean, whatever, &c., &c.) were effective; all generated half a dozen to a dozen and a half error messages about broken depencies &c. At that point I decided to try to copy my data to a flash drive, install a fresh OS, copy my home data back over, & proceed. <--- Note that I've done this before, more than once; & as recently as 2022, on this Dell Optiplex / Ubuntu 22.04 install I'm working from as we speak. I've migrated several Linux installs since I began using Red Hat Fedora in 2005; I've upgraded or migrated from Ubuntu 6, to 8, to 10, to 12, to 14, to 16, and to 18, sometimes smoothly on the same machine, other times migrating my data to a new computer. (Yes, it's true, I'm stupider than I've ever been. But who isn't?)

I could not however copy any folders onto an external drive. Correction: the folders, yes, but none of the contents. This was the case whether I was working from terminal (with -r) or the GUI. I could copy individual files, but not folders; and so, I could'nt copy my Thunderbird profile, with my e-mail history. Nor could I copy my home folder. 

My last resort was going to be to individually drag over the files I really, really, really needed. But that's when I lost access to my hard drive & data. 

What does the fact that grub (I guess) displays the 18.04 launch screen, but then is unable to get past that to the actual OS? That purple screen isn't in the BIOS, is it? It's on the hard drive, right?

---

### Post by briandu2 on 2024-11-16
Just as a note: You state that you (@rudy5) have a Dell xps failure. Be aware that you may still have challenges since you may require dell drivers. Not helpful I know, but it may become an issue, so don't rush to format anything!

Having had a similar problem before (enough times), I booted on a Ventoy USB, where I placed the Ubuntu version (22.04 in your case?) and booted up from there.  Then reinstalled the OS BUT.......**did not reformat the drives** (so you do not lose your data!)

Alternatively, after Ventoy USB/Ubuntu boot up, then you can copy the data (usually the biggest drive/partition) to another usb based drive.  
You CAN mount the drives (once you booted up) from USB to lo examine where your home directory is (then you know which partition it is).  Use GParted and you can see the partitions on your drive so you can know which partition has your home.
Assume GParted states /dev/sda (with dev/sda1 and dev/sda2). 
Then, open a terminal and do the following: 
mkdir qaz
cd qaz
sudo mount /dev/sda2 .   (note the "." and the assumption is /dev/sda2 is the drive with your data.   [if not: then press cd~ and repeat the process with zaq instead
In either case above, you will be able to see your home directory   (BTW qaz or zaq are arbitrary names)
Once you haver mounted the drive above, you open the file manager to go directory qaz and see if your home folder is there. (Rinse and repeat as zaq etc. as necessary)

I suggest that when you get to gparted then post the sizes of the partitions i.e. /dev/sda1. /dev/sda2......./dev,sdb1, /dev/sdb2......  That will certainly help.
PLUS you have verified that /devsda2 is your home directory (or whichever it is -assuming you did the terminal work as described)

Whatever you do  - do not format a partition, otherwise game over for you.
Lastly, you are using linux, it is very rarely that you cannot get out of the hole.  Just steady nerves!!  Especially when you a newbie!!! I remember my time sweating bullets!

---

### Post by rudy5 on 2024-11-18
Hi briandu2, thanks for your detailed reply.

AFAIK, my XPS-13 is up to date in terms of Dell drivers &c.; I remember watching these get checked and updated by the BIOS back in September, early on in this adventure. 

```
Having had a similar problem before (enough times), I booted on a Ventoy  USB, where I placed the Ubuntu version (22.04 in your case?) and booted  up from there.  Then reinstalled the OS BUT.......**did not reformat the drives** (so you do not lose your data!)
```

Are you saying that re-installing the OS overtop an existing OS will leave the old home directory untouched, i.e., the data intact?

One of the options offered by the Dell boot-up menu is to revert to the shipped setting, which was Ubuntu 16.04. Do you have any knowledge or views about what will  happen if I select this --- will I end up with an Ubuntu 16.04 operating system, with my October 2024 home folder?

There's more (and I have to do a bit of further studying), & am meantime much obliged for your answers to these queries!

---

### Post by oldfred on 2024-11-18
With my Windows Dell system the reinstall of the Dell image totally reverted system to as purchased all my data was gone. 
Not sure then with a Linux system whether it checks the format box or not on install. I would expect it does.

You can reinstall to same / (root) but not check format. You never check format on a separate /home partition.
Your files then are not changed, but if you modified system files (like grub) those would be the original default settings.

Benefits of a release-upgrade (over clean install) by guiverc, but I prefer clean install & restore from backup
[https://ubuntuforums.org/showthread.php?t=2501145](https://ubuntuforums.org/showthread.php?t=2501145)
Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) & 
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)
[https://ubuntuforums.org/showthread.php?t=2496620](https://ubuntuforums.org/showthread.php?t=2496620)

---

### Post by him610 on 2024-11-19
> Is there anybody with sufficient knowledge of Ubuntu linux, and the Dell XPS-13, living within ca. 150km of Vancouver, B.C., to undertake this task for me?
Are there no Linux User Groups (LUG) in the Vancouver, BC or Washington State areas that could provide some assistance on your issue?

---

### Post by yancek on 2024-11-19
Linux User Group in Vancouver at the link below.

[https://vanlug.ca/](https://vanlug.ca/)

Doing an install of 22.04 WITHOUT formatting would seem to be the simplest solution.  I did it twice in the last month on a different Linux distribution and there's no reason it would no work on Ubuntu.  Nobody is going to guarantee anything obviously as it easy for a user to make a mistake.

If the drive in question is sda which you posted above with 4 partitions, leave sda1 along as it will be used for EFI boot files.  Since you don't have windows you can delete sda2 and use that 3GB for your / filesystem partition or create another small data partition.  When you get to the point of selecting partitions, select sda3 for the / mount point for the filesystem and make sure you do NOT select to format that partition.  That has always been an option with Ubuntu installs but I have not done a clean install of 22.04 so...?  You an leave the swap partition, no need to change anything.

The link below explains the installation.  It is the ubuntu.com site and you can find instruction on the installation on the menu on the left, Section 6, Type of Installation.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

---

