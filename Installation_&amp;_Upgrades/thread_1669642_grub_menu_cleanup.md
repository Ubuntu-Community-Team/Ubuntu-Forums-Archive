---
title: "grub menu cleanup?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-01-18
A PC I have just upgraded still shows a lot of grub menu entries, however, only the latest two are shown as 'installed' when looking with synaptic

sudo update-grub produces:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.24-28-generic
Found initrd image: /boot/initrd.img-2.6.24-28-generic
Found linux image: /boot/vmlinuz-2.6.24-27-generic
Found initrd image: /boot/initrd.img-2.6.24-27-generic
Found linux image: /boot/vmlinuz-2.6.24-26-generic
Found initrd image: /boot/initrd.img-2.6.24-26-generic
Found linux image: /boot/vmlinuz-2.6.24-25-generic
Found initrd image: /boot/initrd.img-2.6.24-25-generic
Found linux image: /boot/vmlinuz-2.6.24-24-generic
Found initrd image: /boot/initrd.img-2.6.24-24-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
done


How do I get rid of the obsolete ones, leaving the two latest relevant ones please?
Do I just find them and delete them.....?
tia

---

### Post by Quackers on 2011-01-18
In synaptic did you choose to "completely remove" all previous kernels? There should be 3 entries to delete for each kernel (only 2 if you choose to "completely remove" the first entry).
You could try entering 2.6.24 into the search box and see what comes up as being still installed, if any.

---

### Post by candtalan on 2011-01-18
> **Quackers said:**
> In synaptic did you choose to "completely remove" all previous kernels? There should be 3 entries to delete for each kernel (only 2 if you choose to "completely remove" the first entry).
You could try entering 2.6.24 into the search box and see what comes up as being still installed, if any.

I have not attempted to use synaptic to -remove- any items, I have only used it to examine what is apparently available via synaptic.
This is what I see  just following an install of ubuntu 10.04 and then updates.

I did the re-install, from ubuntu 8.04.4 to ubuntu 10.04 using a re-install, using the advanced manual install technique where the / partition is nominated but is NOT set to format. I think this allows user space stuff to remain during the new install. It seems to have worked well. But I had not expected a lot of old kernels things to still remain  :-)

However, because most of them do not seem to be showing up in synaptic, certainly not as being 'installed' does this mean that they are in the obsolete places and can now be manually tracked down and deleted? And then I can do  update-grub again?
tia

---

### Post by Quackers on 2011-01-18
ubuntu-tweak has a nifty tool to delete old kernels. It may be worth a try.

---

### Post by kansasnoob on 2011-01-18
You might want to check out the Grub Customizer:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I've tried it and I'm fairly impressed.

---

### Post by candtalan on 2011-01-18
Thanks for the replies. My initial confusion is reducing. Synaptic only shows the two kernels etc  installed with Ubuntu 10.04.
Update-grub seems to be using the location 
/usr/src
which also includes the obsolete stuff from 8.04.4.

This may possibly be a consequence of me re installing 'over' 8.04.4 using a 'not format' method for the partition '/'  (maybe?)

Is there anything against me simply deleting the obsolete stuff (linux-headers-2.6.24-28 and the like)
because it is not 'installed' as indicated by viewing synaptic?
tia

---

### Post by Rubi1200 on 2011-01-18
> **kansasnoob said:**
> You might want to check out the Grub Customizer:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I've tried it and I'm fairly impressed.
I just wanted to suggest that ;)

Yes, I had a first look at it too and it seems to be quite handy.

---

