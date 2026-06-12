---
title: "Please Help applying UDF 2.5 patch"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by jackelmatador on 2007-05-20
Hi Everyone,

So I am a noob to Linux and have been doing ok just reading and hacking my way around.  I recently go the XBOX 360 HD DVD drive and was trying to follow the instucions on [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD) 
The problem I am having is how exactly do I apply the patch.  I tried several things

1) Just copied the file to the directory shown, that obviously did nothing
2) I tried running from the terminal:  sudo patch -p1 < UDF-2.50_linux-2.6.20.patch  and the response I get is the following, I enter udf.ko (or the full path makes no difference) when asked for the file to patch

can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux/fs/udf/inode.c       2007-02-04 20:44:54.000000000 +0200
|+++ linux-2.6.20.1/fs/udf/inode.c      2007-03-01 19:13:09.000000000 +0200
--------------------------
File to patch: udf.ko
patching file udf.ko
Hunk #1 FAILED at 1171.
Hunk #2 FAILED at 1209.
Hunk #3 FAILED at 1839.
3 out of 3 hunks FAILED -- saving rejects to file udf.ko.rej
can't find file to patch at input line 50
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux/fs/udf/osta_udf.h    2007-02-04 20:44:54.000000000 +0200
|+++ linux-2.6.20.1/fs/udf/osta_udf.h   2007-02-06 19:13:52.000000000 +0200
--------------------------

3) Lastly out of desperation I just tried to copy the patch file directly as udf.ko, and that did not work as well

Please HELP!

---

### Post by jackelmatador on 2007-05-21
So after some research I found out I need to actually apply this patch to the orginal source code (duh but I am a noob).  I can download that source in the same place as the patch.  My question then is after compiling the UDF filesystem with the patch applied do I just copy the new UDF.ko to the correct location and everything will work fine?  Do I also need to recompile the kernel?  I haven't done anything yet because I am still at work, but would like to try it tonight.

---

### Post by jackelmatador on 2007-05-22
So I have played with it some tonight and just can't get the stupid thing to compile, so unless I get some help I am out of luck.

---

### Post by jackelmatador on 2007-05-22
HAHAHAHA I have finally found it, now I have to figure out what to charge my work!

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?action=AttachFile&amp;do=view&amp;target=udf.ko](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?action=AttachFile&amp;do=view&amp;target=udf.ko)

Damn I couldn't for the life of me figure how to find that udf.ko file!  Thank You
[http://psubuntu.com/forum/viewtopic.php?p=1033&sid=8a19d7147843206afce828c01db377fc](http://psubuntu.com/forum/viewtopic.php?p=1033&sid=8a19d7147843206afce828c01db377fc)

I will try tonight and cross my fingers.

---

### Post by dvdgorila on 2007-06-12
any luck with this? i tried copying the file to the respective folder but no joy.

---

### Post by ac4000 on 2007-06-21
Patched udf.ko for 7.04 with 2.6.20-16.  Unzip and put in /lib/modules/2.6.20-16-generic/kernel/fs/udf (or the appropriate).  Should mount just fine with "mount /dev/scd0 /media/hddvd" or equivalent.  This worked for me with the above kernel revision; couldn't find it online except for -15, so I compiled this one.  YMMV, of course.

---

### Post by sl1pkn07 on 2007-07-27
very thanks!!

---

### Post by tribble222 on 2007-09-26
> **ac4000 said:**
> Patched udf.ko for 7.04 with 2.6.20-16.  Unzip and put in /lib/modules/2.6.20-16-generic/kernel/fs/udf (or the appropriate).  Should mount just fine with "mount /dev/scd0 /media/hddvd" or equivalent.  This worked for me with the above kernel revision; couldn't find it online except for -15, so I compiled this one.  YMMV, of course.

Thanks! You rock!!

---

### Post by BLKMGK on 2007-12-22
Has anyone gotten this working on Gutsy 7.10? Kernel is 2.6.22-14-generic on this distro (Mythbuntu). I see the source [patch]("http://sourceforge.net/project/showfiles.php?group_id=295") on Sourceforge but am honestly not yet up to compiling my own kernel:(

---

### Post by cipitin on 2008-01-01
I couldn't find a udf 2.5 module for gutsy anywhere so I downloaded the kernel source, applied the patch from [http://sourceforge.net]("http://sourceforge.net/tracker/index.php?func=detail&aid=1738126&group_id=295&atid=300295"), and compiled the kernel module myself.  I'm using mythbuntu version 7.10 with 2.6.22-14-generic kernel.  Unzip and copy to appropriate location.  Be sure to back up your original udf.ko file before overwriting it with this one in case it doesn't work for you.

---

### Post by BLKMGK on 2008-01-02
Wow, THANK YOU!

If I could trouble you a little more, would you mind checking out this [thread]("http://ubuntuforums.org/showthread.php?t=652349")? I attempted to do much the same thing you did, even found that I didn't need a kernel recompile as I'd assumed just the one module, but all the source I was finding for the kernel was wrong?:confused: Apparently you had no issue which makes me wonder what I've screwed up:mad: I suspect that possibly ENVY installed the wrong source but even pulling down kernel source via the package manager didn't help. If you've got _any_ ideas I'd appreciate hearing them! 

At some point I need to be able to do this myself and be more self relient - you've certainly shown me it's possible to compile this code and that it's my setup. I want to tackle getting a wireless XBOX 360 running on a patched XPAD module next! :)

Again, a big thank you - I was just about to install full on desktop Ubuntu with all the trimmings to another machine or a VM in order to make another run at this. You've saved me a good bit of work I think, much appreciated!

---

### Post by emk2203 on 2008-01-12
Thanks for the precompiled module!

One issue remains for me, however: In contrast to the older UDF discs I have, this one with 2.50 mounts ro only. I browsed through your sourceforge link, but couldn't find an answer.

According to fstab, it should mount as user, so I am stuck. Any insight on this?

---

### Post by pwn on 2008-02-18
Why didn't I see this post before :[

I've been trying to get this to work since October. Thanks for this :D

---

### Post by addisor on 2008-02-18
Will this patch work on 7.10 64bit?

---

### Post by HellSpawn on 2008-04-04
Anybody  has a udf.ko for 64bit ubuntu 7.10??:(:confused::confused:

---

