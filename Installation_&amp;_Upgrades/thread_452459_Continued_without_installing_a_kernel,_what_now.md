---
title: "Continued without installing a kernel, what now?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Sebastral on 2007-05-23
Computer; Neoware mini-pc with Cyrix MediaGX 233 Mhz cpu

Installation procedure; feisty alternate [from iso]("http://ubuntuforums.org/showthread.php?t=316093")

Situation; apparantly can't find sutable kernel on iso so at one time asks 'continue without installing kernel?'

It finishes the installation fine but obviously can't boot without kernel. The only things I can do right now is fire up the installation again or hook the hd on my desktop pc. So no live-cd booting.
As far as I understand I don't need a special kernel for this particular cpu, or do I? Eitherway, can I just manually place a kernel? If so, how would I do that in a situation where the hd is out of his natural habitat?

---

### Post by blazercist on 2007-05-23
i dunno anything about that cpu, is it i386?  if it is you can probably plug the hd in and download the kernel_header and kernel_image debs and chroot that filesystem and simply unpack them.

---

### Post by Sebastral on 2007-05-23
Wikipedia says; Introduced in 1997, the MediaGX CPU was an x86 processor manufactured and designed by Cyrix and later after merger manufactured by National Semiconductor. The core is based on the integration of the Cyrix Cx5x86 CPU core with hardware to process video and audio output (XpressRAM, XpressGRAPHICS, XpressAUDIO). 

I guess so? Should I try 386 or generic?

---

### Post by blazercist on 2007-05-23
try generic. although i believe the first x86 was 386 generic should work.

---

### Post by Sebastral on 2007-05-23
Downloading from [https://launchpad.net/ubuntu/feisty/i386](https://launchpad.net/ubuntu/feisty/i386) takes forever so to get this straight;

a) I copy linux-image*.deb and linux-headers*.deb to target hd
b) in terminal I type; sudo chroot /location/target/hd/
c) I move to directory debs are located
d) I type; dpkg -i linux-image*.deb and linux-headers*.deb
e) I fix grub

and I'm done?

---

### Post by Sebastral on 2007-05-23
Sweet, I'm in business!

I copied the following files to /media/targethdpartition/root/ ;

linux-image-2.6.20-15-generic_2.6.20-15.27_i386.deb
linux-headers-2.6.20-15_2.6.20-15.27_i386.deb
linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb

then did a; sudo chroot /media/targethdpartition/

then dpkg -i'd the deb's in same order listed above

then installed grub but didn't have to really because grub was already installed by installer and editing menu.lst would be sufficient. So I added;

title		Ubuntu, kernel 2.6.20-15-generic
root		(hdtargethd,targetpartition)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/targetpartition ro vga=791
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hdtargethd,targetpartition)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/targetpartition ro single
initrd		/boot/initrd.img-2.6.20-15-generic

unmounted the targethd, placed in back and it booted flawlessly :popcorn:

Thank you for supporting blazercist :)

---

### Post by stchman on 2007-05-23
> **Sebastral said:**
> Computer; Neoware mini-pc with Cyrix MediaGX 233 Mhz cpu

Installation procedure; feisty alternate [from iso]("http://ubuntuforums.org/showthread.php?t=316093")

Situation; apparantly can't find sutable kernel on iso so at one time asks 'continue without installing kernel?'

It finishes the installation fine but obviously can't boot without kernel. The only things I can do right now is fire up the installation again or hook the hd on my desktop pc. So no live-cd booting.
As far as I understand I don't need a special kernel for this particular cpu, or do I? Eitherway, can I just manually place a kernel? If so, how would I do that in a situation where the hd is out of his natural habitat?

That processor is below the specs of Ubuntu 7.04.  I have an old P3-450 with 256MB RAM that runs really slow with Ubuntu.  I would recommend Puppy or Damn Small Linux on an older machine.

---

