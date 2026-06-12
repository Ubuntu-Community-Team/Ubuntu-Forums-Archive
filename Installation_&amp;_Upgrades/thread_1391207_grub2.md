---
title: "grub2"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by camstar on 2010-01-26
I have installed Ubuntu Karmic and made a few changes to the Grub2 so that when it starts it shows the following:

Ubuntu Karmic
Windows Systems

That is all.
After letting the updates run and install (I asked to keep the same Grub) it now shows me a double entry of Ubuntu Karmic,  the rest is fine. I can choose either one and it will boot.
How can I get rid of one entry.
Thanks for the help.
SP

---

### Post by unmole on 2010-01-26
This should help you out
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by darkod on 2010-01-26
Are you sure it's double entry? I guess you have something like:

Ubuntu 2.6.31-14
Ubuntu 2.6.31-17

It's easy to think it's the same kernel. :)

---

### Post by camstar on 2010-01-27
you are correct darkod. Is there a way to get id of the first one?

---

### Post by darkod on 2010-01-27
There is but it is highly recommended to keep at least one older kernel that's working for you. That way if the latest kernel is corrupted or something, you can always select to boot the older one and it will work.
I can't really explain it in linux, I'm also new. The kernel is sort of the core files, and you can boot older kernel but still all your programs are there, it's not like another OS. Very different compared to windows for example. If windows gets corrupted, that's it.
This is why keeping two kernels is recommended.
But if you really want to remove it, open Synaptic Package manager (System-Administration), in the search box type linux-image-2.6.31-14 (or whatever you want removed), and mark that package for Complete Removal.
MAKE SURE you don't remove all kernels, there will be nothing to boot.
After removal, if you are using the new grub2 coming with 9.10, in terminal run:
sudo update-grub

and it will remove the kernel from the menu because it can no longer find it on the disk.

---

### Post by James2k on 2010-01-27
Keeping an older kernel to boot into could be a life saver if one of them fails. I'd keep two kernels on your grub for a back up.

---

