---
title: "fglrx patch arch_fglrx_2.6.34.patch fails"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by laidbackwebsage on 2010-05-29
Not sure what's going on, but I can't get "fglrx" to update/patch via synaptic or apt (commandline). "fglrx-amdcccle" fails, also because it depends on "fglrx".

I've attached a file of the errors from apt.

help...  please...  :(

---

### Post by ba0bab on 2010-05-30
I have the same problem. I found this on launchpad:

> Binary package hint: fglrx

After upgrading to latest version 2:8.732-0ubuntu0sarvatt2~lucid dkms fails with error 6. The consequence is that building the fglrx module fails. When compiz is enable logging in fails. The reason for this problem is a bug in the file arch_fglrx_2.6.34.patch.
The first 2 lines contain a patch which doesn't exist.

After I've changes these lines to:

--- a/kcl_wait.c	2010-04-13 20:02:46.494496561 +0200
+++ b/kcl_wait.c	2010-04-13 19:52:00.054563389 +0200

The bug is fixed.

from [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/587427]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/587427")

However, I don't understand the instruction to fix the problem. Anybody who can clarify the fix?


```
sudo dpkg --configure -a
[sudo] password for emil: 
Setting up fglrx (2:8.732-0ubuntu0sarvatt2~lucid) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.732 DKMS files...

------------------------------
Deleting module version: 8.732
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.732 DKMS files...
Building only for 2.6.32-22-generic
Building for architecture i686
Building initial module for 2.6.32-22-generic

Error! Application of patch arch_fglrx_2.6.34.patch failed.
Check /var/lib/dkms/fglrx/8.732/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_DK.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle

```

---

### Post by laidbackwebsage on 2010-05-30
Your reply helped me fix this, and the fix is (relatively) easy.

This assumes that the aborted attempt to install "fglrx" and "fglrx-amdcccle" via apt-get is still extant on your computer. If you rolled it back or got rid of it somehow, go ahead and re-run it so all the files will be present on your machine.

Now, open a terminal and do the following:
[LIST=1]
[*]> sudo updatedb
[*]> locate arch_fglrx_2.6.34.patch
[*]Foreach listed version of the file, do > sudo gedit <file>
[*]Replace the first 2 lines of each file with:
  >  --- a/kcl_wait.c 2010-04-13 20:02:46.494496561 +0200
+++ b/kcl_wait.c 2010-04-13 19:52:00.054563389 +0200
   and save the file. Remember to do this for ALL the files. (On my machine there were 2.)
[*]Now do the following: > sudo apt-get --no-download install fglrx fglrx-amdcccle
[*]Reboot
[/LIST]

Voila! Fixed!

Thanks for the link to the bug report...

---

### Post by MidasTouchBR on 2010-05-30
Thank you, guys, for posting the problem and the solution. I've googled it and here is the only place that I've found that mentions it. For me, worked like charm!

---

### Post by ba0bab on 2010-05-30
You're welcome, and thanks for clarifying the fix :)

---

### Post by scottiw2000 on 2010-05-31
I want to add my thanks for the fix. I *never* would have come up with that on my own, and it worked beautifully. Thanks!

---

### Post by Segitz on 2010-06-01
Yup, thank you too...

I traced the bug to the patch, but I am not much into this kind of stuff, so I wasn't able to fix it... thanks for doing so!

---

### Post by leocor on 2010-06-01
Fantastic!! Thank you!!

leocor

---

### Post by JoZ3 on 2010-06-02
Tnx so much.:P

---

### Post by slayerboy on 2010-06-03
Thank you for this fix!  I can't see how they didn't find this before releasing the update. :P

---

### Post by thethimble on 2010-06-03
Thank you SO much! You really saved me from a big headache.

---

### Post by sanoelk on 2010-06-05
Thanks! This worked for me. :)

---

