---
title: "Using GRUB to boot WinXP on a separate HD"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by nifty_nev on 2010-01-06
Hi all, I have been a happy little GRUB user for a while now, but now I want to use GRUB to boot a physically separate WinXP hard drive, and I can't seem to do that. Normally GRUB is easy, (I even have a nice splash screen of my own making). Its a champion solution for booting into Ubuntu Linux on /dev/sda5 or Win XP on /dev/sda1.
 
My second HD which Linux recognizes as /dev/sdb, has a Win XP boot sector and Win XP in one partition.
 
Normally I boot off /dev/sda using GRUB, and from Linux I can mount and have access to /dev/sdb - that works well. Occasionally however, I need to boot the separate Win XP system on the second HD, and to do that I switch the boot drive in the BIOS, but lately that is getting to be a bit tedious.
 
Initially I though to give the additional boot choice to GRUB, I simply had to edit /boot/grub/menu.lst and point to the second HD (where /dev/sdb = hd1 in GRUB speak). Unfortunately, when I select the new choice, it simply boots Win XP off the first HD.
 
I'm confident GRUB does look at the first partion on hd1 as expected as I can induce an error by having hd1 disconnected, or write silly partion numbers into menu.lst. So if it does in fact find the first partion on hd1, why doesn't it boot? Why does it default to WinXP on hd0?
 
I have diligently tried physically swapping SATA drive cables and playing with bios switching and have messed about a fair bit with menu.lst to make sure I have drive and partition numbers right, but all to no avail. I have also tried changing rdisk(0) in boot.ini to rdisk(1) on the second drive when it is not the boot drive.
 
I'm just about out of ideas now guys so can you help? I'm afraid the only other thing I can think of is that the second hard drive requires a Linux boot sector if I am going to boot it up from GRUB, but somehow that doesn't make sense. Surely GRUB can work across physically separate drives, so I'm open to other ideas first. Thanks in anticipation.
 
Nifty Nev :P

---

### Post by darkod on 2010-01-06
I would edit the XP entry in menu.lst to be as the original, booting your XP from /dev/sda.
Then add another title entry for the other XP which should be something like:

title Windows XP #2
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

See if that works.

---

### Post by raymondh on 2010-01-06
My good friend, presence1960, would say this:

Let's get a better look at your setup & boot process. In ubuntu, use [this link]("http://sourceforge.net/projects/bootinfoscript/") to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Now, I may not have the analytical skills of a presence1960 but I'm willing to give this a shot :)


Regards,

Raymond

EDIT : I type slow so you could also try darko's suggestion to re-map + chainload windows first.

---

### Post by nifty_nev on 2010-01-06
Thanks Darko & Raymond for your kind assistance. Darko, I used your code to modify menu.lst and it worked perfectly. Well done! :D
 
Raymond, with the solution now in hand, I didn't run the script, but thanks anyways. :)
 
When I get time, I would like to revisit this. I curious to know why simply pointing to (hd1,0) and making it active in my original code does not work. :confused:
 
cheers
Nifty Nev

---

### Post by darkod on 2010-01-06
> **nifty_nev said:**
> Thanks Darko & Raymond for your kind assistance. Darko, I used your code to modify menu.lst and it worked perfectly. Well done! :D
 
Raymond, with the solution now in hand, I didn't run the script, but thanks anyways. :)
 
When I get time, I would like to revisit this. I curious to know why simply pointing to (hd1,0) and making it active in my original code does not work. :confused:
 
cheers
Nifty Nev

I'm not 100% sure myself, but I think XP has to "think" it's on the first drive. Because hd1 is the second drive, it doesn't work. You have to "make it think" it's on hd0 with the map commands.
I'm not even trying to understand why it has to think it's on the first drive, I just use it if it's working. :) Glad you got it working now.

---

### Post by raymondh on 2010-01-06
> **darkod said:**
> I'm not 100% sure myself, but I think XP has to "think" it's on the first drive. Because hd1 is the second drive, it doesn't work. You have to "make it think" it's on hd0 with the map commands.

yup.

a good read from herman ....

[http://members.iinet.net.au/~herman546/p15.html#Windows_on_a_non-first_hard_disk](http://members.iinet.net.au/~herman546/p15.html#Windows_on_a_non-first_hard_disk)

Glad you got it working as well.  Happy Ubuntu-ing :)

---

