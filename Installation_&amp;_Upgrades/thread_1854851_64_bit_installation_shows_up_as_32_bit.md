---
title: "64 bit installation shows up as 32 bit"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by nikhilpatwardhan on 2011-10-05
Hi,

I installed 64 bit Ubuntu (Windows installer) on two machines with Intel Pentium-R E 5700 dual core processor. On one of the machines, when  do a uname -a post installation, I can see x86-64. However, on the other machine with the same CPU, it shows i686, which I guess, means that a 32 bit version has been installed. This baffles me as i sued the same ISO image for installation(ubuntu-10.04.3-desktop-amd64.iso) on both machines. Am I missing something here?

Thanks
Nikhil

---

### Post by nikhilpatwardhan on 2011-10-05
Fixed. My mistake. I was using the wrong ISO.

---

### Post by haqking on 2011-10-05
> **nikhilpatwardhan said:**
> Fixed. My mistake. I was using the wrong ISO.

make sure you mark the thread as solved.

cheers

---

### Post by 450rOOST on 2011-10-05
I am new to ubuntu and and about to download to a cd to try, it recommends 32 bit.  Why is that? Would 64 not be faster?  Sorry for my ignorance.

---

### Post by Bluesan on 2011-10-05
> **450rOOST said:**
> I am new to ubuntu and and about to download to a cd to try, it recommends 32 bit.  Why is that? Would 64 not be faster?  Sorry for my ignorance.

If you take the time to read through the myriad of other threads on the forums discussing this, I think most of it had to do with flash issues.

However, a 64-bit version of flash is easy to get now, and it looks like it will be standard for 11.10.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

[https://answers.launchpad.net/ubuntu/+source/flashplugin-installer/+question/173230](https://answers.launchpad.net/ubuntu/+source/flashplugin-installer/+question/173230)

Personally, my advice would be, if you have 64-bit architecture, install the 64-bit version of Ubuntu.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

But, there's nothing wrong with staying with 32-bit. It'll run just fine on a 64-bit machine. It's up to you...

---

### Post by oldos2er on 2011-10-06
None of it had to do with flash; the website maintainers (*not* the developers) assumed people downloading Ubuntu wouldn't know which architecture they would need, so they steered people toward 32-bit.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940?comments=all](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940?comments=all)

---

### Post by Bluesan on 2011-10-07
> **oldos2er said:**
> **None of it had to do with flash**; the website maintainers (*not* the developers) assumed people downloading Ubuntu wouldn't know which architecture they would need, so they steered people toward 32-bit.

[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940?comments=all](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940?comments=all)

I stand corrected, thanks.

---

### Post by oldos2er on 2011-10-07
No problem.

---

