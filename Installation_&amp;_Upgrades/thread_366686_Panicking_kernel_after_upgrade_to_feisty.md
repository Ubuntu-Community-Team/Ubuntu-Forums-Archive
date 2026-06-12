---
title: "Panicking kernel after upgrade to feisty"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by halkonst on 2007-02-21
My new kernel is very shy, it panics every time I try to boot it. There's really no getting through to it...

[story]
I needed a feisty version of the libc6-dev package for the newest version of ntfsprogs to work, that's how it started.  After installing the new libc6-dev (version 2.5-0ubuntu11) I got alot of strange dependency problem when trying to install other edgy packages like the kubuntu-desktop, build-essential and some other ones (libc6 got tons of depends and reverse-depends). Apparently they needed the older version to work. So I figured I'd better upgrade everything to feisty versions just to make things work again, rather than removing the new libc6 and reinstalling the older version which might have been the better choice.  Anyway I changed every occurrence of "edgy" in my /etc/apt/sources.list to "feisty", did an apt-get update followed by an apt-get dist-upgrade and I was upgraded. On reboot tho things didn't go too well, the prompt said my kernel was panicking and It wouldn't boot. So now I'm back on the edgy kernel but with feisty packages and it don't feel right. Aside from having a ton of packages listed in my synaptic that I'm not allowed to install, I want my ubuntu purebred :P.

[questions]
I have removed the feisty kernel (2.6.17-11-generic) from my /boot/grub/menu.lst so it is no longer a boot option, but how do I remove the damaged kernel from my disk completely?

What might have caused the kernel compilation to fail when I was doing it the easy automated way? Is there a guide somewhere to how to manually compile a feisty kernel tailor made for my system?

Is there a way to use feisty versions of certain packages without causing dependency problems or having my synaptic fill up with (to me) useless packages while keeping the edgy kernel?

If my main concern is having a stable reliable OS, but I still want to be able to install the latest versions of certain apps like ntfsprogs, beryl, compiz, etc., would it be wise to upgrade to feisty?

[QUOTE=My specs]
Ubuntu Edgy i386
AMD Athlon64 3000+
512 MB RAM
Radeon 9200SE
[/QUOTE]

Thanks for your time.

---

### Post by jpeddicord on 2007-02-21
That's strange, I had no problems with the new kernel (other than support for my crappy wireless card) but the older Edgy kernels refused to boot.

My recommendation would be to keep using the Edgy kernel for as long as it works, and just make sure that you keep your system up-to-date, keeping the Feisty kernel and testing it now and then. If it still won't boot by RC time, you might try a fresh install.

---

