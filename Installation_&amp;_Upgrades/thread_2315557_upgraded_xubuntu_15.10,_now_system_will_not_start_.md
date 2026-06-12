---
title: "upgraded xubuntu 15.10, now system will not start (boot)"
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by superdad4u on 2016-02-29
HELP!  
First, I know nothing about Linux, I am inquiring for my daughter, so please address replies accordingly and I will pass them on to my daughter.
My daughter is using a Lenovo laptop model T-400 running Xubuntu 14.xx  My daughter received a notice to upgrade and after doing so, the computer will no longer start (boot).
I have several questions:
1.  Is it a hardware compatibility issue?
2.  Is there a different version of Linux that is more suitable for her particular model laptop?
3.  Are there known issues with upgrades to xubuntu running on older laptops?
4.  Is there a fix for this issue?

---

### Post by grahammechanical on 2016-02-29
First, we need to be a bit clearer on what is not happening. You see "will no longer start" can apply to several situations. It could even mean the ON/Off switch is broken. :)

If we have Xubuntu installed so that we dual boot with another operating system then we get a boot menu (called Grub in Linux). If Xubuntu is the only operating system on the machine we do not see the boot menu but it is still present. We need to call it up and we do that by pressing Shift very early as the machine starts to load.

At the boot menu we will see an option called Advance options for Ubuntu. Select that and then select a Linux kernel that has a recovery mode. Linux will then load to a recovery menu. At the recovery menu select Resume. That may load Xubuntu to a working desktop environment.

Your daughter then needs to go to System Settings>Additional Drivers. I cannot explain how to do that as I am not using Xubuntu. If we are connected to the internet and allow the utility time to do its job we will be offered 5 video drivers. One of which will already be active. There will be 4 proprietary video drivers & one open source video driver called X.Org X Server. I suggest activating the open source video driver and then testing a re-start to see if that fixes things.

If your daughter wants to she can then experiment with the proprietary video drivers.

From reading posts on this forum I identify a couple of reasons why an upgrade will fail. 

1) Having a user interface that has been heavily modified. I think that it is best to take the user interface back to the default state as much as possible.
2) Using a proprietary video driver. Installing the latest Xubuntu/Ubuntu will get us the newest Linux kernels and the newest proprietary video drivers to go with them. Support for older video adapters is often dropped from the newest proprietary video drivers.

Also, under Advanced options for Ubuntu we can load the Linux kernel that was running when we upgraded.

Regards.

---

### Post by oldos2er on 2016-02-29
Need to know if ".xx" means .04 or .10, and does that refer to the version before or after the upgrade?

---

### Post by superdad4u on 2016-02-29
Thank you very much for that prompt response, I have forwarded your suggestions to my daughter.  For the record, it is not that the On/Off switch is broken, the operating system just does not start.  Also, it is not a dual-boot system.

---

### Post by superdad4u on 2016-02-29
Thank you for your response.  .xx means .10 and that refers to the version before the upgrade.  Also, my daughter tells me that it was not a upgrade to a newer version of the OS.

---

### Post by kansasnoob on 2016-02-29
In order to properly troubleshoot this we really need more info. The simplest way to collect & provide a lot of info in one fell swoop is using Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You'll see that it can be used via the same live DVD/USB that was originally used to install Xubuntu. You may even get lucky and find that running the recommended repair fixes the boot problem. If not please provide the URL produced by Boot Repair so we can see what we're actually dealing with.

Maybe your daughter could also use the live session to connect to the internet and communicate with us directly :)

---

### Post by sasafrass452 on 2016-03-03
Hi, everyone. I'm the aforementioned daughter having this issue. I'm posting this from my tablet, since I obviously don't have access on my very old laptop. First of all, let me clear up some info.... I was using 15.10, not 14xx. I received an update that caused my system to no longer boot. Here is a thread I started last week reguarding this problem. Please note the date of my post in relation to the update that was issued, as it may help narrow down a solution, or lack thereof.... [http://ubuntuforums.org/showthread.php?t=2314753](http://ubuntuforums.org/showthread.php?t=2314753) . I can't offer much more info, so I hope this helps.

---

### Post by Bucky Ball on 2016-03-03
Third-person threads like this can become incredibly confusing and are generally not very successful. Is there any reason why your daughter can't take over considering she is the one having the problem and who has some idea about Ubuntu? You will have a much better chance of success and save some time. This could become cyclic and lengthy otherwise.

> **kansasnoob said:**
> Maybe your daughter could also use the live session to connect to the internet and communicate with us directly :)

Highly recommended. 'Could you ask her to' and then you passing on the information and her performing the action and asking you to pass on the outcome to us when you are not au fait with Ubuntu in the first place ... put aside a few hours. :|

Much easier and quicker if she's just sitting there copy/pasting directly from the forums or following instructions directly from the thread then responding with the output directly to the thread by copy/pasting details where required. How we going to go if we need to see some terminal output?

We are a friendly bunch and gender is not relevant here. :)

---

### Post by oldos2er on 2016-03-03
> **sasafrass452 said:**
>  I was using 15.10, not 14xx. 

Ok, I've updated the thread title.

> **sasafrass452 said:**
> I received an update that caused my system to no longer boot. Here is a thread I started last week reguarding this problem. Please note the date of my post in relation to the update that was issued, as it may help narrow down a solution, or lack thereof.... [http://ubuntuforums.org/showthread.php?t=2314753](http://ubuntuforums.org/showthread.php?t=2314753) . I can't offer much more info, so I hope this helps.

Please provide the boot repair info requested in post #6.

---

### Post by sasafrass452 on 2016-03-03
> **oldos2er said:**
> Please provide the boot repair info requested in post #6.

Can you please explain how this will help? I don't believe grub is actually broken. The update that caused the problem was issued last week, either wed or thurs. Here's what I believe is the cause....

> The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a black screen.

Did last week's update have anything to do with that?

---

### Post by Bucky Ball on 2016-03-03
Boot infor will tell us exactly what is happening at boot and may give some clues as to why you can't. It gives a lot more info about your boot process than just showing us your grub set up.

Please post the output of that script. When you have run it it will provide you with a link to the script output. Please post that link here. Thanks.

---

### Post by sasafrass452 on 2016-06-02
Hello, everyone. First off, my appologies for not getting back here sooner. I attempted once again to burn the boot-repair disc, & it still wouldn't run. I even tried it on my mother's laptop, which is the same old model as mine, also running xubuntu but without the update(s) that caused my boot failure. This time, it gave me a choice of language, but then the screen went black & nothing happened. Anything I can do, or is it time for a new laptop?

---

