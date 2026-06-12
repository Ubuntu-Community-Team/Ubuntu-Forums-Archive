---
title: "Moving the installation from one harddisk to another"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Saubazi on 2006-08-10
I just bought a new SATA drive. I have couple of IDE drives and my Ubuntu is on one of those at the moment. I'd like to move my whole installation to the SATA drive.

What do I need to do?

Just create the mount points and cp -r everything from root to the new disk modify fstab or is it more complicated than that?

I suppose I need to reinstall grub again or just modify the root entries?

I think it is quite straight forward but I am not 100% sure how to begin...

---

### Post by Saubazi on 2006-08-11
All right I managed to do this - was a matter of using cp -a command and so on. Got the machine to boot and all that but
I got one Ubuntu specific problem. The machine wanted to install some updates, which I agreed to do - fine, got a new kernel and stuff but of course it screwed up the grub completely again 
wanting to boot from the old drive. 

Anyway where are these entries where the updater pulls the values from? How can I avoid that the updater won't pull this stunt once more when I get the next kernel update?

---

### Post by CameronCalver on 2006-08-11
This is what i would do
Copy everything you need to keep onto another hd and then reinstall ubuntu on the sata and then put it back on the sata

---

### Post by Saubazi on 2006-08-11
Sounds like lots of work since everything is working as they should I would need to do reinstall bit and recopy everything, which does not fill me with inspiration - it is only synaptic is messing the things up in updating so somewhere in Ubuntu specific stuff there is still a link to old hardware configuration. Normally, this should work in Linux without too much drama.

---

### Post by Saubazi on 2006-08-11
Additionally already before what disturbed me with these constant kernel updates was that menu.lst was not preserved. I always decided to create a new one, comfortably without the Windows boot option or anything which is present from the new install...

---

### Post by darrenrxm on 2006-08-11
Couldn't you use GParted to copy it to another hard drive?

---

### Post by Saubazi on 2006-08-11
Copying's not the problem anymore that's now done for.

I moved the installation from /dev/hdd to /dev/sda and updated /boot/grub/menu.lst and /etc/fstab accordingly (and reinstalled grub so that it points to /dev/sda1 to look for /boot) the machine booted o.k and was running honky-dory.

The only thing was that it announced some updates yesterday, which I installed - well one of the updates was newer kernel and of course Ubuntu rewrites the /boot/grub/menu.lst to include new kernel as boot option.

The only problem that resulted from this is that it rewrote menu.lst completely and inserted everywhere /dev/hdd4 or hd(1,1)
where I had just a moment ago written (hd2,0) and /dev/sda3, which is the new location - so somewhere in the machine there is file, which still contains old installation location and I am just wondering where and which...

---

