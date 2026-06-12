---
title: "Convert WUBI Ubuntu 10.10 to Standard Ubuntu install"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by RTG1987 on 2010-11-21
Hi,

I installed ubuntu 10.10 using wubi installer, on win 7 64 bit system.
Can you please tell me how can I migrate from wubi install to standard install.
Please help me I want to get rid of issues like free disk space and suspend/hibernate not supported in wubi ubuntu.
Will LVPM help. I saw on the page it says that it does not supports wubi 10.04. Not sure what version I have, just installed the latest from ubuntu's site.

Thanks a million,
RTG

---

### Post by bcbc on 2010-11-21
> **RTG1987 said:**
> Hi,

I installed ubuntu 10.10 using wubi installer, on win 7 64 bit system.
Can you please tell me how can I migrate from wubi install to standard install.
Please help me I want to get rid of issues like free disk space and suspend/hibernate not supported in wubi ubuntu.
Will LVPM help. I saw on the page it says that it does not supports wubi 10.04. Not sure what version I have, just installed the latest from ubuntu's site.

Thanks a million,
RTG

Shrink the windows partition using Windows 7 tools. Prepare the new partition space, creating an extended partition, then inside create two logicals, one for root, one for swap. Then follow this guide to migrate: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Note: some computers come with 4 primary partitions used up. You need to be able to create a new one, so 3 or less and you'll be ok. 

For hibernate the swap partition must be > RAM. I recommend size of RAM + 1GB. (Or minimum + .5GB)

---

### Post by RTG1987 on 2010-11-21
> **bcbc said:**
> Shrink the windows partition using Windows 7 tools. Prepare the new partition space, creating an extended partition, then inside create two logicals, one for root, one for swap. Then follow this guide to migrate: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Note: some computers come with 4 primary partitions used up. You need to be able to create a new one, so 3 or less and you'll be ok. 

For hibernate the swap partition must be > RAM. I recommend size of RAM + 1GB. (Or minimum + .5GB)
Thank You, it worked like a charm.

Created 6GB swap (my RAM is 4GB), another 50 GB for ubuntu.
Followed the commands, as provided in the links. Everything worked. :)

Can you please help me with two more queries:
1) When I load into win7 using grub, I still see the windows boot manger with choice of win7 and ubuntu (wubi's). Shall I just go ahead and uninstall ubuntu via window's control panel. I think it won't affect me now.
2) How can I change the order of os's and time of selection in grub.

Thanks in advance,
RTG

---

### Post by RTG1987 on 2010-11-21
> **RTG1987 said:**
> Thank You, it worked like a charm.

Created 6GB swap (my RAM is 4GB), another 50 GB for ubuntu.
Followed the commands, as provided in the links. Everything worked. :)

Can you please help me with two more queries:
1) When I load into win7 using grub, I still see the windows boot manger with choice of win7 and ubuntu (wubi's). Shall I just go ahead and uninstall ubuntu via window's control panel. I think it won't affect me now.
2) How can I change the order of os's and time of selection in grub.

Thanks in advance,
RTG
Hi bcbc,

I uninstalled the wubi's ubuntu and also saw a utility named startup manager that can be used to rearrange the boot order, and increase/decrease the time.

I just checked out so many helping threads by you on the ubuntu forum.
Great job, and thanks again from noobes like me, you're really helping in our transition.

RTG

---

### Post by bcbc on 2010-11-21
> **RTG1987 said:**
> Hi bcbc,

I uninstalled the wubi's ubuntu and also saw a utility named startup manager that can be used to rearrange the boot order, and increase/decrease the time.

I just checked out so many helping threads by you on the ubuntu forum.
Great job, and thanks again from noobes like me, you're really helping in our transition.

RTG
Cool, you're welcome.

You can use startupmanager to set the menu item to boot, but it's statically set by item number. The grub menu is automatically updated whenever a new kernel is installed (or an old one removed). So you will have to run startupmanager again when this happens. 

drs305 has written a comprehensive guide to customizing grub 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
Right at the top he links to meierfra's 'custom menu' option. Which I followed and works well. 
On the down side, it's a little more technical than running startupmanager...

---

### Post by RTG1987 on 2010-11-21
> **bcbc said:**
> Cool, you're welcome.

You can use startupmanager to set the menu item to boot, but it's statically set by item number. The grub menu is automatically updated whenever a new kernel is installed (or an old one removed). So you will have to run startupmanager again when this happens. 

drs305 has written a comprehensive guide to customizing grub 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
Right at the top he links to meierfra's 'custom menu' option. Which I followed and works well. 
On the down side, it's a little more technical than running startupmanager...
Yea its more technical, but will go through it and will try to understand it.
Thanks for your suggestion, looking forward to fun ubuntu computing.

---

### Post by RTG1987 on 2010-11-22
Hi bcbc, 

I am now able to suspend/hibernate but the process is very-2 time consuming, I can shut down and start my computer again faster.
I made a swap of 6 gb, do I need to increase it more, or do I need to make some settings changes. Can you please help me on this as well.

Thanks,
RTG

---

### Post by bcbc on 2010-11-22
Look in /var/log/syslog and see if there are any messages that can explain it.
```
grep 'PM:' /var/log/syslog
```

How long does it take? How long does it take in Windows?

In my experience, it takes less time to do a normal shutdown or reboot - but if I had to open up the apps and the docs I was working on it would take longer. 

Whereas in Windows, it takes much longer to shutdown/reboot compared to hibernating. But Ubuntu shutdown/reboot is  much quicker than Windows.

---

### Post by RTG1987 on 2010-11-22
In windows the suspend/resume is instantaneous. It takes about 20-30 seconds in linux.
Also the hibernation is faster by almost 50% in windows, and takes around 20-25 seconds.

I ran the command, and have uploaded the output in results.txt.tar.gz file.

It did say:
kernel: [    0.845726] PM: Resume from disk failed.

Not sure if this is the reason.

---

### Post by bcbc on 2010-11-22
> **RTG1987 said:**
> In windows the suspend/resume is instantaneous. It takes about 20-30 seconds in linux.
Also the hibernation is faster by almost 50% in windows, and takes around 20-25 seconds.

I ran the command, and have uploaded the output in results.txt.tar.gz file.

It did say:
kernel: [    0.845726] PM: Resume from disk failed.

Not sure if this is the reason.

That message is standard on startup - I think it always checks the swap to see if it needs to resume.

It doesn't sound like there's a 'problem'. I think the suspend/hibernate software on linux just takes longer than windows (I the code is fairly old). 

I think you just need to decide whether that 30 seconds extra is going to be faster to load up your apps by hand.

---

### Post by RTG1987 on 2010-11-22
> **bcbc said:**
> That message is standard on startup - I think it always checks the swap to see if it needs to resume.

It doesn't sound like there's a 'problem'. I think the suspend/hibernate software on linux just takes longer than windows (I the code is fairly old). 

I think you just need to decide whether that 30 seconds extra is going to be faster to load up your apps by hand.
yeah would rather load the apps manually, because sometimes suspend doesn't even work and I have to hardboot.
But would have been better had linux kicked window's *** in this functionality as well.
Looks like will have to wait for the newer code to do the job. :)

Thank You

---

### Post by bcbc on 2010-11-22
> **RTG1987 said:**
> yeah would rather load the apps manually, because sometimes suspend doesn't even work and I have to hardboot.
But would have been better had linux kicked window's *** in this functionality as well.
Looks like will have to wait for the newer code to do the job. :)

Thank You

I'm not sure why the suspend wouldn't always work. Mine does. Sometimes if you're using ndiswrapper or have some other hardware attached you need to add some custom scripts to remove on freeze and restart on thaw. 

The best way to figure out what to do is to search on your specific hardware brand/model. Usually someone has figured it out and posted something on how to fix it.

---

