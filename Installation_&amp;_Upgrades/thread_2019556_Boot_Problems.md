---
title: "Boot Problems"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by lionelt on 2012-07-05
Hello everyone!

I post here because I have a nearly similar problem to cirrus's since 2 weeks now, and I searched quite much to solve it. 

I'm working on a Asus eeepc type netbook, 2 Go RAM, intel atom processor  and nothing special otherwise, dualboot with windows 7 (I never used).
I have updated precise pangolin some months ago, and everything was working fine, but one day I had the following:
- When starting without an USB flash inserted, I get the megatrends  blabla, and then when usually the GRUB appeared, it just says "read  error..." on a black screen (nothing more).
- I can enter the BIOS, change boot prioritys, so that's what I did.
- Starting with an USB flash on which Ubuntu 12.04 64bit is installed  (as my previous version) it took some time to finally show the userinterface (after 2 hours of "loading ubuntu") 
"Disk utility" shows my partitions, windows and ntfs file system to the left, 221GB ext4 files + 2GB Linuxswap in the middle and ARGH! and "unallocated space" to the right, with NOTHING in it! There used to be my ubuntu there! 
In the /media I find a 10 GB filesystem with ubuntu folders (bin, boot, sys, tmp, usr etc...) but they are not those I had on the disk...  (and those 10 GB are not those of the stick as it's 4 GB large)

My question:
1) Do you believe my preferences and installed programs are lost? (have I lost my ubuntu system?)
2) How did this happen? The first time I tried to boot from stick, I shut the computer down (I/O button) while it was loading Ubuntu, because stupid as I was I thought it couldn't take so long (2 hours!) and that it was probably hanging... Was this the error?
3) If yes, how could I prevent it in the future?

Thanks very much for your help, I'm so glad this forum exists and you cannot realize how hard I love you for all the work you do it's just amazing!

Lionel

---

### Post by lionelt on 2012-07-05
Sorry guys I think I just found the disk system data... Under Devices 10 GB FileSystem XD

(I was a little bit confused forgetting I was booting from USB flash)

1) Now should I use one of the commands those two sites advise? (I didn't find an english page, but as my mothertongs are german and french... however i would be pleased if you knew an english page for this kind of problem: restauring grub2 when unable to boot from disk)

[http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub](http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub)
[http://wiki.ubuntuusers.de/GRUB_2/Reparatur](http://wiki.ubuntuusers.de/GRUB_2/Reparatur)

2) I just saw that the disk filesystem didn't have the folder called rofs, is this somehow important?


Lionel

---

### Post by oldfred on 2012-07-05
As mentioned above, Boot-Repair.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

And all the links in drs305 signature in his post above. He has posted more good info than just about anyone and before there were grub2 manuals.

---

### Post by lionelt on 2012-07-05
Thanks so much for your response!

I found those two and felt bad that I said I didn't find antyhing in english but I didn't want to post more to not annoy everyone:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
[http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html](http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html)

I tried geekmitra's one but it didn't work for me, "failed to run command '/bin /bash': No such file or directory" after having typed "sudo chroot /mnt"

I'm gonna try the boot repair software then, as apparently it also works from live usb! =D

Btw I noticed that I have two "linux" partitions, i already noticed this before I don't know where it comes from, one is big 210 000 000 blocks the other little 10 000 000 blocks .

 Best regards, 
Lionel

---

### Post by lionelt on 2012-07-05
Hello!

Software sadly didn't work so here is my pastebin link:
[http://paste.ubuntu.com/1076590/](http://paste.ubuntu.com/1076590/)

I still get read error and I don't know what to do...
Would it be possible to save the system files (i mean the files of programms and preferences etc... hope they are called "system files") to a stick, reinstall ubuntu, and than paste the folders in the /media, instead of those that are there?

Thanks!
Lio

---

### Post by YannBuntu on 2012-07-05
hi Lio
> **lionelt said:**
> [http://paste.ubuntu.com/1076590/](http://paste.ubuntu.com/1076590/)

the problem is:
```
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!
```

---

### Post by lionelt on 2012-07-05
> **YannBuntu said:**
> hi Lio


the problem is:
```
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!
```

Hi YannBuntu!
Do you think this is preventing the GRUB?
Problem is I still don't know how to get into windows, as I don't get into a system choise program. Only way for me to use the laptop is the stick with Ubuntu (and this takes around 2 hours to start =P )
Otherwise, I don't need windows, so maybe do u think the problem could be solved if I clear the windows partition, leaving only Ubuntu?

Thanks so much!
Lio

---

### Post by oldfred on 2012-07-05
The 100MB sda1 Windows boot/repair partition does look corrupted. You need to run chkdsk on that partition first. That is unusual as it is a small partition and only used to boot, so corruption is very uncommon. Your sda2 Windows partition also is not showing the third Windows boot file (winload.exe). Sometimes that is other partition type errors. Can you mount from Ubuntu and see if that file is really there in the Windows folder/path shown below?

Boot files:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD     /Windows/System32/winload.exe 


What takes 2 hrs to boot, USB? That still is very long. How much RAM do you have?

Other than the Windows sda1 corruption, install looks normal. It does not look like you are mounting the Windows sda1, so that should not be the issue. But I am not sure what grub does in checking other partitions as part of its boot process.

---

### Post by lionelt on 2012-07-06
> **oldfred said:**
>  Can you mount from Ubuntu and see if that file is really there in the Windows folder/path shown below?

Boot files:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD     /Windows/System32/winload.exe 



Hello again!
I recon it's probably quite early in the morning in the us right now =P

1) I don't know how to search for the files... In fact, when I try to mount the windows system reserved through "home" user interface, I get this message: 


[SIZE=1]"Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error [/SIZE]
 [SIZE=1]Failed to read of MFT, mft=6 count=1 br=-1: Input/output error [/SIZE]
 [SIZE=1]Failed to open inode FILE_Bitmap: Input/output error [/SIZE]
 [SIZE=1]Failed to mount '/dev/sda1': Input/output error [/SIZE]
 [SIZE=1]NTFS is either inconsistent, or there is a hardware fault, or it's a [/SIZE]
 [SIZE=1]SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows [/SIZE]
 [SIZE=1]then reboot into Windows twice. The usage of the /f parameter is very [/SIZE]
 [SIZE=1]important! If the device is a SoftRAID/FakeRAID then first activate [/SIZE]
 [SIZE=1]it and mount a different device under the /dev/mapper/ directory, (e.g. [/SIZE]
 [SIZE=1]/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation [/SIZE]
 [SIZE=1]for more details."[/SIZE]

(Seems to be exactly as you told me...)
I'm not sure how to search the boot files from the terminal, should i go root and "sudo -s"  ?

2) Well maybe I exagerated a little bit it maybe takes just 1 1/2 hr to boot... What I have observed since the problem began:
I've in fact lost a little bit RAM, but I still have 1.9 GB which should be ok XD
Windows usually also is in the first disk drive "hardwarely", and windows seems to have the problem. 
The problem with "read error" began the day I plugged my computer in a TGV (french train) plug which didn't work... My little computer architecture knowledges let me ask: *MAYBE* did this cause a hyper tension when the train started and burned some components (as both 1. RAM bar and this part of hard disk are the first to be under tension)? (sadly my computer wasn't on at this moment, I only tried to put it on when the train was already rolling...)

Thanks very much for your help!
Lionel

---

### Post by oldfred on 2012-07-06
The system reserved is the  partition with the corruption. But sda2 is your main install and has the rest of system. You should be able to mount it in Nautilus and drill down and see files & folders.

You will need a Windows repairCD or USB to run chkdsk on your sda1 partition. And maybe other repairs. You cannot run chkdsk from Ubuntu.

---

### Post by lionelt on 2012-07-06
Hello again!

I tried some little things I saw on other websites, but didn't work...
I've decided to simply delete windows, should be working this way...
But I firstly wanted to ask: 
If the problem with windows was linked to a hardware problem, do you believe that if I tried resizing a partition to the partitions left by windows, it could make those partitions I resized unreadable?

I also believe I've lost all my data, trying to install grub on all dev/sda partitions, and as it didn't work it crashed, and in one of those partitions (dev/sda6) was my data... I don't know where it is anymore, cannot see it from the stick...

I see my extended partition (221 GB data, named dev/sda6) in disk utility, partition editor (gparted) and see that most of the space is used, as it was before, BUT I cannot access it... :'(
Do you think it is lost?

Thanks! =D
Lionel

---

### Post by oldfred on 2012-07-06
You can run e2fsck to see if that solves any issues in sda6.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors:
sudo e2fsck -f -y -v /dev/sda6

---

### Post by lionelt on 2012-07-06
Hello!

Thanks for the response!
On my life session the disk partitions seem to be mounted per default (the session hasn't started it's still launching (those famous 2 hours) but I'm foreseeing), do you think that just using disk utility and telling "unmount" for example will do it? 
What do you mean with swap off do you mean "unmounting" the swap partition I have on the disk?

[SIZE=1]Thanks again I'm sooo sorry for the time but it's just that my nerves are at an end it lost me so much time and I seem to have done a big error here so I've nearly got tears in the eyes because all this was so unecessary...)[/SIZE]

Lio

---

### Post by lionelt on 2012-07-06
Hey!

Yeah go everything back again! Oh this is such a relief thanks you SOOO much and thank all the ubuntu forums for their help!
One last question, before I try the suppress windows reinstall grub and boot, how to get permission to copy files from your filesystem (which I have repaired and now is mounted and yay I see my files!) I cannot make a nautilus file...

Lio

---

### Post by oldfred on 2012-07-06
Is this from liveCD. Nautilus should let you copy files.

If it is a permission issue, you can try this, but be careful not to move or delete any system files as you have Admin rights to everything.

gksudo nautilus

---

### Post by lionelt on 2012-07-06
Hello!

Sorry I don't get it I cannot find gksudo nautilus (alt+f2 -> gksudo nautilus)...
That I cannot copy the files has it maybe something to do that the external hard is formated ntfs? (no probably not =P)

Do you know how I could enter my user password to get acces to those files? Nautilus I cannot find sorry XD

Lio

---

### Post by lionelt on 2012-07-06
From live cd (usb) yes =D
I still haven't done anything about the windows and grub, so that still is the only way for me to access the files =P

---

### Post by oldfred on 2012-07-06
LIveCD has no password, just press enter.

Boot Repair also has some functions. I have not kept up with all the updates Yann has added.

---

### Post by YannBuntu on 2012-07-06
> **lionelt said:**
> Sorry I don't get it I cannot find gksudo nautilus (alt+f2 -> gksudo nautilus)...

- first open a normal Nautilus (file manager) and click on the partition (on the left panel) in order to mount it. If it does not want to display the files inside this partition you may need to : open a terminal (Ctrl+Alt+T), type "gksudo nautilus" to open another file browser with admin rights. This one should let you see and copy the files.

---

### Post by lionelt on 2012-07-07
Hello!

0) The rufs folder (in live usb / ) apparently mounts drives, so it probably is normal that I don't have it in my harddisk /
[rufs]("http://manpages.ubuntu.com/manpages/intrepid/man1/rofs.1.html")

1) The problem with nautilus (I may not have explained it well) was that when I first tried to open it gksudo, it gave me this: 
[SIZE=1]Nautilus could not create the required folder "/root/.config/nautilus".[/SIZE]
  [SIZE=1]Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.[/SIZE]
So I followed this link: [http://ubuntuforums.org/showthread.php?t=1531820](http://ubuntuforums.org/showthread.php?t=1531820)
And finally I could copy the files to an external hard disk! =D

2) Then I destroyed the windows ntfs partition with gparted.

3) Then I retried to reinstall grub, but apparently it had errors. And I still cannot start the computer. It may be linked to the "hard" location of the partition on the disk: is it too far so that the BIOS cannot access it?

---

### Post by drs305 on 2012-07-07
Moved to own thread.

---

### Post by lionelt on 2012-07-07
> **lionelt said:**
> Hello!
[SIZE=1]
0) The rufs folder (in live usb / ) apparently mounts drives, so it probably is normal that I don't have it in my harddisk /
[rufs]("http://manpages.ubuntu.com/manpages/intrepid/man1/rofs.1.html")[/SIZE] 

1) The problem with nautilus (I may not have explained it well) was that when I first tried to open it gksudo, it gave me this: 

[SIZE=1]Nautilus could not create the required folder "/root/.config/nautilus".[/SIZE]
  [SIZE=1]Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.[/SIZE]

So I followed this link: [http://ubuntuforums.org/showthread.php?t=1531820](http://ubuntuforums.org/showthread.php?t=1531820)
And finally I could copy the files to an external hard disk! =D

2) Then I destroyed the windows ntfs partition with gparted. (edit:) and I destroyed also the system reserved windows with gparted

3) Then I retried to reinstall grub, but apparently it had errors. And I still cannot start the computer, gives me "read error". It may be linked to the "hard" location of the partition on the disk: is it too far so that the BIOS cannot access it?
**In gparted, are the partitions you see on the left those who are nearest to the begin of the disks? **(in fact my / is completely to the "right" in the visualisation of gparted)

6) In gparted, I have the problem that I cannot do anything to my / partition: I get: "daemon is inhibited" when I try to make "test"
**How could I move it to the left? I thought of copying it to the big partition that windows left on the left of the visualisation bar of gparted?**

5) I still don't know how I can launch the netbook without having to reinstall Ubuntu without deleting my "old" ubuntu, which was full of programs.
[SIZE=1]
6) "quiet boot disabled" just determines what is shown by the bios (little note for myself)[/SIZE]

Thanks very much!
I am sorry to ask you for a little more help... I thought I would have finished today but apparently not...

Lionel

---

### Post by oldfred on 2012-07-07
Post screen shot of gparted with paperclip icon in edit panel at top. You may have Linux in the extended partition which is also a primary partition.

Some old BIOS or newer systems with BIOS set in IDE legacy mode and it seems a few others have issues booting from beyond 137GB. Start of drive is on left in gparted.

HOWTO: install Ubuntu on big disk (BIOS limitations)
[http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

---

### Post by lionelt on 2012-07-07
Thank you very much! 

I'll follow your thread and post a screenshot as soon as computer has restarted! 
One question to the thread: it shouldn't be a problem to move the whole / into the empty ext4 partition (80 GB) I created on the left, shouldn't it? If I copy the / partition into the latter one with gparted? (and reinstall grub (for the +/-10th time =P )) I'm asking this because I would dislike having separate boot and / partition...
And if this doesn't work well I'm lost 

Lionel

---

### Post by lionelt on 2012-07-07
Hello!

Okay here's my screenshot gparted (haha "paperclip" is a great word =D )! 
dev/sda6 are my files, 
dev/sda1 is the empty space left by windows, 
on the extreme right dev/sda4 with my /  (and a little swap + unallocated space)

1) I still had the question: it wouldn't be a great risk to copy the / to the sda1, deleting it on the left and installing grub in the sda1 would it?
2) How is it with saving files on your live stick? This isn't right is it?

Thanks very much for your help! Hope I can pay this back one day =D

Very pleased,
Lionel

---

### Post by oldfred on 2012-07-07
It is not particularly easy to move an install. You also have to reset fstab entries with new UUIDs and maybe some other settings. But you can.

I prefer to keep data separate from system, both for Windows & Linux. For most I suggest a separate /home, but I use a couple of separate data partitions as I have multiple installs and mount data in all of them. I do not try to share a /home.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by lionelt on 2012-07-07
I'm back again, because I still don't know what to do...

I copied my / into the sda1 partition and now I try to reinstall GRUB chrooting, following this thread: 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Problem is I cannot even mount:

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  donegives:
"mount: mount point /mnt/temp/dev/ does not exist"
same for   dev/pts  ,  /proc  ,  /sys

Shall I maybe restart the live usb because he cannot mount the sda1 since I changed it?  It's what I'm gonna do right now =)
(free boot still gives "read error")

Thanks you for everything

---

### Post by lionelt on 2012-07-07
Okay I believe I'm just going to reinstall ubuntu, this should be an easy solution! =)
I'll try to find where my firefox preferences and more complicate programs were located and put them back into their folder, if possible...

---

### Post by oldfred on 2012-07-07
You should not have to chroot but just reinstall grub with the two line quick version, and only if that does not work use the full chroot.
You also have to edit fstab with new UUID.

If a space or character  is off, the all in one line command will have problems.

You can chroot one line a time and see if one line gives an error:

sudo -i
mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /usr/ /mnt/usr
cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
chroot /mnt

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by lionelt on 2012-07-08
Hello again!

I tried what you told me but it broke at "mnt/dev"...

When I checked my sda1 partition (on which I wanted to copy /)  with  disk utility, it gave me this: *daemon is inhibited*[SIZE=1]
[SIZE=2]This is what I found considering "daemon is inhibited" , but I begin to think that it is purely a **hardware problem** as there seems to be no way of formating the beginning of my disk without problems...
[/SIZE]I had the same problem and reinstalled udisks in Synaptic.
The command below will do the same:[/SIZE] [SIZE=1]
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall[/SIZE] [SIZE=1]
Hope that helps.[/SIZE] 

And today I tried to install ubuntu from the stick onto this partition  sda1 but it told me that there were errors and I should try another  partition (in the installation window called "installation type"). 
Btw: the launching of the first installation window (language) nearly took 1 hour too, so there definitively should be a hardware problem somewhere)

If you think too that this could be the issue, I'm gonna open the machine finally and look a little bit (maybe the bios isn't linked well to the beginning of disk, or this one is "broken" or something...)
And don't worry I won't be even angry if it fails, I mean I cannot do anything since 2+1/2 weeks now so it cannot be worse :D

Thanks again for the help! I'm so grateful (even if nothing seems to work out =P )
Lionel

---

### Post by lionelt on 2012-07-08
[B]*Failed to unmount partitions*

[/B]I get this error message while installing: 

[I]The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:
/tmp/tmp.ApT9nnNLen
Please close any applications using these mount points.
Would you like the installer to try to unmount these partitions again?

[/I]I believe it's probably that the partition sda1 I wanted to use to install / is at the same time the very partition mounted by the stick for installation (if such a thing exists)
Problem is I tried partitionning this partition sda1 but I cannot as something is wrong on it, so I don't know where to install my / as the whole idea was installing / on sda1...

Maybe that's why everything takes so long to start (live and install), it's actually that the beginning of the disk is corrupt (but not dead) and the usb live/installer looks for the partition and takes a long time to analyse it (when I was live usb, gparted and disk utility also took an eternity to start)

So this is getting nearer to a hardware problem I believe...

Lionel

---

### Post by oldfred on 2012-07-08
Try e2fsck on sda1 and see if that corrects any data errors. From Disk Utility and click on drive. In right panel is the Smart Status. Does it show green? All I really know is green is good, but it can do a lot of tests also.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by lionelt on 2012-07-09
Hello!

I did what you told me (e2fsck) on the free ext4 partition, it didn't work...
I searched a little bit and finally decided to delete the partition (with terminal, but gparted would have done the same probably), then REformat it again into ext4, and then your code seemed to make something! Disk utility told me the partition was clean!
Thanks very much for this! 

Now there even are 2 improvements: 
1) The computer starts way faster than before with live usb! (some minutes instead of 2hours)
2) I tried to install ubuntu on the free partition, installer crashed, BUT it seemed to do something at least =D. And now, when I start the netbook booting from disk, it doesn't show "read errror_" anymore but only the blinking "_"...

Well, it's a little improvement =P (I hope =P)

I btw am sure now that there is some physical error on the sda1 partition, as even after deleting it, it says that 5 GB ar used... I also tried fiddling a little bit making various partitions but sadly the 5 GB tend to divide up between the partition pieces, so I couldn't make an entire free partition...7

So thanks a lot oldfred for everything, I'll tell if it works again you are great anyway, thanks so much!
Lionel

---

### Post by lionelt on 2012-07-09
Hello again!

PROBLEM SOLVED!!!!

After deleting partition, reformating, redeleting, reformating, I saw that it enhanced the launch capacity of the computer, so after I time I tried to reinstall GRUB using the famous chroot method 
[Purge and Reinstall GRUB]("http://ubuntuforums.org/showthread.php?t=1581099")

So finally I believe that I just went past the problem, first deleting windows, than_ deleting partition_ (this seems to be the the most important step)  BEFORE reformating (this several times) and finally reinstalling GRUB!

Thanks so much this forum is so great I am flabbergasted!

Lionel

---

### Post by oldfred on 2012-07-09
Glad you got it solved. :)

---

