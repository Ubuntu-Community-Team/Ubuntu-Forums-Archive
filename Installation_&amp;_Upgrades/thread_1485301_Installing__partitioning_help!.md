---
title: "Installing / partitioning help!"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by rbolio on 2010-05-16
So heres the deal in  a quick resumé


My gf's laptop had ubuntu and windows side by side but she decided to remove ubuntu to free up some space on her hdd.

So via windows i messed up and simply deleted the ubuntu partitions (/home and swap).  

This how ever killed the grub menu.

So now, i am re installing ubuntu in the hdd with a smaller space, how ever in the install menu in the partitions set up, i CAN (how i was planing to) expand the windows partion....

How ever...if I do Change it, will it format the partiton or simply add space as it is planned.... 

Whats the min. space for ubuntu 9.10 so i can get grub back (hp mini...no cd drive for win cd)...

Please help!

---

### Post by darkod on 2010-05-16
If your goal with installing ubuntu is just to have windows booting, DON'T!!!

Also, don't try resizing the windows system partition with the ubuntu installer. You said you don't have cd-rom but I guess you have bootable ubuntu usb stick that you are using now, and that's all you need because ubuntu is wonderful. :)

Boot into live mode (Try Ubuntu), and do the following to make windows boot (I assume you have only one hdd device called /dev/sda, if not, adjust the command):

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you. That will install generic mbr on /dev/sda and provided your boot flag is still set on the windows partition as it should (actually on the partition holding the windows boot files, if it has that small 100MB boot partition), after you restart you'll see windows.

After that use Disk Management inside windows to enlarge the system partition, or just format the unallocated space into new ntfs partition.

PS. You see, ubuntu even does the job for windows. :)

---

### Post by rbolio on 2010-05-16
> **darkod said:**
> If your goal with installing ubuntu is just to have windows booting, DON'T!!!

Also, don't try resizing the windows system partition with the ubuntu installer. You said you don't have cd-rom but I guess you have bootable ubuntu usb stick that you are using now, and that's all you need because ubuntu is wonderful. :)

Boot into live mode (Try Ubuntu), and do the following to make windows boot (I assume you have only one hdd device called /dev/sda, if not, adjust the command):

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you. That will install generic mbr on /dev/sda and provided your boot flag is still set on the windows partition as it should (actually on the partition holding the windows boot files, if it has that small 100MB boot partition), after you restart you'll see windows.

After that use Disk Management inside windows to enlarge the system partition, or just format the unallocated space into new ntfs partition.

PS. You see, ubuntu even does the job for windows. :)



I thank you sir! :)  , ill get answer you if i have any problems :)


btw, this wont delete any data on the already existing windows partition right?

---

### Post by darkod on 2010-05-16
> **rbolio said:**
> I thank you sir! :)  , ill get answer you if i have any problems :)


btw, this wont delete any data on the already existing windows partition right?

No, it will just remove part of grub2 which is on the MBR of the hdd. With deleting the ubuntu partition grub2 config files are gone and that's why it doesn't work. Writing generic mbr on the hdd will make windows boot unless there is another problem which is very unlikely. We know what the problem is here. :)

---

### Post by rbolio on 2010-05-16
There we go! :) 

Thank you! :)

---

