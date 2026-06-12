---
title: "Error screen when trying to boot from CD"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by applescruff on 2010-09-04
I am a newbie (obviously, since this is an installation problem) and slightly computer illiterate in general.

I tried to boot from the installation CD I burned.  At first I thought it was going to work because I got a purple screen with the Ubuntu logo on it, but then it changed to an MSDOS-looking screen (white text on black screen) with the following message:

(initramfs) mount : mounting /dev/loop0 on //filesystem.squashfs failed : Input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs



I don't know if you need any of my computer info, my current OS is 64-bit Vista, trying to install 32-bit Ubuntu

---

### Post by applescruff on 2010-09-04
Could the ISO have not been burned to disk correctly? I notice that while it's downloading it says the file size is 686 MB but then when it's done, it says 206 MB.  I have downloaded the ISO twice with same result.

---

### Post by plucky on 2010-09-05
See [Howto Md5sum](https://help.ubuntu.com/community/HowToMD5SUM)

Or 

Use a [Bittorrent](https://help.ubuntu.com/community/BitTorrent) to download the Iso.

Also burn the image to CD at the slowest speed possible.

Good luck

---

### Post by gibbogle on 2010-09-05
> **applescruff said:**
> Could the ISO have not been burned to disk correctly? I notice that while it's downloading it says the file size is 686 MB but then when it's done, it says 206 MB.  I have downloaded the ISO twice with same result.

I had exactly this experience, except that the first iso I downloaded was about 500 MB, not 206 MB.  I downloaded it again and got a much bigger file.  This checked out OK with md5sum, and ran properly.  I don't know why the downloads don't work, perhaps overloaded servers.

---

### Post by applescruff on 2010-09-06
I was hoping to try the md5sum, but there doesn't seem to be a hash for the 10.10 beta version? This might be just as well, as I read the md5sum "how-to" and didn't really understand it.  So I will try bittorrent next.... thank you for your help so far

---

### Post by plucky on 2010-09-06
> **applescruff said:**
> I was hoping to try the md5sum, but there doesn't seem to be a hash for the 10.10 beta version? This might be just as well, as I read the md5sum "how-to" and didn't really understand it.  So I will try bittorrent next.... thank you for your help so far

Look [Here](http://releases.ubuntu.com/maverick/) for Maverick Beta Releases and Md5sums.

Bittorrents have always worked for me.

Good Luck

---

### Post by Morbid Justice on 2010-09-06
Ha, I just posted a thread similar to this one.  I'm having the same issue.  Plucky, I noticed you link and saw that it mentioned something about DVD image installs.  However, I can't seem to find that one.  I don't have a CD to burn to right now.  Can I burn it to a DVD and make it work?

---

### Post by plucky on 2010-09-06
> **Morbid Justice said:**
> Ha, I just posted a thread similar to this one.  I'm having the same issue.  Plucky, I noticed you link and saw that it mentioned something about DVD image installs.  However, I can't seem to find that one.  I don't have a CD to burn to right now.  Can I burn it to a DVD and make it work?

All the images are CD images,but I think you can burn the image to a DVD and it should work.(Very Wasteful unless it is a RW DVD)

Good Luck

---

### Post by Morbid Justice on 2010-09-06
Yes, but I'm kinda in a pickle and need to right now.  Thanks for the help...I was starting to think I was being ignored and I just joined.  Usually it takes at least two posts before I'm ignored. ;)

---

### Post by applescruff on 2010-09-06
I used Bittorrent, the cd took a looooong time to load/boot but ultimately worked.  Thank you.

---

### Post by Morbid Justice on 2010-09-08
I have it installed now.  I can't tell you how excited I am now about Linux again!  Ubuntu is working flawlessly thus far even though I'm using 10.10.  At lest so much better than Opensuse ever did for me.  Thank you for your help.
):P

---

