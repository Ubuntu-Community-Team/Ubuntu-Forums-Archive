---
title: "&quot;Installed&quot; kernels not available"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bill_p on 2010-04-17
When the updates for Lucid include kernel updates, how do I make these available to use? If I recall under 9.10, when there was kernel update, it would be automatically available when I booted. I did an upgrade from 9.10 to 10.04 Beta 1 which installed kernel 2.6.32-16. 

In the course of continuing to update my system, there have been several kernel updates, up to 2.6.32.21.  Synaptic shows .16 through .21 installed, but I do not see these as options, even after running update-grub.  I only see 16 in the boot directory. How can I fix this and is it possible to have kernel updates be usable automagically after they are installed? 

Thanks.

---

### Post by Owen.C93 on 2010-04-17
> **bill_p said:**
> When the updates for Lucid include kernel updates, how do I make these available to use? If I recall under 9.10, when there was kernel update, it would be automatically available when I booted. I did an upgrade from 9.10 to 10.04 Beta 1 which installed kernel 2.6.32-16. 

In the course of continuing to update my system, there have been several kernel updates, up to 2.6.32.21.  Synaptic shows .16 through .21 installed, but I do not see these as options, even after running update-grub.  I only see 16 in the boot directory. How can I fix this and is it possible to have kernel updates be usable automagically after they are installed? 

Thanks.
Are they in /boot ? There should be lots of files relating to lots of kernel versions.

I don't know if this helps but try```
update-initramfs -u
```

---

### Post by clhsharky on 2010-04-17
HI

```
uname -r
```

Will tell you the kernel your on.

Sharky

---

### Post by rbmorse on 2010-04-17
Restart the machine. As it reboots, as soon as the POST is complete and the O/S starts loading, press and hold the left shift key. This should bring up the GRUB boot menu. On my machine, it lists all of the installed kernels (.16 - .21)

---

### Post by bill_p on 2010-04-17
Thanks for the quick replies.  Some answers:

/boot only has files for .16, so update-initramfs -u did nothing but work on the .16 kernel files present.

```
me@mycomputer:~$sudo update-initramfs
update-initramfs: Generating /boot/initrd.img-2.6.32-16-generic

```Also:
```
me@mycomputer:~$ uname -r
2.6.32-16-generic

```grub menu only shows the .16 kernel (plus other typical items on a dual boot machine), but no other linux kernels.

That's the thing, I'm booting into .16. Synaptic shows other kernels installed, but nothing other than .16 is in /boot.  It is like they are not installed. I've not seen kernels marked in Synaptic as "installed", but not available to use - they always have shown up in /boot and on the grub menu.

I guess I can simply compile the latest kernel from source, or install the deb files. I am just curious as to why they may not be installing correctly (other than "this is beta" <g>).

---

### Post by Owen.C93 on 2010-04-17
Thats very odd.

Make sure headers and image are installed in synaptic. Preferably through update manager though. Are you getting any errors in the update process?

---

### Post by garvinrick4 on 2010-04-17
Update your grub just incase that is all it needs. Never know.

sudo update-grub

---

### Post by drs305 on 2010-04-17
Try uninstalling one of the newer kernels and then reinstalling it from the command line. Watch to see if update-grub finds the new kernel as the -20 kernel is (re)installed.

```

uname -r # Check to make sure you aren't using the -20 kernel
sudo apt-get purge linux-image-2.6.32-20-generic
sudo apt-get install linux-image-2.6.32-20-generic

```

---

### Post by bill_p on 2010-04-17
Ok--getting closer, but still confused...and apologies for the long post, but I am curious...

I followed what drs305 suggested (thank you for the tip), after reconfirming that .16 was the booted kernel version. I tried the .21 kernel, which Synaptic Package Manager showed as installed:

```
me@mycomputer:~$ sudo apt-get purge linux-image-2.6.32-21-generic
<snip>
Package linux-image-2.6.32-21-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Hmm....

Then:

```
me@mycomputer:~$ sudo apt-get install linux-image-2.6.32-21-generic
<snip>
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-21-generic 
<snip>
```And magic, it installed, updated grub and the .21 kernel is available. I am booted with that kernel now and of course it is in /boot, etc, etc.

Yay, but , what the heck happened?

Synaptic package manager showed all the kernels from .16-.21 installed. Meaning that for each kernel it had the following listed as installed (check box to left of package name showed solid):
- linux-headers-2.6.32.XX
- linux-headers-2.6.32.XX-generic
Each of these had an installed version listed and as far as I know looked to be installed, but except for .16 were not.

The only difference is that now for .21 only (not even .16) there is also the little Ubuntu logo to the left of the package names (does this mean anything for this issue?).

Why did these not install when update-manager "installed" them and why would synaptic package manager show them as installed?

Not sure I can mark this as resolved, even though I fixed the symptom. 

Again thanks for the quick and helpful answers.

---

### Post by seeker5528 on 2010-04-19
> **bill_p said:**
> 
Synaptic package manager showed all the kernels from .16-.21 installed. Meaning that for each kernel it had the following listed as installed (check box to left of package name showed solid):
- linux-headers-2.6.32.XX
- linux-headers-2.6.32.XX-generic
Each of these had an installed version listed and as far as I know looked to be installed, but except for .16 were not.

The linux-headers packages are not the kernel, they are just stuff you need in order to compile modules.

The packages that contain the kernel are linux-image-XXXXX, with linux-generic and linux-image being metapackages that will pull in the default kernel automatically.

So installing linux-generic or linux-image will install the default kernel and make sure it stays up to date with the default.

Similarly if you wanted the rt kernel or the server kernel you would install linux-image-rt or linux-image-server to make sure you are kept up to date with the default versions of them.

Later, Seeker

---

