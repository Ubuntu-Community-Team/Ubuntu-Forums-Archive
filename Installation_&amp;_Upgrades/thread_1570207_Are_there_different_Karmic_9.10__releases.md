---
title: "Are there different Karmic 9.10  releases"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2010-09-07
and if so how do I install a specific one? Or better yet, revert back to an earlier release.

I have two systems running.
2.6.31-22-generic #**60**-Ubuntu **aphrodite** release 
2.6.31-22-generic #**63**-Ubuntu **amaterasu** release

I googled the #60 and #63 and it listed release names highlighted above, is this correct?

If it is, how can I install the aphrodite release?

I have one system working great (#60), while the other exhibits problems playing back 1080p video files (#63).  The only HW difference that could affect the dropping frames is the 8200/8300 Nvidia chipsets (with the 8200 working perfectly) and then of course the Karmic releases.
I have re-installed the system and files twice and even upgraded new releases of Nvidia drivers (195 > 256) with no success.

My next step is to try and install the same exact release of Karmic if indeed there is a difference between #60 and #63.  But how, Any suggestions?

My next step might be to use clonezilla and clone the OS (Root) and try that. But then the chipsets for sound are different as well as the ehternet chipset. But that shouldn't impair the video

Thank you

---

### Post by gzarkadas on 2010-09-08
These names you put in bold are host names (ie the names given to the computers by the user upon installation), not ubuntu releases. They are output by `uname -a'. The numbers with the (#) sign are kernel builds, as numbered by Ubuntu. #60 is for example for 2.6.31-22.

Since you seem to have trouble with the #63 build of the kernel, try to boot by an older one (that is on the grub menu during boot scroll down the list and choose another kernel, say 2.6.31-22) and see if your problem disappears. If yes, you can make that kernel the default.

---

### Post by speed32219 on 2010-09-14
Thank you for the clarification.  Problem I have is since it was a newer isntall there is no option to select a different version or earlier build. This is a server build without a GDM.

Can I do it using aptitude from the CLI?

If so, an example of the command line with the #60 build would be greatly appreciated.

---

### Post by gzarkadas on 2010-09-14
You can use aptitude to select and install a specific kernel version package, since they are at the repositories. 

Before doing so though, execute this command from the terminal:
```

ls /boot/vmlinuz*

```to see what kernels exist in your system; they do not get deleted during  updates, so if no manual deletion of previous kernels has been  performed in the past there should appear more than one entries. Then it  will be easy to modify the grub startup files, to make them appear.  Along with the existing kernels list post also whether you use Grub or  Grub2.

Now, if you use aptitude, you should select the 'linux-image-2.6.31-21' and 'linux-headers-2.6.31-21' packages, because looking at the Ubuntu pool the next ones are (from the .deb filenames) the 2.6.31-22_.63_ series which most probably (since the extra, 5th argument must be the ubuntu kernel build id) are giving you the reported error.

If -and *only* if- aptitude chokes because you want to install a version older than the currently installed (I don't know whether it will happen, but I mention it in any case), you can download the debs from the Ubuntu pool and install them manually with dpkg. This is a bit more involved than it sounds; you will need to also post what type is your cpu (32 / 64 bit) and whether you have more than 4GB Ram, in order to make the correct selections.

---

