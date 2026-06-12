---
title: "bugreport for system not booting?"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by schmolch on 2010-04-24
No version of Lucid boots on my Desktop machine.
It either just hangs or the kernel panics early.
[B]
How do i file a bugreport about this?[/B]

---

### Post by 23meg on 2010-04-24
See if [https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot) helps.

---

### Post by schmolch on 2010-04-24
No it does not.
The Live-CDs only have buggy kernels and the install (upgraded from 9.04] does not even show grub.

---

### Post by kansasnoob on 2010-04-24
Could you possibly be more descriptive?

My mental telepathy is out of whack right now :)

---

### Post by Mr. Picklesworth on 2010-04-24
> **schmolch said:**
> No it does not.
The Live-CDs only have buggy kernels and the install (upgraded from 9.04] does not even show grub.

Well, if it isn't showing grub, it isn't the kernel ;)
Something weird may have happened when it updated grub.

---

### Post by Unicast on 2010-04-24
I'm having the same problem.

I was running the 10.04 beta2 and performed a dist-upgrade today, but when I rebooted by laptop (specs below) it hung on a black screen straight after the unbuntu boot loader screen (one with 5 red dots).

If I hold down shift on boot it brings up grub. If I select kernel version 2.6.31-20-generic it boots fine. If I select 2.6.31-21-generic (default) it hangs.

So I thought I'd try a clean install. Downloaded the RC, burnt to cd and rebooted. Get to Ubnuntu boot loaded screen (red dots one) and the screen blanks out again and halts. Tried nosetmode (think that's right) and it does the same. Just can't get the RC cd to boot at all.

Wondering if it's a kernel related issue.

---

### Post by schmolch on 2010-04-24
> **kansasnoob said:**
> Could you possibly be more descriptive?

My mental telepathy is out of whack right now :)

I did that in my other posts.
This post is only about this question:
[B]
How do i file a bug if the system does not even boot?[/B]

---

### Post by Irihapeti on 2010-04-24
Report a bug against "linux".

A trick I've used (to get around Launchpad's preference for using apport-bug) is to find another bug involving "linux" and then use the "report a new bug against linux" (or however they word it) option at the bottom of the page.

For more info, see [here]("https://wiki.ubuntu.com/Bugs/FindRightPackage#During%20boot").

---

### Post by schmolch on 2010-04-24
Thanks!

---

### Post by k3lt01 on 2010-04-25
Read [this]("http://ubuntuforums.org/showpost.php?p=9134347&postcount=721") and [this]("http://ubuntuforums.org/showpost.php?p=9141943&postcount=736"). If it is the same as your issue post the relevant details in the report listed.

---

### Post by Unicast on 2010-04-25
> **k3lt01 said:**
> Read [this]("http://ubuntuforums.org/showpost.php?p=9134347&postcount=721") and [this]("http://ubuntuforums.org/showpost.php?p=9141943&postcount=736"). If it is the same as your issue post the relevant details in the report listed.

Thank you very much.

I've got the 855GM chipset here on my Dell D400 laptop, and can confirm that adding i915.modeset=1 to the kernel options allows 2.6.32-21 to boot.

I made the changes permanent by editing grub:

```
gksu gedit /etc/default/grub
```

Added i915.modeset=1 as below:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

Saved the changes, and updated grub using:

```
sudo update-grub
```

Not ideal, but it works.

Just hope they sort this one out in the final version.

---

### Post by k3lt01 on 2010-04-25
Glad to be able to help Unicast, did you add to the bug report? If you haven't already please do as it can only help the devs work on making Ubuntu better for us all.

---

### Post by Unicast on 2010-04-25
> **k3lt01 said:**
> Glad to be able to help Unicast, did you add to the bug report? If you haven't already please do as it can only help the devs work on making Ubuntu better for us all.

Added my comments to the bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379?comments=all)

Many thanks again. :)

---

