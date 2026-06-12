---
title: "dkms?"
date: 2009-01-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-01-05
Can anyone explain what dkms is for? It seems to be installed by default in Jaunty, and maybe Intrepid, but it doesn't seem to be needed. removing it doesn't stop anything working as far as I can tell.

---

### Post by qamelian on 2009-01-05
[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

---

### Post by autocrosser on 2009-01-05
In my case, DKMS is used to build the nVidia driver & Ralink wireless driver...all depends on your hardware/driver needs.

---

### Post by scradock on 2009-01-05
> **qamelian said:**
> [http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

Yes, that tells me why it's good for developers and vendors. Does it do anything useful for me - i.e. is the latest-greatest OS driver going to fail to install properly next time there's a kernel upgrade if I don't have it installed and enabled?

I'm not using fglrx - the OS x-x-v-ati and x-x-v-radeon drivers are doing great work for me.

---

### Post by autocrosser on 2009-01-06
It's safe to say that if you do not see any DKMS builds during kernel upgrades that you do not need it.....and if you tend to only have open-source on your system, that would be the case.

That being said, you might just try to delete it--if it will remove quite a few packages that you know are important.......that would be a question to take up with the devs.

---

### Post by scradock on 2009-01-06
Thanks - synaptic removes the dkms package cleanly without any other changes.

Guess I don't need it, and if I ever do it will no doubt be fetched and installed....

---

### Post by Quikee on 2009-01-06
Well, it is not only usable for non-open source drivers. VirtualBox (ose) for example uses it for compiling its kernel module. 
Alternative is to provide the module for every kernel release - as this was done previously and was painful when new kernel was released but not the module. 
Any "external" kernel module could be done this way (for example btrfs until it is included in the kernel).

---

