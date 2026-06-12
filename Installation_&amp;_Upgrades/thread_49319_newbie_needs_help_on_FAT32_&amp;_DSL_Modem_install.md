---
title: "newbie needs help on FAT32 &amp; DSL Modem install"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by wizer on 2005-07-15
Hi
I apologise for asking this Q; esp on the FAT32 but I'm only a fews old on Linux.  I finally managed to get my install to work on my Fujitsu S7021 after changing the video driver from i810 to vesa (my actual device is i915).

I want to use a FAT32 partition to share between my XP and linux.  I already have data in it.  After looking through the forum, I have added the following to my fstab:
              /dev/sda2   /media/DataDisk  unmask=000   0    0


I get the following error message when I boot up.
             FAT: unrecognised mount option "unmask=000" or missing values

I tried replacing unmask=000 with rw.  I was able to see my data but could not write (ie read-only).  What can I do to get it to be read-write?


I also need some help to install my ADSL dial-up which is my primary internet connection.  I have a Aztech DSL500U.  Does anyone know how I can get this to work?

Thank you very much for your help.

Andrew

---

### Post by badrinarayan on 2005-07-15
It is umask, not unmask.
You may find this site very helpful - [http://www.ubuntuguide.org](http://www.ubuntuguide.org)
That should answer your questions. Feel free to post back here again, if you fail...

Also, the DataDisk directory is probably read only.
Do a [FONT=Courier New]chmod 777 /media/DataDisk[/FONT]

Regards
Badri

---

### Post by wizer on 2005-07-15
Dear Badri
Thanks for the help :)

It worked partially.  After correcting from unmask to umask, I no longer had an error.

I could create a file in Linux in one of the Directories & view it in XP.  However on another director called Andrew, I couldnt write (even though gedit didnt indicate that files in there were read only).  I notice that this folder, unlike the others, had a small padlock icon in its right corner.  The only difference between this directory and the others is that it is hidden in XP (Dir only.  Sub-dir do not have the hidden attribute).

Also, I am not sure where I am to put the chmod command that you mentioned in the earlier post.

Thanks for your help.

---

### Post by wizer on 2005-07-16
Dear Badri 
:)  I figured out how to work the chmod command that you gave me earlier.  U were right to predict that I would need it. My problem with Andrew was that root was considered the owner so no write permissions.  Once I ran chmod 777 /media/DataDisk/Andrew on it via the root terminal, I had full access to it.  Thanks so much for helping me with this FAT32 access problem. :-P 

Would you know how I can solve my DSL modem problem.  It's quite inconv to have to boot into XP every time I want to access the internet.


Andrew

---

