---
title: "DO I NEED linux-generic &amp; FRIENDS? Current is 4.13, package still points to 4.4..."
date: 2018-03-03
forum: Installation &amp; Upgrades
---

### Post by spamhog on 2018-03-03
Hello!
One line for the quick:
It's Feb 18, 16.04, linux 4.13 BUT linux-generic STILL pulls in 4.4.

Details:
- 16.04 (upgraded), running a linux 4.13...
- a while ago, didn't boot (my stupid error, I had edited fstab on host instead of a VM)
- used Boot Repair from live, chose to install a kernel
- this brought in an old 4.4 kernel
- updates went on to newer kernels, all works fine, running up to date kernel
- but **4.4s became impossible to remove without removing linux-generic inux-headers linux-image-generic**
- played with "set to manual" / "set to auto"
- no matter, removing 4.4s still tried to pull linux-generic

So I did this:
- purged linux-generic inux-headers linux-image-generic
- purged all 4.4s
- checked that grub-update kept the current kernels
All worked fine.

I tried reinstalling linux-generic but that again tries to pull in linux 4.4.

QUESTION:
[B]ARE linux-generic inux-headers linux-image-generic
NEEDED TO DRIVE UPDATES
TO THE LATEST KERNEL
OR CAN I LIVE FINE WITHOUT?[/B]

Less practical and more theoretical question: I think I had seen linux-generic before using boot-repair, and back then old kernels were not an issue, so it wasn't that suite that dragged them in. Is that right? Was linux-generic overridden by something else? What was that pulled in the latest kernel???
Thanks for any help!

---

### Post by jeremy31 on 2018-03-03
Is linux-generic-hwe-16.04 installed?  That package currently depends on the linux-image, linux-headers, linux-image-extra of the 4.13 kernel, see [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#hwe-16.04](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#hwe-16.04)

---

### Post by spamhog on 2018-03-03
Excellent question, thank you jeremy31, **linux-generic-hwe-16.04 is not installed**.

I had considered installing either **linux-generic-hwe-16.04** or **linux-generic-lts-xenial** and I think neither was installed before I messed with boot-repair.

It *superficially* looks like both should properly drive kernel updates... BUT...

1) both are marked optional

2) linux-generic-lts-xenial still depends on linux-generic, so it's back to square one and I don't understand how it could work in an upgrade... which leaves linux-generic-hwe-16.04 as a good candidate

3) I wonder what did that job after the upgrade to 16.04 but before installing the 4.4.x kernel with boot repair. Was there perhaps a pinned ad-hoc version of linux-generic installed during the upgrade that depended on the latest kernel but wasn't the same as the one on the repo?

Is linux-generic-hwe-16.04 the canonical specifier of the latest kernel?

---

### Post by jeremy31 on 2018-03-03
The linux-generic-hwe-16.04 is used in the 16.04 point releases so people won't be on a EOL kernel for a long time as it should always depend on a supported kernel.
If the 4.4 kernels work for you, I would reboot and use the Grub menu to use a 4.4 kernel and then remove the 4.13 kernel as it will be EOL by August

---

### Post by spamhog on 2018-03-03
OK, thanks! Reinstalled linux-generic and purged all of the 4.13.x kernels.
All is fine.  If I got it right
- linux-generic is GA, comes with 16.04, and depends on 4.4.x, which is LTS and will be supported til 2022
- linux-generic-hwe-16.04 is from the minor release, and depends on 4.13.x, which will EOL sooner.

Before going back to 4.4.x I made a couple of tests

**A) installing  linux-generic-hwe-16.04**

Before uname -a gave:
... 4.13.0-26-generic #29~16.04.2-Ubuntu SMP ...

After  installing and rebooting:
... 4.13.0-36-generic #40~16.04.1-Ubuntu SMP ...

Kernel version went UP but Ubuntu version went DOWN.

**B) Tried apt dist-upgrade**

Nothing to upgrade.


All is fine but... just curious
- if linux-generic-hwe-16.04 is meant to drive a rolling kernel upgrade, then it's not happening according to the schedule, it should be at 4.15 now
- linux-generic-hwe-16.04 triggered a point release downgrade, what to do to upgrade to a point release?

Just academic for me but it may help someone else.

---

### Post by deadflowr on 2018-03-03
> if linux-generic-hwe-16.04 is meant to drive a rolling kernel upgrade, then it's not happening according to the schedule, it should be at 4.15 now
Nope
The rolling is not based on kernel at large (or whatever may be the latest upstream kernel) but on the kernels from the latest supported releases of Ubuntu.
so 4.13 is the kernel used on Ubuntu's latest stable release, 17.10.

Then next and last kernel stack upgrade will be to whatever version 18.04 uses.
That update will come sometime in  July/August when the next point release comes out.
It'll freeze at that kernel for the remainder of 16.04.


Edit:
If, by chance, you would like to roll a more closer to upstream kernel, then you can do so with a little ease with ukuu:
[https://github.com/teejee2008/ukuu]("https://github.com/teejee2008/ukuu")

---

