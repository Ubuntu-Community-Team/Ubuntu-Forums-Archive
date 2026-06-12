---
title: "Help me down-grade from Lucid"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by SaikoRonin on 2010-02-19
I have been having some problems with my computer since upgrading too Ubuntu Lucid Lynx.  For some reason it didn't start immediately but some time after upgrading.

My Usb ports aren't detecting anything, my ps/2 mouse won't move but it can click.  And my DVD/RW drive wont detect blank dvds.

I used to use my first hard drive Sda1 as 320 gb of Swap(I know a big waste of space) and my second hard drive sdb 500gb as ext3 for ubuntu.

Now I dont have access to another computer, and I cant make a usb drive or another boot cd,  I have an hardy heron cd that has some corrupted files,  that I managed to save my computer with after my first few attempts at changing systems.

So I have Kubuntu 9.10 on an .iso file.  I would like to put this on my sda1 drive that is now 317 gb ext3 and 3 gb of swap and has a faulty hardy heron installed on it.  However when I try to blank out that ext3 portion and set up the kubuntu to be installed from grub it messes up my master boot record and I get a Grub: ERROR 15 message, and I have to reinstall the faulty Hardy Heron from cd to fix grub and get back onto lucid.


So I guess I need to put my master boot record on my sdb drive somehow, or switch my personal files to my sda and then try to install over sdb...

Who has some ideas for me?

---

### Post by darkod on 2010-02-19
Lucid Lynx is still under development and should not be used as main, day to day system. Only as testing. It gets released in April.

If you want to install the Kubuntu 9.10 you have, just start the install process and in Manual Partitioning tell it to use the current partitions you have on the 320GB disk. But with linux you have to do this manually.

Just select the bigger root partition, click on the Change button at the bottom, and select filesystem as ext4, mount point as / and tick the format box. Of course, this will DESTROY any data you have on this partition.
Then do the same for the smaller swap partition selecting filesystem as swap, and mount point as swap.

In the last screen, before clicking Install, click on Advanced and put grub2 where ever you want, depending which hdd you plan to boot from. It would be best to be on the same disk as kubuntu.

If you boot from the correct hdd you should see no grub errors. You are seeing the errors probably becaue you are still booting from some grub which uses the hardy config files and when you delete that partition, it has no config files to find.

Justpay attention what you install and where, and it should be fine.

---

### Post by SaikoRonin on 2010-02-19
OK this may sound stupid, but how do I start the install process from the .iso while I still have my O.S. in use.  From the command Line preferably

---

### Post by raymondh on 2010-02-19
> **SaikoRonin said:**
> OK this may sound stupid, but how do I start the install process from the .iso while I still have my O.S. in use.  From the command Line preferably

for reference

[http://ubuntuforums.org/archive/index.php/t-28948.html](http://ubuntuforums.org/archive/index.php/t-28948.html)
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

Raymond

---

### Post by davec51 on 2010-02-19
I went through the upgrade to 10.04 a few days ago. The upgrade stopped midway (actually at the "cleaning up" point) and told me that the installation would be impossible. However, my 9.10 installation was gone. I'm wondering whether to reinstall Koala or forget the whole thing; I have a GRUB I in another partition and I could just hook up to that. Is there a frugal installation method?

---

### Post by SaikoRonin on 2010-02-19
That link requires some sort of external media with a "grub" on it

this ubuntu documentation is a lot more informative but unfortunately I was still having trouble with my grub after trying a few of the methods, however it may help dave c51 [Linux Installation]("https://help.ubuntu.com/community/Installation/FromLinux")

---

