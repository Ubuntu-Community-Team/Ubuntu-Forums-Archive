---
title: "Quick &amp; Simple Question"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Hoosier205 on 2007-03-26
Ok folks...I have a quick and hopefully simple question...

I am currently, and only recently, working with Edgy. I have a dual-boot system with XP and I have a 350GB external hard drive which contains my torrent data, iPod related media, and various audio/video media. I have had a hard time getting both read and write access to this external drive though...

I had also considered upgrading to the Feisty Beta. Now I am really excited about it after reading this:

> 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

**Ubuntu 7.04 can read and write files on the NTFS drives commonly used by Windows.**

Ubuntu 6.06 LTS and 6.10 came with older, beta versions of the NTFS 3G driver. These worked well for many users but were not guaranteed to be stable. Use Ubuntu 7.04 for stable access to NTFS partitions. Alternatively, a stable version of NTFS 3G for older versions of Ubuntu can be obtained from a third-party software repository - see MountingWindowsPartitions/ThirdPartyNTFS3G. 

Will this **(an upgrade to Feisty)** give me the read/write capability I'm looking for on my external hard drive? Or only internal?

Thank you!

---

### Post by nyinge on 2007-03-26
You don't necessarily have to upgrade to Feisty to get NTFS read/write support.  This [post]("http://www.ubuntuforums.org/showthread.php?t=217009") does a good explanation of how to get the required packages and a detailed procedure in order to setup successfully on Edgy.

---

### Post by Hoosier205 on 2007-03-26
Ok, thank you. Now this may be a stupid question...but humor me please...

     1. Using the instructions in the post you recommended...I would be using "ntfs-3g" and going through the terminal in Edgy. Correct??

     2. If I upgraded to Feisty I could use the tool mentioned here...

         [http://www.ubuntuforums.org/showthread.php?t=337970&highlight=external](http://www.ubuntuforums.org/showthread.php?t=337970&highlight=external)

         I would be using a program (so-to-say). Correct??

Now, let's say that I did upgrade to Feisty with the intention of using the ntfs-config tool...is this something that will really let me change from read-only access to read/write? Or is it buggy and not working fully?

My concern is that I upgrade to Feisty...the tool doesn't work...and then I'm stuck. Does the method mentioned in the post you suggested work in Feisty as well? If it does...then I would feel confident I could get it working.

Thank you again!

---

### Post by Hoosier205 on 2007-03-26
Oh well...I've spent the last two hours searching for answers like crazy. It looks as if ntfs-config works in both edgy and feisty. I'm going to upgrade to Feisty and hope for the best. Thanks for the help.

---

### Post by nyinge on 2007-03-27
Nope.  At the step #3, he shows you how to do it using ntfs-config.  Only if you choose the manual route, you'll be fiddling with the terminal.

The package you want "ntfs-config" seems to only exist in Feisty's repos, but you can grab the ready-made package from this other [website]("http://flomertens.free.fr/ntfs-config/").  The link in the other post doesn't seem to be working.  Now...  under the download section, there's a deb file for Edgy and Feisty.  If you havn't upgraded to Feisty, you can download the deb file, and install it in the Terminal:
```
 sudo dpkg -i [ntfs-config_0.5.5-1_i386.deb]("http://flomertens.free.fr/ntfs-config/download/ntfs-config_0.5.5-1_i386.deb") 
```

---

