---
title: "Can't autodate kernel anymore"
date: 2015-05-29
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2015-05-29
I had been taking the autoupdates to Ubuntu 14.04 faithfully until about 2 months ago when a kernel upgrade disabled USB and WiFi.  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1440174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1440174). 
The only way I could keep going was to install grub, and boot to an earlier kernel image:

Linux 3.13.0-46-generic x86_64 works
Linux 3.13.0-48-generic x86_64 does not.

Since then I have been looking at the releases to see if bug 1440174 is fixed.  It does not appear to be.  But I would like to try the more recent kernels to see if it might be.  However, now, the auto-installer won't let me install kernels, at least not when running under 3.13.0-46.  I haven't tried 3.13.0.48 yet.  

What is the best way to get back up-to-date to at least see if there is a workable version for me?

---

### Post by grahammechanical on 2015-05-29
Even if we are running on an earlier kernel Software Updater should still work and it should still bring in revisions to the Linux kernel which often replace a buggy kernel package.

Likewise, there are two commands that should still work

```
sudo apt-get update
sudo apt-get upgrade
```

There was a period when I was testing the development version of 15.04 when an upgrade to the latest kernel broke the OS in some way and for weeks I had to use an earlier kernel until I received a revision to that latest kernel that fixed the problem. There were several revisions that did not fix the problem. I just kept running Software Updater every day until I got the one revision that fixed the problem for me. (The development versions receive daily updates. The stable versions less so.)

I do not understand what you mean by "auto-installer won't let me install kernels." 

Regards.

---

### Post by stevecoh1 on 2015-05-29
What I mean is this:  The auto-updater first pops up with this popup infoming me that not all packages can be installed.
Upon clicking "Continue", I see that the kernel packages are among the ones that will not be installed.
I would attach screenshots, but am not sure how to do it with this interface.  They don't seem to work, I just get IMG tags in the preview.  Not sure what to put as the "URL" the interface is asking for.  Tried just the path to the file and also tried with a file:// url and neither worked.

---

### Post by tokyobadger on 2015-05-30
From the information you have provided it appears you have 2 problems:
1) 3.13.0.48 boots but is not fully functional on your hardware ie USB and wifi not working
2) When you boot a working kernel, the package manager will not update the installed software

For the first problem, I'll just note that the bug you linked to has some inconsistencies: the poster describes his release as 14.04.2 but his kernel issue is related to 3.13.0.48. 14.04.2 comes with 3.16.xx series of kernels so I'm not sure if I would rely on this bug report solving your issue.

For the second problem, we need to see what is going on with the package manager and the graphical interface updater will not tell us why it's not able to update all packages.

Can you open your terminal and show us the output of the commands grahammechanical suggested above
```
sudo apt-get update && sudo apt-get upgrade
```
When we see the output we might have an idea of what solution to offer.

For reference:
The 3.13 kernel for 14.04 (Trusty) has updates up until 3.13.0.54 and will be supported/updated up until 2019 for both 14.04 and 14.04.1 releases.
Booting a lower working kernel version should not prevent you from installing a newer version. The more likely culprit is an issue with the package manager.

[Trusty release notes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Official_flavours) with instructions for updating to the later point releases

[Information on the Hardware Enablement Stack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) and which kernel versions they use

---

### Post by stevecoh1 on 2015-05-30
Thanks.  Your understanding of the situation is not quite correct  - the same auto-update issues occur with 3.13.0-48.  Upon booting 3.13.0-48 I have to use wired connection, and put up with the hated touchpad since my serial mouse isn't recognized.  Under these conditions the same auto-update messages occur.

Be that as it may, running 

```
sudo apt-get update && sudo apt-get upgrade
```

under 3.13.0-46 retrieved and installed a whole bunch of stuff.  Log attached. No errors seem to have occurred and the process ran to completion.  No kernels beyond 3.13.0-48 were installed.

Upon rebooting with -48, as expected, the same USB and WiFi issues continued to plague the system.  Only by booting to 3.13.0-46 do I get a stable system.  When I run the software update app, it thinks for a long time, gives me the same message about not being able to install everything, but this time when I press Continue, it tells me that my system is up-to-date.

So what to try next?  

Run 

```
sudo apt-get update && sudo apt-get upgrade
```

again under -46?
run it against -48?
Or something else?

Thanks, again.

---

### Post by tokyobadger on 2015-05-30
Thank you for clarifying the issue. Running the commands under either kernel will yield the same results.

I noticed in the log that files related to 3.13.0.53 were installed but not the key files.

It would be helpful to know what hardware you have, I'm assuming a laptop, but specific model and hardware would be helpful.

I see 3 options right now:

1) continue booting the 3.13.0.46 kernel as it works and wait until 16.04 the next LTS is released

2) reinstall the 3.13.0.48 kernel and see if that will resolve the updating issue; boot into 3.13.0.48 with a wired internet connection and
```
sudo apt-get install --reinstall linux-image-$(uname -r)
```

3) upgrade to 14.04.2 which uses the 3.16.xx series of kernel (14.04.3 will come in August 2015, kernel version not yet confirmed); boot into either of your current kernels (but if the 3.13.0.48 with wired internet connection) and
```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```
My recommendation would be (1) if it is critical for work or for study to have a functioning system and (3) if you have your files backed up and will not risk "downtime" for work or for study. The merits of upgrading are that you will get a newer kernel with (hopefully) improved hardware support as well as other newer software. If you go for (1) I'd file a bug report at launchpad

---

### Post by stevecoh1 on 2015-06-01
Computer is indeed a laptop, Lenovo T-540p.

I am going to stick with 1 for now.  I am getting ready to move this month from my home of 22 years and I just need a computer that works.  Alhough #2 might be a fairly risk-free alternative, since I can always go back to -46.

Thanks.  

What good will a bug report do, as the one that is already open does not seem to have drawn serious attention: [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1440174](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1440174)

---

### Post by efflandt on 2015-06-02
Note that **sudo apt-get upgrade** only upgrades existing packages, it does not install any new dependencies that updated packages may require, so that may not install packages with unmet new dependencies. **sudo apt-get dist-upgrade** is smarter about updating dependencies. See **man apt-get**. Maybe you need to try seeing if anything can be fixed with **sudo apt-get update && sudo apt-get -f install** [or install synaptic and check its filters for Broken or Upgradable (upstream) packages to see if something was held back].

Have you looked farther back in your term.log files with zless to see if or when something tripped up somewhere? There appeared to be a bunch of 3.13.0-46 updates. My desktop is connected by WiFi only and uses USB keyboard, mouse, Android MTP connection, etc., so maybe the issue is rare hardware specific. This is the time line of when updates happened for me about that time:

Feb-25 3.13.0-46.75
Feb-27 -46.76
Mar-3 -46.77
Mar-12 -46.79
Mar-23 -48.80
Apr-9 -49.81
Apr-15 -49.83
Apr-30 -51.84

---

