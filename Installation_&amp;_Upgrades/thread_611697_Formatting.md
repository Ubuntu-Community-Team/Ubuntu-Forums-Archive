---
title: "Formatting"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Evisc on 2007-11-13
Have used g-departed to create an ext3 partition and an swap partition, but when i try to install Ubuntu, it freezes when it is time to format the two partitions for the installment. Is this a common problem? Dos anyone have any solutions? All help appreciated!

---

### Post by dabl on 2007-11-13
It takes a little while to format ext3, especially if it is a large partition -- are you sure it is "frozen"?

The swap partition format type needs to be set to "Linux Swap", and the other one is set to "ext3".

If you can't get the *buntu installer to do it right, download the ISO for a GParted Live CD, and do it that way.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

HTH!  :)

---

### Post by Evisc on 2007-11-13
The mouse hangs and I've left the computer on for the entire night, so I'm pretty sure it freezes... I've partitioned the hard disk using GParted making a partition set as swap and the other as ext3, but the Ubuntu installation still wants to format it again and hangs trying to do so... 
Any idea how to avoid this?

---

### Post by Perpetual on 2007-11-13
I have read that some people have problems installing from the live cd and I had the same problems with the RC of Ubuntu 7.10 (the final did work though).  What you can try to do is first run the disc check from the menu of the live cd and make sure the burn is good.  Also, you can download the Alternative cd and use it to install Ubuntu.  It uses a text based installer rather than graphical and tends to have fewer problems.

---

### Post by dabl on 2007-11-13
Also, if you format the partitions with GParted, then there is no necessity to set them to format again during Ubuntu installation.  Just set it NOT to format them.  :)

You also could try reiserfs on the data partition (not the swap). I have been using it for a year with zero issues, except that it is considerably slower on the boot.  The good news is, there is no "mandatory fsck every x boots" like there is with ext3.  Just a thought ...  :)

---

### Post by Evisc on 2007-11-13
I read somewhere that there is a size limit for swap partitions of 2 GB. Is this true?

---

### Post by Perpetual on 2007-11-13
answer when googled...

[i]How large can my swap space be?

Currently, the maximum size of a swap partition is architecture-dependent. For i386, m68k, ARM and PowerPC, it is "officially" 2Gb. It is 128Gb on alpha, 1Gb on sparc, and 3Tb on sparc64. An opteron on the 2.6 kernel can write to a 16 Tb swap partition. For linux kernels 2.1 and earlier, the limit is 128Mb. The partition may be larger than 128 MB, but excess space is never used. If you want more than 128 MB of swap for a 2.1 and earlier kernel, you have to create multiple swap partitions (8 max). After 2.4, 32 swap areas are "officially" possible. See setting up swap for details.

footnote: "official" max swap size: With kernel 2.4, the limit is 64 swap spaces at a maximum of 64Gb each, although this is not reflected in the man page for mkswap. With the 64 bit opteron on the 2.6 kernel, 128 swap areas are permitted, each a whopping 16 Tb! (thanks to Peter Chubb for the calculation) [/i]

I am not sure if that even answered the question :)

---

### Post by Evisc on 2007-11-15
Yeah, that's what i saw to... I made my swap disk less than 2GB to be safe and tried using the alternative cd. I didn't have to format the ext3 partition, but the installers insists on formating the swap partition, and crashes when it tries to...

---

### Post by Perpetual on 2007-11-16
> **Evisc said:**
> Yeah, that's what i saw to... I made my swap disk less than 2GB to be safe and tried using the alternative cd. I didn't have to format the ext3 partition, but the installers insists on formating the swap partition, and crashes when it tries to...

Did you happen to try the alternate cd?

---

