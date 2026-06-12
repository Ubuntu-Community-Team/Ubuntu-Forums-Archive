---
title: "how to purge kernel - not in dpkg -l , not in synaptic, no by apt-get remove"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by masuch on 2013-02-06
Hi,

I have noticed on virtualbox that in /boot directory are left some files - old kernel:
initrd.img-2.6.38-11-generic (and config , abi , vmlinuz , ... )

I cannot remove / uninstall them using dpkg , synaptic , apt-get purge/remove  linux-image-2.6.38-11-generic ... because they simply not showed by those commands ,even after update, It could not locate those packages. How can I remove that kernel 2.6.38-11 ? Do I need to download them separatelly or is there some another solution ? ( I do not want to delete them because update-initramfs could later complain about module trying to assemble them in the next future - which already happened to me.)

thank you,
kind regards,
M.

---

### Post by darkod on 2013-02-06
Hmm, I don't have much experience with this, but it sounds like the files are just some left overs. Otherwise the apt-get remove should do the trick.

In the past there might have been complaints after deleting kernel files directly, but in this case if these files are only left overs it looks OK to delete them with rm.

You can try update-initramfs -u after that, and it should update the initramfs without those files I guess.

Otherwise, since there doesn't seem to be a way to uninstall them, I guess they will always stay there if you don't use rm to remove them.

---

### Post by masuch on 2013-02-07
Ok, 
I removed them manually and run update-initramfs -u -k all - seems ok for now.

---

