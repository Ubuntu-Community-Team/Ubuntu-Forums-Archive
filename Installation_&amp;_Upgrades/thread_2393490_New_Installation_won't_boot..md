---
title: "New Installation won't boot."
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by A Traveller on 2018-06-04
Hi all.

I have just installed Ubuntu 18.04, however, it won't boot and I think it could be the way I have prepared the hard drive as I am not very knowledgeable on that subject, like most Ubuntu technical subjects. The following is what I did and I was wondering if anyone could spot something silly that I may have done and possibly suggest a solution.

Completely wiped the drive with DBAN.

In GParted, I did the following:

Formatted the 'Free space preceding (miB)' to ext 4, as a Primary Partition and allocated 8Mb to it. It wouldn't let me do just 1Mb.
Formatted the 'New size (miB)' to ext 4, as a Primary Partition and allocated 144Gb to it.
Formatted the 'Free space following (miB)' as linux-swap and allocated 8Gb to it.

Ubuntu Installation:

To install, I chose 'something else'. After all these years, I see they still haven't made it clear if 'alongside' means on the same disk as your other Ubuntu only or on a different disk to your other Ubuntu also. Anyway.....

dev/sdb3, ext4, 328 Mb, used 1mb
dev/sdb1, ext4, 151641 Mb, used 2576mb
dev/sdb2, swap, 8389 Mb, used unknown
freespace, 2Mb

For installation type, I chose dev/sdb1, ext4, 151641 Mb, used 2576mb.
For device for boot loader installation, I chose the partition I created for GRUB, i.e. dev/sdb3, ext4, 328 Mb, used 1mb.

During the installation process, I got presented with the usual two errors which I usually get about no root file system and something else, which I address by doing the following:

Double-click on the relevant line and choose ext4 and the forward slash on its own from the drop downs.

I also get a message telling me that the "following will be formatted: partition #5 on sda". Why is it messing with my other hard drive? It also tells me that partition #3 on sda will be formatted, which I assume would be for GRUB.

Anyway, the installation completes successfully, but, as the subject line states, it does not boot. No error, etc, just stops at Verifying DMI Pool Data...AMD Data Change...updating new data to DMI.

The MD5 and SHA256 both check out.

I have also tried adding bios_grub and boot flags to the first partition, but that didn't work either. My plan now is to reformat the drive, omit the first partition created for grub and just let all the grub stuff be done in the main partition, as how I have always done it before. Unless, anyone can offer any simpler advice.

Thanks.

---

### Post by A Traveller on 2018-06-05
Update. Managed to partially solve the issue by deleting all the partitions and creating the first boot partition as empty instead of ext4. This did the trick, along with setting it as a BIOS Boot Partition/bios_grub flag and reinstalling Ubuntu.

Now I actually get to the Ubuntu dots screen and nothing happens, just like over a year ago when I gave up and decided to try again when any bugs had been fixed. Don't believe the same problem still exists and I will have to go the annoying task of working through the following sticky thread!!!!! Thankful there is somewhere to turn though!

[https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by oldfred on 2018-06-05
You never install grub to a partition.

If BIOS boot you want to install grub to same drive as install. It defaults to sda or first drive if NVMe or MMCblk type. So if more than one drive you have to use Something Else as that is only option that gives choice on which drive to install grub.

Also if you use the newer gpt partitioning, you have to have a 1 or 2MB unformatted partition with the bios_grub flag.  With Ubuntu you can use gpt whether old BIOS system or newer UEFI system.
I started converting drives to gpt back in 2010 with my BIOS only system.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by A Traveller on 2018-06-05
Sorry, oldfred, I misunderstood the information I came across regarding the 1 or 2Mb partition. I thought it was for bootloader/grub files or something.

Anyway, thanks for pointing that out.

Yes, this is the first time I am using gpt.

Before I embark on the giant thread, I thought I'd give the instructions at the following a try in case it might fix the problem, however, that didn't go too well! I now get the following error every time I boot to my main drive.

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

(following on from the following page)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

"Serious errors were found while checking the disc drive for /boot".
Press I to ignore, S to skip mounting or M for manual recovery.

Luckily for me, if I press S to skip, I am able to login as normal. The error never goes away and Ubuntu never does anything to try to fix the error, so I just have to put up with it. I find it very annoying how Ubuntu keeps wanting to mess with my main Ubuntu drive when I'm trying to deal with the new one. This is why I usually disconnect my main drive before dealing with the new install (18.04), but stupidly kept it connected this time. Dear Mr. Ubuntu, leave the other drives connected to my pc alone. I will tell you if I want you to mess with them!!!! If I want to install Ubuntu on drive x, focus on drive x only!!!

---

### Post by oldfred on 2018-06-05
Do you have a separate /boot partition. That is not required with most desktops, but is often used with LVM or LVM with encryption.

Have you run fsck? New systems just look to see if partition is flagged needing fsck, but does not normally run it.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by A Traveller on 2018-06-06
Hi oldfred.

Well I hadn't planned on having a separate /boot partition but read at the page linked to before that "Some computers can't see boot files (/boot) if located far (>100GB) from the start of the disk. This is why it is sometimes necessary to create a separate /boot partition at the start of the disk." So I thought I'd give that a try.

No, I have not run fsck. Thank you for your instructions. I will try to follow them after I have managed to solve the problem with the 18.04 not booting as I am just very happy that the 10.04 is still working despite the errors and don't want to touch anything that might upset it at the moment. I think I might print out the advice in the giant sticky thread so that I can follow it now. As far as I know, my system should more than capable of handling the latest Ubuntu.

Thanks.

---

### Post by oldfred on 2018-06-06
I retired my 2006 laptop and it last had 12.04 on it.
Just to see how it worked, I installed 16.04 on it and it seemed like it worked better. :)
Have not tried 18.04.
I do use full Ubuntu but then install the fallback or gnome-panel. The gnome-panel is more like the old gnome you have in 10.04 and is more lightweight.
Some of the other lightweight versions also are more similar to the old gnome in 10.04.

The far from start of drive was an issues with very old IDE based systems. But some that had IDE, not AHCI in BIOS seemed to replicate that issue.
My solution always is to use a 25GB / (root) partition at beginning of drive. Then all the boot files will always be in the first 137GB of drive. And I use rest of drive for data, or you can use as /home.

---

### Post by A Traveller on 2018-06-09
Thanks for the explanation, oldfred.

As planned, I have started working through the giant sticky and the following is where I've got to so far.

The sticky asks, Are you having these problems?...stuck at splash screen...

YES.

Step 1 asks,  Do you have a Grub Menu? and if Yes: Go to step 2... 

YES.

Step 2 asks Does the Linux Kernal boot?

I don't know how to tell. I've tried both steps 3 and 4.

Step 3:
I have accessed Recovery Mode via Advanced options for Ubuntu and booted throught that, however, I can't recall what the exact outcome was. I think it was the black screen where it shows e.g Mydisk: clean, 141721/9281536 files, 1690715/37108886 blocks or list of processes undertaken and then going nowhere.

When I tried entering something by dropping to a command line (not sure the exact name) from the Recover Mode menu, I got the following:

Press Enter for maintenance
(or press Control-D to contnue):
root@mycomputer:~# gedit /etc/default/grub
Unable to init server: Could not connect: Connection refused.

(edit 1595): Gtk-WARNING ##: 14:05:22.445: cannot open display:
sudo: unable to stat /etc/sudoers: Permission denied (not sure if it was a spelling error, but 'stat' was spelt exactly that way)
sudo: no valid sudoers sources found, quitting...
sudo: unable to initialise policy plug-in
root@mycomputer:#~

Step 4 asks Can you boot a graphical XSesion from a text console session? From the command line type
Code:
sudo service gdm start # substitute "lightdm" when appropriate

I am able to get to the 'GRUB_' prompt, however, I don't recall the exact words but it says that it doesn't recognise the command or something like that for anything that I type, including 'sudo'. I've tried:

sudo service lightgdm start
service lightgdm start

As I tried over a year ago, in the edit screen, I also tried to replace 'quiet splash' with 'nosplash' and 'nomodeset', as well as removing 'vt_handoff'. I didn't have an '=7' as shown in the sticky, however, same result as before.

As per the sticky, I tried 'nosplash --verbose text', however, still the same. Please see below for some of the failures I manage to catch.

Failed to start Network Name Resolution
Failed to start Network Time Synchronisation
Failed to start Avahi mDNS/DNS-SD Stack
Failed to start Accounts Service
Failed to start System Logging Service
Failed to start Dispatch daemon for systemd_networkd
Failed to start Disk Manager
Failed to start WPA Supplicant
Failed to start Login Service
Failed to start Modem Manager
Failed to start Thermal Daemon Service
Failed to start Network Manager
Failed to start Tool to automatically collect and submit kernal crash signatures
Failed to start GNOME Display Manager

Is it possible to carry on with the instructions in the sticky if the various command prompt screens won't accept anything? Also, none of the shortcut keys worked at any stage to bring up any terminal, etc. The only thing that worked was page up and page down, which helped me in writing down the errors/failures listed above.

I can access any of the files installed on the 18.04 hard drive from my other 10.04 hard drive. Could that be of any use?

Oh, and I also tried following the steps at the following link, but that didn't work either.

[https://www.onetransistor.eu/2016/03/plymouth-fix-nvidia.html](https://www.onetransistor.eu/2016/03/plymouth-fix-nvidia.html)

There was no file called 'spalsh', but created one and added the line framebuffer=y

Anything else I could do?

Thanks.

---

### Post by Dennis N on 2018-06-09
> I am just very happy that the 10.04 is still working...

Ubuntu 10.04 cannot run recent Firefox versions because Firefox requires newer versions of some libraries. The last version it can use is Firefox 45.0.2. So it is probably should not be considered safe to use on the Internet. But, Ubuntu 12.04 will run current Firefox. I have a 2005 Dell 6000 with an IDE drive that runs well with Ubuntu MATE 18.04 so there is life in those "old" machines.

---

### Post by oldfred on 2018-06-09
If not getting graphical IDE to start, you cannot use graphical tools like gedit.

If you want to edit a file several terminal editors are available. I use nano which is old school, you have to use arrow keys, but copy & paste does work, it just copies to where cursor is, not where you want to paste it.
sudo nano -B /etc/grub

Normally if you boot in recovery mode, you can log in. But you were at root?
If your do not have your user in /etc/sudoers, it may be install is not correct or you just did not log in?

---

### Post by A Traveller on 2018-06-09
Thanks for your comments, Dennis N.

I'm not using 10.04 out of choice! It is beyond annoying now that many websites cannot be viewed properly and a lot now cannot even load at all (connection/certificate/various errors). The functions don't work on a lot of these sites as I can't update flash/java, etc.

My pc may be a few years old, however, the specs are still quite good and more than enough of handling the latest Ubuntu, etc. I need to install a recent OS as soon as possible before the 10.04 stops letting me do anything at all! I know it's based on Ubuntu, but I am thinking of trying Zorin to see if I can at least log in! Might try Lubuntu also but if Ubuntu doesn't work, not sure if Lubuntu will.

Thanks oldfred, no login as yet at any point. Not sure if I was "at root".

I have installed more than once and considering the same problems when I tried installing a year ago, I don't think a bad install could be the problem.

Will try sudo nano -B /etc/grub when I manage to muster some motivation to get going again!

Thanks.

---

### Post by A Traveller on 2018-06-11
I get the following when I tried sudo nano -B /etc/grub at the GRUB screen and in recovery mode.

GRUB screen:

Can't find command 'sudo'

If I leave out sudo, I get@
Can't find 'nano'

Recovery Mode:

root@mycomputer:~# sudo nano -B /etc/grub
sudo: unable to stat /etc/sudoers: permission denied
sudo: no valid sudoers sources found, quitting...
sudo: unable to initialise policy plug-in
root@mycomputer:#~

I also tried choosing the option to fix dpkg in Recovery Mode, which informed me that 5 new packages are going to be installed and 81 packages are going to be upgraded but when I accepted, I got 'could not resolve gb.archive.ubuntu.com' and 'restoring original system state'. I then tried enabling networking, however, now I cannot even get to a grub screen any more. It just stops at the black screen just before it says booting from CD/DVD (which is my first boot device). It doesn't even show booting from CD/DVD any more. It just stops before that. UPDATE - am able to access GRUB/Recovery Mode again and tried fsck. Noticed the comment 'etc/default/rcs no such file or directory'. The check took only a few seconds and stopped at [ OK ] Reached target Swap. Is that normal or am I supposed to leave it for a few minutes?

I'm wondering if Ubuntu is worth all this effort.

Thanks.

---

### Post by A Traveller on 2018-06-12
I have now tried installing Lubuntu but get the exact same problem, i.e. stuck at the Ubuntu screen with the dots (blue instead of purple, this time).

I have now also tried installing Zorin, but it's the same problem as when I installed Ubuntu 16.04 a year ago; stuck in the black screen login loop. I have tried nomodeset and nosplash for this but that hasn't worked. Am getting the same failures as with Ubuntu 18.04.

Surely, SOMEONE must know what the Ubuntu people have changed between 12.04 and 16.04 that is causing these problems for so many people!

---

### Post by Dennis N on 2018-06-12
```
Recovery Mode:
root@mycomputer:~# sudo nano -B /etc/grub
```

Choosing **Recovery mode > root shell prompt** makes you root, so sudo should not be used. Then nano will work.
Then, **/etc/grub** is not the correct location for the grub settings, which I assume is what you are after. It should be **/etc/default/grub**.

---

### Post by A Traveller on 2018-06-13
Thanks for your suggestion, Dennis N.

I followed your instructions and got the following errors:

Unable to create directory /root/ local/share/nano/: no such file or directory.
It is required for saving/loading search history or cursor positions.

I then pressed Enter again just to see if I can get back to the root@mycomputer and then the nano grub settings appeared (the one with the hidden timeout and grub_gfx mode - 640x480, etc) but I couldn't change any of them. I got the errors:

Error writing etc/...read only file system

and

File 'etc/default/grub is unwritable'.

I also tried 'service gdm start' again whilst I was in nano and got the comment:

Starting GNOME display manager...
and then an error that the above failed.

I also disconnected my monitor from my nvidia graphics card, removed the card from the pc and attached the monitor to the onboard graphics (ATI Radeon HD 3000 graphics DirectX10) but this made no difference at all. Not sure if this needs to be tested by installing the OS after changing the graphics connection.

Thanks.

---

### Post by Dennis N on 2018-06-13
> File 'etc/default/grub is unwritable'.
Right. Because the file system state is 'read-only' as the warning says at the top of the recovery mode menu. That's how it starts up. If you plan to edit files in recovery mode, see step 8 of "Booting into recovery mode" in this wiki article:

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by A Traveller on 2018-06-16
Thank, Dennin N. Yes, I have come across that webpage before. I did vaguely recall that I had read something to do with making something writable, but wouldn't have known where I had read it as I have now read info from what seems like a million different websites now in trying to fix this. Anyway, for the moment, I am going to try another OS that is not based on Ubuntu/Debian because I really have had enough of trying to solve this problem for over a year and getting nowhere. I need an up to date OS because the software on my main Ubuntu 10.04 has become very restrictive (mainly for the Internet). Anyway, thank you very much for all your help. I might need it again if I revisit this issue! There is one thing that I have come across AFTER having deleting Ubuntu 16.04, which I did not get to try. Maybe I could try that with 18.04 also. It was related to editing/deleting an xauthority file. Sounded promising, but am not holding my breath! Thanks again, Dennis N/oldfred.

---

