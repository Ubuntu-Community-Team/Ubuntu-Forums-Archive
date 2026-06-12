---
title: "How Do I Backup Kernel In Case Of Emergency?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by dodo3773 on 2010-10-19
Recently I was messing with a script that messed up my wifi. My ethernet port is a little messed up. So, I thought that I would be able to just choose the old kernel, reboot, then update the kernel again with working wifi. The problem is that I did not update grub. So after I removed the old kernel I booted my computer and nothing. I popped in my Ubuntu live cd hoping that I could just reinstall grub from there, but that was a mess. So, I did a clean install and I am back up now. [INDENT]       Is there a way I can just download a deb package of my current kernel (or make one) to reinstall in case of emergencies? Do I have to roll my own kernel if I want any kind of backup? I am perfectly fine with the one from the update manager but I would like to be more prepared for an emergency if this happens again. Thank you in advance.[/INDENT]

---

### Post by efflandt on 2010-10-20
If you uninstall kernels, you should always leave at least one previous kernel version in place just in case you run into any issues with the current kernel.  I have never had such an issue, but sometimes the current kernel is updated several times, and if something trips you up in such a case, it is handy to have an alternate kernel to enable you to boot.

---

### Post by dodo3773 on 2010-10-20
I went to   /var/cache/apt/archives
and I found these three .deb packages

linux-headers-2.6.32-25_2.6.32-25.45_all.deb

linux-headers-2.6.32-25-generic_2.6.32-25.45_i386.deb

linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb

I copied them and put them in my home folder. Is that it? I just double click and install these if I need to?

---

### Post by dodo3773 on 2010-10-20
> **efflandt said:**
> If you uninstall kernels, you should always leave at least one previous kernel version in place just in case you run into any issues with the current kernel.  I have never had such an issue, but sometimes the current kernel is updated several times, and if something trips you up in such a case, it is handy to have an alternate kernel to enable you to boot.

Yeah that is what I did, but I did it through synaptic and forgot to update grub. I was thinking that the deb would do that for me if I was to forget again. I don't know what I was thinking that day.

---

### Post by dodo3773 on 2010-10-28
Does anyone know the answer to this one? I figured one of you guys did. I guess I will just have to find a way to mess something up and give it a test try. I just wish I knew if there was a certain order to install them in.

---

