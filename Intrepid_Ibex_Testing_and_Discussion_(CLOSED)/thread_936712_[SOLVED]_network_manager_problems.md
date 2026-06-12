---
title: "[SOLVED] network manager problems"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-10-03
I still have a problem with network manager.

Firstly I did not suffer from the network manager asking for a password on boot that has never been an issue - my problem is as follows:

1. On resuming from suspend network manager tries to connect but fails and after a while times out, asks for my WPA key and tries again. It never connects.
2. The above problem also occurs when 'restarting' the laptop.

The only way to get NM to connect is from a power down situation.

Driver is ath_pci

---

### Post by wilsong on 2008-10-03
Try updating your NM to the one I listed in this forum, i know its for the not connecting issue, but it should hopefully resolve your wpa, issue too (crosses his fingers) 
[http://ubuntuforums.org/showthread.php?t=934575&page=2](http://ubuntuforums.org/showthread.php?t=934575&page=2)

---

### Post by Peter09 on 2008-10-03
No - I think the thread that you have posted is about having to re-enter the key everytime, that is not the same problem that I have.

---

### Post by wilsong on 2008-10-03
yes i know it is, but there is a newer version of NM, that I think also corrected your bug too.. i was reading about the WPA thing on launchpad and it recommended the same network manager, i would recommend trying it atleast couldnt hurt ;)

---

### Post by FuturePilot on 2008-10-03
> **Peter09 said:**
> I still have a problem with network manager.

Firstly I did not suffer from the network manager asking for a password on boot that has never been an issue - my problem is as follows:

1. On resuming from suspend network manager tries to connect but fails and after a while times out, asks for my WPA key and tries again. It never connects.
2. The above problem also occurs when 'restarting' the laptop.

The only way to get NM to connect is from a power down situation.

Driver is ath_pci

I have the same problem. The same exact thing happens. At first I thought it was a Network Manager problem because it kept asking for my password. I installed the new build of Network Manager from the repo mentioned above. It did fix the problem of NM not remembering the password but this other problem remains. I'm also using ath_pci. I'm starting to think it may be a driver issue.

---

### Post by wilsong on 2008-10-03
> **FuturePilot said:**
>  but this other problem remains. I'm also using ath_pci. I'm starting to think it may be a driver issue.


darn, I will check and see what i can find, sorry that it didn't work, Ill be back with more info if i can..

---

### Post by Peter09 on 2008-10-03
Yes, I believe that I am at the new version of NM, I think it came down ths morning. The failure to resolve my problem prompted me to write the thread.

---

### Post by wilsong on 2008-10-03
Hey Peter Check out I know it hardy but it sounds familiar ;), if you want to open a new bug for it.. i didnt see one, thats about the closest thing i could find! 

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/192058](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/192058)

---

### Post by Peter09 on 2008-10-03
Firstly thanks for the help.

I looked at the thread and was somewhat confused by the description of the problem, there seemed to be a mixture of 'cannot see the networks' to cannot connect, so this may be the same bug.

Also could not understand whether it was going to be fixed or was fixed.

---

### Post by wilsong on 2008-10-03
> **Peter09 said:**
> Firstly thanks for the help.

I looked at the thread and was somewhat confused by the description of the problem, there seemed to be a mixture of 'cannot see the networks' to cannot connect, so this may be the same bug.

Also could not understand whether it was going to be fixed or was fixed.

Well it looked like it was from hardy, and it look like the guys problem got fixed with an update, he was running 0.65 Network Manager, and now we have .7 NM... thats probably good enough reason to post your own bug, they might ask you to perform task to see whats causing it, if i had your same setup i would post the bug, but i dont have the hardware.. if you need help setting up a launchpad account or posting the bug just ask.. hope all goes well!

---

### Post by Peter09 on 2008-10-03
Thanks,
I have a launchpad account but have never posted a bug before, I'll give it a try

---

### Post by FuturePilot on 2008-10-03
**This has been fixed. ath5k is no longer available in the kernel, but in the linux-backports-modules package. These instructions are no longer needed.**
Ok after some searching and experimenting I think I've nailed it. It seems to be this bug:
[https://bugs.launchpad.net/ubuntu/+bug/262516]("https://bugs.launchpad.net/ubuntu/+bug/262516")

It looks like the 2.6.27 kernel is loading the ath_pci driver by default which is conflicting with the ath5k driver. I got my wireless working by blacklisting the ath_pci stuff.

If you want to give it a try add this to the bottom of /etc/modprobe.d/blacklist
```
blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal

```
Then reboot and try connecting.

---

### Post by Peter09 on 2008-10-03
Yes, just done a reboot and it worked, great, another bug down.

Thanks to all

---

