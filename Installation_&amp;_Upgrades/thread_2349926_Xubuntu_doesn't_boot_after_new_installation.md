---
title: "Xubuntu doesn't boot after new installation"
date: 2017-01-19
forum: Installation &amp; Upgrades
---

### Post by gupperino on 2017-01-19
So first off I just want to say hey! This is my first time on the Ubuntu forums so I'm doing my best to follow the rules and guidelines, but if I mess something up please let me know so I can make appropriate changes! So lets get into it shall we?

[B]The Backstory:
[/B]I recently acquired an old Dell Inspiron Mini 1012 from ebay. It has a 1.66ghz Intel Atom with 2gigs of ram. I also switched out the 160gb HDD with windows 7 for a 250gb HDD that is presumed to be empty (well now it has Xubuntu on it). The machine works fine on windows. I first installed Kali Linux as I was hoping to have a small netbook to do some pen-testing on. The install went fine and overall I had no issues, except that it was slower than I would have preferred. I also realized that a more basic/general OS such as ubuntu would work better in the long run because it would lighter and more useable for day to day tasks. So I tried Ubuntu, only to find the same performance issue as with Kali. Xubuntu was the next choice and the one I would prefer to go with. I installed it that seemed to run smoothly. I installed some basic things such as wireshark and aircrack as well as ran some basic system updates (just apt to upgrade, update, and dist-upgrade). I also made sure that the intel video driver was installed and updated as I read that that can cause issues. So this is where things went south.

[B]The Issue:
[/B]I restarted the laptop only to get a terminal style message that read: 
```
/dev/sda1: recovering journal
/dev/sda1: clean, ######/##### files, #######/###### blocks
```
(I replaced the numbers with # just to save time and because they don't seem important.) 
So what happened next? Well I waited for 20 minutes only to see no change. I don't really know whats wrong but I would like to find a useable fix for this. I've done some research but it's been unclear how to solve this and the tips scattered around the internet don't seem to really help. I don't really know how to use GRUB recovery mode but I can follow instructions if they're given.

I really hope that someone here can help find a fix to this and explain whats going on! Thanks a bunch,

~ Gupperino

---

### Post by gupperino on 2017-01-20
Bump! Still need some help with this! I'll wait a few days and perhaps install Elementary or Lubuntu and see if those perform decently without this error.

---

### Post by oldos2er on 2017-01-20
Thread moved to *Installation & Upgrades*

---

### Post by oldfred on 2017-01-20
What is sda1?
Post this:
sudo parted -l

You may need a full fsck if format is ext4.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by gupperino on 2017-01-21
Hey, thanks for getting back to me! The result of sudo parted -l is as follows:

```
Number  Start   End    Size    Type      File system     Flags
 1      1049kB  248GB  248GB   primary   ext4            boot
 2      248GB   250GB  2135MB  extended
 5      248GB   250GB  2135MB  logical   linux-swap(v1)

```

I will try the other steps you gave me as well and reply again!

EDIT:

No errors with the fsck commands just some basic info about the partitions. Still having trouble booting.

---

### Post by gupperino on 2017-01-23
Bump, still need help with this!

---

### Post by mörgæs on 2017-01-24
> **gupperino said:**
> ...install Elementary or Lubuntu

Yes, your Atom processor is one of the weaker members of the family, and giving it the lightest possible workload is a good idea. Even Xubuntu might be too much.

---

### Post by oldfred on 2017-01-24
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

