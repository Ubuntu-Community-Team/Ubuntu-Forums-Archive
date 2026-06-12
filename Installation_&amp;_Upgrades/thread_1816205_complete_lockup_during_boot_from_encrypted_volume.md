---
title: "complete lockup during boot from encrypted volume"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by hirscherne on 2011-08-01
Hello,

I've installed Ubuntu 11.04 on a Fujitsu Esprimo E900. During installation, I've used the guided encryption setting because neither GRUB nor LILO would ever install on the LVM configurations I created myself. :mad:

So after installing Ubuntu 11.04, when I boot regularly, the computer freezes completely. When I try to launch the recovery mode kernel, I get this far and then the computer locks up, too.

[[IMG]http://farm7.static.flickr.com/6141/5975543312_ee32f5e786.jpg[/IMG]]("http://www.flickr.com/photos/germanium/5975543312/")
[Ubuntu lockup during boot]("http://www.flickr.com/photos/germanium/5975543312/") by [germanium]("http://www.flickr.com/people/germanium/"), on Flickr

You can see the label is sdb5_crypt which is a bit odd since the partition is on /dev/sda. However, I already tried changing grub.cfg to /dev/sda instead of /dev/sdb but that didn't do anything.
This is all a bit odd to be. The funny thing is I've been trying to set this computer up for a month and I'm a professional programmer (Java, JavaScript, Groovy) with 20 years of programming experience and I never thought Ubuntu would be this hard to install on a more-or-less stock Intel box.

Does anybody have an ideas what this could be?

I'm attaching the GRUB config and the output of lshw, I hope it's useful.

Thanks for any help.

---

### Post by hirscherne on 2011-08-06
I'm experimenting with different options and this is what I've tried:

[LIST]
[*]normal kernel, root /dev/sda instead of /dev/sdb, nosplash, acpi=off -- locks up
[*]normal kernel, root /dev/sdb, nosplash, acpi=off -- locks up
[*]rescue mode, root /dev/sda -- locks up
[*]gfxpayload=text, root only /dev/sda (from /dev/sdb,msdos1), no quiet, no splash, no vt.handoff=7 -- locks up
[*]nomodeset -- got a text Ubuntu logo and not the USB device output seen in the screenshot above and the prompt to enter the passphrase, but can't enter anything. I can't even switch to another TTY. Could it be dm_crypt doesn't support USB keyboards?
[*]xforcevesa -- locks up
[*]i915.modeset=0 xforcevesa -- same as nomodeset
[/LIST]

Do you think it would be a good idea to try a PS/2 keyboard?

---

### Post by hirscherne on 2011-08-12
I've organized a USB to PS/2 adapter and I was able to enter my password now.

Is it just me or is it incredibly stupid that GRUB works fine with an USB keyboard but dm_crypt/LUKS doesn't?

Of course, after booting, the next problem came up -- /dev/sda1 wasn't mounted at /boot. Mounting it manually from a shell worked but exiting the shell locked it up.

Installing Ubuntu on an encrypted disk feels a lot worse than creating Gentoo from stage 1 in 2004. I can't believe 1. I'm trying to do this for one and a half months now and 2. this is Ubuntu I'm dealing with.

I guess I'll clone the disk of my existing notebook because Ubuntu is so unbelievably broken.

[WMA to MP3]("http://media.io") ~ [QR Code Generator]("http://invx.com") ~ [Pearson Correlation]("http://pearsoncorrelation.com") ~ [PDF to TIFF]("http://pdfimg.com") ~ [Forex Data Feed]("http://currencyfeed.com") ~ [URL="http://spearmancorrelation.com"]Spearman Correlation Coefficient
[/URL]

---

