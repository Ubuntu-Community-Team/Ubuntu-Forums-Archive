---
title: "Computer does not poweroff since upgrade from kernel 3.19.0.25"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by Simon_Cropper on 2016-02-22
Hi,

I have been trying to resolve this for a while and have not been able to solve the issue.

The problem is simple, since the kernel was upgraded from 3.19.0.25 the computer will not shutdown properly. It starts the sequence then halts after 6-10sec -- it does  not poweroff the computer, it seems to stop at a higher running state with the logoff screen still visible. To shutdown the computer I have to press the power button until the computer actually powers off. As a work around I have reverted back to kernel version 3.19.0.25 and at each new kernel upgrade tested again. Despite multiple upgrades this problem has not disappeared.

I have read many many blogs and posts on related issues but nothing that has been suggested works. It appears to me that it was about this time that the Upstart system was changed for the Systemd system, and this somehow has made ubuntu incompatible with my hardware. I have tried reinstalling Ubuntu 14.04 LTS (which I currently use with the Mate Desktop), changed various desktop environments and moved to the latest Ubuntu release or different 'flavours' -- essentially if the distro has the latest kernel my shutdown does not work.

I can't believe I am the only one with this problem, yet few seem to be reporting the issue. 

Can anyone suggest how I can proceed?

Thanks Simon

---

### Post by coldraven on 2016-02-23
Using Ubuntu 15.10 I had the same problem but in my case it was 4.2.0-19-generic that broke it. The solution was to make grub use an earlier version.
See here: [http://ubuntuforums.org/showthread.php?t=2300290&p=13399859#post13399859](http://ubuntuforums.org/showthread.php?t=2300290&p=13399859#post13399859)

---

### Post by Simon_Cropper on 2016-02-23
coldraven,

Yeah that has been my solution to date. I have used GrubCustomizer to specifically select kernel version 3.19.0.25 but I note we are now around 3.19.0.51 and there still is no fix, no official recognition of the problem and no mention whether it is going to be resolved. 

To be honest this concerns me. The whole idea with Linux is that you can use it on older machines (although mine is not that old), yet this shift appears to be drawing a line in the sand. I will not be able to upgrade to more up-to-date versions of Ubuntu because they will want to integrate with the latest kernel -- at least that is what happened when I did a clean install of Ubuntu 15.04 and 15.10 to try and resolve the problem.

The other thing that is irritating is that I was originally and currently using 14.04 LTS -- how is ripping the kernel out from under your OS, stable? This is very poor. In addition, the lack of timely resolution and interest in this topic has me looking into alternative solutions -- that is, non-Linux based systems. 

Thanks Simon

---

### Post by Simon_Cropper on 2016-02-24
As outlined above I am having a problem with how the kernel talks to my machine.

The workaround for this issue is to hold the kernel at version 3.0.19.25. 

What is the implication of not upgrading your kernel?

My understanding is that the kernel is the main conduit between the OS  and hardware. Upgrades aim to improve performance and plug security  issues. Holding a kernel at a particular version is likely to put your  computer at risk the longer you don't upgrade.

Is my understanding correct? Should I be concerned?

P.S. I have asked this as a separate question as I considered it to be a different  question to the issue being triaged. A moderator has asked my to post it here.

---

### Post by Simon_Cropper on 2016-02-24
OK. I solved this problem.

After ferreting through by the system files I saw a few warning about the BIOS. I checked Intel's Website and there was an upgrade available that seemed to solve an issue of overlapping memory addresses. Not obviously the same but my logs indicated that various sectors of my BIOS were returning unexpected values, which did not stop the kernel starting but obviously was not good.

I downloaded the updated BIOS and applied it and now my system turns off as expected.

---

### Post by coldraven on 2016-02-25
> **Simon_Cropper said:**
> As outlined above I am having a problem with how the kernel talks to my machine.

The workaround for this issue is to hold the kernel at version 3.0.19.25. 

What is the implication of not upgrading your kernel?

My understanding is that the kernel is the main conduit between the OS  and hardware. Upgrades aim to improve performance and plug security  issues. Holding a kernel at a particular version is likely to put your  computer at risk the longer you don't upgrade.

Is my understanding correct? Should I be concerned?

P.S. I have asked this as a separate question as I considered it to be a different  question to the issue being triaged. A moderator has asked my to post it here.

I too would like to know the answer to that. My laptop is over five years old so I doubt that any newer kernel will make it work better. I presume a newer kernel would recognise more modern peripheral devices.

---

### Post by gordintoronto on 2016-02-25
A newer kernel also closes security holes.

---

### Post by Simon_Cropper on 2016-02-25
Hey coldraven, did you check whether your problems were solved by a BIOS update?

---

### Post by coldraven on 2016-02-26
> **Simon_Cropper said:**
> Hey coldraven, did you check whether your problems were solved by a BIOS update?
I have the latest BIOS but this laptop is about five years old so I don't expect any newer versions to appear.
If any new security issues arrive I'll try a newer kernel, skipping the one that caused problems.

---

### Post by Simon_Cropper on 2016-02-26
Fair enough. My computer is only 6 years old. My BIOS was dated 2007 with an update for 2009. I have been operating the computer fine for all this time. I presume, it was only the change from Upstart to Systemd that brought the problems to light.

BTW, although I can turn my computer off, I noticed it can hang if the computer is allowed to idle for extended periods. Obviously I am still going to need to make some minor adjustments to the BIOS and GRUB -- I made so many changes over the last few months that I probably did not reinstate a setting to the original state.

---

