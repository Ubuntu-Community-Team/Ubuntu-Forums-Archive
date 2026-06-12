---
title: "Installing on new Inspiron 7559"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by chris_heatley on 2016-01-26
I recently purchased a dell inspiron 7559 with a core i5-6300HQ processor.

I am looking for information on getting a kernel appropriate for my laptop, and any specific install instructions.

Thanks!

---

### Post by QDR06VV9 on 2016-01-26
> **chris_heatley said:**
> I recently purchased a dell inspiron 7559 with a core i5-6300HQ processor.

I am looking for information on getting a kernel appropriate for my laptop, and any specific install instructions.

Thanks!
That's pretty vauge(kernel??)
Any way see if this sheds any light...[http://askubuntu.com/questions/689380/dual-boot-on-dell-inspiron-7559-laptop/691750](http://askubuntu.com/questions/689380/dual-boot-on-dell-inspiron-7559-laptop/691750)
You would probably want Ubuntu 15.10 or any DE that suit's your taste.
Another Link to Veiw....[http://software.techforums.space/software/ubuntu-1510-on-dell-inspiron-7559-f97a840a.html](http://software.techforums.space/software/ubuntu-1510-on-dell-inspiron-7559-f97a840a.html)

---

### Post by grahammechanical on 2016-01-26
As a general rule, the newer the hardware the newer the Linux distribution.

As for instructions, a lot will depend on whether the machine comes with another OS pre-installed or not.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by chris_heatley on 2016-01-26
Thanks.  I am vague as I haven't used Linux in a long time.  I have heard that there is a kernel "ready to go" for this laptop with no driver issues.

I just want whatever is easiest to install so that I can begin re-familiarizing myself with the environment of Linux.

---

### Post by QDR06VV9 on 2016-01-26
Ubuntu 15.04 (say to the current Linux 4.2 mainline kernel PPA) or run likely any other modern distribution out there, you won't get kernel mode-setting support and working 3D acceleration for Skylake's HD Graphics... You'll get a low resolution display and fall-back to the LLVMpipe Gallium3D driver. Yes, even with modern kernels. 

On Ubuntu the latest mainline kernel (they're stock kernel avoids this issue)** you need to append to your kernel command-line**: i915.preliminary_hw_support=1. When adding that to your kernel command-line in GRUB (or editing your GRUB configuration for it to be persistent) the i915 DRM driver initialized fine on these kernels and lit up the i5-6600K's HD Graphics 530 just fine. With Linux 3.19, 4.0, and 4.2 are the kernels tested so far. 
From this forum [http://ubuntuforums.org/showthread.php?t=2307347](http://ubuntuforums.org/showthread.php?t=2307347)
Just a heads up..

---

### Post by chris_heatley on 2016-01-26
Would I be able to get support for my GeForce gtx 960?  I thought there was some kind of "thing" that I could install that is already specific to this particular laptop?  I am just unfamiliar with the process of finding it, and searching inspiron 7559 didn't return anything helpful that I could find

---

### Post by QDR06VV9 on 2016-01-26
[COLOR=#000000]From this forum [/COLOR][http://ubuntuforums.org/showthread.php?t=2307347](http://ubuntuforums.org/showthread.php?t=2307347)
And Here.....[http://software.techforums.space/software/ubuntu-1510-on-dell-inspiron-7559-f97a840a.html](http://software.techforums.space/software/ubuntu-1510-on-dell-inspiron-7559-f97a840a.html)
And if I find any thing else Relevant I will post here..
Kind Regards and Good Luck

---

### Post by chris_heatley on 2016-01-26
Many thanks for your time! I will let you know how I do once I finish reading that stuff.  I have a partition set aside (from my windows 10 drive) but wanted to make sure I had good info before installing.

---

