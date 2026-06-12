---
title: "Trying to update but need more partition room."
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by reb682 on 2016-10-22
I am trying to do the update from Ubuntu 16.04 to 16.10. I have
windows8. Kubuntu 16.10, and ubuntu 16.04 at this time. When I do the
update I get the message that I need more room for the update. I have a
large drive but do not know how to move the partitions to make use of
the space.

[https://www.dropbox.com/s/1hus78v3njkhbdu/Partitions.png?dl=0](https://www.dropbox.com/s/1hus78v3njkhbdu/Partitions.png?dl=0)

**** Barmann

---

### Post by Bucky Ball on 2016-10-22
And where exactly do you want to move them? Don't you mean resize them? You are going to need to give more detail about what you want to do, but you are going to need 20Gb for another install and you can use the existing swap.

Firstly: *Make reliable backups of all data you do not want to lose.* If you're careful all should be well, but mistakes do happen.

However you decide to manipulate them, best to boot into a live session from install media ('Try Ubuntu' from Ubuntu disk or USB) to do it. You are obviously going to need to shrink one of the larger partitions. sda2 is your Windows partition I'd say and all up that needs about 50Gb, depending on which version. If you shrink that one (with Win tools), defragment it several times before doing so, preferably with something a little stronger than Wins default app.

*** Important note: Do NOT shrink the Win partition with Gparted or any other Linux tools. *Always use Win software for resizing Win, Linux for Linux*. ;) 

I'm presuming you're talking about sda5 which is almost full, and not the / partition in your screen shot, sda7? Being specific in you first post and giving as much info as you can saves time asking and answering basic questions and gets your issue fixed quicker. :) 

Don't resize it, get rid of what's taking up all the space. What do you have in there??? If it is personal data, it shouldn't be there. You have personal data all over probably, in sda2, sda5 and sda7? You should have it all in one place then link to it from ALL installs.

That way, sda7 can be shrunk to 25Gb and you will have enough free space for half a dozen other installs. I'd start by getting all your personal data on to two backups for complete security then dig in, but* make a solid plan with pen and paper first*. Don't go into it wondering how you're going to go about it. 

You could start by moving all personal data from sda5, shrink it to an appropriate size. It is never a good idea to keep all your personal data in your Windows partition in the first place, an even worse one linking to that data from a Linux install. Either way, that could be shrunk to an appropriate size also, leaving more free space. Fine linking to an NTFS storage partition, but not the Win OS one. Can be problematic.

One last thing to keep in mind: a legacy mode install will only handle four partition per drive, EFI as many, technically, as you can get on there. You install looks to be legacy. This means you can have one more partition (an extended partition counts as ONE partition and the logical partitions inside them are not included in the count). 

PS: It is technically an *upgrade* to 16.10, not update. :)

---

### Post by reb682 on 2016-10-27
My ubuntu 16.04 is on sda5. Can I go to the sda3 extended and move some to sda5. I have KDE partition open but do not want to do anything without knowing what I am about. If I would be better to move all my data to another place. How would I do that and then link to it. I have a 64Gig thumb that I could formate (if I knew how) and then load my data on it. Thdata shows up in Ubuntu and Kubuntu. Kubuntu is the one I use most of the time.
Thanks for any advice/help.
**** Barmann

---

### Post by Geoffrey_Arndt on 2016-10-28
Hmm, . . suggest you do the following otherwise the chances of you totally _hosing ALL the OS's on this PC are high_:

1).  Goto youtube and watch about 1/2 dozen (that be 6) videos related to using gparted and/or re-sizing partitions using gparted.   It's worth the investment in time.   Pay me now, or pay me "more" later.
2).  With the usb thumb drive plugged in, you can change to it by clicking the drop-down in the upper right quad of the gparted partition screen.   Then, you must unmount it to format it - I don't recall exactly the menu item, but by clicking through all and observing the options, you'll find it.  You can format it fat32 or ntfs to store your data on it.   Don't make it a Linux file system unless you understand how to change file permissions.
3).   Re going to sda3 . . . no, you can't do that.   You have to go to sda7 (Kubuntu partition) and resize it.   sda3 is just a label for the whole extended container (with sda5, sda7, etcl inside of it).

---

### Post by Bucky Ball on 2016-10-28
You just find the stick in Gparted then right click and unmount the partitions on it. That's it. Right click on those partition and delete, resize, whatever. 

To clear a USB stick to create a Ubuntu USB installer, I do this then 'Devices> Create partition table' the right click the empty space and create one FAT32 partition that takes up the full USB. That's it.

---

