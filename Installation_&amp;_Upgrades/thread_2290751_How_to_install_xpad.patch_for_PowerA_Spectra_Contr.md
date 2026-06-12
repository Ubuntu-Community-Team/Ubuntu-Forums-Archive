---
title: "How to install xpad.patch for PowerA Spectra Controller"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2015-08-14
All,
I running Ubuntu 14.04.3, kernel 3.19.0-26-generic #27~14.04.1-Ubuntu SMP and can't get the PowerA Spectra Controller to work. The product code/vendor info is  "0x24c6, 0x542a, PowerA Spectra Controller. , 0, XTYPE_XBOXONE ".

I searched on Internet and found that the same problem here: [http://superuser.com/questions/880462/editing-xpad-c-of-the-3-18-kernel-for-xbone-pad-support](http://superuser.com/questions/880462/editing-xpad-c-of-the-3-18-kernel-for-xbone-pad-support)

It looks like there needs to be a patch to xpad to make it work. Here: [https://gist.github.com/benbancroft/2a5d9bca700c29615f4d](https://gist.github.com/benbancroft/2a5d9bca700c29615f4d)

Can you guys kindly provide the steps to install this path?


Thanks so much in advance.

Best Regards!

---

### Post by dino99 on 2015-08-15
[http://ubuntuforums.org/showthread.php?t=1624005](http://ubuntuforums.org/showthread.php?t=1624005)

---

### Post by webusr1 on 2015-08-15
Thanks for the Link to "How to install .patch file". I have one more question regarding the original files.

I assume that the original file is xpad.c. and I understand that I have find it and place it in the same directory with xpad.patch before running patch p1 xpad.patch.  However, where can I find xpad.c and are there any .h files too?

Thanks again.

---

