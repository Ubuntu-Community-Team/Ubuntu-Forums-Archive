---
title: "Nvidia problems with Kernel upgrade to 2.6.32-23-generic"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by rocsco on 2010-06-30
Hi

Upgraded to latest kernel 2.6.32-23. Ubuntu 10.04

I run a twinview video configuration of 2 screens @ 1920x1200.

On booting, X wanted to go to low res for the session, which reverted to one screen (that is, I lost the twin view), but actually kept the 1920x1200 res on the one.

I restarted X on got both screen working with the second as a replica of the first.

Something has changed in this version of the kernel.

Reverted to the previous Kernel version (22) and all is sweet (twin view is back working). But this can only be a temporary workaround.

Would appreciate any help to fix this.

Regards
Ross

---

### Post by smoosh on 2010-06-30
2.6.32-23 breaks the fglrx driver for ATI cards also - at least for me. What did they do to that kernel??

---

### Post by CCC999 on 2010-06-30
Same with my machine, dual boot with Windoze. After update to 2.6.32-23 won't boot to Ubuntu (hangs on Ubuntu splash). Have Nvidia card...bad update for me!

---

### Post by realdude19 on 2010-07-01
Great.. So should I not download the new update? I am currently downloading it as I type... 

Please tell me it doesn't break all Nvidia setups...

---

### Post by chewit on 2010-07-01
I'm running an nVidia setup, nVidia ION on one 20inch screen. Everything seems fine for me.

It appears the update has affected a few people, no internet, ati and nvidia problems.

Just rollback to the old kernel, report the bugs, it will be fixed in another kernel release.

---

### Post by breek on 2010-07-01
here i am too.
ubuntustudio 10.04 64 bit with nvidia driver now low res after reboot.
no time to fix it now... damn!

i suggest not to upgrade now

---

### Post by abadr on 2010-07-01
A temporary solution is to boot using the previous kernel. Since 10.04 is using Grub2 which hides the kernel and OS boot menu, press shift while booting to make it show again. Boot using an old kernel and using Synaptic or similar tool remove the latest kernel. 

Hope this helps

---

### Post by Racoonator on 2010-07-02
Hi,

It's because Nvidia driver doesnt find the kernel module for the new release.

Try this, install dkms and linux-headers-generic packages. 

Stéphane

---

### Post by kellemes on 2010-07-03
> **Racoonator said:**
> Hi,

It's because Nvidia driver doesnt find the kernel module for the new release.

Try this, install dkms and linux-headers-generic packages. 

Stéphane

Indeed..
In my case I had to..

purge nvidia-current
install linux-headers-`uname -r` build-essential
install nvidia-current

All fine now.

---

### Post by Kirk M on 2010-07-16
> **Racoonator said:**
> Hi,

It's because Nvidia driver doesnt find the kernel module for the new release.

Try this, install dkms and linux-headers-generic packages. 

Stéphane

Now this is strange. I updated to Kernel 2.6.32-23 in Lucid without any problem whatsoever and I'm running a dedicated NVidia card. And DKMS was already installed, I didn't have to install it manually. I'll admit I run a much older machine as you can tell from my signature so maybe that's why I had no trouble. Compatibility for old hardware was taken care of quite awhile back, perhaps?

I also use the Hardware Drivers module to install the proprietary NVidia driver (195 this time around for Lucid) and haven't had a problem for the past 3 versions, I don't "roll my own" as it were. Older hardware compatibility again?

Also, I'm not quite sure I understand what a previous post said about GRUB2 not showing Kernel updates by default when GRUB2 has always shown any new kernel updates I've added in the past. It's done so (for me) since Ubuntu started using it. Just wondering why it doesn't show for some folks and does for others.

Hope you folks get things figured out. I'm always hoping I can duplicate a problem, find a fix for it and post it on the forums but this time I haven't had any luck. ;)

---

### Post by efflandt on 2010-07-16
Maybe the people with issues used some other method than Hardware Drivers or Synaptic to install their video drivers.  And that may be why kernel updates do not automatically include everything they need.  I had no trouble with kernel 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 and nvidia(1.95) for a GT220.  I had simply used Hardware Drivers to originally activate it.

Kirk M, the thing mentioned about GRUB2 is that the default is to NOT show the grub menu at all if there is no other OS on the computer.

---

### Post by Kirk M on 2010-07-16
> **efflandt said:**
> ...Kirk M, the thing mentioned about GRUB2 is that the default is to NOT show the grub menu at all if there is no other OS on the computer.

Oops, my mistake. I've been dual booting for so long now I'd completely forgotten. Been a long time since I had a single load of Ubuntu on a machine.

---

### Post by breek on 2010-07-25
i fixed the 2.6.32-23 but the same issue happened when installing the new 2.6.32-24.
the problem is that the meta package linux-headers-preempt (as in ubuntustudio i have preempt kernel installed) wasn't installed, so the new headers are not installed by default.
to solve the problem i've booted with a working kernel, and managed the packages from synaptic:
- installed linux-headers-preempt that installed linux-headers-2.6.32-24-preempt and linux-headers-2.6.32-24 as dependencies
- checked nvidia-current as reinstall

and everything is ok now ;)

---

### Post by paulmh_5 on 2010-09-10
Hello.  I think I have the same issue.
Unfortunately I'm Linux noob in every sense of the term.

Would someone be able to translate the solution into the coloured pictures and large text version so I understand :-(

I tried some of the commands mentioned in the previous posts but theres obviously something I've missed because most come back with some error or another.

Thanks

---

