---
title: "Ubuntu 14.04 kickstart"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by jason116 on 2016-03-26
Hello,


I'm setting a Ubuntu 14.04 kickstart. For the most part it works, although it hangs at a prompt that I can't seem to get rid of. 


It hangs at Configuring grub-pc. Saying that I chose not to install GRUB to any devices. 
I choose (manually) Continue without installing Grub? I select yes and it finishes without issue. (It does configure this later on and it works) how do I stop this prompt?


I've tried the following with no luck to my kickstart config.


```
# Continue without installing GRUB?
preseed grub-pc grub-pc/install_devices_empty boolean yes
```


and 


```
# Setup the disk
d-i grub-installer/only_debian boolean yes
```


Should add in that this is on being run on Xencenter 6.5 and that this is a VM.


Any thoughts?

---

### Post by jason116 on 2016-03-28
Bump.

---

### Post by Bucky Ball on 2016-03-28
*Thread moved to **Virtualisation**.*

> **jason116 said:**
> Should add in that this is on being run on Xencenter 6.5 and that this is a VM.

Yep. See if this gets you more action.

No idea if it is in any way related to the [bugs reported here]("http://www.linuxquestions.org/questions/ubuntu-63/system-config-kickstart-not-working-in-ubuntu-14-04-a-4175502357/").

---

### Post by jason116 on 2016-03-28
I don't think that's it.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/580408)

Maybe. Shouldn't really matter if it's virtualized.

---

### Post by grahammechanical on 2016-03-28
Mention kickstart to me and I immediately think of the motor cycle that I had when I was a young man. It did not have an electric starter. 

Perhaps you should be asking this on a different forum?

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/ch-kickstart2.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/ch-kickstart2.html)

But after reading this

[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

Regards.

---

### Post by jason116 on 2016-03-29
I'm using a similar kickstart on CentOS and it's working fine.

---

### Post by jason116 on 2016-03-30
Tried other kickstart scripts for ubuntu 14 as well, same issue.

---

