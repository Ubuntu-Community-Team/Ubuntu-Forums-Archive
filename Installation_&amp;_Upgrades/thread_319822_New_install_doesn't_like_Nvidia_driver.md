---
title: "New install doesn't like Nvidia driver"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by goldenatom on 2006-12-16
I just did a new install and I can't seem to get the Nvidia driver to work quite right. Everytime I boot up I get a message saying X has failed to start up. When I look at the error message it tells me that the Nvidia kernal version and the driver version don't match up. If I put in ```
 sudo rmmod nvidia && sudo modprobe nvidia 
``` and then ```
sudo /etc/init.d/gdm restart
``` everything works just fine. But on the next boot up I have to do it again. What am I doing wrong here?

---

### Post by goldenatom on 2006-12-16
I should have said that I'm using a geforce ti4200. On my last install I was using the nvidia beta driver, but apparently theres a new beta driver. When I tried to install that one, it told me I had an unsupported card. I used the non-beta driver .9631 I believe.

---

### Post by goldenatom on 2006-12-16
Any ideas out there? This is driving me nuts.

---

### Post by goldenatom on 2006-12-18
I've tried all three nvidia drivers that are listed in the beryl wiki. The newest beta (9742) says my card is unsupported. The 9629 works, but I get errors when I try using beryl. The 9631 works, but gives me the errors I mentioned before when I reboot. Is there any place where I can get the old beta driver? That one worked just fine. I'm going nuts here...

---

### Post by Bear Knuckle on 2006-12-19
> **goldenatom said:**
> I've tried all three nvidia drivers that are listed in the beryl wiki. The newest beta (9742) says my card is unsupported. The 9629 works, but I get errors when I try using beryl. The 9631 works, but gives me the errors I mentioned before when I reboot. Is there any place where I can get the old beta driver? That one worked just fine. I'm going nuts here...

Same problem here. It seems like the kernel-module is resettet after every boot-time.

What is wrong here?

---

### Post by awlllwa on 2007-03-07
I have the same problem as well, same card but i have the 64mb version.  the only problem is im a linux newb so since it was a new ubuntu install i just reinstalled.  I didnt know the commands to reset x.

---

### Post by goldenatom on 2007-03-08
Did that fix your problem? Moving to Feisty fixed it for me.

---

