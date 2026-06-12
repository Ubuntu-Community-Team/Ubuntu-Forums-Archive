---
title: "Trying to install 8800 drivers **FRUSTRATION!**"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by HeXp£Øi± on 2007-08-22
So i installed 7.04 x86 and let the os download and install the driver for my 8800. After installation it fails to boot into the gui. I'd like to manually download the driver from the nvidia website and try it but what do i open the file with?
I'm so damn frustrated i've been trying to get this thing going for half the day. Haven't used Linux since redhat 5.1 and i can't believe it hasn't progressed to the point where it can recognize and open and dang file.

Motherboard eVGA 122-CK-NF68-AR (680i) and videocard is an 8800gts.

Please help prove to me that linux has become something useful besides a hacking box and that i am merely ignorant here.

---

### Post by logos34 on 2007-08-22
Here's the guide you want to use (read down to 'Method 2'):
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

but the servers are down right now, or the link is broken (it worked until recently though)

---

### Post by HeXp£Øi± on 2007-08-22
Thanks for the link. Hopefully it is back up soon. Another question;
How do i access the GUI if a driver fails to install properly? I know that it can be done from the cd but that doesn't access my main install. I realize also that there is a "safe mode" from the boot options but this doesn't access the GUI but only the command line. If i could just access the GUI in safe mode from the hd this probably wouldn't be such a big deal.

---

### Post by logos34 on 2007-08-22
Well I can't seem to find a single mirror for that link I gave you.  darn.  but here's the version for dapper 6.06:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

(Method 2 will give you some idea of the steps you'll go through.) 

And here's a couple more links:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

> How do i access the GUI if a driver fails to install properly? I know that it can be done from the cd but that doesn't access my main install. I realize also that there is a "safe mode" from the boot options but this doesn't access the GUI but only the command line. If i could just access the GUI in safe mode from the hd this probably wouldn't be such a big deal.


You CAN access your disk partitions from the live cd -- they will mount if you just click on them in nautilus browser. 

The 'safe graphics' option on the livecd menu gets me the GUI (in fact it's the only way I can get a screen that isn't all wonky).  [Edit: But the recovery mode kernel boot option on the grub menu gets you the command line only -- no gui safe mode like in Windows.]

To run the nvidia installer (the .run file) you downloaded, you would ordinarily need to halt the gdm and drop to the console, it's just not recommended that you run the installer from within recovery mode.  (I did it once successfully, though)

---

### Post by logos34 on 2007-08-22
Here's a mirror site for that link I gave you (it's on the author's website - duh)

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

