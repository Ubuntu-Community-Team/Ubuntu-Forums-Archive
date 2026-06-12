---
title: "How does Ubuntu manage kernel installation?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by mbobak on 2007-05-15
Specifically, where does Ubuntu store defaults about the root device, etc?

Here's my problem:
On initial installation of Ubuntu, I ended up making my root device hd(1,0), which is an error, it should be hd(0,0).  So, when I booted, it errored out, I was able to use the grub editor features to make the necessary change, and boot was successful.  Once I was logged in, I edited /boot/grub/menu.lst and modified it to read 'hd(0,0)', and that was fine, the next time I booted no problem.

So, here's the problem:
Every time the kernel gets updated, synaptic installs it into menu.lst automagically, but it STILL USES hd(1,0)!
So, every time a new kernel is installed, I have to follow behind it and fix this problem.  Is there a config file squirreled away somewhere that has 'hd(1,0)' in it?  Can I modiify this without having to reinstall my entire system??  Help!

Thanks,

-Mark

---

### Post by mbobak on 2007-05-18
Still looking for a clue here.....anyone?

---

### Post by mpvano on 2007-05-18
Read the ENTIRE menu file for grub. You'll find that it uses a set of template command lines in the comments to specify what the "update-grub" program should do to create new automatically generated kernel entries.

Modify the template line that applies to your kernels and they will automatically end up with the correct command line generated the next time the kernel is updated.

The comments are quite clear, but make sure you read them all, because there are several different templates that can apply under different circumstances....

As you've already found, changing the kernel arguments and the fstab is usually all you need to do to switch volumes, but watch out for any new issues related to the guid based volume names - it's possible you no longer need to even modify fstab....

hope this helps,

Mario

---

