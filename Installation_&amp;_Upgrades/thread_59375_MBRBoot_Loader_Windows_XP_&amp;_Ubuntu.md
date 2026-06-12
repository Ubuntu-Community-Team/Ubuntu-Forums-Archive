---
title: "MBR/Boot Loader Windows XP &amp; Ubuntu"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by Bateman on 2005-08-23
Hi,

I'm running a dual boot on my laptop with Windows XP & Ubuntu.
Was just wondering if someone could tell me if I would be able to fix the boot loader in the MBR if I replace my Windows XP installation with an image made with Acronis True Image. I used to have XP and Suse and if I replaced the XP installation with an image, the boot loader would be broken. I was always able to fix it with the Suse cd though. Would I be able to do this with an Ubuntu cd?

Thanks!!

---

### Post by glug101 on 2005-08-23
[QUOTE=Bateman]Hi,

I'm running a dual boot on my laptop with Windows XP & Ubuntu.
Was just wondering if someone could tell me if I would be able to fix the boot loader in the MBR if I replace my Windows XP installation with an image made with Acronis True Image. I used to have XP and Suse and if I replaced the XP installation with an image, the boot loader would be broken. I was always able to fix it with the Suse cd though. Would I be able to do this with an Ubuntu cd?

Thanks!![/QUOTE]
 You should be able to fix this using the Ubuntu livecd.  I make no claims about the Ubuntu install cd but that might work too.  Really, any livecd should work.  Mount the partition, then run chroot and then run the grub boot loader.  For a much better explaination of how to do this (using the gentoo livecd which is excellent for this) check out the gentoo install manual.  (I'm a recent convert from Gentoo ;) )

Here are some links to the relevant chroot instructions (just skip over the mirror select part):

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=6#doc_chap1)

---

### Post by DemiUrge8 on 2005-08-24
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

That thread might help you out too.

---

### Post by glug101 on 2005-08-24
[QUOTE=DemiUrge8][http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

That thread might help you out too.[/QUOTE]
 Much nicer, I'll remember this one....

---

