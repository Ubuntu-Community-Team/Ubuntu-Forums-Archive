---
title: "revert to old kernel"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by gauol on 2012-09-11
I have my new system working mostly how I want it to however I went to update tonight and noticed that it seems to be a more complete update. That is I think its attempting to upgrade to 12.04.1 and the new kernel. The last kernel update I did resulted in breaking my software RAID and I am now booting off 3.2.0-27-generic.

So my question any reason to think I would not be able to boot to the old kernel?

---

### Post by Bucky Ball on 2012-09-11
Hit shift at boot. This should take you to the grub menu. Select the old kernel.

If you want to change the kernel order around, Grub Customizer makes it really easy to do so:

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

The new kernel update seems to be causing problems for many, if that is what you are doing. You say it is attempting to upgrade to 12.04. What are you running now? A regular update will not do this.

---

### Post by mastablasta on 2012-09-12
> **gauol said:**
>  That is I think its attempting to upgrade to 12.04.1 and the new kernel. 
 
no. 12.04.1 is only designation for the image of the OS. and it only means 12.04 along with all updates up to certain point in time (when the image is made/frozen).
or in other way if oyu installed 12.04 and applied all updates up to now, you already have 12.04.1
 
as for kernel try to lock it in synaptic. otherwise you can also deselect it on update in update manager.

---

### Post by gauol on 2012-09-12
I'm 12.04 on three machines, 2 work laptops and my home desktop, I have been performing updates weekly (probably not last week). Last night when I went to update the machines I was presented with the "Distribution Upgrade" dialog on all three. I don't a big problem let this go on my work systems but on my home machine I need to be sure it won't break my RAID. I somewhat new to Ubuntu, not Linux, so I guess my confusion is if I allow a dist upgrade will it clean out the old kernels or the will they remain? ( updating to 3.2.0-29-generic broke my so I am booting 3.2.0-27-generic now)

(You guys respond so quick its great, many thanks to all)

---

