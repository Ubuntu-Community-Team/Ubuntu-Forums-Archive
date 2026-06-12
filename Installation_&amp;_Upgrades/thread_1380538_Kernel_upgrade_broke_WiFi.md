---
title: "Kernel upgrade broke WiFi"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by alanrlow on 2010-01-13
[[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#")Hi all, I'm running Ultimate Edition 2.4 on an Acer Aspire 3500 lappy, yesterday I allowed my system to upgrade the kernel (from 9.10 kernel 2.6.31-17 to 2.6.31-18 generic) as per usual but when it rebooted I had no WiFi. The network manager didn't even have a wireless section, only wired, and I couldn't setup a wireless network either. If I reboot into the earlier 2.6.31-17 kernel everything is OK. 
Another problem is that even tho I have no screensaver enabled and no power saving options enabled, (ie screen never disabled) after a short time of no use the screen goes blank. If within a few minutes I touch the pad or hit a key the screen returns but if it's been an hour or so nothing I do will wake it up,even tho there is still disk activity etc, and the only way to recover is with a hard reset, hold power key to reboot. 
Any ideas?
Thanks,
 
Regards,
Alan.

---

### Post by Drooling_Sheep on 2010-01-14
I have a similar issue with wifi on my acer aspire 1410.  The wifi will work, but it's intermittent and sometimes it kernel panics.  I booted it into 2.6.31-17 and so far everything's working as it should.  The kernel panics were happening when I was disabling/enabling networking with network-manager which would allow the wifi to work again for a short time.  After 2 or 3 of these it would kernel panic and I'd have to reboot.

---

### Post by alanrlow on 2010-01-14
> **Drooling_Sheep said:**
> I have a similar issue with wifi on my acer aspire 1410.  The wifi will work, but it's intermittent and sometimes it kernel panics.  I booted it into 2.6.31-17 and so far everything's working as it should.  The kernel panics were happening when I was disabling/enabling networking with network-manager which would allow the wifi to work again for a short time.  After 2 or 3 of these it would kernel panic and I'd have to reboot.

Not quite the same. After the latest kernel upgrade the NetworkManager Applet 0.7.996 has no Wireless Network shown and at the bottom is missing the Connect to hidden Network and Create New Wireless Network option. They're simply not there as an option. When I boot the earlier kernel everything is ok.

Alan.

---

### Post by Geffers on 2010-01-14
> **alanrlow said:**
> [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#")Hi all, I'm running Ultimate Edition 2.4 on an Acer Aspire 3500 lappy, yesterday I allowed my system to upgrade the kernel (from 9.10 kernel 2.6.31-17 to 2.6.31-18 generic) as per usual but when it rebooted I had no WiFi. The network manager didn't even have a wireless section, only wired, and I couldn't setup a wireless network either. If I reboot into the earlier 2.6.31-17 kernel everything is OK. 

Any ideas?
Thanks,
 
Regards,
Alan.

Linux is a lot better of late but still on occasions this wifi issue occurs.

I've had this before with earlier versions and have never been able to positively resolve it, sometimes a reboot cures the problem but it is annoying.

At least you are able to boot the older kernel.

Geffers

---

### Post by alanrlow on 2010-01-16
> **Geffers said:**
> Linux is a lot better of late but still on occasions this wifi issue occurs.

I've had this before with earlier versions and have never been able to positively resolve it, sometimes a reboot cures the problem but it is annoying.

At least you are able to boot the older kernel.

Geffers

Thanks for the reply. In my case a reboot does nothing, the NetworkManager Applet 0.7.996 has no wireless networks shown, only wired networks. It's like it's forgotten all about wireless. 
You're right, I can boot the earlier kernel but I want t boot the new one because if I miss interrupting GRUB it will boot the new one and then  I have to reboot to select the earlier kernel.

Alan.

---

### Post by falconindy on 2010-01-16
> **alanrlow said:**
> [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#")Hi all, I'm running Ultimate Edition 2.4 on an Acer Aspire 3500 lappy, yesterday I allowed my system to upgrade the kernel (from 9.10 kernel 2.6.31-17 to 2.6.31-18 generic) as per usual but when it rebooted I had no WiFi. The network manager didn't even have a wireless section, only wired, and I couldn't setup a wireless network either. If I reboot into the earlier 2.6.31-17 kernel everything is OK. 
Another problem is that even tho I have no screensaver enabled and no power saving options enabled, (ie screen never disabled) after a short time of no use the screen goes blank. If within a few minutes I touch the pad or hit a key the screen returns but if it's been an hour or so nothing I do will wake it up,even tho there is still disk activity etc, and the only way to recover is with a hard reset, hold power key to reboot. 
Any ideas?
Thanks,
 
Regards,
Alan.
Sounds like you installed an extra module for your network driver. You'll need to do that for every new kernel.

---

### Post by mikerobinson on 2010-01-18
I am having a similar problem after latest kernel upgrade on my Acer TravelMate 2310. The wireless section does not even show up. Booting to 2.6.31-17 or earlier kernels "fixes" the problem, but a real fix would be better. 

I have also never manually installed kernel modules for anything on this computer and I have upgraded only through the package managers and have about 6 kernels installed. All work fine but the latest one. It must be a bug in the latest kernel.

---

### Post by alanrlow on 2010-01-18
> **mikerobinson said:**
> I am having a similar problem after latest kernel upgrade on my Acer TravelMate 2310. The wireless section does not even show up. Booting to 2.6.31-17 or earlier kernels "fixes" the problem, but a real fix would be better. 

I have also never manually installed kernel modules for anything on this computer and I have upgraded only through the package managers and have about 6 kernels installed. All work fine but the latest one. It must be a bug in the latest kernel.

Yep, that agrees exactly with my experience. I can't imagine we are alone so I hope a fix is coming soon. I don't understand how these problems can be released for something that has been rock solid for ages. 

Do you also have the problem of DPMS blanking the screen after 10 minutes and not being able to recover without a reboot?
An inelegant solution I have found is to enter "xset -dpms" in a terminal. Mind you it's isn't permanent and can revert at whim.

Alan.
PS: The Update Manager has just popped up, I wonder what it wants to break now?  ;-(

---

### Post by alanrlow on 2010-01-18
> **falconindy said:**
> Sounds like you installed an extra module for your network driver. You'll need to do that for every new kernel.

Nope, nothing extra installed. Has always worked faultlessly from day one, no need to install anything, let upgrade manager do its thing the other day, bingo, NO WIRELESS!! Boot the earlier kernel, every-thing's fine..

Alan.

---

### Post by mikerobinson on 2010-01-18
> **alanrlow said:**
> Do you also have the problem of DPMS blanking the screen after 10 minutes and not being able to recover without a reboot?

I think this has always randomly happened for me using any kernel, but I do remember it doing it with the newest kernel the other day as well. I usually have suspend/hibernate disabled though.

---

### Post by 8086 on 2010-01-26
My flatmate (also using Acer) lost WIFI after "upgrading" to 2.6.31-18.

---

### Post by alanrlow on 2010-01-26
> **8086 said:**
> My flatmate (also using Acer) lost WIFI after "upgrading" to 2.6.31-18.

Has he managed to fix it yet? Is there a fix for it or do I have to boot the earlier kernel until the next release? And hope it's been fixed again..

---

