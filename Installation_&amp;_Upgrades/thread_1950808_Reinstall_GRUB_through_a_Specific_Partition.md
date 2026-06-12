---
title: "Reinstall GRUB through a Specific Partition?"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2012-04-01
Sorry that my title's so confusing, but I couldn't figure out a better way to say it.  I triple boot my computer: Ubuntu 11.04, Windows 7, and Ubuntu 12.04 (all 64-bit).  All of my GRUB settings are "on" my Ubuntu 11.04 partition, so whenever GRUB gets updated on my 12.04 partition, all of my GRUB customizations get overwritten.  I'll link to a thread I made a while ago that has a few GRUB fixes that have saved my life (well, not exactly saved my life, but you get the idea):
[http://ubuntuforums.org/showthread.php?t=1873849]("http://ubuntuforums.org/showthread.php?t=1873849")

I used to do this in order to fix this problem:
```
sudo grub-setup /dev/sda
```
I'm pretty sure that that's all that I used to do, and it worked perfectly.  However, when I do that now, my laptop bootloops when I start it up; it runs the ASUS splash screen, but when the GRUB menu is supposed to appear, the computer restarts instead.  Luckily, I know another fix.  I use a bootable flash drive (Ubuntu 12.04) and run this through Terminal (replace "/dev/sda5" with the partition that has your preferred GRUB settings, and replace "/dev/sda" with your hard drive; these can be found in GParted):
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Does anyone know another way to fix this so I don't have to go through the whole process of booting from a flash drive?

Well, actually, I just had an idea.  Instead of running this through my primary partition,
```
sudo grub-setup /dev/sda
```
should I run this?
```
sudo grub-install /dev/sda
```
If that's my problem, I need to get one of those Easy buttons from Staples. :mrgreen:

I should have listened to oldfred on one of my other threads:
[http://ubuntuforums.org/showthread.php?t=1872283]("http://ubuntuforums.org/showthread.php?t=1872283")

He said this:
> **oldfred said:**
> Your second install of Ubuntu will write its grub2 boot loader to the MBR and you will be booting from it. Its os-prober should find both Windows and your other install.

But you may have issues on grub2 updates as both systems are set to rewrite the grub2 boot loader to the MBR.

I have several / (roots) in my sdc drive as I have installed many versions of Ubuntu and not overwritten the older ones.

You may want to also make a shared NTFS partition for data. That data then can be used by Windows (d: ) and both installs of Ubuntu. I have my Firefox & Thunderbird profiles in a shared NTFS partition so I have the same bootmarks & email in whatever system I boot.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

One user posted this a long time ago.
> I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep 'stage1' install in sync.

One thing that tricked me up about this is that, when you are going through the first few pages, you have to hit "tab" and then "enter."  I was trying to figure out a special key that went to the next page, but you just have to hit "tab" to highlight the "OK" button (you can't click it with the mouse).

---

### Post by oldfred on 2012-04-01
If you can boot from the other install into the one not in the MBR.

#reinstall from working (not liveCD) system
sudo grub-install /dev/sda

Otherwise the two commands to mount and install will work to reset it.

But grub remembers which drive's MBR to reinstall to. So a major update does reinstall grub to the MBR.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I think you can unchoose everything to blank out the setting or choose a partition (even though not recommended) just as a throwaway, so it does not overwrite the MBR that you want to keep with another install. 

I also like to have a grub.cfg and grub in a USB flash drive that is configured to boot hard drive. But you have to manually configure grub.cfg.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

