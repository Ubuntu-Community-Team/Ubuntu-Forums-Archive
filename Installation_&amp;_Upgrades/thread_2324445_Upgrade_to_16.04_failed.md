---
title: "Upgrade to 16.04 failed"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by TicoJohn on 2016-05-13
I have an Intel NUC5i5RYH and have been running Lubuntu 15.10 for several months with NO PROBLEMS. Today I went ahead and allowed the installer to upgrade to 16.04.  BAD IDEA! On restart the computer failed to restart. I see an error message "unsupported splx structure" . I have no idea what that means, but it probably means that I will have to re-install 15.10 .  I AM NOT A HAPPY CAMPER !  I have pretty much enjoyed using Lubuntu to this point, but I have to say that all the years I have used Debian I have never had a failure on upgrading.

---

### Post by vasa1 on 2016-05-14
> **TicoJohn said:**
> I have an Intel NUC5i5RYH and have been running Lubuntu 15.10 for several months with NO PROBLEMS. Today I went ahead and allowed the installer to upgrade to 16.04. BAD IDEA! On restart the computer failed to restart. I see an error message "unsupported splx structure" . I have no idea what that means, but it probably means that I will have to re-install 15.10 .  I AM NOT A HAPPY CAMPER !  I have pretty much enjoyed using Lubuntu to this point, but I have to say that all the years I have used Debian I have never had a failure on upgrading.
Searching the net for "unsupported splx structure" throws up some results but I don't know which would relevant to your case:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1510616](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1510616)

Did you try a live USB of 16.04 before upgrading?

---

### Post by TicoJohn on 2016-05-14
No, I did not try a live version before upgrading. If I had the live version of 6.04 I would have tested first. I will probably try to install 15.10 again, as I have the live version. Fortunately I made a backup of /home before trying to upgrade. I hae searched all over the internet for a solution and most things point towards a problem with WiFi. Not sure why there would be a problem when going from 15.10 to 16.04 unless something became unsupported in the kernel. I don't use WiFi, even though the NUC has WiFi built in.

---

### Post by kansasnoob on 2016-05-14
I would first try booting the older kernel from the advanced grub boot menu. 15.10 will only be supported for another two months so it makes sense to try and troubleshoot this.

---

### Post by TicoJohn on 2016-05-14
Well, I have already re-installed 15.10.  I will download the "live" version of 16.04 and see if it boots. I will then, hopefully, be able to give some meaningful feedback on this issue.

---

### Post by TicoJohn on 2016-05-14
I downloaded 16.04 and put in on a USB stick (using dd). 16.04 booted and seemed to work, although there was no audio (probably need to install pulseaudio as I had to do with 15.10). However, when I shut down and then booted back in to 15.10 there were some issues. 
1) My FireFox browser settings were changed.
2) There was no audio in the browser. 
I don't understand why booting from the USB stick would make changes to my hard drive. I'm not real keen on installing 16.04 at this point. As I only use the NUC as a Home Theater PC, and occasional web browsing, I am not real worried about updating.  But if someone could tell me why the changes were made to the HDD I would really like to understand.

---

