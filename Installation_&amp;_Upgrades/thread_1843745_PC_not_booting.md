---
title: "PC not booting"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by kulkarniniraj on 2011-09-13
Hi,
   I've recently reinstalled winXP. Then to recover ubuntu I did grub-install. But since then, I am not able to boot any OS. It doesnt show grub menu nor does it go to XP directly. It only shows a black screen and stays there. So I think MBR is modified but in some wrong way.

   Important thing is that I had ubuntu 10.04 previously, now upgraded to 10.10. But I tried to install grub through 10.04 live USB, is it root cause of problem? By the way I've checked that both (installed one and live USB) grub versions are GRUB2. SO no grub mismatch there.

   Any idea, how to resolve this problem?

Thank you
Niraj

---

### Post by 2F4U on 2011-09-14
This article states

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

that you should restore grub with that liveCD that fits your currently used version of Ubuntu. So, your problems may stem from using an older liveCD.

---

### Post by garvinrick4 on 2011-09-14
> **kulkarniniraj said:**
> Hi,
   I've recently reinstalled winXP. Then to recover ubuntu I did grub-install. But since then, I am not able to boot any OS. It doesnt show grub menu nor does it go to XP directly. It only shows a black screen and stays there. So I think MBR is modified but in some wrong way.

   Important thing is that I had ubuntu 10.04 previously, now upgraded to 10.10. But I tried to install grub through 10.04 live USB, is it root cause of problem? By the way I've checked that both (installed one and live USB) grub versions are GRUB2. SO no grub mismatch there.

   Any idea, how to resolve this problem?

Thank you
NirajHave you got your machine booting? Usually boot problems are handled very fast in this Forum. Somehow you slipped through the cracks, does not usually happen, we apologize. Let us know if you got your machine booting?

---

### Post by kulkarniniraj on 2011-09-14
I am trying to find liveCD/USB of 10.10 I will let you know once I try restoring grub from it. By the way response in 4-5 hrs is still a pleasant experience, so don't worry about that.

---

### Post by garvinrick4 on 2011-09-14
If you can run this boot_info_script as in link below, it will be relatively easy to
diagnose the problem. 10.04 disk should do, we can install and then upgrade if have to
once booted. Use the live cd (install Cd using Try ubuntu) and download this script to desktop and extract it. Will get a script after extracted called boot_info_script.sh make sure it is on Desktop.
Then run these commands copy and paste would be easiest.
```
cd Desktop
``````
chmod +x boot_info_script.sh
``````
sudo ./boot_info_script.sh
```Will now have a file called RESULTS. copy and paste to this thread. Will be easier to read
if after pasted highlight whole thing and hit # sign in upper right of message box, will put
in a nice little box that way. Below is site to download boot_info_script in a zip file. If have any problem just say so.


[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by kulkarniniraj on 2011-09-14
> **2F4U said:**
> This article states

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

that you should restore grub with that liveCD that fits your currently used version of Ubuntu. So, your problems may stem from using an older liveCD.

Thanks for that. This solved my problem.

---

### Post by garvinrick4 on 2011-09-14
Please marked as Solved so others may benefit from the link you used, enjoy your Ubuntu. Thread tools in upper left to mark as Solved.

---

