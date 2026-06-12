---
title: "Installation problems, (screenshot)"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Veevose on 2011-05-05
Hey guys, i guess there are a lot of explanations for my issue somewhere here on the forum, but don't hate me for making a new thread, the forum is HUGE!. 
Ok so i am running the live cd of ubuntu v.11.04. 
I have and asus laptop currently running win 7 and iOS.
I deleted the partition with the ios (25gb) of my 320 gb HD using the ubuntu live cd.
Now the space that used to be the ios installed on has 25gb. I just want to install Ubuntu 11.04 on that partition which is unused right now. I tried the (visual) guide for this and i ended up with an error.
so this is what i did: 
From 25GB unallocated i press *add* and added  the * / * as logical with 20gb allocated and left 5 more gb for the swap and hit *install now*. Now,after the region and keyboard layout stuff from the installation i get this error: see attachment for screen shot.

---

### Post by Rubi1200 on 2011-05-05
Please do this from the LiveCD:

```
sudo parted -l
```

Run this command in the terminal and post the output back here in a new post.

Thanks.

(note that is a lowercase L not 1 in the command)

---

### Post by Veevose on 2011-05-05
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   105GB  105GB   primary   ntfs
 3      105GB   296GB  191GB   primary   ntfs
 4      296GB   320GB  24.1GB  extended
 5      296GB   316GB  20.0GB  logical   ext4
 6      316GB   320GB  4119MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ 

don't know what to do next...
______________________________________

hmm the disk is read-only...
thanks for the quick reply

---

### Post by Rubi1200 on 2011-05-05
Did you happen to save the logs mentioned in that error message?

The output looks fine to me. You have 3 primary partitions, but then an extended with logical and swap.

Theoretically, there shouldn't be an issue with that.

The warning you saw is nothing to worry about. It refers to the file-system on the LiveCD.

I would try installing again, using manual partitioning. Select the 20GB partition and mount it as "/" and also tell it to format the partition. The swap partition is already created so that should also be okay.

One last thought just occurred to me; how old is the computer?

Before you do any of this, go into BIOS and see if the whole disk is recognized i.e. beyond the first 137GB. If not, enable large disk option if you have it.

---

### Post by Veevose on 2011-05-05
Hmm, so i started BIOS, went to check the settings you asked me to (i checked, it was displaying 320 gb with no other hidden or locked memory)

Ok so now i restarted the PC, put the live cd back inside, booted and so on and i think to myself: hey man lets give it another shot.

I did the exact same thing as posted earlier and now i am actually installing the 11.04 Ubuntu.

I really don;t know what happened and why it is working but i will keep you updated if i fully install the OS. 

Thanks again.

---

### Post by Veevose on 2011-05-05
wow i spoked too early... failed again.

my laptop is 3-4 years old. It's an asus mv-50SV T8300 Dual Core 2.40Gz.

---

### Post by Rubi1200 on 2011-05-05
You need to save the logs the error message shows so we can try and figure out what is happening.

If you post them here, please wrap the text with code tags for easier reading. Or upload the text file. You should probably also submit a bug report as the message suggested.

---

### Post by Veevose on 2011-05-05
Here is the error i get: 
weird right?

---

### Post by Rubi1200 on 2011-05-05
Okay, here is what I suggest.

First, use the Disk Utility on the LiveCD to confirm that the hard-drive is healthy, which we hope it is.

Then, download a new image and burn it to a new CD. 

Before burning, check the integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then, burn at the slowest speed possible that your burning software allows.

After that, try and install again.

---

### Post by Veevose on 2011-05-05
"failed to launch disk utility" DAMN! i can;t believe this. Is there something i can do ? i just got really panicked right now...

I burned this copy at 4x, i don;t think that should be a reason for not working.

But i wonder, what if it has something to do with the fact that i had apple crap leopard OS installed on that partition?

But i formated it.. it shouldn't be a problem right? why would it fail to install?

Also i used easy BCD so i could dual boot win 7 and iOS (leopard). maybe that's got something to do with it.

Or maybe my HD is pretty messed up, which in this case i refuse to believe.

Just checked integrity: It matches, so my Iso its fine.

I downloaded my ubuntu 11.04 from the official website: ubuntu.com

---

### Post by Veevose on 2011-05-05
yes! finally. i am running ubuntu 11.04!

You were right about burning the image again. i think that was the problem after all.

When i made the first dvd of the image i burned it with windows 7 program (which sucks). Now, when i burned this other copy i used nero and burned it at 4x.

So i wouldn't know at what speed wast that silly win7 was burning my iso because i couldn't select the writing speed.

But i suppose you were right about trying to burn the iso again at lowest speed possible. IT WORKED!

Thank you very much for your time and tips mate, helped me out on this one.

Once again i am a happy ubuntu user! haven't used it since v. 8x or something:guitar:

---

### Post by Rubi1200 on 2011-05-06
Excellent! I am really pleased you got this sorted out and can enjoy Ubuntu :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

