---
title: "Kernel 2.6.30 Boot &quot;Error 13&quot;"
date: 2009-05-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coutts99 on 2009-05-08
Hi,

I have upgraded to Karmic and all is working well :)

However, when I install linux-image-2.6.30-3-generic and reboot, I get "error 13: Invalid or unsupported executable format". Any ideas what this means?

I upgraded another machine yesterday and that worked fine.

---

### Post by ronacc on 2009-05-08
there have been occasional reports of this with any of the 2.6.30 kernels , usualy with ext4 , in my case letting karmic install its own grub fixed it .

---

### Post by coutts99 on 2009-05-08
Yep ext4.

How can I fix it? Re-run grub-install?

---

### Post by ronacc on 2009-05-08
that would be worth a try , make sure you have the latest grub , you can check in synaptic . I don't know if anyone has figured out why this happens , it seems pretty random .

---

### Post by coutts99 on 2009-05-08
> **ronacc said:**
> that would be worth a try , make sure you have the latest grub , you can check in synaptic . I don't know if anyone has figured out why this happens , it seems pretty random .

Ah bugger!

Grub error and it won't boot at all now :)

Running from Intrepid boot CD now and downloading a Jaunty one as this one does not mount ext4 :)

I really should stop messing about with my machine when I'm at work :)

---

### Post by linux6994 on 2009-05-08
I reformated to ext4 loaded Jaunty then modified /etc/apt/sources.list to karmic and all is well.

---

### Post by coutts99 on 2009-05-08
> **linux6994 said:**
> I reformated to ext4 loaded Jaunty then modified /etc/apt/sources.list to karmic and all is well.

I done the same on two machines, my home one and my work one, home one is fine, work one is now buggered :)

---

### Post by davideotape on 2009-05-08
I'm getting the same error with the same kernel on ext4. Is there a bug report for this?

---

### Post by ronacc on 2009-05-08
it is possibly this bug , I am adding my comments to it .
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/365331)

---

### Post by coutts99 on 2009-05-08
> grub-install --root-directory=/boot /dev/sda

Oops, I missed the root-directory option :)

---

### Post by davideotape on 2009-05-10
```
grub-install --root-directory=/boot /dev/sda 
```

Is this what I need to run to get the new kernel working then?

(and I know I'd need to change the drive to what I want :))

---

### Post by coutts99 on 2009-05-11
I've just done grub manually, don't trust grub-install after it borked my box :)

```
grub

root (hd0,0)
setup (hd0)
```

I'm back up and running now, haven't tried the 2.6.30 kernel, I'll reboot in a bit and try :)

Yep this fixed it, up and running in 2.6.30 now.

---

