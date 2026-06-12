---
title: "Can't update nVidia driver. Can't run directly and Sudo doesn't recognize"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2022-02-14
I'm trying to update my nVidia driver to the latest proprietary release.

I successfully uninstalled the old/default driver (now using the "Nouveau" Open source driver), downloaded the latest official driver from the nVidia website, and set the permission to "Run as program".

But when I try to run it directly from the desktop, it says it "must be run as root". So I try to use "**sudo**" and run it from the command line: **cd Downloads** then **sudo apt install NVIDIA-Linux-x86_64-510.47.03.run**), which results in:

**[COLOR="#FF0000"]E:[/COLOR] Unable to locate package NVIDIA-Linux-x86_64-510.47.03.run**

I copy/pasted the filename so I know it's correct. I have no idea what to try next. Any advice appreciated.

---

### Post by ubfan1 on 2022-02-14
The Nvidia driver 510.47.03 is in the standard repos, so no need to download from Nvidia.  From the Software & Update/Additional Drivers tab, select the 510 and apply.  Then, when the kernel updates, the Nvidia driver module gets remade for the new kernel automatically.  Just to answer your question: 1)ensure the .run file has the execute permission (chmod +x @.run)  then 2) sudo ./*.run   But really, that way you will be frequently having video problems with every kernel update.

---

### Post by Mugsy323 on 2022-02-14
> **ubfan1 said:**
> The Nvidia driver 510.47.03 is in the standard repos, so no need to download from Nvidia.

Thx for the reply.

Apparently, I needed to reboot after uninstalling the old driver before trying to install the new one. It worked this time. :P

---

### Post by ubfan1 on 2022-02-14
You may mark this as "Solved" from the Thread Tools popdown near the top of the thread.

---

