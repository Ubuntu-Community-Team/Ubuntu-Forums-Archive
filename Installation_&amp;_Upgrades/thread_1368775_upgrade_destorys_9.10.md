---
title: "upgrade destorys 9.10"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by clive49 on 2009-12-31
Hello I've been using 9.10 amd 64 and then decided to check for upgrades. I download the upgrades and bang all I endup with is fsck trying to do a clean of the drive and the cursor just flashing. How long should fsck sit with just the cursor flashing?

Many thanks in advance

---

### Post by dstew on 2009-12-31
Can you boot an earlier kernel?

---

### Post by clive49 on 2009-12-31
Thanks for your help.
I'm new to Ubuntu so I doubt I'd know how to.
What I have done is use the install disc to save any data I had, and then done a clean install.
This install is on a 60 gig disc using the whole disc.
Then I started the update process and only updated a few at a time. There were 166 updates. I'm now left with 9. They are: 'Grub-common' , 'grub-pc' , 'linux-generic',  'linux-headers-2.6.31-16(new install)' , 'linux-headers-2.6.31-16-generic(new install)' , 'linux-header-generic' , 'linux-image-2.6.31-16-generic(new install)' , 'linux-image-generic' , 'linux-libc-dev'.

Any Ideas which ones to untick?

Many Thanks

---

### Post by presence1960 on 2010-01-01
> **clive49 said:**
> Thanks for your help.
I'm new to Ubuntu so I doubt I'd know how to.
What I have done is use the install disc to save any data I had, and then done a clean install.
This install is on a 60 gig disc using the whole disc.
Then I started the update process and only updated a few at a time. There were 166 updates. I'm now left with 9. They are: 'Grub-common' , 'grub-pc' , 'linux-generic',  'linux-headers-2.6.31-16(new install)' , 'linux-headers-2.6.31-16-generic(new install)' , 'linux-header-generic' , 'linux-image-2.6.31-16-generic(new install)' , 'linux-image-generic' , 'linux-libc-dev'.

Any Ideas which ones to untick?

Many Thanks

do you have more than one hard disk? if so open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```

on the last window choose the disk that has GRUB installed on it's MBR. This will insure that GRUB2 (grub-pc) gets installed to the correct disk.

---

