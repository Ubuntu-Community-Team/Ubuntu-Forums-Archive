---
title: "Partition question - advantages of boot / upgrade later"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by wbm on 2010-02-09
Hello, after playing around with Ubuntu now for a few month I think I have it figured out now enough to do a real and clean fresh install.
Originally I had everything just installed with the default one partition.

For this new and fresh install I want to create separate partitions for home etc.

Option 1: three partitions
/ (root)
/swap
/home

Option 2: four partitions
/ (root)
/boot
/swap
/home

Question 1: what is the advantage of having a "boot" partition?

Question 2: how do I later do upgrades?
E.g. the point of the separate partitions is to be able to do a clean reinstall while keeping the home directories as is.
What are the step by step instructions so I won't overwrite my home partitions later?
Thanks

---

### Post by raymondh on 2010-02-09
> **wbm said:**
> Hello, after playing around with Ubuntu now for a few month I think I have it figured out now enough to do a real and clean fresh install.
Originally I had everything just installed with the default one partition.

For this new and fresh install I want to create separate partitions for home etc.

Option 1: three partitions
/ (root)
/swap
/home

Option 2: four partitions
/ (root)
/boot
/swap
/home

Question 1: what is the advantage of having a "boot" partition?

Question 2: how do I later do upgrades?
E.g. the point of the separate partitions is to be able to do a clean reinstall while keeping the home directories as is.
What are the step by step instructions so I won't overwrite my home partitions later?
Thanks

Hi.

A /boot is an advantage if you are trying to avoid an error 18.  That is when your system (or BIOS) is of older vintage and cannot access an OS beyond either 8gb or 137gb. Usually happens when we put a larger HD :)  Sometimes, by just installing the kernel within the limit overcomes the error 18, hence no need for a /boot.  Sometimes, it's much better to have a dedicated GRUB partition which makes GRUB independent of any OS.

If you're system is quite new, say 2004 or newer, the BIOS may be 'strong' enough to seek a OS beyond 137gb.  If not, you can always try to flash it.

Other than that (and wanting to multi-boot various distros), I don't see any advantage of a /boot.

I like your idea of separating root (/) from /home.  That way, should you need to reinstall, you just re-install OVER the existing root (of course, mounting and formatting it).  As for keepiing your /home in case you do re-install, you just mount it but DO NOT FORMAT.  A quick guide in re-installing and keeping the existing /home:

-  Select manual in the install process (step 4)
-  Highlight the existing root (/) partition
* select mountpoint from the drop-down box (that'll be /)
* format ext3 or ext4
- Highlight the existing /home
* select the mountpoint (/home)
* DO NOT FORMAT
-  proceed with the install

To minimize permission errors when re-installing root (/) and using the existing /home, use the same username and password.

Upgrading is also the same.  You upgrade the root (mount and format) whilst retaining /home by mounting it but not formatting.

Raymond

Herman on GRUB.  Lots of good info here:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by wbm on 2010-02-12
Thank you raymondh for the reply. Sorry that it took a while to get back to you here.
That was very helpful and I'll try that. I also appreciate the info about the boot partition.
Maybe you know the answer to this too, would temp be part of the / (root) partition?
I would assume it is.
E.g. when burning DVDs, my current temp space keeps running out after 2 burns, as I gave root only 14 gb.

---

### Post by raymondh on 2010-02-12
> **wbm said:**
> Thank you raymondh for the reply. Sorry that it took a while to get back to you here.
That was very helpful and I'll try that. I also appreciate the info about the boot partition.
Maybe you know the answer to this too, would temp be part of the / (root) partition?
I would assume it is.
E.g. when burning DVDs, my current temp space keeps running out after 2 burns, as I gave root only 14 gb.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html)

---

### Post by wbm on 2010-02-12
> **raymondh said:**
> [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html)

Thanks, that's what I thought. I'll better allow for a hefty root partition then.

---

