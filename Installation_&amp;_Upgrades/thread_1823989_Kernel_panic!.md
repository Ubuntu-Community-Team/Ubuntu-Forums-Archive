---
title: "Kernel panic!"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by taylor179 on 2011-08-13
hey, i just installed Ubuntu 11.04 on my computer after alot of hassle with 'burn the disc slower' stuff. now when i try to boot into it i get a kernel panic, something along the lines of 'kernel-panic: unable to mount: VFS unknown...' i can't remember what comes after unknown. and i've allready done a chkdsk with no bad results. i've been having problems with this alot, different distros just not liking my computer. 
Any help is Greatly appreciated!
Thanks,
Taylor

---

### Post by manzdagratiano on 2011-08-13
I would suggest booting the computer with the LiveCD and then pasting here the contents of
```

$ sudo fdisk -l /dev/sda

```When asked for the password, just hit enter.

Then, mount your /dev/sda as:
```

$ sudo mount /dev/sda /mnt

```
paste here the contents of the file /mnt/etc/fstab. It is possible that this is entirely the issue between wrong drive numberings (for instance, I have had this issue with the gentoo installer labeling my drives as hda's instead of sda's).

Also, the best possible method of install, in my honest opinion (or IMHO if you will), is the booting from USB drive method - no need to burn a CD, and if things go wrong, the USB drive can be re-prepared in a matter of minutes.

---

### Post by taylor179 on 2011-08-13
I reinstalled it and i'm sure its the right partition. now after choosing ubuntu 11.04 in grub it stops almost immediately after at 'Booting Ubuntu 11.04 (sda5)' :/

EDIT:
I can get into my ubuntu recovery boot sooo... if that can help at all :/

---

### Post by manzdagratiano on 2011-08-13
Can you try booting from your install CD and running the above commands? I modified a little what I was asking for (seems like I had posted in a hurry!)

---

