---
title: "Ubuntu with Windows 7 on VM - slow?"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Depravitus on 2011-01-01
Hello everyone, glad to be on these forums. :guitar:

I started using Linux about 6 months ago and am in love, especially with Ubuntu -- 10.10 hasn't been a disappointment either.

The problem is, I am a graphics designer. I use 3D programs like Maya and Carrara, as well as other artistic programs like Photoshop. Unfortunately I can't replace these with Blender and Gimp (both great programs but not suitable for me).

Since I don't want to dual-boot, I am looking into the option of having Ubuntu as my main operating system and running Windows 7 through a virtual machine, but I have never done anything like this before.

Does anyone know if this is a viable option without sacrificing a lot of performance during intensive CPU and GPU calculations? And if so, what is the best software/method of doing this? I am willing to dish out some money for quality, if necessary.

* 4 gigs DDR3 dual-channel RAM
* AMD 1090T x6 Black Edition CPU

Thanks in advance!

- Depravitus

---

### Post by carl4926 on 2011-01-01
Win7 should run fine in Virtual Box
Not sure about your applications, never used those.

Give win7 1.5GB of memory in the VBox settings and Ubuntu will be fine with that.

---

### Post by Depravitus on 2011-01-01
Thanks for the response, Carl.

The software I run requires all the RAM and CPU it can get its hands on, going to have 8 gigs in about a week.

Would Ubuntu be fine with 2 gigs, then 6 gigs going to Win7?

Or better yet, can it be set up so that each OS takes whatever it needs at the time, or do the numbers have to be static?

- Depravitus

---

### Post by wilee-nilee on 2011-01-01
Your going to have problems if your a graphics designer, dual boot it and you will be set.

---

### Post by dgw on 2011-01-01
> **Depravitus said:**
> Would Ubuntu be fine with 2 gigs, then 6 gigs going to Win7?

Ubuntu should be fine with 1 GB or less of RAM unless you're doing something that requires a lot of RAM in Ubuntu. 

Windows 7 runs really well in Virtualbox. I think you ought to give it a try. If it's slow, you may have to dual boot, but using Virtualbox is really convenient because you can use both OS's at the same time.

---

### Post by carl4926 on 2011-01-01
> **wilee-nilee said:**
> Your going to have problems if your a graphics designer, dual boot it and you will be set.
That gets agreement from me too
But give VBox a try

---

### Post by CharlesA on 2011-01-01
Haven't run into problems running Win7 in VBox, but I don't know how well it'll work for running Maya and whatnot.

I heard that Vbox 4 added some 3D stuff, but I haven't had a chance to upgrade just yet.

If you tell the VM to use 6GB of RAM, it'll reserve 6GB of RAM when the VM is running. There isn't a way to tell it to use only how much it needs, as the guest OS needs to be able to use all the memory if needed.

---

