---
title: "Patching Ubuntu Kernel to 2.6.35.4"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by silverwolf5 on 2010-08-29
Hi, I'm new to Ubuntu and Linux, I've installed recently the latest version of Ubuntu (64 bits) on my notebook (Acer Aspire 5535), which has an AMD Athlon X2 QL-62, ATI Mobility Radeon HD 3200 and 4GB of RAM.
The system runs pretty well, but I experience some hangups from time to time, resuming from hibernation won't show any image which forces me to shutdown the computer, and some ubuntu applications lock up, like the Administration > System Test (if I decide not to give admin priveleges).

I believe this is something to do with the kernel (using the 2.6.32-24-generic actually), I intend to patch it to the newest stable release in [www.kernel.org]("http://www.kernel.org") which is 2.6.35.4. After I download it I used the command: "patch -E -p1 <patch 2.6.35.4" I do get lots of *.rej files, I believe to be some error files. I also tried the same command with "sudo".

I restart the system and nothing happens, I end up with the same kernel.
Is there an easy way to do this step-by-step for noobs and keeping all drivers/programs/and graphical appeareance?

Thank you.

---

### Post by davidmohammed on 2010-08-29
pre packaged ubuntu specific kernels can be found [here]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") - you'll find the latest maverick kernel ready for you to install be just downloading and installing 3 deb files.

---

### Post by silverwolf5 on 2010-08-30
I've found the packages, but do I need to to install only the "image" or do I need the "header" also? For "amd64". (what the header is supposed to do anyway?)
I intend to keep everything as before, themes, drivers and such.

By the way, if it works ok, how do I remove the old kernel?

Thanks for the help.

---

### Post by dino99 on 2010-08-30
to remove old kernels:

into synaptic, you select it for deletion, that it (image+header)

to install from kernel mainline:

in that order:
- header-all
- header
- image

of course, select the same kind of packages (i386 for 32 bits, amd64 for 64 system)

---

### Post by silverwolf5 on 2010-08-30
Thanks for the help guys, worked just fine.
Hopefully won't freeze anymore.
Thumbs up for you two. \\:D/

---

