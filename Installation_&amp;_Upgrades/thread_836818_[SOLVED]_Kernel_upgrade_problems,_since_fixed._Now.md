---
title: "[SOLVED] Kernel upgrade problems, since fixed. Now 2 kernels at GRUB"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by KenBW2 on 2008-06-21
The other day I was told I had updates available. Incidentally they were kernel upgrades. The trouble is that I ran out of disk space mid-upgrade and it caused a few problems.
I've since fixed them but am left with both the old and new kernels in the GRUB menu. The new kernel (2.something-15) breaks my wifi drivers. Basically I'm bothered that having 2 kernels is taking up the precious little disk space I have.
Is there a way to get rid of one, preferably the -15 one?

It's the eeepc in my signature.

---

### Post by eric_stewart on 2008-06-21
> **KenBW2 said:**
> The other day I was told I had updates available. Incidentally they were kernel upgrades. The trouble is that I ran out of disk space mid-upgrade and it caused a few problems.
I've since fixed them but am left with both the old and new kernels in the GRUB menu. The new kernel (2.something-15) breaks my wifi drivers. Basically I'm bothered that having 2 kernels is taking up the precious little disk space I have.
Is there a way to get rid of one, preferably the -15 one?

It's the eeepc in my signature.

I have a post on this in this forum.  I found that the new kernel broke my machine's ability to boot.  Some upgrade!

[http://ubuntuforums.org/showthread.php?t=836825](http://ubuntuforums.org/showthread.php?t=836825)

/Eric

---

### Post by damphoud on 2008-06-22
You can install QGRUBEditor.

---

### Post by KenBW2 on 2008-06-22
@damphoud

I know how to edit the GRUB, but I want the kernel removing since it obviously is taking up space I don't have

@eric_stewart

Thanks, I'll give that a try

---

### Post by Pumalite on 2008-06-22
Boot with the kernel you are going to keep, and remove the other through Synaptic.

---

### Post by KenBW2 on 2008-06-22
So just to make sure - the packages I'm removing are:
linux-headers-2.6.22-15
linux-headers-2.6.22-15-generic
linux-image-2.6.22-15-generic
linux-ubuntu-modules-2.6.22-15-generic

Any I've missed out?

---

### Post by Pumalite on 2008-06-22
Looks right. (it always good to have at least 2 kernels, in case one fails)

---

### Post by KenBW2 on 2008-06-22
I did it by way of aptitude to make it easier. It tells me:
> 
$ sudo aptitude purge linux-headers-2.6.22-15 linux-headers-2.6.22-15-generic linux-image-2.6.22-15-generic linux-ubuntu-modules-2.6.22-15-generic
[...]
The following packages are BROKEN:
  linux-headers-generic linux-image-generic 
The following packages will be REMOVED:
  linux-headers-2.6.22-15{p} linux-headers-2.6.22-15-generic{p} 
  linux-image-2.6.22-15-generic{p} 
  linux-ubuntu-modules-2.6.22-15-generic{p} 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 139MB will be freed.
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.22-15-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.22-15-generic but it is not installable
                       Depends: linux-ubuntu-modules-2.6.22-15-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-headers-generic
linux-image-generic

Score is 188

Accept this solution? [Y/n/q/?] 


Looks scary. Should I accept?

---

### Post by Pumalite on 2008-06-22
What kernel are you booting and which one is your backup?

---

### Post by KenBW2 on 2008-06-22
I'm booting -14
I'm getting rid of -15
I'm not keeping a backup - too little free space

I was just worried about the dependencies being unresolved and it screwing things up. Would I have any problem with the above solution?

---

### Post by Pumalite on 2008-06-22
No; if you really want to keep just .14

---

### Post by KenBW2 on 2008-06-22
Sorry to keep bugging...
I just want to be sure I'm not about to screw things up again. I'm ok to accept the aformentioned solution am I?

---

### Post by Pumalite on 2008-06-22
Yes.

---

### Post by KenBW2 on 2008-06-22
@Pumalite
Thanks for your help, all is well again. And I have 137MB Free Space! :P

@damphoud
Thanks, I've been thinking about getting an app for that for a while

---

### Post by Pumalite on 2008-06-22
Good luck!

---

