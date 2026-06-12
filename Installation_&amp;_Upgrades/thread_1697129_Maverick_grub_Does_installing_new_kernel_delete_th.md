---
title: "Maverick grub: Does installing new kernel delete the old?"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Embedded Linux Guy on 2011-02-28
Hi, I just installed a new kernel yesterday via dpkg (2.6.38-999) and was disturbed to find one of my old kernels (2.6.32-25) is now gone. Furthermore I can't re-install it with apt because it isn't in the Maverick repository (I had it leftover from Lucid). I don't remember agreeing to delete this kernel, nor is there any record of removing it in /var/log/apt/history.log. So my questions are: 

1] Do the Ubuntu packaged kernels specify a limit as to how many kernels can be installed?

2] Where is this documented and how can I change it? 

$ aptitude search linux-image-2.6.32-25
c   linux-image-2.6.32-25-generic     - Linux kernel image for version 2.6.32 on x86

---

### Post by Quackers on 2011-02-28
Not in my experience. Have a look in synaptic and in the search box enter 2.6.32 and see what comes up

---

### Post by Embedded Linux Guy on 2011-02-28
Quackers: Below is the message from synaptic when I double-click 2.6.32-25. At this point I am afraid to install any new kernels in case it starts deleting my old ones (currently my grub boot screen is full with 8 entries or so).

Package linux-image-2.6.32-25-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by Quackers on 2011-02-28
Just try searching for 2.6.32 only and see how many come up as installed

---

### Post by Embedded Linux Guy on 2011-02-28
According to synaptic there are no 2.6.32 kernels installed. It had definitely gone away - there is no more entry in in /etc/grub.d and no file in /boot.

$ dpkg --listfiles linux-image-2.6.32-25-generic
Package `linux-image-2.6.32-25-generic' does not contain any files (!)

---

### Post by KegHead on 2011-02-28
Hi!

It should be there.

By any chance do you Ubuntu Tweak?

If so, it will show you.

KegHead

---

### Post by Quackers on 2011-02-28
Hmm, I don't know what happened there. Try searching for 2.6.35 and see how many kernels appear

---

### Post by ajgreeny on 2011-02-28
Use the command ```
grep menuentry /boot/grub/grub.cfg
```in terminal.  It will show all the entries in your grub.cfg file which will equate to the kernels and recovery modes and windows and memtest86+ which are installed at the moment.  That will give be your definitive answer.

---

### Post by Embedded Linux Guy on 2011-02-28
ajgreeny: Thanks for this tip; the kernel is definitely not listed. I will start keeping a backup of grub.cfg so I can detect any monkey business in the future.

KegHead: Tweak looks like a possibly useful program although I did not see any way to manage kernels with it (other than Package Cleaner to remove them).

All: I just downloaded and installed a Lucid .deb for 2.6.32 so I'm reasonably happy now (til the next time one of my kernels disappears :)

[http://packages.ubuntu.com/lucid-updates/i386/linux-image-2.6.32-28-386/download](http://packages.ubuntu.com/lucid-updates/i386/linux-image-2.6.32-28-386/download)

---

