---
title: "Dual Boot Problem, Win 10 / Ubuntu... HP Elitebook 8460p"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by bbneo on 2017-10-29
I would appreciate any help with identifying the source of this new-onset booting problem on a dual booting machine that has been working fine for the past 2 years.

When booting, it says:



"An operating system wasn't found.  Try disconnecting any drives that don't contain an operating system."  


The pastebin for the boot-repair is here:           [http://paste.ubuntu.com/25844488/](http://paste.ubuntu.com/25844488/)


I  migrated this hard drive to an SSD (Crucial) prior to setting it up for dual  boot about 2 years ago, and it has been running fine since then... mostly in  Ubuntu.  Recently son started using it for gaming with Steam (it has a  GPU), and it would heat up... not sure if that is a factor.  Boot_Repair  report seems to see the hard drive and not find problems with it.  


Thank you.

---

### Post by oldfred on 2017-10-29
You need Windows boot flag on sda1 or probably sda2 as they have boot files. Not sure how boot flag got moved as it should only be on partition with Windows bootable files. Not sure if sda1 is a boot partition or recovery partition. Your sda2 seems to have all the boot files also. Grub does not use boot flag.

You are missing your ext4 logical partition. Typical from a Windows major update which has had a bug for years that it conveniently forgets to write Linux logical partitions back into partition table when updating. Data is still there, you just need to restore entry in partition table. You will have to reinstall grub.
And if Windows 8 or 10 make sure fast start up is off or grub will not boot Windows. Make sure you have a Windows repair/install/recovery flash drive to fix Windows as even on some minor updates it may turn on fast start up, and then you need Windows fixes as grub will not boot it again.

```
 /dev/sda4 [COLOR=#ff0000]        677,038,078[/COLOR]   976,773,119   299,735,042   5 Extended
/dev/sda5         [COLOR=#ff0000]968,488,960[/COLOR]   976,773,119     8,284,160  82 Linux swap / Solaris 


```

You have a gap from start of extended and start of swap. Normally your Linux partition would start a couple of sectors after the start of the extended and end somewhere before the start of swap.

You can use testdisk or parted rescue. It looks like newest testdisk now uses sectors rather than the old CHS which it used for years.

       backup partition table before any changes, so you can get back to current if changes not correct, and copy file to external backup drive.
sudo sfdisk -d /dev/sda > PT_sda.txt 

All these are similar, users may have explained slightly differently, so review several to understand process.

 [SOLVED] Windows 10 update, Stuck in grub rescue 
[https://ubuntuforums.org/showthread.php?t=2373061](https://ubuntuforums.org/showthread.php?t=2373061)
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

