---
title: "Dual Boot Linux: Hibernate and Swap space"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by stlu on 2012-06-26
I understand that in a dual boot situation, setting one of the OS to hibernate will leave a resume image that could get ugly is the other OS is booted while the hibernate image remains.

So, is it a sound measure to provide two swap partitions, or does the kernel scan all swap rather then referring to /etc/mtab when looking for a resume image?  Or do I need to adopt a policy of never letting either OS hibernate?

Thanks

---

### Post by stlu on 2012-07-20
Ok, well I guess I will just never let them hibernate, since nobody has an answer.

---

### Post by oldfred on 2012-07-21
Ubuntu boots fast enough that I do not find much advantage to hibernation.

Any auto installs will find all swaps, but if you edit fstab you can remove any or all swaps if you want.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

But even if swap is not written into, any writes into the other install will corrupt hibernation and cause major issues. Best to then set any mount to read only. Even a separate shared partition if data is in hibernation may cause issues. I prefer to share data like my Firefox & Thunderbird profiles in every install including XP and multiple Ubuntu's. I cannot hibernate if I want the advantage of sharing data.

I do not do it (yet), but many suggest virtual installs as a way to have both systems running. Then there is not rebooting. You do need a bit more RAM to maintain system functionality.
[https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)

---

