---
title: "Help!- can't boot anything after trying dual boot"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by pikaia on 2008-03-07
I've been trying for 2 days now to fix and correct this issue.  I initially tried to dual boot TinyMe (a small version of PCLOS) on an old machine that had Xubuntu on it.  My intention was to learn how to set up a dual boot, and play with TinyMe for potential use on my Thinkpad 600E.  I could never get TinyMe to boot properly after installing it several times and it even somehow screwed up my Xubuntu install.  It (xubuntu) would start loading the Usplash and then error out to a blank screen with no error messages.  I thought I'd figured out how to dual boot by installing TinyMe and PCLOS together without issues, but when I installed Xubuntu over PCLOS I now get more problems.  Xubuntu booted once, and now will no longer do so... it says that there is an illegal executable??

My main concern is after thinking I figured out the dual boot I resized and partitioned the hard drive on my 600E and installed TinyMe.  After install it brought up the TinyMe boot selector and I chose the default, but it errored out to command line after a few seconds.  But now, the Ubuntu install that was on the other partition won't boot either.  It starts to load and then spits out a stream of "Command Not Found" errors before coming to a "Hit Ctrl-D for Maintenance" or Enter to continue option, and then reboots to the same errors.  I've tried startx and can't figure out how to access the boot/grub from a livecd.  Is there ANY way I can salvage the Ubuntu partition?  This 600E was a pain in the butt to get configured and I'd hate to do it all over again if I didn't have to.

Please help... thanks.

---

### Post by confused57 on 2008-03-08
> **pikaia said:**
> I've been trying for 2 days now to fix and correct this issue.  I initially tried to dual boot TinyMe (a small version of PCLOS) on an old machine that had Xubuntu on it.  My intention was to learn how to set up a dual boot, and play with TinyMe for potential use on my Thinkpad 600E.  I could never get TinyMe to boot properly after installing it several times and it even somehow screwed up my Xubuntu install.  It (xubuntu) would start loading the Usplash and then error out to a blank screen with no error messages.  I thought I'd figured out how to dual boot by installing TinyMe and PCLOS together without issues, but when I installed Xubuntu over PCLOS I now get more problems.  Xubuntu booted once, and now will no longer do so... it says that there is an illegal executable??

My main concern is after thinking I figured out the dual boot I resized and partitioned the hard drive on my 600E and installed TinyMe.  After install it brought up the TinyMe boot selector and I chose the default, but it errored out to command line after a few seconds.  But now, the Ubuntu install that was on the other partition won't boot either.  It starts to load and then spits out a stream of "Command Not Found" errors before coming to a "Hit Ctrl-D for Maintenance" or Enter to continue option, and then reboots to the same errors.  I've tried startx and can't figure out how to access the boot/grub from a livecd.  Is there ANY way I can salvage the Ubuntu partition?  This 600E was a pain in the but to get configured and I'd hate to do it all over again if I didn't have to.

Please help... thanks.

You may want to post the output of(from the Xubuntu  live cd):
```
sudo fdisk -l
```
-l is a small "L"
please designate which is your Xubuntu & TinyMe partitions.

If you haven't already, you could try reinstalling Xubuntu's grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you reinstalled TinyMe on a pre-existing partition, the UUID in Xubuntu's /etc/fstab may have changed, which would prevent Xubuntu from booting properly...you can mount your Xubuntu root partition, using the live cd:
```
sudo mkdir /media/xubuntu
sudo mount -t ext3 /dev/xxx /media/xubuntu
cd /media/ubuntu/etc
sudo cp fstab fstab_backup
gksudo mousepad fstab
```
substitute /dev/xxx for the Xubuntu partition, e.g. /dev/sda1
if you know which partition TinyMe is being mounted on, place a # in front of the UUID entry.

---

### Post by pikaia on 2008-03-08
I did try reinstalling the grub using the live cd... it didn't help.  Nor did SuperGRUB.

Does it make a difference if the install that was on the drive was a minimal ubuntu + xfce (and some other packages)?  I just want to be as clear as possible before making things worse.  

I think I understand everything, except for the last line.  The # in front of the UUID entry... when and where would I do that?

Thanks.

EDIT:  Here is the fdisk output:
Disk /dev/sda: 6448 MB, 6448619520 bytes
15 heads, 63 sectors/track, 13328 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
Disk identifier: 0xc9b6c9b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7101     3355191   83  Linux
/dev/sda2            7102       13328     2942257+   5  Extended
/dev/sda5           12402       13328      437976   82  Linux swap / Solaris
/dev/sda6            7107        7327      104391   83  Linux

---

### Post by confused57 on 2008-03-08
If TinyMe is /dev/sda6, find the entries to mount #/dev/sda6 & place a # in front of the line with UUID...here's an example of part of my fstab:
```
# /dev/sdc1
UUID=a53fae38-f4ad-407a-b577-1bafd3645ea8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc2
UUID=f319f891-6780-4f79-874e-8f0c2aea7490 /home           ext3    defaults        0       2
# /dev/sdc3
UUID=83aeb5b6-8655-48f9-8371-8d62e738ffb0 /media/data2    ext3    defaults        0       2
# /dev/sda1
# UUID=f811d48c-0207-4897-a57c-c1ebfcf02e13 /media/sda1     ext3    defaults        0       2
# /dev/sda10
# UUID=6839aa73-b8db-4894-9c75-9d03ff582822 /media/sda10    ext3    defaults        0       2
# /dev/sda3
# UUID=ab9af521-d395-44c5-8cdb-bac4fa384abd /media/sda3     ext3    defaults        0       2
```

Notice that I've placed a # in front of the UUID line for sda1, sda10, and sda3...you'll need to place a # in front of your # /dev/sda6 in your /etc/fstab.
You should have mousepad text editor on the live cd, or you can use nano:
```
sudo nano fstab
```
after you've mounted your Xubuntu root partition, using the live cd.

---

### Post by pikaia on 2008-03-08
Hmm.  Well that didn't work.  I didn't have any TinyMe UUID lines in the fstab.  What I did find however is that it looks like both installs are merged onto that partition.  If I open the mounted drive (3G Volume) I see the files for my old minimal ubuntu install and files that are clearly PCLOS in origin, such as 'harddrake', 'gweled', 'emerald' along side the files I've installed, such as Kazehakase and Iceape.  Is this just the way its been mounted or have they really been merged?  And if so, HOW?

Question.  When I entered in the code you listed I used sda1 (as it was listed on the fdisk, should this have been hda1?

---

### Post by confused57 on 2008-03-08
> **pikaia said:**
> Hmm.  Well that didn't work.  I didn't have any TinyMe UUID lines in the fstab.  What I did find however is that it looks like both installs are merged onto that partition.  If I open the mounted drive (3G Volume) I see the files for my old minimal ubuntu install and files that are clearly PCLOS in origin, such as 'harddrake', 'gweled', 'emerald' along side the files I've installed, such as Kazehakase and Iceape.  Is this just the way its been mounted or have they really been merged?  And if so, HOW?

Question.  When I entered in the code you listed I used sda1 (as it was listed on the fdisk, should this have been hda1?
It appears that TinyMe was installed on the Xubuntu partition, which could happen if the partition wasn't formatted first by TinyMe during the installation.  I don't know any way of getting rid of TinyMe on sda1 that would recover your Xubuntu back to the way it was before...other than a reinstall.

Yes, you would need to enter sda1, because that's how the Xubuntu live cd recognizes your partitions from the output of fdisk -l.

---

### Post by pikaia on 2008-03-08
Ok... my heart just broke a little.  But I'll get over it.

I do know I always ONLY checked the clean partition to install, and not my minimal ubuntu partition, especially since this is the second machine this has happened on.  

Question.  I cannot figure out how to get that damn program to install properly.  I choose a partition, format and install.  When I assign mount points, if the other partition is mounted as root (/) it won't, so I would mount it as /boot.  But that would never work.  I mean I like the OS, but either I'm really not too bright, or Lilo doesn't play well with GRUB, or something.

Perhaps I'll try it by itself and see... unless some miracle worker can help salvage the dead (that is my OS).

---

### Post by confused57 on 2008-03-08
> **pikaia said:**
> Ok... my heart just broke a little.  But I'll get over it.

I do know I always ONLY checked the clean partition to install, and not my minimal ubuntu partition, especially since this is the second machine this has happened on.  

Question.  I cannot figure out how to get that damn program to install properly.  I choose a partition, format and install.  When I assign mount points, if the other partition is mounted as root (/) it won't, so I would mount it as /boot.  But that would never work.  I mean I like the OS, but either I'm really not too bright, or Lilo doesn't play well with GRUB, or something.

Perhaps I'll try it by itself and see... unless some miracle worker can help salvage the dead (that is my OS).
Unless someone can suggest some way to recover your Xubuntu install, I would recommend just reinstalling a minimal Xfce...once you get it installed and working OK, then resize your Xubuntu partition to make room to install TinyMe(I've never installed Tinyme, so don't know how large the partition needs to be to install on).  It can be kind of tricky installing a new OS, especially when it uses lilo as the bootloader. 

 When you install TinyMe, you shouldn't have to set any mountpoints for your Xubuntu install and shouldn't need a /boot partition with the size of your hard drive, just set the TinyMe partition as mountpoint / (root) and you may need to set the swap partition(not sure if it's automatically set or not when installing TinyMe). 

 Dont' install lilo when you're installing TinyMe.  You can use a symlink grub boot entry to boot TinyMe from Xubuntu's grub:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

I or someone else can help you if you have trouble getting TinyMe to boot from Xubuntu's menu.lst.  I've made my share of mistakes installing different distros, especially ones that use lilo or incorrectly recognizes the order of my hard drives.

Added:  If there is an option to install lilo to the TinyMe root partition, you can use a chainloader entry in Xubuntu's menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
chainloading would probably be the easiest way

Here's a guide for using lilo:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

---

