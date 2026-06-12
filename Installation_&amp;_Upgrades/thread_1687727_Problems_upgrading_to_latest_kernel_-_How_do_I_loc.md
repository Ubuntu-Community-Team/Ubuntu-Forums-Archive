---
title: "Problems upgrading to latest kernel - How do I lock kernel version?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by TCWriter on 2011-02-14
A month ago, I bought an Ubuntu Desktop from Zareason. 

Nice machine and all, but while it works fine on the 2.6.35-22 kernel (10.10 version of Ubuntu) it shipped with, upgrading it to the latest Ubuntu kernel (2.6.35-25) results in a mouse/screen freeze (after login, but before it reaches the desktop). 

I don't know where the problem lies, but until I figure it out (with the Zareason folks), I'd like to lock the kernel at version -22. 

Using Synaptics, I used the "Lock Version" command on "Linux Generic" and "Linux Image Generic" (in the Meta Packages category). 

Now the Update Manager still wants to upload new Linux kernel headers (some for -22, some for -25). 

Two questions:

[LIST]
[*]Do I need to find and lock some kind of header file stuff too?
[*]Will locking it at the -22 kernel and updating everything else cause any issues?
[/LIST]

Any other observations for a relatively non-techie Ubuntu user?

Thanks!
TC

---

### Post by lidex on 2011-02-14
When I have this issue, I generally just uninstall the offending kernel/headers and continue booting with the good one. I would continue to install updates and at least try the newer versions until the issue is resolved.

---

### Post by MountainX on 2011-02-14
> **TCWriter said:**
> A month ago, I bought an Ubuntu Desktop from Zareason. 

Nice machine and all, but while it works fine on the 2.6.35-22 kernel (10.10 version of Ubuntu) it shipped with, upgrading it to the latest Ubuntu kernel (2.6.35-25) results in a mouse/screen freeze (after login, but before it reaches the desktop). 

I don't know where the problem lies, but until I figure it out (with the Zareason folks), I'd like to lock the kernel at version -22. 

Using Synaptics, I used the "Lock Version" command on "Linux Generic" and "Linux Image Generic" (in the Meta Packages category). 

Now the Update Manager still wants to upload new Linux kernel headers (some for -22, some for -25). 

Two questions:

[LIST]
[*]Do I need to find and lock some kind of header file stuff too?
[*]Will locking it at the -22 kernel and updating everything else cause any issues?
[/LIST]

Any other observations for a relatively non-techie Ubuntu user?

Thanks!
TC

Yes, you should do the same locking procedure for the headers too.

I have been doing what you describe (locking at a specific kernel) and upgrading everything else. No problems.

---

### Post by TCWriter on 2011-02-15
Thanks for the help. I may upgrade a kernel at a time (about four behind) and see where the problem lies.

---

