---
title: "No access to bios boot order on Asus X205TA"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by jackn on 2015-12-21
Would like to proceed to a fresh install of 15.10 on the Asus X205TA laptop.

Made a 64-bit install DVD.
The computer won't start from the optical drive, however.

I can access the bios, but under the 'boot' tab, nothing like the usual boot priority order is displayed.
It only shows EFI or Windows boot options. 
Neither one of those boots off of the optical drive.
I keep ending up in Windows, and cannot test Ubuntu on this laptop.

I've disabled "secure boot", a suggestion I've seen on the French Ubuntu forum.
No cigar.

A network install would be a way to get around this hurdle, but I'd rather first test 15.10 on this relatively recent laptop with a live CD. 

What can I do?
Thanx for the input.

Jackn

---

### Post by oldfred on 2015-12-21
Some systems were created with 32 bit UEFI to keep them as Windows only systems. They wanted to be like a Mac and lock users into Windows only. Linux did not have a 32bit UEFI then. And they were UEFI class 3 which has no CSM or BIOS boot. And then not the easiest to add Linux to, even now that a 32bit UEFI boot has been created. And drivers can be an issue.

Installing 15.10 should be the same, 14.10 now obsolete.
 Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

Mega-thread with 300 posts on issues and some solutions.

 Asus X205TA hardware support in Ubuntu
[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)

---

### Post by jackn on 2015-12-21
Oldfred, this is prompt and complete.

I'm going to study this and then take action.

Thank you so much for your attention and advice.

Jackn

---

### Post by ubfan1 on 2015-12-21
The Asus x205 needs to have the USB boot device present to be able to set it into the boot order.  Remove or replace it and the entry disappears, or puts the Windows hard disk back in first place.

---

### Post by jackn on 2015-12-21
This is intriguing, ubfan1.

If I got your point, my USB optical drive should appear in the book order if it is plugged in at boot time.
In other words, it could only be missing from the boot order if it wasn't plugged at the time.

I sure hope sth like that exists, but this hasn't been my experience.

In my hands, though my USB optical drive will be plugged in at the time of startup, it doesn't appear in the bios boot tab.

Did I misunderstand your point?
Thank you for the quick response and this lead.

Jackn

---

### Post by grahammechanical on 2015-12-21
We are talking about an external USB optical drive, are we?

There may be other sections of the UEFI relating to USB devices that need to be altered. Also, the optical drive may need to be holding a disc with an OS on it for it to appear as an option in the boot order. Or it may be seen as an USB external drive and so come under a different section of the UEFI.

I know that this is the case with my BIOS boot system. Under one heading I can set the (non USB) optical drive to be first in the boot order. Under another heading I can set a USB memory stick as first to boot from before either of the 2 hard drives. The USB stick with Ubuntu on it is seen as an external USB drive.

Regards

---

### Post by ubfan1 on 2015-12-21
My experience is with USB thumbdrives getting removed from the first place in the bootorder.  If one is present and set first in the bootorder, it will stay there until it is removed and another boot occurs.  If a different USB is used (well different vendor, never tried with another from the same vendor), it will be put after the hard disk entry.  Other things worked fine on that machine, booting from a USB3 button with Ubuntu 14.04.

---

### Post by jackn on 2015-12-21
Yes, grahammechanical, we're talking an external optical drive.

Whenever I tried to boot from the Ubuntu DVD, I had the external (USB) optical drive plugged in at startup and loaded with the official 15.10 release.

I don't know whether the release itself, ubuntu-15.10-desktop-amd64, could affect the issue. 
I don't expect this to be the case, but I wouldn't know.

Could the DVD not be recognized for UEFI compatibility issues?
Alternatively, it is 64-bit, while Asus for some reason send the machine with 32-bit Windows 10.

I don't know, but I never saw the slightest indication that the laptop bothered with the optical disk at boot. 
And I've never seen a boot order in the bios.

Thank you for sharing about your BIOS.
Jackn

---

### Post by oldfred on 2015-12-21
Not sure if 64 bit versions works, but the issue is that the 64 bit version has 64 bit UEFI. 
And your system only boots with 32 bit UEFI, so you have a major work around. 
Standard 32 bit Ubuntu does not include 32 bit UEFI as it is not standard.

---

### Post by jackn on 2015-12-21
OK, oldfred.

I didn't know that the system being 64-bit could influence the boot.

I remind you that, in any case, no external drive item appears in the BIOS boot order.
And, so, if a compatible system were inserted into the external optical drive, would it then be recognized and loaded?

But this discussion suggests a test: if the 64-bit poses a problem, I should be able to boot with a 32-bit UEFI flavour. 
And it seems like people do add a UEFI feature to their systems.
I wouldn't know how to go about this myself, but I could explore.

Finally, I'm surprised by what your saying (as I am by Asus using a 32-bit Windows on a 64-bit machine).
To the extent that I understand this, the 64-bit modality is inherent in the machine's processor and firmware.
Shouldn't the machine then be able to boot with a 64-bit system?!
At boot time, after all, it's not Windows that runs the machine.
Or is the 32-bit preference also baked into the BIOS (which I think runs things at that point).

I took some time to answer as we're off each other day/nighttime-wise, as I live in France.
Thanks a bunch oldfred for this pointer.

jackn

---

### Post by jackn on 2015-12-21
This clears up things, ubfan1.

For my part, never saw anything other the UEFI, secure boot and 'Windows' boot under the BIOS's boot tab.

Thanx for adding this observation.

jackn

---

### Post by oldfred on 2015-12-21
This now is a bit older, and they had to totally recompile themselves. 
 New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)


 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

---

### Post by jackn on 2015-12-22
This looks very helpful, oldfred.

I looked at the first link, [http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855), which seemed the most promising one.
I'm afraid the discussion there is way over my head.

I thought you were linking to a 32-bit Ubuntu which comes with UEFI.
Is there such a thing?
Is there a clear, step-by-step guide to handling this issue?
Sorry, I would need that, as the secure-boot-UEFI-32-64-bit and what not now make up a blurry swirl in my head, and I can't see how I'd proceed.

Thanx for the accompaniment all along, oldfred.

---

### Post by oldfred on 2015-12-22
I do not think there is just a UEFI 32 bit download like there is for 64 bit. And before there really was nothing. You really just need bootia32.efi for both live installer & after install.

This user has a different system but goes thru details of making your own 32 bit UEFI.
[https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/](https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/)

More info:
[http://unix.stackexchange.com/questions/155557/installing-linux-on-an-32bit-uefi-only-machine](http://unix.stackexchange.com/questions/155557/installing-linux-on-an-32bit-uefi-only-machine)
[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)
[http://blogs.intel.com/evangelists/2015/07/22/why-cheap-systems-run-32-bit-uefi-on-x64-systems/](http://blogs.intel.com/evangelists/2015/07/22/why-cheap-systems-run-32-bit-uefi-on-x64-systems/)

After install:
It looks like you just replace in /EFI/Boot the bootx64.efi with bootia32.efi.
[http://ubuntuforums.org/showthread.php?t=2254317](http://ubuntuforums.org/showthread.php?t=2254317)

---

### Post by jackn on 2015-12-22
OK, oldfred.

In all honesty, no way I can take this on right now, what with how I need the box for work and the workload.
I will go back to it in the summer, as, like the rest of us, I love Linux, and, on top of it, I hate the idea of manufacturers and MS owning our boxes even after they've sold them to us.

FWIW, one last detail.
I actually got two Asus boxes, as I really use my laptop heavily both at work and at home.
And I thought I did the due diligence and cleared my purchase with what the forums said about compatibility.
Indeed, the more powerful box, Asus E202, is said to work very well with 15.10. I haven't yet installed Ubuntu on it, as it just came in, but I mean to, and expect no issues, given what other owners say.

My due diligence didn't go far enough, though.
I just assumed the X205 model, the one which started this thread, was the same, with less powerful features.
Big mistake there.
That it uses flash memory for storage, and not a hard disk, apparently makes for a big difference.
There may also be other differences, in BIOS and otherwise, which mean it is much less compatible.

In the summer, I'll deal with this calmly. Also, Ubuntu's compatibility with the hardware may improve further by then.

I'm very grateful for all the help, oldfred.
jackn

---

