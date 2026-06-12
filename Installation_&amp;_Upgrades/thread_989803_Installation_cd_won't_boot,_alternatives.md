---
title: "Installation cd won't boot, alternatives?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Jerfo on 2008-11-22
So, first of all, hello everybody!

I'm a total newbie and technology illiterate, so all of this has been rather tough for me... long story short, I tried to install Ubuntu 8.10, first I used the Alternate one but it seems the cd got corrupted (according to what I read, most likely while it was being burnt), so I couldn't install the base system, after several failures I decided to try a new and fresh download, oh and btw, I did md5sum check (but only AFTER I had burnt the cd, I didn't know about that beforehand) and the file was fine.

So I used downloaded the Desktop one (via torrent, in case it matters), did the md5sum before burning, burnt at a dramatically lower speed and tried again, now it got even worse, it wouldn't even boot, basically, this is the error message I got (and I did search quite a bit for an answer but found none that was clear enough, it seemed barely like hypothesis)

disk error 80 ax=4,200 drive 9f

Tried on both drives and both returned the same error message.

So I continued to check around this site and came across this interesting option to install it from the HDD but wasn't truly capable to understand how this hole Lilo or GRUB thing worked; so, if you could provide me with any aid I'd really appreciate it.

---

### Post by tommcd on 2008-11-22
Some quick googleing indicates that error is likely due to a corrupterd CD. How did you burn the CD? And how did you verify the md5sums? If you are burning from Windows, try using Infra Recorder or Iso Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
I used Iso Recorder the very first time I burned an Ubuntu CD and it worked well. To verify the md5sums, see this:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It is possible to install Ubuntu without a CD. You will need to partition your hard drive first. You can use the GParted live CD for that:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
What you do is setup your partitions with GParted, then boot from a usb stick that has grub on it and install from the partition that has the Ubuntu.iso on it. It is a bit complicated for a beginner though. Here is a tutorial:
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
I would try to burn a good CD that passes the md5sum check and install from that. Try Infra Recorder or Iso Recorder, and burn at the slowest possible speed. Use a CDR, not a CDRW.

And welcome to the Ubuntu forums!

---

### Post by Jerfo on 2008-11-22
I did the md5sum check with winMd5Sum and burnt the cd with my DVD-RW reducing speed from 40x to 8x. The hard disk is already partitioned, it was done during my first attempt to install with the Alternate cd.

---

### Post by Jerfo on 2008-11-22
It is well said that often, the most common answer is the correct one... so upon deciding that my mental health recovery would turn out to be more expensive after seeing how complicated the other option would be, I simply decided to burn a new CD and am currently (and happily) writing to you from my freshly installed Ubuntu, thank you very much! =)

---

### Post by xc1024 on 2008-11-22
for future - better go green. use usb stick to install ubuntu. even if you make something wrong, you can just wipe it and make it again. there is, I think a tool in 8.10 live cd to make a usb install. it acts just like a normal live cd... except safer, greener and of course faster.

---

### Post by tommcd on 2008-11-23
> **Jerfo said:**
>  I simply decided to burn a new CD and am currently (and happily) writing to you from my freshly installed Ubuntu, thank you very much! =)
Just curious, but since you said the first CD that you burned passed the md5sum check, what did you do differently when burning the second CD? Different media?, slower speed?, different CD burning program?, anything?

Anyway, glad you got Ubuntu installed!

---

### Post by Jerfo on 2008-11-25
The only thing I changed was the speed reduction to 4x (that's what I told the program whose name now I can't remember since it was left on windows and I can't check it) but it's the one ubuntu suggested for iso files, anyway, the thing is I chose 4x but it burnt at 8x, at first I thought I was just careless and didn't notice I had chosen something else, but the last time I burnt it (thanks to which I got this installation working), I made sure I chose 4x but it still said it was burning at 8x... oh well, no biggie since it ran, and that's all that counts.

---

