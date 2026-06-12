---
title: "Boot problem after upgrade to 23.10"
date: 2024-07-14
forum: Installation &amp; Upgrades
---

### Post by snideatlondon on 2024-07-14
I've ended up with an unbootable system after upgrading my Dell XPS13-7390 (BIOS version 1.24.0) from 22.04 to 23.10 this morning. 

Boot-repair wasn't able to fix it with its default settings. Its output is at [https://pastebin.ubuntu.com/p/NVT4sZtDGG/](https://pastebin.ubuntu.com/p/NVT4sZtDGG/). 

Adding a new boot entry in BIOS for the file boot-repair recommends (efi/ubuntu/grubx64.efi) doesn't help, and I get redirected back to BIOS.

This is not a dual-boot device. There is only Ubuntu on the root partition. 

I note that 'Nvram is locked' but I am not sure how to unlock it. I've tried enabling / disabling TPM support in BIOS but that didn't help either. 

Does anyone have any suggestions on what else I can try?

Many thanks!

---

### Post by snideatlondon on 2024-07-14
Purging and reinstalling grub with boot-repair fixed my problem. Long live yannubuntu!

---

### Post by TheFu on 2024-07-14
> **snideatlondon said:**
> Purging and reinstalling grub with boot-repair fixed my problem. Long live yannubuntu!

Support for 23.10 ended 7/11/24.  You need to move to 24.04 ASAP!  If you wait, it will be 10x harder because the repos will be gone and that will break the update attempts.  [https://tuxcare.com/blog/ubuntu-23-04-end-of-life-is-near-upgrade-to-ubuntu-23-10/](https://tuxcare.com/blog/ubuntu-23-04-end-of-life-is-near-upgrade-to-ubuntu-23-10/)

Move to a supported ASAP release.  If you don't want 24.04, you can backup your data and install the prior LTS release, 22.04.  If you have really new hardware, 24.04 will likely work better.

---

### Post by djozinovic on 2024-07-16
I experienced the same problem (going from 22.1 -> 23.04 -> 23.1). I have a dual-boot system and can't boot into ubuntu (I can into windows though).  Can you tell me the exact options you used to run the boot-repair because the default settings do not work for me ([https://paste.ubuntu.com/p/M2pvjywNWq/](https://paste.ubuntu.com/p/M2pvjywNWq/)) ?

---

### Post by TheFu on 2024-07-16
> **djozinovic said:**
> I experienced the same problem (going from 22.1 -> 23.04 -> 23.1). I have a dual-boot system and can't boot into ubuntu (I can into windows though).  Can you tell me the exact options you used to run the boot-repair because the default settings do not work for me ([https://paste.ubuntu.com/p/M2pvjywNWq/](https://paste.ubuntu.com/p/M2pvjywNWq/)) ?

Mostly housekeeping stuff ... sorry:

For clarity, there isn't any 22.1 release.  The 2nd number is a month. October.  "10".  The trailing zero matters.  22.10, 23.10.  See how that works?  It is short for "2022 October" and "2023 October" releases.  The leading zero in ".04" similarly matters - "April".

Also djozinovic, your boot issue may seem similar, but in these forums, it is best to start your own thread for each problem rather than "me too" existing threads, so specific help for 1 person doesn't conflict with others.

---

### Post by djozinovic on 2024-07-19
> **TheFu said:**
> Mostly housekeeping stuff ... sorry:

For clarity, there isn't any 22.1 release.  The 2nd number is a month. October.  "10".  The trailing zero matters.  22.10, 23.10.  See how that works?  It is short for "2022 October" and "2023 October" releases.  The leading zero in ".04" similarly matters - "April".

Also djozinovic, your boot issue may seem similar, but in these forums, it is best to start your own thread for each problem rather than "me too" existing threads, so specific help for 1 person doesn't conflict with others.

Thanks for the cool information! 
I solved my problem by using a live USB (Ubuntu 23.10) and then chrooting into the existing system. I reinstalled GRUB and it was still not working. I then upgraded the OS version to 24.04 (from the live USB) and it works since then. Hopefully this will help someone.

---

