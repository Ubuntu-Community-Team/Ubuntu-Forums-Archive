---
title: "Taken to Grub Rescue after formatting Ubuntu partition"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by alec433lawrida on 2011-03-19
Good evening, 

I've recently run into a problem with/ or more like without Ubuntu.

I have obviously Googled and tried a number of things, following quite a few threads but nothing seems to work. ( of which where, using the original windows 7 disk to boot into the repair function, where i was instructed to use the bootsect command) but to no avail. So any help will be much appreciated, I would also like to, if possible not loose any of my data. Much thanks

I was running Windows 7 and Ubuntu 10.10

I decided to delete Ubuntu from one of my hard disks( since I gave it a 200GB partition and rarely used it) 

To do so I used the Windows disk manager. Hence I deleted the partition on which I installed Ubuntu.

Upon restart I was presented with " error: no such device" and a series of characters.

What should I do from here?

Much thanks

Alec

---

### Post by coffeecat on 2011-03-19
Hi, welcome to the forum.

> **alec433lawrida said:**
> ( of which where, using the original windows 7 disk to boot into the repair function, where i was instructed to use the bootsect command)

Not quite. You need the bootrec command. See here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You'll need 'bootrec /FixMbr' because you need to put Windows code back in the mbr to replace the 'non-standard' code as Microsoft describes the perfectly good grub code.

Explanation. When you installed Ubuntu, some grub code was written to the mbr which replaced the original Windows code. But this also  needs  the large amount of grub code and the grub configuration file, all of which are on the Ubuntu root partition. So now, when you switch on, the tiny amount of grub code in the mbr has nowhere to go, so to speak, and you get the error that you see. In fact there's some more grub code in the embedding area which is between the partition table and the first sector of the first partition, but that won't affect Windows' functionality and can safely be left there. The series of characters you see in the grub error is the UUID of the now non-existent Ubuntu partition which grub is trying to find.

Running 'bootrec /FixMbr' from the Windows 7 repair console will write Windows code back into the MBR and so long as the boot flag is set on your Windows partition, Windows will boot up when you next switch on.

All of this presumes that you want Windows only on that machine.

However, if you want to reinstall Ubuntu, that will reinstall grub with a new grub menu and you will be able to boot both Windows and Ubuntu.

---

### Post by alec433lawrida on 2011-03-19
Thanks for the quick reply and thorough explanation.

I decided to grab an extra hard drive that I had and Re-Install windows 7 on it - Then use this HDD as my os hd. After which I intend to plug the other hard drives back in.

My question now is - Will I be able to read all the data stored on my hard drives. Regardless of the grub problem? This is a fresh install on a new, separate hard drive.

Thanks :D

---

### Post by coffeecat on 2011-03-19
> **alec433lawrida said:**
> My question now is - Will I be able to read all the data stored on my hard drives.

Depends. Do you mean use Windows to read an NTFS partition? Then of course.

Apart from that: do you intend to use Ubuntu?

---

### Post by alec433lawrida on 2011-03-19
Yep thats sorted out everything.

Thank you for all your help :)

And Yes I do intend to Use Ubuntu (Though not on the PC I've just formatted but my netbook )

Thanks again 

:)

---

