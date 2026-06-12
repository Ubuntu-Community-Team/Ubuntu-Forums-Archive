---
title: "Ubuntu won't boot - &quot;random: nonblocking pool is initialized&quot;"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by earthboundbob on 2015-11-17
Hello folks.

I've got a problem. And I'm by no means an experienced user, so please bear with me.

After removing old kernels to free up space and applying a software upgrade, I restarted Ubuntu and found that it would not boot properly. I was able to boot into Recovery Mode, but then I stupidly meddled with the graphics drivers in System Settings > Software & Updates > Additional Drivers. Specifically, I switched the driver from open source (x.org, I think?) to a proprietary NVIDIA driver. I restarted, and that's the last time I've been able to get into Ubuntu.

Now, when I get to the GRUB2 menu, Recovery Mode isn't an option. I've tried many times to boot with a USB (which works perfectly well on my laptop), but when I try entering live mode, I get a bunch of text on the screen that ends with the following two lines:

"Switched to clocksource tsc"
"random: nonblocking pool is initialized"

The cursor blinks at the bottom of the screen indefinitely. I can enter text, but nothing else happens.

I have scoured these forums and the Internet for days looking for fixes for this. Nothing seems to be working. I've poked around using the grub prompt and I can see that my files are all still there, but I cannot locate a kernel, nor can I find vmlinuz or initrd. I've updated my BIOS to the latest version, but still no luck. Any help you can offer is greatly appreciated!

---

### Post by ian-weisser on 2015-11-18
Boot from your LiveUSB, backup your data, then reinstall.

While it may be possible to ressurect your system, the multiple and compounding problems ("would not boot properly", "switched the driver", "cannot find a vmlinuz or initrd") makes troubleshooting very difficult and probably not worthwhile. Days and days of frustration.

A single problem is a good experience to learn from. A multiple problem isn't.

---

### Post by tgalati4 on 2015-11-18
If you deleted all of your kernels, then you can't get to recovery mode.  You want at least 2 kernels.  The current version kernel for your system, and one backup kernel--for situations like this one.  

With a proprietary graphics driver, any updates to the kernel generally require reinstalling the proprietary graphics driver.  Going from open source graphics to proprietary graphics can leave you with a blank screen if there is a compatibility issue.

I have to agree with *ian-weisser*, your system is in a mangled and indeterminate state.  Troubleshooting is difficult if you can't boot into a recovery shell.  Follow his advice and backup your important data and perform a fresh install.  

Trying to simply restore your kernel and graphics from a Live Session is difficult and puts your data at risk.

---

### Post by earthboundbob on 2015-11-18
Many thanks for taking the time to reply.

The only problem with your suggestion, ian-weisser, is that I can't seem boot with a LiveUSB. The error message I get appears when I try to do just that. Like I said, I know my files are still in there somewhere, but if I'm unable to boot regularly or with a LiveUSB, is it possible to back them up? Can this be done through grub? Any ideas for fixes that might make a LiveUSB boot possible?

---

### Post by ian-weisser on 2015-11-18
Make a new LiveUSB (or overwrite the old one) on a working computer. LiveUSB images generally cannot be 'fixed', and are intended to be disposable.

When you create a new LiveUSB, test it (boot from it) on that working computer. If your system has problems, rule out as many possible causes as possible.

---

### Post by tgalati4 on 2015-11-19
When you boot, hit F12 or esc to bring up the Boot Devices menu, then select USB to boot from.  Sometimes you have to enable "Allow Boot from USB" from BIOS as it is normally turned off as a security precaution.

---

### Post by earthboundbob on 2015-11-19
Booting from a USB was one of the first things I tried to do. I just tried it again, with a fresh Ubuntu ISO, and, again, it works perfectly on my laptop, but not on my PC. What happens is, the Unetbootin window comes up, and I select, "Try Ubuntu without installing." After a brief delay, I just get a black screen with white text, ending with "random: nonblocking pool is initialized," and then a cursor blinking indefinitely. Something seems to be preventing the computer from booting from the USB, but I have no idea what it could be. Is my motherboard or some other piece of hardware shot?

---

### Post by tgalati4 on 2015-11-19
It's booting from USB alright.  I think the problem may be switching graphics modes during boot.  This happens right after creating the random generator device /dev/random.

[http://tamxuanla.blogspot.com/2015/06/random-nonblocking-pool-is-initialized.html](http://tamxuanla.blogspot.com/2015/06/random-nonblocking-pool-is-initialized.html)

Try using the *nomodeset* switch.

---

### Post by earthboundbob on 2015-11-20
It worked! Thank you!

---

