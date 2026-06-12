---
title: "Lucid Server - Won't Boot from Software RAID"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Antimatter47 on 2010-05-06
Hello all,

I'm trying to install Lucid server (64 bit) and I'm having trouble getting it to boot from software RAID.  The hardware is an old Gateway E-4610D (1.86GHz Core2 Duo, 2GB RAM, 2 500GB HDs).

If I install on a single HD, it works fine, but if I set up RAID1 as described [here]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/"), the install completes fine, but on reboot this is what I get:

```
mount: mounting /dev/disk/by-uuid/***uuid snipped*** on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init= bootarg.

```

...Followed by a BusyBox prompt.  I'm not a *complete* Linux newbie, but I have absolutely no idea where to go from here.

When I set up the RAID using the ubuntu installer, I created identical main and swap partitions on each of the two drives (all four are set as primary), made sure the bootable flag was on on the two main partitions, then created a RAID1 out of the two main partitions, and another RAID1 out of the two swap partitions.

In searching the forums, I've seen a couple other posts about this same problem, but no solutions yet.  Any ideas?

Thanks!

---

### Post by Stason on 2010-05-06
Check this out: [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by Antimatter47 on 2010-05-06
> **Stason said:**
> Check this out: [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

It looks like this is just about fakeraid.  Is it also applicable to regular software RAID?

---

### Post by Antimatter47 on 2010-05-07
Anyone?

---

### Post by c600g on 2010-05-07
I was not even able to complete installation, as grub could not install itself.

I posted a message about this a few days ago, and no one responded. Perhaps [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/485604") is applicable?

---

### Post by morrty11 on 2010-05-09
Ran into the same issue yesterday. I have two 500GB drives I setup software RAID on and then proceeded to install Ubuntu 10.04 64-bit server. When the install completed and it popped out the CD and rebooted I got the No init found busy box error.

---

### Post by Antimatter47 on 2010-05-10
I thought I might have been doing something wrong with the RAID setup, so I tried the exact same configuration with debian lenny, and it worked fine.  This leads me to believe that it is in fact a bug, not user error.

Is there any way to fix this?  Are the ubuntu install CD images ever updated?  (If I download the iso again in a couple of months, is there a chance that this would be fixed?)

---

### Post by Caveman2010 on 2010-05-10
I spent two days in a similar problem with hardware RAID. I went back to 9.10 and it works fine.

---

### Post by pdk on 2010-05-12
I also have the same problem. Installed grub using a rescue disk to the mbr
When the system boots 
>grub
>find /vmlinuz
(hd0,0)
(hd1,0)
root (hd0,0)
kernel (hd0,0)/vmlinuz
boot 

can't find device bad block ....
I will create a bug report

---

### Post by mutrax on 2010-05-13
Been there, fixed that. ;)

[http://ubuntuforums.org/showthread.php?t=1467481&page=3&highlight=mutrax](http://ubuntuforums.org/showthread.php?t=1467481&page=3&highlight=mutrax)

fixed it by doing the partitioning with the 8.04 server install disk, and then installing lucid on the 8.04 crated MD's.... Guess the partitioner from lucid has a bug.

Regards,
Ed

---

### Post by morrty11 on 2010-05-13
So you didn't touch the partitioning at all, just installed on top of the existing partitions?

Just trying to understand how you did this. You didn't do an upgrade, you did a fresh install over the existing partitions from what I understand, right?

---

### Post by mutrax on 2010-05-13
> **morrty11 said:**
> So you didn't touch the partitioning at all, just installed on top of the existing partitions?

Just trying to understand how you did this. You didn't do an upgrade, you did a fresh install over the existing partitions from what I understand, right?

yes, I had an existing md0 raid1 partition as /, and md1 as swap created by a previous 8.04 install. Just went and reformatted the md0 as a ext4 / partition in the lucid install.

This means that on a fresh install, you need to do the partitioning with the 8.04 disk (guess applying the changes and exit the installer before install and raid1 sync works to), and the install with the 10.04 disk.

Might I mention this is a serious bug for me personally because I sell 95% of my servers raid1 configured. This is a elementary feature that should work. Not only for me I presume.

Regards,
Ed

---

### Post by gecka on 2010-05-15
I am facing the same problem (/dev/md0 as / ext4 and /dev/md1 for swap). 

Thanks for your fix, downloading 8.04 right now, will report if it works. Unbelievable thought ....

---

### Post by Cryptomaster on 2010-05-15
Anyone know if this has come to an confirmed bug in 10.04 ?

Best Regards
/Tobias

---

### Post by okplayer02 on 2010-05-15
Same issue here i have a Proliant DL 380G6 server im trying to install RAID 1 on and having issues at the point with GRUB anyone have issues with this server also

---

### Post by bananafishbones on 2010-05-15
I'm getting the same error as the thread creator!! This must be a bug.

---

### Post by mutrax on 2010-05-16
Oh yeah, forgot to mention that in my case I'm talking about software raid.:oops:

---

### Post by Blue Duck on 2010-05-21
Same issue. Will try to fix it using 9.10 installation CD for the partition's step, then installing from 10.04, and let you know.

Blue Duck

---

### Post by pdk on 2010-05-21
I've been playing with this situation for about 2 weeks now.
I create my partitions with parted on the sysreccd version 1.3 and it works 100% for 8.04. It does not help with 10.04.
I create 20gb partitions. Some one managed by using the whole disk and installing the old grub.
I mounted the system and installed grub but can only get to an initramfs.
I copied the /boot/grub from the rescue disk in place of the grub2 stuff to get stage 1 and 2, created a menu.lst with root /dev/sda1
When I tried to chroot from the initramfs I got segmentation error.
I put in a question about this when trying to create a bug. So far no answers.

Peter

---

### Post by pdk on 2010-05-22
I can confirm success with the 8.04 partition setup.
The version of parted on ubuntu 8.04 is 1.8.9. (Can't be sure that this is the version of the install disk. Would have to get to the shell to find out)
Peter

---

### Post by TIm Blokdijk on 2010-05-26
Another conformation from me, setting up software raid1 with [Ubuntu 8.04.4 i386 server edition]("http://releases.ubuntu.com/hardy/ubuntu-8.04.4-server-i386.iso.torrent") with /boot on the array, completing the installation.
Removed the 8.04.4 disk, boot into the 8.04 system to confirm that the system worked as advertised.
Rebooted with the Ubuntu 10.04 i368 server edition disk inserted, started the installation and replaced the ext3 partitions with ext4 in the manual disk setup. Leaving the actual raid setup as it was configured for 8.04.4 and the thing still manages to boot itself with /boot on the array.

Thanks, for the heads up on this!

---

### Post by waffletten on 2010-07-07
Same problem as original poster on a new build using 10.04LTS server to make software RAID1 server. I was able to get 10.04 RAID1 working by:
1.)Build RAID1 software array with 9.10 server install CD
2.)Installed 9.10 server, made sure it worked
3.)Popped in 10.04 server disk and reformatted previous RAID ext4 / to  ext4 /
4.)Installed 10.04 server
5.) It works!

 Why is a fundamental bug like this present in 10.04?

---

### Post by scottgun on 2010-07-25
Ditto, same issue.  Partitioned software raid 1 with 10.04 installation (64 bit).  Completed install and on first boot got the same error.  I am uber peeved.

It's been 2 months since this was first reported.  Where is the support?

---

### Post by scottgun on 2010-07-26
I was also able to establish RAID 1, after running the partition manager in the 8.04 installer.  It wasn't as easy as initially advertised however.  I started by establishing my physical volumes on each disk and running the Configure Software RAID to establish the RAID devices.  I then selected the formatting options for each RAID device; swap and ext 3 /root.  When I tried to save the partitions and proceed, I was presented with [a well documented bug]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/305500") that further impeded my progress. I was given the option to back out but taking that made the partitioning proceed and then promptly hang on the formatting of the ext3 (good ol' 33%).

I pulled the plug and booted gparted, which recognized the 2 arrays that I had created.  The swap was formatted but the primary was not.  I used gparted to format the primary array.  This took about 30 minutes for a 2 x 1TB RAID 1 array.

I then booted the 10.04 installer, which recognized both of the formatted arrays and allowed me to use them for installation without incident.

---

### Post by Geoff Ballinger on 2010-08-06
Thanks to the hint about using an older installer to build the RAID - worked for me too. The only additional complication worth mentioning is that if you have made a few attempts with the 10.04 installer you are likely to have some dodgy MD devices defined. You need to explicitly remove these using 10.04 or they will confuse the 8.04.4 installer.

I have opened a bug for this on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/612224](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/612224)

... surprisingly couldn't find any existing bug report for this but perhaps I am being thick?

Geoff.

---

### Post by mutrax on 2010-08-06
> **Geoff Ballinger said:**
> <SNIP!>

... surprisingly couldn't find any existing bug report for this but perhaps I am being thick?

Geoff.
Aaawww... *facepalm* I always presume that a problem this big is already filed... Let this be the last time a problem like this remains unnoticed from the coders...

---

### Post by nimdAroineS on 2010-08-06
I have had the same problem. Apparently the system confused the partitions and is unable to mount /dev/mdx.

The solution that has worked for me is to install a 9.10 server from scratch and then run apt-get dist-upgrade to 10.4.

If I start the computer with SystemRescueCd and the option to boot with the operating system in the hd, then everything works perfectly.

---

### Post by unlogic on 2010-08-14
I usually use Mandriva but seeing how Ubuntu offers 5 year of support for it's LTS releases i decided to try Ubuntu server 10.04.1 x64 on two quad core Intel machines with two 500GB drives each.

The installation goes smooth but just like everyone else in this thread the system fails to boot after wards.

I've never had any problems like this with Mandriva over the last five years and what shocked me even more was that I got the same behavior with the nightly build of Ubuntu server 10.04.1 which is about to be released in a few days...

I ended up having to use the workaround mentioned in this thread that is to partition the drives using a different Linux installer (Mandriva 2010.1 in my case).

I've subscribed to the bug at launchpad but it really puzzles me how a significant bug like this can go unfixed for so long in a server distro.

---

### Post by JamesA on 2010-08-20
I can confirm this is also a bug, the error is staring me in the face right now using an iso only downloaded tonight, and this was reported back in may?

Time to download 9.04 and start again..

---

### Post by Yepman on 2010-11-02
I have the same problem, 6 months after the first bug report. I can not understand this.

Ubuntu 10.04 Server really really sucks! This is on the same poor quality level I am used from Windows. Nothing works as it should! I did setup a server and had tons and tons of problems, which I did not have with older versions of Ubuntu. It seems quality testing is not present.

Major problems I had / have:

[LIST]
[*]Installation from USB Stick not possible. Needed hours to find out that special command must be given at boot.
[*]Grub2 did not install on raid1, crypt, LVM configuration... had to perform several tricks in busy-box during install to make it finally work. This was in June. Now it is November and still the same problem on a new machine with raid1 and crypt. HOW is it possible to distribute a Linux version marked as "server", which can not be installed with raid 1 ??? This is ridiculous.
[*]Driver for my satellite receiver card buggy, does not work. I.e. it works for a single card, but I have two of them in the same machine and then it fails with a crash (DVB TT-1600). Downloaded a patch from the internet (also from May 2010), but with every kernel update I must recompile and install the driver now manually, because the bug fix does not make its way into 10.04
[*]MythTV does not work due to initial misconfiguration by the installer
[*]XWindows remote desktop does not work, because they use a gdm which has bugs / problems!!! It can NOT be made to work!!! NO remote Desktop with 10.04!
[*]fetchmail did not work correctly for multi-drop configuration, used the same config file as for older servers. Turned off multi-drop.
[*]Samba forgot its password, because I had once set erroneously "unix password sync = yes". Setting it to "no" later did not help, because several files in /etc/pam.d were not updated correctly as they should to reflect the setting changes. Edited the pam.d files manually.
[*]Xubuntu Desktop once crashed and messed its configuration files... desktop unusable! This was really Windows-like! Needed to setup a new "dummy" user and copied the config files from its home directory over to the old user.
[/LIST]
These are only the major problems... there were tons of other problems I did forget. I am switching now to Debian.

Goodbye Ubuntu!

---

### Post by scrapper82 on 2010-11-27
can confirm this bug as well. Solution read on...

...
No init found.  Try passing init= bootarg.SOLVED this problem in a workaround:
BAD
Partitioning RAID 1:
sda1 sdb1 = /boot              EXT4
sda5 sdb5 = /                    EXT4
sda6 sdb6 = /var               EXT4
sda7 sdb7 = /home            EXT4
sda8 sdb8 = /usr/local        EXT4
sda9 sdb9 = /swap             SWAP   <--- Problem this will not work in Lucid Lynx!

GOOD
SOLUTION RAID:
sda1 sdb1 = /boot              EXT4
sda5 sdb5 = /                    EXT4
sda6 sdb6 = /var               EXT4
sda7 sdb7 = /home            EXT4
sda8 sdb8 = /usr/local        EXT4

NON-RAID:
sda9 sdb9 = /swap             SWAP   <--- Problem! don't put swap into RAID!
but they dont work in a RAID just one swap and another swap which extends the first one.
This solved my problem and i could install and boot Lucid Lynx.
After this i got another independent problem with ureadahead... you will face this as well i guess. but thats another issue with Lucid Lynx. (you can solve ureadahead problem here: [http://ubuntuforums.org/showpost.php?p=9555086&postcount=9](http://ubuntuforums.org/showpost.php?p=9555086&postcount=9))

than hopefully ubuntu server 10_04 lucid lynx will work!

greetings
scrapper

---

