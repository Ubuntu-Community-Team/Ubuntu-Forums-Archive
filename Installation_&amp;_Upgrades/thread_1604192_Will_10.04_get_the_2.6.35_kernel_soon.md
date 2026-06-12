---
title: "Will 10.04 get the 2.6.35 kernel soon?"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by allbread on 2010-10-23
I currently have both a laptop (Thinkpad W500) and workstation with SSD drives and would like to install 10.04 on both - I'd rather stick with the LTS release than upgrade to 10.10 if I can avoid it however as both will be using SSD drives as their primary I need to have a kernel with TRIM support.

I know that MM has the latest kernel - will this kernel be backported to the 10.04 repository at any point or will 10.04 be stuck with 2.6.32 for the forsee-able future?

I've found a couple procedures for upgrading the 10.04 kernel to the latest version however if it will updated in the 10.04 repository at some point then I'd rather just wait for that.

---

### Post by oldfred on 2010-10-24
I do not know anything about Ubuntu's plans but have never seen them backport to a newer kernel. Each version of Ubuntu has the same kernel version. They do backport some specific security issues into the older kernel and that is why you see updates to the kernel but the 2.6.35 will not change.

---

### Post by allbread on 2010-11-05
> **oldfred said:**
> I do not know anything about Ubuntu's plans but have never seen them backport to a newer kernel. Each version of Ubuntu has the same kernel version. They do backport some specific security issues into the older kernel and that is why you see updates to the kernel but the 2.6.35 will not change.

So in other words - I shouldn't expect 10.04 repository to have a 2.6.32+ kernel anytime soon (if ever)? 

I was interested in this as I know that the latest kernel (2.6.35) has native TRIM support. I've found a couple tutorials on how to manually upgrade the kernel in 10.04 to the latest but have also read that there are drawbacks to this... 

What problems might I run into if I manually upgrade the 10.04 kernel to 2.6.35?

---

### Post by coffeecat on 2010-11-05
> **allbread said:**
> What problems might I run into if I manually upgrade the 10.04 kernel to 2.6.35?

Best thing is to try it and see. Installing a new kernel doesn't affect the rest of your system and doesn't remove the old kernel. So long as you don't uninstall the 2.6.32 kernel yourself, it will still be there and there will still be grub entries so that you can boot into it if you encounter problems with the 2.6.35 kernel.

What tutorials did you find? Were they about compiling your own? You can do this but it can be - um - fun. On the other hand, installing the Ubuntu Maverick 2.6.35 kernel is relatively easy.

---

### Post by allbread on 2010-11-05
> **coffeecat said:**
> Best thing is to try it and see. Installing a new kernel doesn't affect the rest of your system and doesn't remove the old kernel. So long as you don't uninstall the 2.6.32 kernel yourself, it will still be there and there will still be grub entries so that you can boot into it if you encounter problems with the 2.6.35 kernel.

What tutorials did you find? Were they about compiling your own? You can do this but it can be - um - fun. On the other hand, installing the Ubuntu Maverick 2.6.35 kernel is relatively easy.

They were for installing the MM kernel - "backporting" I believe was what they called it. I think the caveat was that my 10.04 installation would then not receive any subsequent kernel updates... 

I'm wanting to stick with 10.04 because of the LTS support but I'm beginning to think 10.10 might just be easier...

---

### Post by lightrush on 2010-11-14
Hey,

I think this is what you are looking for:

[http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway](http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway)

I have written a small HOWTO on that topic. I also use that kernel because of TRIM :) .

---

### Post by spiky001 on 2010-11-14
Just an add on to this can the newest kernal be installed on even earlier systems i,e 9.10 8.04

---

### Post by lightrush on 2010-11-14
Not "the easy way". You may be able to pull the DEB packages from lucid-proposed and manually installing them on your system. Your mileage may vary though. Try it out and see how it is. If the results aren't positive you can always boot with the older kernel and un-install them. :)

If that fails you could always compile packages yourself.

---

### Post by allbread on 2010-11-16
> **lightrush said:**
> Hey,

I think this is what you are looking for:

[http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway](http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway)

I have written a small HOWTO on that topic. I also use that kernel because of TRIM :) .

Thanks for your response - I ended up installing Linux Mint 10 since that is a distro I've been wanting to try out for awhile anyways...

Is TRIM enabled by default in 2.6.35 or do I need to configure it as such?

---

