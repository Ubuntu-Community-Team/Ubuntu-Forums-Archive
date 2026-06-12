---
title: "triple boot"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-10-23
Hello;  I want to install kubuntu, lubuntu and xubuntu alongside each other on the same laptop, so I can try them out. are there any issues I should be aware of before i attempt
this.  I am assuming since they are all buntu, it shouldn't mess up my MBR, and that grub
menu will give me the option of booting into each.
        I do have 12.04 on here now but I plan to wipe it, if i want it back i will do a fresh install as i am not that happy with it since I did the updates anyway.
         If it matters it is an acer 5735Z, intel dual core,3gb ram, 350 gb HD
Thank's :)

---

### Post by oldfred on 2012-10-23
Just create 3 25GB  logical partitions for /. If current swap sized ok you can use it for all of them as long as you do not hibernate nor encrypt.

Which ever one you install last will be the default boot, but you can easily change that by booting into which ever install you want as default and run this:

sudo grub-install /dev/sda

I would not try to share /home although since so closely related it might work. Better to just create a /mnt/data partition and you can store data in that and mount it in all three partitions.

I have my Firefox & Thunderbird profiles in a shared NTFS (to share with XP also) and I have mounted them in every install I have (many). All new data now goes into a shared ext3 partition as XP is not now used.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by offgridguy on 2012-10-23
Thank you for the info oldfred.

---

### Post by Hodevah on 2013-02-24
Hi. Sorry for posting in an old thread that is from last year but I have googled a few times on tri-booting and I do realize that there are Windows tools available but I am wondering that if I install a 2nd Linux OS alongside Ubuntu and Windows 7, does the other Linux such as Mint automatically recognize the current install of Grub?

If so, would it still be ok and also how is it possible to have the second install of Linux recognize that  a current swap file of 16 Gigs already exists?

I imagine that the '*alongside windows'* dialogue during Mint's install would not be appropriate, is that correct?

Thank you in advance and please do tell me if it is appropriate that I post in this thread which originally belonged to someone else. Or if I should start my own thread.

---

### Post by oldfred on 2013-02-24
Since Windows also, perhaps a new thread, but I have not moved it yet.

Whichever you install last is the one that has control of the MBR. Most Ubuntu's do not give an option to not install grub2's boot loader. You can force it into the PBR of the install partition more a a throw away or not to be used. Then the update from you Ubuntu or first install will find the new install.

Never use Windows to create partitions for Linux. It does not know about LInux partition, may convert to dynamic from basic which creates huge issues, and sometimes when extended partition already exists it does not correctly update partition table.

Best to manually partition with gparted and use Something Else or manual install. Then you choose which partition to use as / (root) and it will auto find an existing swap. You cannot hibernate if using the same swap.

If just trying out another install you only need 10 to 25GB for /. I actually use only 25GB for all my installs but have separate data partitions and my /home is tiny.

---

