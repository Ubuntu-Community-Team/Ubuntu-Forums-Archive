---
title: "Latest Kernel with AMD 32-bit processor"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by fredringwald on 2017-04-01
It appears that ubuntu distribution kernels since linux-image-4.8.0-22-lowlatency are compiled for AMD 64-bit processors. I am running an AMD A8-5600K four-core processor, and I am unable to run the latest kernels. I am currently running linux-image-4.8.0-22-lowlatency, but have had to remove package linux-image-lowlatency because the auto update installs later kernels which don't appear to support my processor.

The following page suggests that the latest kernel only supports AMD 64 bit processors:

[https://launchpad.net/ubuntu/+source/linux-hwe/4.8.0-45.48~16.04.1](https://launchpad.net/ubuntu/+source/linux-hwe/4.8.0-45.48~16.04.1)

I would appreciate any advice or information regarding ubuntu kernel support for my AMD 32 bit processor.

Thank you!

---

### Post by jscythe on 2017-04-01
"AMD A8-5600K" is both AMD64 and i386 processor, BOTH i386-32 and AMD64/x86-64 bit. 
> The following page suggests that the latest kernel only supports AMD 64 bit processors where EXACTLY does it says so? Page says both "Architecture i386 amd64".
> unable to run the latest kernels - How EXACTLY you are not able to run "latest" kernels and what you see on screen? - record video and post youtube link if you can't explain.
Btw, any particular reason why you use lowlatency and not generic kernel?

---

### Post by fredringwald on 2017-04-01
jscythe,

First, please let me thank you for your reply. I have several responses to your questions.

1) I agree, it appears that I was wrong regarding the capability of my A8 processor. I drew that conclusion when I was not able to get Chrome for linux to work after Google dropped support for AMD 32-bit processors, and knew that my processor was several years old.

2) Sorry, I wasn't complete in my statement regarding the page I referenced. Under architectures, the only AMD architecture that I saw was AMD64, and I intended to say that the only AMD architecture supported was AMD64, I was inappropriately ignoring the long list of other architectures that I thought were not relevant to my situation.

3) The latest kernels (everything I have tried since linux-image-4.8.0-22-lowlatency) will start to boot, won't finish, and will then return me to my BIOS screen where I can choose to enter BIOS setup. The video at: [https://youtu.be/2DjKyANL-v8](https://youtu.be/2DjKyANL-v8) shows this process. I have scrubbed my /var/log/syslog and cannot find any information suggesting why the later kernels aren't completing the boot process.

4) I am using the lowlatency kernels because that was the default kernel installed by the ubuntu studio installation disc when I shifted to ubuntu studio years ago. They have served me well, and I haven't given my kernel choice a second thought since. From the genesis of linux in the early 1990s until about 10 years ago when my work demands ramped up, I compiled my own kernels regularly. I was an early user of minix and Coherent, wrote a number of programs in c, pascal, and other languages, and regularly compiled and ran emacs, gcc, etc., as well as many other projects. I recently retired, and have discovered that linux has changed a lot in the last 10 years, and I have a lot to learn to catch back up to the point of fluency that I once had. 

Again, thank you for your reply to my question. I will welcome any help offered, and will gladly provide additional information as needed to isolate the problem.

Fred Ringwald

---

### Post by jscythe on 2017-04-01
Alright, from video it looks like boot process went far enough into device enumeration, but it may be UEFI/BIOS issue too. Could you please share content of tail (around 300 lines) "/var/log/dmesg" (or dmesg.log) and possibly "/var/log/boot.log" before failure?

---

### Post by fredringwald on 2017-04-01
jscythe,

I appreciate the response, and don't know how to provide the information you have requested. My /var/log/dmesg file have file creation times from last July. The dmesg command only provides kernel ring buffer messages from the current boot, which was successful since I booted linux-image-4.8.0-22-lowlatency after linux-image-4.8.0-45-generic did not complete the boot process. As I scour my /var/log/syslog, I don't find meaningful boot messages associated with the incomplete boot of linux-image-4.8.0-45-generic. I have a /var/log/boot from last August, and a /var/log/boot.log from today that doesn't have meaningful data from the incomplete boot.

Is there a way to enable the boot logging or some other way to capture it so we can figure this out?

Sorry to be a pain, I just don't see a way to capture the data.

Thank you,

Fred Ringwald

---

