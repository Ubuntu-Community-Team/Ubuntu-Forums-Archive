---
title: "*Sobs* I jacked my jive all up"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by pr3@ch3r on 2006-11-14
Alright I have a new Acer desktop with a sata drive, and I added my 20gb ide under the dvd/rw. The scheme is this:

sda = windows media center

hda = dvd/rw
hdb = 20gb linux drive

I installed Ubuntu over SLED 10.0 on the 20gb hdb and grub originally wanted to go on to hda which obviously isnt going to work, so I told it hdb and would manually boot through the POST option like I had with SLED. This didn't seem to work as Grub screwed up everything. Even my (supposed to be) untouched SDA wouldn't boot windows. So I reinstalled via the live cd and this time let grub do its thing on hda thinking maybe it would by default install on hdb correctly this time. Nope. So then I get tired of trying for the day and type in the command:

dd if=/dev/zero of=/dev/sda bs=512 count=1 as well as with hdb to clear out grub which in the past has worked fine, but then I never had to different types of channels and drives, always ide. 

Now before I ran that linux command to clear the mbr I tried with my xp pro cd and it wanted admin pass, which I gave the correct one and it wouldnt accept it. After typing the linux command I tried again with the XP cd and it didnt ask for a password, so I typed fixmbr and STILL its not working. I get the same error (Disk Boot Failure, Insert  System Disk and Press Enter) everytime I try even with different methods via POST.

PPppplllleeeeeeeeezzzzz dont tell me I have to reinstall windows and download all my steam games again, it will take days ](*,)

---

### Post by NonaWeisbaum on 2006-11-14
I did this once and ](*,) this dude here cannot truly express my emotions about it.
I am kind of a n00b, so maybe there is a way around this that I couldn't find anywhere.. but I had to reinstall everything. So many w0w patches... *weeps*

---

### Post by pr3@ch3r on 2006-11-14
ya *sniff* but I think I may have found a work around. I used the 20gb and installed windows xp pro on it, and downloaded a partition recovery program. Im going to see if I can recover the table and get everything spiffy again. Will update shortly my findings.

---

### Post by Herman on 2006-11-15
The 'Alternate' Install CD allows you to install Ubuntu and  to control how (where) to install a bootloader.  I'm not sure if you can with a 'LiveCD' now, but last time I checked, it wasn't an included feature.

I hope nobody else will copy your example of a 'dd' command for zeroing their MBR.

You don't ever need to 'zero' your MBR to get rid of Grub, you simply overwrite it with another bootloader's IPL code. Just FIXMBR would have been sufficient.

The 'IPL' of the bootloader lives in the first 446 bytes of the MBR, that's the only part you need to be concerned with.

If you want to back up a MBR first, you can use a 'dd' command to back up the first 446 bytes, (the bootloader part of the MBR), for example,
```
sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1
```and, to restore it again, ```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1
```Note: Replace 'hda' with 'sda' for sata or SCSI disk. Replace hda with hdb if it is a second hard disk, and hdc if it's a third... and so on.

For a slightly more verbose explanation, [Click Here]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

 You could have backed up your MBR with the LiveCD before you began the install if you had thought of it. It is not necessary to touch the whole 512 bytes of your MBR, which also includes your partition table. It is best to leave the partition table alone and use disk partitioning software for working with that.
You also zeroed your 55aa bootable device signature, which is the cause of your 'Disk Boot Failure, Insert  System Disk and Press Enter' message.

I hope you will be able to recover your partition table okay, but it's your own fault, not the software's.

Regards,  Herman

Edit: I'm afraid this post might be interpreted as I'm using an unfriendly tone, but I don't mean it, I'm friendly really, just trying to point out a mistake before it gets repeated by others. :-D

---

### Post by pr3@ch3r on 2006-12-02
Sorry I'm way late to the game. No I couldn't restore the partitions to a recoverable state. I could see them and access them but could not get them to boot, due to the cleaned out mbr im sure as you suggested. I had cleaned it out before and it worked fine, however this time around it didnt suffice. I wish I would have known what you posted about it however, the post I found about 2 months ago had been my method ever since. Anyways Im running Vista rc2 now in place of media edition and its just as legal so im happy. My ubuntu is just fine now as well with xgl *big grin* the problem i still have which I guess can be solved by using the alternative install cd is that the grub install on the normal gui doesnt make any sense. Now matter what it says its going to install correctly from what Ive found. but when you touch it and change it to 'properly' install it does not work. For example. I tried reinstalling the whole os and typed 'sda' instead of 'hda' which in the real world would allow proper drives to be loaded for my SATA harddrive controller, but it then failed. I then reinstalled it again (third time) and touched/changed nothing  on the grub screen and it worked fine. Retarded to say the least. They should just make that screen idiot proof with a sticky that says "Despite what this indicates it'll work when you reboot" lol. But ya thanks for the info, I'll be saving it for the next catastrophy hehe. Now off to the mess of source compiles I want to try....

---

### Post by psycosmyth on 2006-12-03
i gave up on the same issue but it was more of a security thang, i used the bios settings or just reached in and pulled the plugs, yeah, bootload that.
i had to partition cause i toasted one drive, :mrgreen:

---

