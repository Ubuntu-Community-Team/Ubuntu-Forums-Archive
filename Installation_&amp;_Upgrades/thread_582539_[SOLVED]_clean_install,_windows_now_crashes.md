---
title: "[SOLVED] clean install, windows now crashes"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by andnobodyslept on 2007-10-19
Just finished a clean install of gutsy using the alternate install CD. After everything was all said and done, gutsy ran great, but when I tried to boot into windows it started up for a second, then flashed the blue scree and my computer restarted. I'm just wondering if this has any thing to do with my install, the only thing that would change anything is the fact that I wasn't able to mount my windows partition as /windows with the partitioner. Could it be a MBR problem? I really don't know, just want to see if there is an idea out there before I get rid of windows forever...:)

EDIT: I can access all the files from the windows partition through ubuntu, I just can't boot the OS

---

### Post by Herman on 2007-10-20
One thing it could be is your Windows partition number has changed somehow, that can happen but it is rare. That can be fixed simply by editing boot.ini with a new partition number, (if that's what's wrong, I'm only guessing). But the catch is you will need to boot Windows in order to gain access to boot.ini before you will be able to edit it. boot.ini is a hidden, read-only system file.
Try going to this website and downloading one of the CDs you can get from there, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")
Be sure follow the instructions in that site and see if you can get Windows to boot with one of those CDs.
Those CDs have NTLDR, NTdetect and a special multi partition capable boot.ini file in them, so they should be able to boot Windows almost no matter what!
If you follow the instructions in that site you will almost certianly be able to get Windows to boot sooner or later.

Regards, Herman :)

---

### Post by Herman on 2007-10-20
A copy from the output from 'sudo fdisk -lu' might help shed some light on your  problem too, if you could post that here,
```
sudo fdisk -lu
```
Apart from that, if you could write down the exact error message you are getting when Windows tries to boot, that might help too, or any other clues you can think of.

---

### Post by Wiebelhaus on 2007-10-20
That's a BSOD , See if you can't boot into safemode and change the setting to automatically reboot so you can get a good look at that blue screen of death.


BTW if that setting isn't set by default that means you don't have SP2 installed , you should install it , it makes XP not suck as much , still sucks but w/e.

---

### Post by kamaboko on 2007-10-20
Gutsy completely hoooozzed my Vista install.  Whatever....  In the mean time I'm trying to figure out how to get the damn sound to work.  (vostro 1400)

---

### Post by andnobodyslept on 2007-10-20
The first thing I did was try safe mode, I didn't even get a blue screen of death, it just ran some text about drivers loading then rebooted. Also I have SP2 installed.
Here is fdisk -ls
```
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x291c291b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    34780724    17390331    7  HPFS/NTFS
/dev/sda2        34780725    44548244     4883760   83  Linux
/dev/sda3        44548245    76196294    15824025   83  Linux
/dev/sda4        76196295    78156224      979965   82  Linux swap / Solaris

Disk /dev/sdb: 15.3 GB, 15364339200 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30008475 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b7d2b7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    29993354    14996646   83  Linux
```

Thanks for the help, I really don't care that much about windows, I'm more of a fan of problem solving, so I like a challenge before I just wipe it and try again.

Ian

EDIT: Messed some things up, now have a much better understanding of Windows booting problems, but in the end decided to back up my gutsy partition and make the full leap to ubuntu. Windows was just taking up space anyway.

---

### Post by Herman on 2007-10-20
> Thanks for the help, I really don't care that much about windows, I'm more of a fan of problem solving,  Me too! :)
Your fdisk -ls output looks okay to me, it indicates Windows is still in partition 1, which would be normal. Likely that's the partition number it would have been installed with, so your boot.ini file should have been be okay.
This is the first time I have noticed the disk identifier being included in an fdisk output, I tried it and I'm getting that too in Gutsy. Another new improvement, Gusty is full of pleasant surprises! That should be useful for troubleshooting certain problems.

> Windows was just taking up space anyway. Yes, that's the way more and more people are feeling these days. I deleted Windows the other day from the computer of some friends of mine who have used Ubuntu for a while. 
They begged me to delete their Windows for them. It was loaded with encrypted files produced by a virus and kept getting re-infected no matter what we tried. After trying out Ubuntu C.E. for a while and not having an ounce of trouble with it, they only want Ubuntu in their computer.  Now they have a Ubuntu C.E. and Gutsy Gibbon dual boot, and are as pleased as punch.

Another friend of mine has a browser hijack in their Windows and they were amazed when I showed them what Ubuntu can do. They run a business that depends on their computers being able to work properly and they can't afford to be held up by those type of problems. Their computers are almost brand new and they have spent a fortune already on trying to keep them working, and they still keep having more and more problems.

It just takes a little while for people to learn how to use Ubuntu and when they do, it's pretty hard to make them go back. More and more people are seeing the light every day now. Everyone I know who has Windows has a lot of trouble with it.

Good on you for deleting it!
That's the ultimate way to fix the problem. :lolflag:

Regards, Herman :)

---

