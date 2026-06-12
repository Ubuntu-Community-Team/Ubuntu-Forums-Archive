---
title: "Installation issues"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by izudragonov on 2011-05-30
My friend recently install Ubuntu 11.04 on his laptop. I also tried to install it on my desktop, but ran into a huge problem (I think). First I tried to install it 32-bit from a CD, It usually crashed immediately after the disk booted. I tried it with a 64-bit CD, this time I made it to the disk menu, after selecting install it gave me an error message. I then tried using an 8 GB USB drive, this time I got a rapidly scrolling lines of code terminating to a command line at the bottom. It was scrolling so fast I could not read it and it appeared to have went through several thousand lines. The command line would do nothing when I entered commands, not even an error saying that I typed something wrong. The same exact thing happened when I tried to run Ubuntu in demo mode. I have used Windows exclusively all my life, and I have never seen something like this, I have Windows 7 on a 90 GB SSD and a 1.5 TB HDD for data. I think Windows is conflicting with Ubuntu when I try to install it. I would like to dual boot Windows 7 and Ubuntu. I also would like to know which computer games have compatibility issues with Ubuntu, or a resource where I could find such information. Sorry for being so long winded, but I really am clueless at this point, any help would be appreciated, thank in advanced!   :)

---

### Post by torhan386 on 2011-05-30
I am also having issues installing version 11.04. Im trying to install it from a cd onto a brand new drive, i dont want windows any more. My windows install is on a seperate drive. I keep getting this error.
 
 can not mount /dev/loop0  (/cdrom/casper/filesystem.squashfs)
failed /devices/virtual/block/loop0
 
 
  Please help i'v been trying all day to get this installed. I'v also tried to install it in windows to the new drive, it gets a ways in and says access denied and shuts down.:(

---

### Post by Quackers on 2011-05-30
Have you checked the md5sum od the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by torhan386 on 2011-05-30
Ok i did that. It came up as 8b1085bed498b82ef1485ef19074c281 on the iso. checking this with the md5sum file on the cd they came up differant. is that the file i check it against?

---

### Post by dFlyer on 2011-05-30
> **torhan386 said:**
> Ok i did that. It came up as 8b1085bed498b82ef1485ef19074c281. Maybe i'll try the amd 64 bit version next.

Okay md5sum is correct. I don't know if this will fix your problem. I've had some problems with the last few version of ubuntu burning them to cd. I usually end up with that loop. When I burn the iso to a dvd everything just seems to install well. Realize it's a waste of dvd space but burning to cd's were also a waste.

---

### Post by izudragonov on 2011-05-30
I severely doubt the check sum is wrong, 1 CD was used to install successfully on a computer already. I also used 3 other separately downloaded versions between the other CD and the 2 USB attempts.

---

### Post by torhan386 on 2011-05-30
I used the 64 bit version and it worked great. Although it wouldn't recognize my sata drive on install. So i had to install over windows. I like my new OS!

---

### Post by Kossilar on 2011-05-30
>  this time I got a rapidly scrolling lines of code terminating to a command line at the bottom. It was scrolling so fast I could not read it and it appeared to have went through several thousand lines. The command line would do nothing when I entered commands, not even an error saying that I typed something wrong.

I'm trying to install on a Dell D600 Latitude and I'm having the same problem. Hashes are fine. If I let it sit it eventually moves on to a command line: (initramfs)

Looking at the output before it gets to this point it appears to be having trouble mounting some of the file systems needed to install the OS. I'm using the alternate iso from a USB stick, but no luck.

---

### Post by colleyvolley on 2011-05-30
ok I have an old version that my ex put on here and i'm trying to update it to the newest 11.4 on my emachines netbook it downloaded but now i'm stuck because I cant open it up to actually update it..... i'm COMPLETELY lost ...HELP ME!!!:(

---

### Post by izudragonov on 2011-05-30
If I format all of my hard drives and start from scratch does anyone think this error would be resolved?

---

