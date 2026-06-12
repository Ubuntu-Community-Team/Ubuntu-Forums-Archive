---
title: "X1 Carbon 6th gen: Secure Boot support"
date: 2019-09-23
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2019-09-23
I just upgraded to a Lenovo X1 Carbon 6th gen, and I would like to dual-boot it with 18.04. (Win10 Pro, i7-8650U, HDR WQHD, Intel UHD Graphics 620, 16/1TB) 

[This guy]("https://thornelabs.net/posts/installing-ubuntu-1804-lts-on-a-lenovo-thinkpad-x1-carbon-gen-6.html"), citing [this]("https://wiki.ubuntu.com/UEFI/SecureBoot"), says Ubuntu supports secure boot. But [here]("https://ubuntuforums.org/showthread.php?t=2147295") it says to turn it off. Is there a guide specific to this laptop for Ubuntu/Win 10 dual-boot setups? I would like to keep both the fingerprint reader for Windows and secure boot if I can. But if I have to turn off both, then that's what I'll do.

See also: [https://medium.com/@hkdb/ubuntu-18-04-on-lenovo-x1-carbon-6g-d99d5667d4d5](https://medium.com/@hkdb/ubuntu-18-04-on-lenovo-x1-carbon-6g-d99d5667d4d5) 

I'm completely new to Win 10, and so I apologize if this has been covered elsewhere. A link will be fine.

---

### Post by CatKiller on 2019-09-23
Secure Boot support is pretty robust these days. The Ubuntu components are signed by the Canonical key, and the Canonical key has been signed by Microsoft, and your motherboard will accept Microsoft's key. So with a properly implemented UEFI (*cough*) it should all work OK.

However, things that *aren't* Ubuntu components - most prominently the Nvidia kernel module and Oracle's VirtualBox hypervisor - *aren't* signed by the Canonical key. If you want to use either of those with Secure Boot then you need to sign them yourself with a Machine Owner's Key.

It's not too hard to do that, but it's a bit of a faff. Since Linux users don't benefit as much as Windows users from Secure Boot, and (particularly initially) there have been some really ropey UEFI implementations, and it's a bit of a faff to get the (very widely used) Nvidia kernel module working with Secure Boot, it's pretty common to recommend just turning it off to get Ubuntu up and running.

If you're interested in Secure Boot, and you've signed your own bits, and everything's working properly, that's the time to turn it back on. Basic troubleshooting, really, to limit the ways that things can not work.

---

### Post by sks24 on 2019-09-24
Thanks CK.

So, I turned off Secure Boot last night but still couldn't get a WinPE Easeus emergency USB disk to boot. I will almost never boot Windows on this laptop, so I'll have to return to this so I can get Ubuntu up and running. Maybe in the next day or so I'll post screenshots of my bios. It seems like that's the first thing which must be gotten right. If you could point me to something which illustrates this "key signing" I would appreciate it; it's completely new to me.

---

### Post by CatKiller on 2019-09-25
> **sks24 said:**
> If you could point me to something which illustrates this "key signing" I would appreciate it; it's completely new to me.

The [ Secure Boot page](https://wiki.ubuntu.com/UEFI/SecureBoot) of the Ubuntu wiki shows the steps involved, but isn't that strong on the explanation. I think I had to read *other* pages elsewhere for each of the steps before it clicked for me, and I can't remember now which ones they were and may well be different for you, anyway.

The general process is that you
[list][*]generate a key, if you don't already have one. It's the same process as you'd use to generate other cryptographic certificates, so you should have all the tools you need already
[*]use that key to sign the modules you're interested in
[*]enrol the key with the MOK manager, which will get you to set a temporary password/PIN and reboot
[*]your UEFI will then ask you for your temporary password/PIN and then confirm that you want to enrol that MOK.
[*]that MOK will then be used to verify the kernel modules at boot time [/list]

I managed to do it, and it worked, and I broadly understood what I was doing at the time that I did it, but I'd need to look it up again (and ideally the command history of what I did) if I ever needed to do it again.

---

### Post by sks24 on 2019-09-26
CatKiller, your roadmap is exactly what I need. I'm pretty good if I have the relevant search terms and an idea of the sequence. So thank you very, VERY much. So, over the next week or so, when I have some free time here and there, I will start chipping away at this. I would like to leave the thread open for now if that's OK.

Thanks again, 
Scott

---

