---
title: "Dual boot on twin drive machine"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by Barney-R on 2013-01-23
I'm trying to install Ubuntu 12.04 as a dual-boot with 10.10 (64-bit in case it's relevant).

I've got two hard drives, a 750GB with the operating system on it (not partitioned as yet) and a partitioned 1TB drive containing most of my files.

The trouble is that, though it recognises the existing 10.10 installation, setup **insists** on trying to install 12.04 to the larger drive. The smaller drive isn't even shown as being available unless I click on "advanced setup", where I'm completely lost. I don't understand most of what I see, and most of the options shown don't seem to be available anyway.

I want to try a **full** installation of 12.04 while keeping 10.10 in  reserve in case anything goes wrong or I change my mind, but I want both installations on  the same drive.

I don't want to physically disconnect the larger drive, and I'm not comfortable making changes in the BIOS, assuming I could disable (and then re-enable) the drive from there.

Any suggestions anyone? In case it's not obvious, I don't really know what I'm doing, so any help will be gratefully received.

---

### Post by oldfred on 2013-01-23
You have to use Something Else or the manual install option. Auto installs will either overwrite an existing or install to unallocated space but you do not necessarily know what it will do.

I prefer to partition in advance, but now you can partition during the install. And you want to be sure to install to the MBR of the drive you install to.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Barney-R on 2013-01-23
Thanks for that OldFred. There's some useful information in those links, but from what I've seen so far, it seems I **can't** have both versions on the same drive, which is what I want.

The second drive contains nearly 800 gigabytes (in 5 FAT32 partitions) that I don't want to interfere with.

I haven't yet partitioned the smaller (750GB) drive which has the operating system (Ubuntu 10.10) on it because I'm not sure how "safe" it would be using the Disk Utility. I'm still a comparative newbie, especially with the technical stuff, and don't want to damage anything (mainly my settings, software, etc.).

Firstly, can I **safely** partition the bootable drive using the disk utility, and secondly, would this make it possible to install 12.04 to that partition (on the same drive as the existing OS)?

Alternatively, have I completely misunderstood what you were telling me?

Just to clarify things, I want to have both versions on the same (smaller) drive.

When I installed Ubuntu in the first place, the installer "wanted" to install to the larger drive, but gave me the option to choose where I wanted it.

---

### Post by darkod on 2013-01-23
You said in your first post the 750GB is for the operating system, but not partitioned yet. Yet it seems it has 10.10 on it already. That's impossible if it's not partitioned yet.

You probably meant without created partitions for the new install, you should be clearer since not partitioned is a disk with no partitions on it.

Anyway, for advice on partitioning please post the screen of Gparted of the 750GB disk. We can help with more direct advice that way.

If 10.10 is taking the whole disk right now, you will have to shrink it and that always involves little risk.

---

### Post by Barney-R on 2013-01-23
I'll try to answer that.

I don't currently have Gparted installed (but I can get it if necessary). The Ubuntu Disk Utility shows a partition divided horizontally, The top part, which represents the OS, says "Extended 18 GB" and the lower part "18 GB Swap S... 18 GB".

The unused space is shown as "732 GB ext4".

Does that help?

Ubuntu 10.10 does currently have the whole drive to itself, which is wasteful, but as I said, I'm not very confident about playing with the technical side of things.

While collecting that information, I noticed a problem. I clicked on the "Extended 18 GB" partition (or perhaps that's not quite the right term), and received a message saying "Warning: The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested".

I installed Ubuntu onto a new drive after the original failed, so presumably setup "got it wrong". I haven't had any problems, so do I need to (move all my stuff off and) reinstall? I'd rather not have to do that yet if it can be avoided.

---

### Post by oldfred on 2013-01-23
Your extended partition currently just has swap. Do not use Disk Utility but gparted. gparted is on liveCD/DVD/Flash tha you will use to install.

I have many Ubuntu installs on my 640GB drive, so you can have as many as you can fit. I use 25GB for most installs, but have data in other partitions so every install can use the same data.

This is now older as I have used the unallocated and install 12.10 and 13.04 over some of the obsolete installs.

---

### Post by Barney-R on 2013-01-23
Thanks for all the advice, both of you.

I've been Googling, and some people say I need to create the new partition in advance, while others say I can do it during the installation.

I think I know what I'm doing now, but I'd appreciate some clarification.

1 - Am I right in thinking I don't need to create the new partition prior to running the installation CD?

2 - Could you clarify what I need to enter after / when I'm creating the new partition? Is it /boot or /root or something else, and does / need a space after it?

3 - Do I need, or will I have the option, to create a swap file? I've got 6GB of RAM, so any swap file will seldom, if ever, be needed.

As far as possible, I want to stay as close to a default installation as possible, and I've got plenty of HD space, so if it wants a swap file, that's ok.

Eventually I'll have a clear out and have just one OS, but for now I want to keep 10.10 in case I don't like 12.04 once I'm able to use it properly (full install).

---

### Post by oldfred on 2013-01-23
this is my standard suggestion, but it depends on whether you may want to dual boot either Windows or other Linux installs or save lots of data in separate data partition(s) and other factors. I do not use a separate /home but have all data from /home in data partitions, so my /home is just about only the hidden settings and being small is easy to backup.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Barney-R on 2013-01-24
Thanks for that OldFred. I'm not sure how much of that I understand, but I'll give it a try later today and see what happens. I've copied my Home folder to another partition, so I shouldn't lose much if it goes wrong.

Perhaps I'll make a full system backup first, just in case, as explained here.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by darkod on 2013-01-24
You can forget about creating new swap partition if you already have another ubuntu version installed. It will use the same swap area. Just remember not to delete it if you decide to delete the other ubuntu version one day.

As for creating partitions, you need basically two.
For the main root partition, create one primary partition of 25GB at the beginning of the unallocated space, filesystem ext4, mount point /.
Then from the rest of the unallocated space create another primary partition, ext4, mount point /home.

Install the bootloader where ever you want, the 750Gb disk for example. Make sure you select the disk, like /dev/sda or /dev/sdb, not a partition (there should not be any number). And remember to set in bios to boot fro mthat disk first.

That's it. The above assumes you will use the existing swap. If you don't have any right now, just create it as third partition. The swap partition is type swap area and doesn't have a mount point.

---

### Post by Barney-R on 2013-01-25
Thanks for all your help, and apologies for not getting back to you sooner. Things have been rather busy here, so now I won't be attempting the install until next week.

I think I understand enough of what you've told me (plus the helpful links), but I won't mark the thread as solved until afterwards in case I need to ask for clarification on anything.

Thank you both.

---

### Post by Barney-R on 2013-02-13
Sorry. Got "called away" for a couple of weeks.

I've been having a few issues with disappearing repositories ("untrusted source" and 404 "not found" messages), so I've decided to forget about dual-booting and go for a clean install of 12.04.

I just need to ask whether there's anything specific I need to know about copying my Home folder (containing both user accounts) and reinstating them afterwards.

Can I simply copy and paste the entire folder to a different physical drive, or do I have to use the terminal? If the latter, could someone give me the necessary code please?

When reinstating, I'm planning to use a separate partition for Home (/home), so do I need to do anything specific to transfer the old files, or can I simply copy and paste, overwriting whatever's there, after installation?

Sorry to be a nuisance, but most of this is new to me.

---

### Post by oldfred on 2013-02-13
I would rather copy /home first, but I think it will work afterwards. I just do not know what the old copy may have that would overwrite something from new copy. 

These are all really the same, use the one that makes most sense to you. Main difference is what copy command is used. I tend to prefer rsync.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses sudo cp -ax * /mnt/newhome where the -ax preserves parameters
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

    
You should also make a list of installed applications.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
It is just a long text file. You may want to edit out any applications that new versions now replace.

Then when you install you have to use manual install or Something Else and choose the existing (new) /home, but DO NOT tick the format. Other partitions like / (root) have to be formatted.

---

### Post by Barney-R on 2013-02-13
Thanks for that oldfred. I won't pretend to understand it all just yet, but I'll follow the links and see what I can learn.

One question I still have concerns the fact that I'm hoping to keep most of my 10.10 settings in conjunction with a clean install of 12.04. I've got a fair idea by now about partitioning the boot drive during installation, and I'm planning to have a separate /home partition this time, but I'm aware that there'll be a lot of "ballast" in my existing home folder, and that there may be compatibility issues.

Any further advice would be very welcome.

I've used copy and paste to transfer my home folder to a second physical drive, so after installing, can I just copy the files back to the (new) /home partition?

Also, I'd welcome any help on deciding which files to keep and which to get rid of.

Sorry. I know I'm asking you to write a book, but whatever you can tell me will be very much appreciated.

Could it be that I only need to copy the Mozilla folder (to keep my cookies, e-mails and settings), the visible sub-folders in home and very little else? (We can but hope). I don't mind reinstalling software and repositories afterwards.

I haven't done much of this kind of thing, so the simpler we can keep it, the better.

---

### Post by oldfred on 2013-02-13
Settings for all the applications you use are in /home usually in hidden or . folders. Firefox & Thunderbird have folders with their profiles in those folders.

You need to make sure if just copy & pasting that you use a Linux formatted partition. You still may have to reset some permissions or ownership, but you can do that for /home. If ownership & permissions get messed up in /, it becomes a new install. 

I went from 10.10, but had also installed each of the newer versions to test. I did not like Unity as my monitor is the older 4:3 and works better with the old style gnome2. So I followed kansasnoob's suggestions and installed gnome-panel or fallback.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

    
If you export the list of applications you will find it very long, but it will not reinstall anything already installed. But I do not remember with which version they converted from OpenOffice to LibreOffice, but you do not want both for example. I do not know all the others that have changed. But best to have list just in case.

---

### Post by Barney-R on 2013-02-13
That was quick! Thanks very much oldfred.

I didn't like Unity either, which is one of the reasons I've delayed so long (I ran the live CD). I'm planning to switch back to Gnome once 12.04 is installed.

Now I'm off to do some snoring. It's after midnight and we "old ones" need our beauty sleep.

---

