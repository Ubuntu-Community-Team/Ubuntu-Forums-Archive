---
title: "Recompiled kernel installs, but dpkg chokes on the post-install script."
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AKMask on 2009-09-25
So I recompiled my kernel from source today, all went fine with the kernel (im using it right now, in fact) but for some reason on the linux-image package that was generated, the post install fails, chokes on:

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-fixed.postinst line 1186.
dpkg: error processing linux-image-2.6.31-fixed (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31-fixed
E: Sub-process /usr/bin/dpkg returned an error code (1)


and now, apt wont install or upgrade anything, whenever i call it it retries to install this kernel, and chokes every time. running dpkg --configure -a doesnt do anything but make it fail again, trying with the force option plays out the above again. Line 1186 of mentioned script is:

  system ("run-parts --verbose --exit-on-error --arg=$version " .

within the context of:

if (-d "/etc/kernel/postinst.d") {
  print STDERR "Examining /etc/kernel/postinst.d.\n";
  system ("run-parts --verbose --exit-on-error --arg=$version " .
          "--arg=$realimageloc$kimage-$version " .
          "/etc/kernel/postinst.d") &&
            die "Failed to process /etc/kernel/postinst.d";
}

Any help?

---

### Post by ultima on 2009-10-03
Hello

I Just stumbled across this thread looking for the same answer.

I found the answer here [https://bugs.launchpad.net/dkms/+bug/292606](https://bugs.launchpad.net/dkms/+bug/292606)

Just reinstall nvidia-common and then purge it

sudo apt-get install nvidia-common
sudo apt-get purge nvidia-common

Then the kernel install completes.

---

### Post by cenwesi on 2009-10-29
yep, this worked for me and it makes sense i have ATI video card and not nvidia on this pc. Btw, this is not karmic specific because it also existed on Jaunty.

---

