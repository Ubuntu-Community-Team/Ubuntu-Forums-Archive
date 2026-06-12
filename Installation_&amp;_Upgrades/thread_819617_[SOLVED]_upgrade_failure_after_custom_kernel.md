---
title: "[SOLVED] upgrade failure after custom kernel"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Adahn on 2008-06-05
Earlier I was experimenting with kernelcheck to compile a new kernels, but never put the new kernels in grub's boot list and kept using 8.04's default kernel.

Later on, to save space, I deleted the usr/src and lib/modules folders relevant to those kernels.  Things were working fine through several updates.

Recently, update gives me the option to do a partial update, but fails.  Synaptic will also fail on opening.  
Both instruct me to dkpg --reconfigure -a
which gives me this message:


Setting up initramfs-tools (0.85eubuntu39) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25.2
Cannot find /lib/modules/2.6.25.2
update-initramfs: failed for /boot/initrd.img-2.6.25.2
dpkg: subprocess post-installation script returned error exit status 1




It's looking for one of the folders I deleted.
Suggestions?

---

### Post by Adahn on 2008-06-07
bump?

---

### Post by ChameleonDave on 2008-06-07
So, in other words you manually removed files and folders installed by a package on your system?

That's a very bad idea.  You should have removed those by removing the package in the package manager.

---

### Post by Adahn on 2008-06-07
Yes.  Mea culpa, mea culpa, mea maxima culpa.
FWIW, these were packages that synaptic's search string did not find.

---

### Post by ChameleonDave on 2008-06-07
Perhaps you need to play with properly removing all traces of those kernels.

Try:
```

man update-initramfs
```

---

### Post by Adahn on 2008-06-07
thanks.
I tried both the -d and -u for -k 2.6.25.2
and get this:

Cannot find /lib/modules/2.6.25.2

---

### Post by ChameleonDave on 2008-06-07
> **Adahn said:**
> thanks.
I tried both the -d and -u for -k 2.6.25.2
and get this:

Cannot find /lib/modules/2.6.25.2

Where did you get 2.6.25.* from anyway?  It's not in the repos.

Try reinstalling it, and then properly removing it.

---

### Post by Adahn on 2008-06-07
> **ChameleonDave said:**
> Where did you get 2.6.25.* from anyway?  It's not in the repos.

Try reinstalling it, and then properly removing it.

It was compiled through kernelcheck, which won't work either.
reinstall how?

---

### Post by ChameleonDave on 2008-06-07
> **Adahn said:**
> It was compiled through kernelcheck, which won't work either.
reinstall how?

Well, I've never used that, but I imagine that it has a method for compiling and installing a version of the kernel, and a method for fully removing it.

Someone else will have to help you with this one.

---

### Post by Adahn on 2008-06-07
Thanks for the help so far.
Searching the entire filesystem found only one hit for 2.6.25.2, as a text file by that name in /var/lib/initramfs-tools
Files for the generic modules going back to 2.6.20 are in that folder as well.

Perhaps I should risk deleting that file.

---

### Post by Adahn on 2008-06-07
deleting that file allowed me to run dpkg --configure -a properly

update is working now.
Thank you for pointing me in the right direction.

---

### Post by ChameleonDave on 2008-06-07
> **Adahn said:**
> 

Perhaps I should risk deleting that file.

Glad that it worked!

However, you're going about things in a risky way.

Instead of deleting things, move them.

For example, instead of this:

```
sudo rm /var/lib/initramfs-tools/2.6.25.2
```

... do this:

```
sudo mv /var/lib/initramfs-tools/2.6.25.2 ~
```

That way, if it screws something up, you can put it back where it was with this:

```
sudo mv ~/2.6.25.2 /var/lib/initramfs-tools
```

Even if it makes the system unbootable, you can still move the file back after booting from the live CD.

---

### Post by Adahn on 2008-06-07
I'll do that in the future.

---

