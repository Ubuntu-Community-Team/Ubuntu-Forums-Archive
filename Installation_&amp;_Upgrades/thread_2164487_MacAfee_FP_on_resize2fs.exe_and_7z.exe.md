---
title: "MacAfee FP on resize2fs.exe and 7z.exe?"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by Graham_Toal on 2013-07-31
I have a Dell Inspiron portable, reformatted last night to factory defaults and Windows 8 using the recovery disk.  I tried to install dual-boot Ubuntu 12.04LTS using the wubi installer from an image I downloaded and checked off the Ubuntu download site. (64 bit image for Win8 systems: "ubuntu-12.04.2-desktop-amd64")

As soon as it unpacks its internal files into the AppData directory, they're deleted by the McAfee installation that comes with this system which claims that resize2fs.exe and 7z.exe are trojans.  Given the virgin state of this system and the disk image from your site which has been there for some time, I seriously doubt that this is a genuine detection.

I just thought you might like to be aware of this.  (I'm not looking for a fix, just letting you know.)

(A separate issue, and not your problem in any way, is that it is nigh impossible to remove this McAfee trial and revert to the copy of Microsoft Security Essentials that should come with Windows 8, but which is disabled due to having McAfee bundled with the system.  The reformat I mentioned was caused by messing up once when trying to remove McAfee.  MSE will not activate because it thinks that McAfee is active, even when it appears to be completely removed...  I'm getting very close to making the system single-boot Ubuntu only, but I do have some legacy apps that I occasionally need Windows for. )

regards,


Graham

---

### Post by lah7 on 2013-07-31
> **Graham_Toal said:**
> I'm getting very close to making the system single-boot Ubuntu only, but I do have some legacy apps that I occasionally need Windows for.

If Windows is really driving you up the wall like it did with me, why not make the full switch already? **For legacy apps,** you can run them in the Wine compatibility layer, or if they're not compatible under Wine, consider running them in **virtualization** software like **Virtualbox **([http://www.virtualbox.org](http://www.virtualbox.org)) which basically runs Windows within Ubuntu side-by-side. This depends if your system has enough RAM, disk space and is willing to sacrifice some CPU. You'll also need your Windows discs handy.

I'm honestly not a fan of McAfee or Norton for thinking they're in total control, many times they accuse genuine apps as malicious and do what they please. If you can,** report this incident** to McAfee as a "false positive" so it lets them know that their software is falsely identifying Wubi as a trojan.

**If you're still wanting to dual boot,** you could try again with Wubi with the virus protection turned off, or prehaps trying via safe mode. You could do it without Wubi or Windows, by first shrinking the Windows' partition to give some unallocated space, and then image the Ubuntu installation media to a CD or USB drive and install to have a true dual boot between Ubuntu and Windows.

---

### Post by Graham_Toal on 2013-07-31
I did try again with the AV disabled, unfortunately because of the UEFI boot issue I now have windows disabled as well :-(  Virtualbox would look very tempting if I had a stand-alone licensed copy of windows to use rather than these ones that are all tied to the motherboards of the systems that they came installed on.

By the way there are lots of posts about the right way to set up a system for dual boot, but none I can find that give a simple way to restore the windows boot after it's broken.  Looks like another late night with the restore DVD again...

G

---

### Post by lah7 on 2013-08-01
I haven't purchased a laptop since Windows 8's been around, I'm really not liking how they're trying to lock down your own system.

One thing you must disable is** secure boot**, this page will help you when UEFI's getting in the way:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Disabling this should unlock your computer to install any OS, not Windows that's already pre-installed.

---

### Post by Graham_Toal on 2013-08-01
Thanks lah7 - and the UEFI stuff is fairly well documented here, unfortunately it's all advice that's best taken before you start tinkering :-)

I was able to repair the broken boot eventually, but since all my data files were on drive C which is the same as the boot drive, the manufacturer's recovery disk forced me to wipe all the user files in the process of reinstalling the OS - it wasn't smart enough to just repair the boot blocks, it insisted on rewriting the whole OS partition.  Fortunately since I had just been through this procedure the day before - and that time being deliberate, so I had time to back up all my files before reinstalling - I was lucky enough to have had everything I wanted to save already sequestered away in a single directory and the recovery disk let me select other items to save by directory.  Although it was a little nerve wracking on account of not having a spare copy on any external media and not being able to make a copy until the repair was complete!

Anyway, what I was getting round to explaining was that if you disable secure boot (which I did), the recovery disk no longer works.  I had to enable UEFI again in order to repair the windows installation.  I suspect that I'd have the same problem trying to create the windows half of a dual boot system if I went that route.

In the end I installed Ubuntu under virtual box, although even that is a pain because you have to manually add a new screen mode for the 1366x768 display, since only 4:3 modes are supported out of the box.

When I find myself digressing like this I guess it's time to mark the thread closed.  Thanks for the advice everyone.

Graham

---

