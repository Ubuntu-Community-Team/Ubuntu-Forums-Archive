---
title: "Text mode installer instructions?"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Jerubaal on 2007-09-12
I want to have XP (OK, I don't, but have to for the time being) and several Ubuntu kernels (ie LTS and also play with newer versions).
I have just reorganised my hard drives using GParted CD to: (not sure if numbering is quite right)
sda (250GB)
sda1 - ntfs - XP Pro (100GB at mo)
sda2 - ntfs - My Documents (65Gb)
sda3 - ntfs - Spare (65GB)
sda4 - ntfs - Swap (4GB)

the other drive is partitioned but with nothing installed on it yet:
sdb (250GB)
sdb1 - xt3 - for /boot (150MB)
sdb2 - xt3 - for / for LTS (15GB)
sdb3 - xt3 - for / for 7.10 i386 (15GB)
sdb4 - xt3 - for / for 7.10 amd64 (15GB)
sdb5 - xt3 - for /home (50GB)
sdb6 - xt3 - for ISOs of repositories cos I am still on dial-up for a few months (50GB)
sdb7 - LinuxSwap (2GB just because I can)
There is ~75GB of unallocated space.

I have read that I need to use the Alternate CD to separate out my /boot, /,  /home.  However, I cannot find any detailed instructions on the text mode installation.  I have looked at [https://help.ubuntu.com/community/Installation/AMD64]("https://help.ubuntu.com/community/Installation/AMD64") and [https://help.ubuntu.com/community/Installation/I386]("https://help.ubuntu.com/community/Installation/I386") but done feel that is detailed enough.

Some threads make it look like the install process will force you to do the partitioning as part of the installation & not allow you to keep the partitions you've already created.

Am I not searching for the correct terms? Please point me in the right direction. I know what it is like when people don't Read The Fantastic Manual, so I have done what I can, but there is sooo much here to wade through!

Thanks in advance!

---

### Post by Pumalite on 2007-09-12
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Jerubaal on 2007-09-12
Fantastic! This looks like just what I was after. Thanks.

---

### Post by Pumalite on 2007-09-12
You are welcome. Let's thank Herman. Happy Ubunting!

---

### Post by Jerubaal on 2007-09-14
I have used the Alternate CD (Dapper 6.06 LTS i386) to install Ubuntu... sort of!

SATA1 is now my drive for Linux distros & SATA2 is for XP. Installation picked them up ok & let me set sda1 as /boot, sda2 as / and sda5 as /home.  Proceeded without too much bother, keeping xt3 formatting and putting GRUB in /boot.

GRUB booted up ok, listing XP as an option as well as LTS. However, neither would load. LTS gave me a 'filesystem not recognised 0x7' sort of message. XP would not load either. Argh! And everything seemed to go so smoothly until then. (It was too late at night to have time to go through it and write it down exactly - that's this evening's task.)

Question: Should I set the XP partition as bootable, or will that be sorted out by GRUB's 'makeactive' in the menu.lst file?  I guess I want it bootable so that I may boot it directly if I needed to.

---

### Post by dabl on 2007-09-14
Re: your Linux partitioning scheme:

That 150MB /boot partition is an unnecessary vestige of other Linuces -- it serves no purpose in *buntu, unless you plan to use an XFS filesystem for some reason.

6 GB is plenty of space for a *buntu root partition, including everything but /home, so you could save some space by slimming down the root partitions.

0.5 GB appears to be plenty of space for swap on newer machines with 1 GB or more of RAM. In point of fact, it is unlikely to be used at all.

Your plan to use a single shared /home partition is fraught with some hazards. The user data that you want to share is not the only thing saved there -- your desktop settings and auto-start program settings are also there.  So, if you have different desktops or start-up configurations for your different Linuces, you're going to have a very confused situation, and probably errors every time you boot a different OS.

Alternate CD is the way to go -- it provides more visibility and control, and you can tell it where you want Grub.

Regarding the boot menu, don't forget the rule "Last Linux Wins".  The operational boot menu will be written by the last one that you install.  You can of course change it manually, but with a little planning you can just sequence the installations to have it end up where you wish.  :)

---

### Post by Pumalite on 2007-09-14
In other words: let Grub install itself in the MBR after you have your other systems installed and Grub will give you a menu that will include all the choices of OS's that you have installed.

---

### Post by Jerubaal on 2007-09-14
So I can have GRUB in the MBR of the Linux drive & leave the MBR alone on the Windows drive, thereby doing away with the /boot partition?

---

### Post by Pumalite on 2007-09-14
MBR normally belongs to Windows in sda1 (where it likes to be). Normally one lets Grub install in MBR
You can install Grub to the /boot section of the partition where Ubuntu is, but you loose all the benefits of multibooting and have to device a special way of booting Ubuntu (inverting the boot order in BIOS as example)

---

### Post by dabl on 2007-09-14
YES, what Pumalite said.  Let Grub go on the MBR where Windows is (sda1), if you want life to be simple. :)

---

