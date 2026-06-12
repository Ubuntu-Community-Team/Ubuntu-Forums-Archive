---
title: "Install won't even start"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by nelmo2 on 2016-09-02
Hi,

Trying to install Ubuntu onto my Windows 7 PC. I don't want Windows to stay but I cannot get my laptop to boot from either the CD or USB. It just boots straight into Windows every time.

I have edited my BIOS settings to put the CD and the USB drive before the hard drive but no luck.

I have the mini.iso install files burnt onto the CD and the full installation kit on the USB pen - nada.

Any ideas?

---

### Post by ubfan1 on 2016-09-02
Did you hashcheck the isos you downloaded?  How did you burn the media?  Do the media work on other computers?

---

### Post by nelmo2 on 2016-09-02
I didn't hashcheck it because the instructions for doing that assume you already have a UNIX environment available, which I don't. I only have the one laptop which only has Windows 7 on it. If that was the issue, wouldn't I at least get some error message?

The instructions just said 'burn the mini.iso to a CD', which seemed strange as it was zipped. So I extracted it first and then copied the extract AND the zipped file to the CD, just in case. I burnt it just using Windows explorer.

---

### Post by mook765 on 2016-09-02
Copying the files to CD will not work. Here is some information how do do the thing with Win7:
[https://technet.microsoft.com/en-us/magazine/dd451080.aspx](https://technet.microsoft.com/en-us/magazine/dd451080.aspx)

---

### Post by nelmo2 on 2016-09-02
Yes, I was just working that out. The problem is that when I downloaded the install (I'm doing the mini version), I got a zipped file, not an ISO image. Is this right? Or is there a way to extract the zip into an ISO image?

---

### Post by yancek on 2016-09-02
Where did you get the iso?  The Ubuntu site below is where you should get it and it will be named mini.iso.  Don't know how you got a zip file.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

There appears to be a utility installed with windows 7 to do an md5 checksum, certutil.  See the link below for examples of how to use it.

 [http://superuser.com/questions/245775/is-there-a-built-in-checksum-utility-on-windows-7/898377#898377](http://superuser.com/questions/245775/is-there-a-built-in-checksum-utility-on-windows-7/898377#898377)

---

### Post by nelmo2 on 2016-09-02
OK, all sorted - I just right-clicked on the zipped file and burnt it to the disc. Install worked fine (I'm writing this from Ubuntu!).

Thanks for the replies...

---

