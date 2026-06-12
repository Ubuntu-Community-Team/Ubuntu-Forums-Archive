---
title: "Can't REinstall 10.10 from USB stick"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by demonboy on 2010-11-12
Hello,

I would like to reformat my hard drive and reinstall 10.10 desktop from a stick. However when I try and boot from the stick it comes up with the SysLinux 4.0... one liner and hangs. I have tried:

- different usb sticks
- running as ISO
- mounting ISO using Startup disk creator
- finding the known Bug re something similar and deleting the first two letters in the last line of a certain file wihtin the syslinux folder

I am currently running 10.10 - is this why it ignores it? I'm not understanding something, obviously, so any help much appreciated.

---

### Post by sikander3786 on 2010-11-12
Did you check the MD5SUM for your Ubuntu Image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also see this one,

[http://ubuntuforums.org/showthread.php?t=1582312](http://ubuntuforums.org/showthread.php?t=1582312)

If everything else fails, you can try unetbootin. Download latest version here.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by demonboy on 2010-11-12
Hi

I used unetbootin but to no avail. I tried downloading the ISO again just to make sure. Also I have saved the link you provided on how to MD5SUM for future reference, so thanks for that.

In the end I followed another thread on wiping the hard disk from within Terminal and am now  doing a clean install. I'm having to do this because the install I did was a bit 'quirky'. For example when clicking 'ok' on a window, it wouldn't disappear. Also I had some problems with Samba. I know they were problems because I have just done an install on my own almost identical netbook and mine runs perfectly. No great shakes as it's a new netbook with no data on it.

Thanks once again for the links.

---

