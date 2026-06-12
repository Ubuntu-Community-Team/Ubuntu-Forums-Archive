---
title: "[SOLVED] NVIDIA driver will not install on HP laptop"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David D. on 2008-10-24
I have an HP laptop (dv6171cl).  The NVIDIA driver and Compiz both worked in Hardy and in Intrepid until a couple of kernel updates ago.  In Hardware Drivers the NVIDIA drivers are listed, and if selected go through the find and install process, but the message to restart never appears.  The next time I start/restart the laptop it displays the message "(EE)NVIDIA(0):Failed to load the NVIDIA kernel module  (EE)NVIDIA:***Aborting***
(EE)Screen(s) found, but none have a usable configuration"  Continuing the boot results in low graphics mode.  Selecting "default grapics" get the native resolution back.  Configuring Xserver manually has the same result.

Rebooting and selecting recovery for kernel 2.6.27 shows a DKMS failure for the NVIDIA drivers.

---

### Post by shane19174 on 2008-10-24
Are these legacy drivers? If so, search the forum here: they're not yet supported.

---

### Post by David D. on 2008-10-24
These are not legacy.  This is happening with 177 and 173. The bahavior is the same trying to activate either one.

---

### Post by David D. on 2008-10-24
> Alberto Milone communicated via email.  The following exchange solved my problem:

please type the following commands and show me the errors that each command gives:
> > sudo dkms add -m nvidia -v 177.80 -k $(uname -r)
> > sudo dkms build -m nvidia -v 177.80 -k $(uname -r)
> > sudo dkms install -m nvidia -v 177.80 -k $(uname -r)
> >
> >   
For sudo dkms add -m nvidia -v 177.80 -k $(uname -r) I get

Error! DKMS tree already contains: nvidia-177.80
You cannot add the same module/version combo more than once.


For  sudo dkms build -m nvidia -v 177.80 -k $(uname -r)

Error! Your kernel source for kernel 2.6.27-7-generic cannot be found at
/lib/modules/2.6.27-7-generic/build or /lib/modules/2.6.27-7-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.


For sudo dkms build -m nvidia -v 177.80 -k $(uname -r)

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (x86_64) first.

type:
sudo apt-get install linux-headers-generic

sudo apt-get install --reinstall nvidia-177-kernel-source

and your problem should be solved.

---

### Post by shane19174 on 2008-10-24
Nice to see you got it worked out. And thanks for making those private communications public, so others can benefit as well.

---

### Post by waynej4 on 2008-10-26
Thanks for posting! I had the exact same problem and this post sorted it out for me.

---

### Post by Gina on 2008-10-26
As I posted in another thread, I did a fresh install of RC yesterday evening and nvidia 177 (& 173) wouldn't download but after a lot of updates 177 installed fine and my nvidia graphics works fine.  Seems there was a bugfix in the updates.

---

