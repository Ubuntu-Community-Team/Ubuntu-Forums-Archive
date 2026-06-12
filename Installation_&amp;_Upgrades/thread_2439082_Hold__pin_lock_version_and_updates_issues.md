---
title: "Hold / pin/ lock version and updates issues"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by timomak on 2020-03-22
Firstly, for a desktop user, i believe that updates may sometimes return a system in a worse state of that before an update is being installed. This is when hold or pin a current good working version is recommended.
I will mention my experience, once, when after kernel update, my usb mobile broadband modem, which i use a lot, did not appeared/detected any more by the system and was finally unusable. It took me much time and effort to find a solution but with no result.

As about updates, my simplified understanding,  is that there are 2 categories. updates (general) and security updates   
But also, many articles are written concerning holding and pinning kernel, programs and other, but is not clear to me what these options do or mean. And of course what happens with security updates. Here are some questions about:

Q1: How hold/pin/lock the system in the current version, not only the kernel but mostly other modules and programs related to network, modems, drivers etc ?
Q2: Are the following commands (these are examples only) correct, and which one respond the Q1 ? 
-sudo apt-mark hold linux-image-4.8.0-46-generic linux-headers-4.8.0-46-generic

-sudo apt-mark hold "linux-generic*" "linux-headers-generic*" "linux-image-generic*" "linux-signed-generic*" "linux-signed-image-generic*" linux-libc-dev
(this command from this source [Easy Linux Tips Project: 39 Tips and Tweaks for Linux Mint - PART TWO]("https://easylinuxtipsproject.blogspot.com/p/tips-2.html#ID7")   said, freezes the hole system at its current state and version)

-run: gksudo leafpad /etc/apt/preferences
Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
Pin: version <insert version here>
Pin-Priority: 1001

Q3: When holding/pinning a version as above , are security updates still installed ?

This documentation about pinning how to seems to be a bit complicated.
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Thank you

---

### Post by Impavidus on 2020-03-23
I've used Ubuntu since 2006 and have never pinned a package. I got maybe four or five bad upgrades over the years, but always managed to solve the issues. So I wouldn't pin packages just in case the next upgrade is bad. Pinning can cause issues, one of them being that you won't get security upgrades either.

To continue getting security upgrades, but not the other upgrades, you can disable the -updates (and -backports) repository, keeping the -security repository enabled. Note that if you already have installed software from -updates, this might cause issues.

Kernel upgrades (which include drivers) are handled specially. The upgrade provides a new version, but the old version isn't automatically removed, so if there's a problem with the new kernel, you can use the grub menu to boot an older kernel. If you've got more than two kernels installed, the oldest becomes autoremovable and you can, but don't have to, configure your system to automatically remove it.

If you pin packages like **linux-image-<some_version>-generic**, new kernels will still be installed, but the old kernel you pinned will never be removed automatically. If you pin packages like **linux-image-generic** (with no version in the package name), you won't get any kernel upgrades.

BTW, the 4.8 kernel series is no longer supported on any Ubuntu version. It should no longer be used. Are you asking because the 4.15 kernel series gave issues for you? Ubuntu 16.04 used to provide 4.8, but now switched to 4.15 for HWE users and continues to support 4.4 for non-HWE users. And one year from now, support for 16.04 will end altogether.

---

### Post by timomak on 2020-03-23
Thank you for your answer.
I use Linux since 2016/ Lubuntu 16,04 and since Sep 2019 Xubuntu 18.04 and i find it very special OS. 
For upgrading to a new version i prefer download and install an image instead of upgrading the old one.
As about updates i install them as soon as they appear.
Answering to your question about Lubuntu 16.04 kernel 4.8, i don&#8217;t use it any more (it was just an example) but indeed i faced issues when installed updates with kernel 4.15 Lubuntu version 16.04.6. Usb mobile broadband modem wasn&#8217;t detected any more. I booted with previous kernel but didn&#8217;t help. I also didn&#8217;t find solution even after communicating usb_modeswitch. Here is the post about that. [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=2868](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=2868)
As about won't getting updates/upgrades, i guess this can be done via the updates gui settings choosing to never search for updates

Another question i need to clarify is about persistent usb live and security updates/upgrades. I thing of having a system like this as, persistent live or fully installed or even as live usb, just for reserve system and/or testing reasons. If you can answer to this will be fine otherwise should i post a new special thread?

---

