---
title: "Witch ubuntu version to stick to 22.04,23.04, 23.10"
date: 2023-11-15
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-11-15
I have ubuntu 22.04 I see it has long term support.

is there a benefit of upgrading to the latest releases .. 23.04 or 23.10 if there is benefit witch one is suggestible ?

Cheers

---

### Post by Rubi1200 on 2023-11-15
Always best to stick to LTS releases for more stability.

From time to time, I like to test the interim releases but that is more out of curiosity than anything else. Plus, I always do it on a separate partition so it does not affect my main install.

---

### Post by ActionParsnip on 2023-11-15
If 22.04 works then I'd stay stick with it. 23.04 and 23.10 are not LTS and you will need to upgrade to the next release when the short support cycle ends.

---

### Post by SeijiSensei on 2023-11-15
The next release with long-term support (24.04) will appear in April. I'd just stick with what you have until then.

---

### Post by Dennis N on 2023-11-15
If you really have Ubuntu (not Lubuntu) then know that the big deal with Ubuntu 23.10 is it's the first Ubuntu with Gnome 45. In daily use, I haven't had a single problem with 23.10 since it was released. But if the new Gnome version isn't of immediate interest, then stick with what you have - you have 5 years support on the LTS versions like 22.04.

---

### Post by TheFu on 2023-11-15
If you want to be a tester, use a non-LTS release.  Thank you for your service.  If you won't file bug reports on 23.10 (23.04 is useless to you at this point), don't bother.

If you have really new hardware (CPU, Motherboard), you may require a newer kernel to get support, but if you have a system happy on any currently supported LTS, I'd stick with it.  Less than a year ago, I moved from 18.04 to 20.04, just before 18.04 support ended.

Also, if you have certain hardware that is known to have issues with newer kernels, best to stay on the newest LTS that works well.  Some realtek NICs/Wifi and some nVidia GPUs have problems.  These things can really ruin your day ... or month.

23.04 has about 2 months of support left, so nobody should be loading it as a fresh install for daily use today.

If I were loading a new OS on hardware I've had lover a year, I'd go with 22.04 today.  

Always remember, "new" is the enemy of "stable." If stability isn't important to you, go crazy. But be prepared for issues.  I did my time as a tester in the 1990s. Stability is much more important to me than anything else ... well, besides avoiding data loss.  I'd rather have my computers burn to the ground than lose any data.  Computers can be replaced. Data cannot.

---

### Post by MAFoElffen on 2023-11-15
I do DEV Testing. I expect there to be problems with that. I generate a lot of Bug Reports. There will be issues and people need to accept that possibility.

But for a daily driver, I use an LTS release for everything I have. When I "need" to do something, I need to depend that it should work. I do the HWE stack on LTS, for my newer hardware. When people say they "need" to go to an interim release because of hardware, I have to question that. There are exceptions, but not as widespread as some make that seem.

My new workstation is 13th Gen Intel. It works out of the box with 22.04 LTS... Even when the hardware is so new, that for Windows, I had to load the drivers from the Vendor for Windows to recognize the new hardware. And even then, I used Linux to be able to get the drivers files there to do that... No. That used to be a problem in the past, which the Linux Community is very pro-active on these days.

---

### Post by TheFu on 2023-11-15
> **MAFoElffen said:**
>    When people say they "need" to go to an interim release because of hardware, I have to question that. There are exceptions, but not as widespread as some make that seem.

I had a chromebook that would only work with 15.10, not 14.04, so the easy answer was to use 15.10 until 16.04 was released a few months.

Have a Ryzen with integrated GPU that wasn't supported until the 5.10.x kernels.  I ran with a 4.15 kernel for a few months, updated the HWE to 5.4.x, but it needed a new install to get 5.10.x GPU driver support. Sure, the GPU worked in VESA mode.  Video playback wasn't great, but it isn't something I do in highdef on that machine, so it wasn't a priority ... er ... until standard support for 18.04 was ending.  Being on a supported release is very important to me.

I was loading Ubuntu Server onto my laptops for a few years, then hunting down the wifi drivers to add later. With Chromebooks, not having wifi drivers basically makes them no have networking, so I dropped back to loading the lightest Ubuntu flavor at the time, then purged the "desktop" and setup most of it to be maintained like a server.  All because the extremely standard, intel wifi drivers weren't included in the server distro. I've had a few systems where the installer version had the drivers and they worked, but post-install, the wrong driver was there and no networking worked.  Riddle me that one Batman?  Foolish issues, at least to an end user.

We all have different experiences and different levels of support we are willing to have.

---

### Post by Claus7 on 2023-11-15
Hello,

as *Dennis N* mentioned, ubuntu 23.10 uses gnome 45, which provides a good glimpse of what is coming ahead, in 24.04, which will be a LTS version as well. If you are not interested for the latest version stick with what you've got, yet 22.04 is a hybrid version according to my opinion, since many apps were moving on to gkt4. I think that with the advent of 24.04 this process will have reached (near) completion, so if you are thinking moving to the next level, ubuntu 23.10 is worth it. If you are not in a hurry, you could upgrade next year, having in mind that a lot will be different though. If I recall correctly Files for example (nautilus), received a great upgrade since 22.04.

Regards!

---

### Post by guiverc on 2023-11-15
As this was asked in the *flavors* section and Lubuntu specifically, I'll provide my 2c as if that's the product being asked about.   FYI:  I'm using Lubuntu currently, but do consider my system a **Ubuntu** system.

Lubuntu 22.04 LTS is a good & stable system, it's only *drawback* **if** it actually a drawback, is the older LXQt desktop on it. The team wrote about that back on release (*it had the same LXQt as 19.10 before it had* *and wasn't upgraded as planned*).

The Lubuntu team re-started the backports PPA, which will allow you to upgrade the LXQt version to the very latest[ LXQt 1.4 released earlier this month]("https://lxqt-project.org/release/2023/11/05/release-lxqt-1-4-0/"), with official notices here

- [https://lubuntu.me/jammy-backports-22-04-3-lxqt-1-4/](https://lubuntu.me/jammy-backports-22-04-3-lxqt-1-4/)
- [https://discourse.lubuntu.me/t/lxqt-1-4-arriving-at-a-lubuntu-backports-ppa-near-you/4670](https://discourse.lubuntu.me/t/lxqt-1-4-arriving-at-a-lubuntu-backports-ppa-near-you/4670)

This is the same LXQt that is actually found in Lubuntu *noble* (what will be 24.04 on release), further it's without a problem that currently exists in *noble* :P

If you want to use the *newest* features that are available in the LXQt desktop, then for sure upgrade... However do note:  Whilst 22.04 to 23.04 upgrades are *supported* by the Ubuntu system, Lubuntu only QA tests the upgrades from release to release & LTS to next LTS; so an upgrade now supported by Ubuntu's upgrade tools from 22.04 to 23.04 was not QA tested by Lubuntu (only 22.04 to 22.10, then to 23.04, before 23.10 was), though I do test [non-destructive re-install testing]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743").


FYI:  I just installed a system for my own usage, and I wanted an LTS release. I actually opted to install 23.10 as that release is the closest to what 24.04 will be, and the *release-upgrade* from 23.10 to 24.04 is the simplest upgrade there is (*thus opens far sooner than 22.04 to 24.04 does*). There are pros & cons with every choice; my decision aims for a payoff in a few months (*not now*).

---

