---
title: "What is best way to update kernel to several versions higher?"
date: 2022-02-23
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-02-23
My Ubuntu-MATE version updated yesterday -- two days early -- from 20.04.3 to 20.04.4.  

I assumed (wrongly) that my kernel would automatically update (to 5.13.xx), in tandem with the 20.04.4 update.  
(I guess because I read that 20.04.4 comes with kernel 5.13 if you fresh-install 20.04.4.)

I'm currently running kernel 5.4.0-100-generic.  I'd like to update to the HWE kernel 5.13.xx.

Would it be a straightforward process to simply use the *Ubuntu Mainline Kernel  Installer* program to install, say, kernel version 5.13.19?
(From what I can see, the problem with using *UMKI* is that there doesn't appear to be a way to specify in that program that I want an **HWE kernel**.)

Also,  the 5.13 versions (in the *UMKI* program) only go up to 5.13.19, and  there are no higher 5.13 unstable and/or RC releases shown.

What would be the best way to update from kernel 5.4.0-100 to an HWE kernel 5.13.xx?  
And which 5.13.xx kernel would be the most stable for an Ubuntu installation?

---

### Post by TheFu on 2022-02-23
Google "ubuntu hwe" ... there's a page there with specific commands to run.
You probably don't want to use *Ubuntu Mainline Kernel Installer*. That is meant for people testing kernels, not end-users.

---

### Post by ActionParsnip on 2022-02-23
Why do you want the newer kernel? Is your hardware not running using the kernel you are running presently?

---

### Post by watchpocket on 2022-02-23
I get the "don't fix it if it's not broke" sentiment, but the idea is to gain all the enhancements possible from a newer kernel.  

My hardware works, but it's new hardware, and my notion, or hope, is that moving to the newer kernel would, generally speaking, be a good thing.

---

### Post by ajgreeny on 2022-02-23
> **watchpocket said:**
> I get the "don't fix it if it's not broke" sentiment, but the idea is to gain all the enhancements possible from a newer kernel.  

My hardware works, but it's new hardware, and my notion, or hope, is that moving to the newer kernel would, generally speaking, be a good thing.
Generally that is not quite the way this works.

If all your hardware is working with the 5.4 kernel series there will be no advantage to moving to the 5.13 hwe kernel series, as you obviously already have all the kernel drivers that may be needed for really new hardware, and don't forget, new hardware does not meab new hardware just for your own system, but new as in newly designed by the manufacturer and for which there may be no drivers in the 5.4 kernels.

I have always managed with the original kernel series of an LTS version, ie, for 20.04 it's the 5.4 series, and that will be supported right to the end of support for the 20.04 version, whereas the 5.3 kernel will lose support before that time and will then, I believe, move to 5.15.

You said it yourself "don't fix it if it's not broke"!

---

### Post by watchpocket on 2022-02-23
Right.  I did just notice the much longer support period for the 5.4 series kernel [here]("https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle"), so I will in fact likely just stay with 5.4.

But it does make me wonder why, if I were installing 20.04.4 anew, that new 20.04.4 install would do so with the HWE 5.13 kernel:

[*"That stack can be enabled manually, but may also be pre-enabled with an Ubuntu LTS release."*]("https://ubuntu.com/kernel/lifecycle")

---

### Post by TheFu on 2022-02-23
> **watchpocket said:**
> Right.  I did just notice the much longer support period for the 5.4 series kernel [here]("https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle"), so I will in fact likely just stay with 5.4.

But it does make me wonder why, if I were installing 20.04.4 anew, that new 20.04.4 install would do so with the HWE 5.13 kernel:

[*"That stack can be enabled manually, but may also be pre-enabled with an Ubuntu LTS release."*]("https://ubuntu.com/kernel/lifecycle")

There are as many reasons as there are people.
Trade-offs for your consideration:
[LIST]
[*]Newer kernels get more updates to fix unstable things.
[*]Older kernels are generally very stable and only security patches get back ported.  There is a huge difference between how many kernel patches there are for 5.4.x and 5.11.x and 5.13.x lines.  5.4.x get probably 80% fewer updates ... which means 80% fewer new bugs.
[*]If you have 12-month or less old hardware - that's not just new to you - but new in the industry - then you may need a newer kernel to gain support.  For example, my Ryzen 5600G needs 5.10.x or later for the GPU drivers to be available from AMD.  It does work on 5.4 kernels, but in VESA mode. None of the fancy stuff.  I'm actually running 5.11.x on an 18.04 install on that Ryzen.
[*]Sometimes newer drivers, especially wifi and ethernet add support for lots of new chips, but break support for NICs that have been working great for 5-10 yrs.  That seems to happen much more often these days. Just look through these forums for broken Realtek 8111H drivers (r8169). There must be over 500 threads about that crappy driver.
[*]I generally don't run the HWE kernel on a system working fine, until about a month before I plan to do an OS upgrade.  Then I'll install the HWE kernel and let it run with my daily workloads.  It is just one less surprise that a release upgrade might bring.  I won't do the HWE upgrade, then immediately move to a new release. I want multiple weeks for everything to simmer.
[*]When buying hardware, eventually every Linux user will get burned.  I've bought hardware with "Supports Linux!" on the box and it turned out to support only the 2.6.x line of kernels with all functions. When 3.x and later were released, only basic functionality was possible.  Spend $200 on some hardware, use it for 5 months, then learn that you either have to go back to an old kernel or use only $35 worth of the capabilities.
[*]Of course, with Linux, support for some devices seems to work 20+ yrs too.  Drivers for my printers from 2007/2008 have long been dropped on Windows, but on Linux, they still work great.  A specialized slide/negative scanner which came only with WinXP drivers - no free updates - has been working perfectly under Linux for years now using F/LOSS.
[*]Newer isn't better. "New" is the enemy of stable.  I tell anyone who will listen NOT to patch daily unless you have an extremely high-risk internet-facing server.  There are so many chances for patches to break things that if there are changes possible daily, you'll never figure out what changed to break it.  Patch weekly, consistently, probably just after a system backup, so you can delineate what's new and possibly what broke the system.
[/LIST]

IMHO.

But it is your system, not mine. You get to deal with the issues and perhaps everything has always just worked for you.  Most of the time, patching does work, but 1-2 times a year, the dependencies in a package will have a huge mistake.  I'd rather not have to deal with that myself and I love that other people patch daily and live through those problems.  I did that back in the 1990s. Not anymore. I did my time. I've earned a stable system - or 20.

---

### Post by guiverc on 2022-02-23
Ubuntu LTS releases have various kernel stack choices.  The installation media dictates which is installed by default.

Ubuntu Server defaults to GA kernel stack, as it's assumed servers want the most *stable* which is the GA stack. Server install using the *live* installer `subiquity` can elect to use HWE though.

Ubuntu Desktop defaults to HWE stack on all 20.04 media; as they've assumed desktop users are running *newish* hardware and will benefit from later *graphics* and like drivers.

Ubuntu *flavors* which includes Ubuntu-MATE, default to the GA stack if 20.04 or 20.04.1 media is used for install; but default to the later HWE stack if media is 20.04.2 or later.

You can have both stacks installed & they'll happily co-exist ***providing* **you're not using close-source kernel modules (*drivers*) that prevent it (*eg. some nvidia software*).  I've also neglected to cover OEM kernel stacks, which desktop media using the `ubiquity` installer can install if your hardware is recognized as benefiting from it (*which includes Ubuntu-MATE*) a different OEM kernel can be used instead of GA/HWE or a specific kernel is used instead (ie. *you maybe using media that defaults to HWE but the installer recommends your hardware benefits from GA kernel so it's used instead*).  To know if this applies; your current kernel (GA) **and**installation media would need to be know (ie. *did you get the expected kernel, or was an alternate used*).

To install the other stack, as already alluded to in prior comments (*via suggestions to look for it I gather*), you can look at the documentation

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you want the most *stable*, you're already using it - the GA kernel stack.

 The HWE stack using 5.13 kernel has only a *supported life* of about 6 months (*for 20.04, it had 9 months with 21.10 but ~3 months had passed before 20.04 users got it*).

(FYI: *The 5.13 kernel rolled out to HWE users 2+ weeks ago, the 20.04.4 name got changed when it reached [RC state with regards the ISO release]("https://lists.ubuntu.com/archives/ubuntu-release/2022-February/005317.html") which is later today UTC time, as the Release Candidate stage means it needs to have it's final 20.04.4 release name, though installed systems had the changes rolled out in the couple of weeks before, with 20.04.4 signifying to those users all upgrades had reached their boxes*)

*I personally have both kernel stacks installed, as it alerts me to when they're hitting user boxes, and it lets me have them available for testing if required for support. My primary box is using jammy. My server installs are always stable & using the GA stack.*

---

### Post by TheFu on 2022-02-23
It is worth mentioning, that having multiple kernel lines installed on a single system will get updates for both and effectively use 2x the storage in /boot/. This may be completely unimportant, or it can be disastrous for systems where a separate /boot/ partition is required, but not sized to hold 6+ kernels.

A patch session that fails with a partially written kernel isn't fun.

---

### Post by ActionParsnip on 2022-02-23
In short, I suggest you stop looking at version numbers and thinking "later version numbers exist so I need this as I'm outdated". The kernel you have is absolutely fine if your hardware is working which is exactly why I asked the question. It's a common misconception by Windows users who blindly chase version numbers. It doesn't work that way with the kernel in Linux. As long as the release you are using is supported then critical updates will come down with normal patches. If your hardware is all working then you don't need a newer kernel.

---

### Post by MAFoElffen on 2022-02-24
For now for the cautionary "Horror Story Section"... Yes, the easiest is to rationalize between the standard series of kernels and HWE series kernels. (But read below what that really means.)

Why? Because of my own experience of testing new kernels and pushing the limits of that, just for the sake of testing. I have broke things again and again, because after going up so many kernel versions, then you start running into other dependency problems of other packages, where other things are not at a certain newer version for it to work right. A 'system' is not just the Kernel.

For the HWE (Hardware Enablement Stack), it is not just the Kernel (and the version of), it includes a lot of packages. And all those packages and package versions are already worked out for what works together...

---

### Post by watchpocket on 2022-02-24
*> As long as the release you are using is supported then critical updates  will come down with normal patches. If your hardware is all working then  you don't need a newer kernel.*
I realized this the moment I saw the far longer support life for the 5.4 series than for subsequent kernels.

I'll now be using the "LTS" kernels for the same reason that I stick to the LTS Ubuntu OS versions -- unless I really know why I might need to deviate from them, or unless I decide get into testing (not likely). 

Thank you all for the insights in your posts here. My perspective on these issues has widened considerably from reading them.

---

### Post by kevdog on 2022-02-24
If really wanting to use a really new kernel, I probably try something like Arch.  I've run git-dkms kernels on this distribution and I really haven't had a kernel upgrade break other than once.  I usually install a backup LTS kernel in order to boot to in case of this issue.  It just depends what you want to do.

---

