---
title: "Ubuntu won't install"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by sophie2cu2 on 2012-02-04
Hi everybody,

I've been using Wubi in Windows for a while. As it's a bit clunky, I decided to do the full Ubuntu install and get rid of Windows completely.

Can't do it. Prepared a CD and rebooted my PC. Once I get past an initial purple screen with a couple of little images at the bottom, all I get is a screen of garbage (well, it is for me as I know nothing about computers).

Here's an example of what I get:

[ 4.989652]  [<c152cfcf>] ? error_code+0x67/0x6c
[ 4.989700]  [<c128683b>] ? vsnprintf+0x2eb/0x390

etc, etc, etc. There are about 20 lines of this stuff and it seems to stop once the screen is full.

Can anybody help? I really would like to get rid of Windows.

Many thanks,
Sophie

---

### Post by QIII on 2012-02-04
Did you check the md5sum against what is given where you downloaded the image?  That would be something to check right up front -- make sure your image is good.  That may not be it at all, but we can start there.


[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sophie2cu2 on 2012-03-23
Hi QIII,

I tried to check the md5sum but didn't get very far. The instructions seem to assume that Ubuntu is already installed. They don't seem to work in Windows. Also, as a complete beginner, I'm finding the instructions a bit hard to get through.

Sorry for the delay in replying - lots of other work.

Any other suggestions?

Thanks,
S

---

### Post by bfmetcalf on 2012-03-23
To check the MD5 in windows you need to download something to allow it I believe.  Google "check md5sum in windows" and you should find some good instructions.

---

### Post by Quackers on 2012-03-23
When this screen of script appears is it on a black background and do your caps lock and num lk lights flash?

---

### Post by sophie2cu2 on 2012-04-05
Hi Quackers,
Black background, and caps come on and stay on. But no flashing.
Does it ring any bells for you?
Thanks,
Sophie

---

### Post by 2F4U on 2012-04-05
> **sophie2cu2 said:**
> Hi QIII,

I tried to check the md5sum but didn't get very far. The instructions seem to assume that Ubuntu is already installed. They don't seem to work in Windows. Also, as a complete beginner, I'm finding the instructions a bit hard to get through.

Sorry for the delay in replying - lots of other work.

Any other suggestions?

Thanks,
S

Check md5sum in Windows:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by sophie2cu2 on 2012-04-12
Hi all,
Md5sum is too complicated for me.
Anyway, I think it may be a hardware problem: I tried the CD I made on another PC and it ran fine. So apparently there are no probs with the CD.
Has anybody any suggestion on how to install Ubuntu by some other means other than a CD?
Many thanks,
S

---

### Post by IHeequ5i on 2012-04-12
I made a bootable usb drive to do my installs with.  I also (accidentally) made a bootable memory card. 

With CDs, Ubuntu is very sensitive to burn speed. You might have better luck if you burn it again at your lowest possible speed.

---

### Post by sophie2cu2 on 2012-04-21
Hi everybody,
I give up. Nothing works. Whatever I try, CD or USB, or even reinstalling Wubi and trying to do it from there, I can't get Ubuntu to install.
But anyway, thanks for all your help and suggestions.
Are there any magicians out there?
S

---

### Post by ex_isp on 2012-04-21
Sophie, you might also try a slightly different version like Mint or Zorin.  There are some supported hardware differences.

Best of luck!

---

