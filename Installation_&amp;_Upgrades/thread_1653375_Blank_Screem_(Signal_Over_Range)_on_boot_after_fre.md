---
title: "Blank Screem (Signal Over Range) on boot after fresh install"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by lekremyelsew on 2010-12-26
Hello.

Let me start off by telling you the problem I had with the Ubuntu 10.10 i386 desktop live CD. When I first tried the live CD I would get the normal screen but when I continued to the "try ubuntu without installing" option the signal went out of range for my monitor. Upon further investigation, the computer would display the line 'Buffer I/O error on device sr0, logical block 177448' along with about 5 other lines of error text about 10 times over, then it would process to create the user login, where it would freeze. Instinctively, I used a different monitor (a smaller one might I add) and got the same problem. I then booted up with the 'nomodeset' option, which worked fine, and installed the OS on a brand new ext4 partition spanning the whole hard drive. Because there is only one partition to boot off of, the boot loader doesn't take me to the screen where the user can select different images to boot off of. So what happens when I attempt to boot from the hard drive is the system gives me a little flashing underscore for a few seconds, then proceeds to the login screen. But because the video signal problem persisted through the install, I get a "SIGNAL OVER RANGE!" error on the computer monitor. With the larger monitor I simply get a "No Signal (Monitor Powering Off)" message. And I cant edit any of the boot parameters because, again, there is no input prompt of any sort from the time the initial boot screen from the computer manufacturer disappears and the signal over range error.

So what I specifically need help with is finding away to include the 'nomodeset' boot option to the normal boot process so that I can login to my own computer and begin to address the original  video problem.
My idea was to use the live CD to edit the grub options on the hard drive, but from the live CD, the file system is read-only.

Any ideas?

---

### Post by sikander3786 on 2010-12-27
Press and hold down Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot.

Once on the desktop, go to System > Administration > Additional Drives and if it is an Nvidia/ATI card, activate the current drivers there and that should get rid of the problem permanently.

If drivers are not available, for a permanent fix, post the output of this command.

Applications > Accessories > Terminal:

```
lspci | grep VGA
```

---

