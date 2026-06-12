---
title: "error message : file not found in grub"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by wayne4 on 2013-10-02
Hello all,

I am currently attempting an usb install of ubuntu v.13 (raring ringtail) on a live version of 9.10 (karmic koala) and am getting the message:

"error : file not found

Press any key to continue. .."


...from grub when booting, and when I press a key, it takes me back to the grub menu to select which os to boot.

I've searched through the forums and came across similar problems,  only in the others the message describes which file is missing. This one leaves me with no direction or filename. Anyone else have this problem, or can offer any advice?

Many thanks in advance

---

### Post by wayne4 on 2013-10-02
Small update, I renamed the isofile to match the filename completely
i e. set isofile="/boot/isos/_ubuntu.iso_"
-to-
set isofile="/boot/isos/_ubuntu-13.04-desktop-i386.iso_"

...and got a little more info back:


     [Linux-bzImage, setup=0x4200, size=0x51a230]
error : file not found

Press any key to continue. ..


Hope this helps

---

### Post by mörgæs on 2013-10-02
> **wayne4 said:**
> 
I am currently attempting an usb install of ubuntu v.13 (raring ringtail) on a live version of 9.10 (karmic koala) and am getting the message:


Do you mean that you have 9.10 installed on the hard disk and want 13.04 in stead?

---

### Post by oldfred on 2013-10-02
Are you using grub2 to loopmount ISO directly?
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by wayne4 on 2013-10-03
> **mörgæs said:**
> Do you mean that you have 9.10 installed on the hard disk and want 13.04 in stead?

Yes, sorry for the confusion

---

### Post by mörgæs on 2013-10-04
'Live' means that Buntu runs in memory as opposed to being installed on the hard disk. 

Please post a complete hardware description.

---

### Post by wayne4 on 2013-10-06
> **oldfred said:**
> Are you using grub2 to loopmount ISO directly?
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)


The above links helped, I manually entered the menuentry in GRUB2 from the flashdrive and it created the menuentry just fine (no warnings or errors)

then as I booted the iso, it said: 

```
error: You need to load the kernel first.

Press any key...
```

---

### Post by oldfred on 2013-10-06
Something in the grub boot stanza is not correct. You have to have correct drive, usually hd0 if same as boot drive, you have to have correct partition usually hd0,1 as most have only one partition. Then you will have sda1 as device. 
Or you may have a typo in something else.

---

### Post by wayne4 on 2013-10-07
Working now!
Mounted the iso on the USB using syslink and unetbootin on separate Mac OS then booted from unetbootin and everything ran smoothly.

Thank you for the help!

---

### Post by mörgæs on 2013-10-08
Good, but did you notice Oldfreds signature?

---

