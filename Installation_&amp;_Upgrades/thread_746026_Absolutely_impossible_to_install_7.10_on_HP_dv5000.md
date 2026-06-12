---
title: "Absolutely impossible to install 7.10 on HP dv5000"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Kigresyl on 2008-04-05
Hello, I've been trying to install 7.10 on my HP dv5000 laptop for a few days now. However, there's always some sort of seemingly random error with both the desktop and alt cd's.

I've checked the ISO's against their md5's, I've tried burning the cds at 1x speed, I've verified the burns with my burning program(IMGburn on windows xp). Whenever I check the CD's with Ubuntu's boot CD checker, they always find some error however.

The many times I've tried installing, any number of strange things happen, from the live portion of the CD loading and the install ending at 26%(complaining that the hard drive couldnt be read),to the normal setup option just going into some sort of terminal(busybox). other outcomes are the screen freezing at the ubuntu logo and the progress bar with my caps lock blinking, random I/O errors, etc...

The alt CD gave me more hope, however there's always some file missing that prevents it from setting up properly.

I've had no trouble installing Windows on it, nor SuSe or fedora years ago, so why would this release give me so many headaches?

I've tried the noacpi nolacpi noapic nolapic boot options, but those had no effect.

I'm downloading the 7.04 install, but hopefully there's something I'm missing that will solve these annoyances. Thanks.

---

### Post by .nedberg on 2008-04-05
Try running a mem-test from the cd. Sounds like it could be somthing hardware related (I am no expert though...).

---

### Post by michaeljking on 2008-04-05
or me the I had many issues with the 7.10 release due to the Kernel verison used, My laptops were all pentium 3 though. 
The new 8.04 beta does work on it lovelly so I am optimistic that in a few weeks I will have an up to date Ubuntu tather than having to use the 7.04 version!!!

---

### Post by karachuonyo on 2008-04-05
I had problems installing Kubuntu 7.10 on a new HP desktop as well. Both the live cd and alternate will start then drop me to CLI and stall. I solved it by using a GParted live CD to partition the hard drive then installed with the 7.10 alternate. Still it could not install properly with sound missing and flaky xorg. I've now installed 8.04 Beta (alternate) and its as so far it's stable and everything works. Will monitor the stability/usability as the packages get upgraded.

---

### Post by dstew on 2008-04-05
> Whenever I check the CD's with Ubuntu's boot CD checker, they always find some error however.That is a clue to what might be the problem. If you burn the CD in one machine, and the CD checks out there, but does not check out OK in another machine, what you have is some data that is marginally readable. So, the disk fails in one CD-ROM drive that seems to work fine in another. If the CD does not pass the integrity test *in the drive you will use to install it*, it will not work.

Sometimes, you can clean the lens of the CD-ROM. Sometimes, it helps to use high-quality media. Use a CD-R instead of a CD-RW. Try to burn in a third computer.

EDIT: Another idea is to try to install the minimal (base or "server") system, which is a command-line system first. Because it is small, maybe you can get it in without errors. Then, go on-line and install the Ubuntu desktop with```
sudo apt-get install ubuntu-desktop
```That downloads the packages over the internet. It takes about an hour at DSL speeds. But, you get the error-checking built into TCP/IP, so you probably won't have any errors or bad packages.

---

### Post by LongTooth on 2008-04-05
I too have an HP dv6000 and I've given up on 7.10. But I was able to install 8.04. So that's what I'm using. 

I've got the laptop hardwired. Don't know how to set up my wireless. Hopefully I'll find the solution as 8.10 progresses. Of course that might not be the case as my HP is using the Broadcom 9431 card. And I've read where Broadcom gives fits to it's users running Linux. We shall see.

But install 8.10. That might solve most of your problems. Well, most of them.

---

### Post by Kigresyl on 2008-04-05
Thanks for the help so far, but....

I've tried using rubbing alcohol on a qtip to clean my cdrom's lens, but that made no difference.

I've tried the 7.04 release and the 8.04b release, both to no success.

Is there some way to do some kind of network install without having an OS already on my system? I remember being able to do something like that back when I installed SuSe Linux, I downloaded the network install ISO, and it booted up and handled the rest. If I could do something like that with Ubuntu it'd probably make my life hella easier.

Oh and I can't get the base system installed on my computer, the install screws up even before then.

Thanks again.

---

### Post by Pumalite on 2008-04-05
These might help (not sure):
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

---

### Post by Kigresyl on 2008-04-06
Well, I've solved the problem... I guess.

I burned the ISO to a DVD instead of a CD. I was able to boot from it without a problem and installed 8.04.

Thanks again guys.

---

