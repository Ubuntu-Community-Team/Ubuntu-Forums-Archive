---
title: "compiling kernel: old config to new not matching"
date: 2006-04-13
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-04-13
I followed this howto: [http://www.ubuntuforums.org/showthread.php?t=157560](http://www.ubuntuforums.org/showthread.php?t=157560) (howto compile newest kernel + ck patch)

and I had a problem: 
It seems the imported /boot/config-blabla is not very "compatible" with the latest kernels. It misses a lot of options originally present in Ubuntu's kernel (the output on the terminal when typed "sudo make xconfig" shows the incompatible arguments in .config I guess). And you have to manually go in there and double check everything (which I can't do, bc I'm clueless  )

One example is iptables. The new config made from the old one totally misses the iptables configuration in the kernel. With the new kernel, you don't have a firewall anymore. To fix that, check out: [http://ubuntuforums.org/showthread.php?t=151824](http://ubuntuforums.org/showthread.php?t=151824)

Anyone now a workaround or something like that so the old config and the new config are working and the resulting kernel works flawlessly just like the ubuntu kernel? 

I would appreciate any help, especially pointers (I don't know what to google for...) thanks .

---

### Post by syg00 on 2006-04-14
I decided it was time I got a more current kernel, so I used your post as a prod.
Used the guide you linked to above as a test.
Copied the config over, and kicked off a make.
Holy shit  !!!!.
There is ***_NO_*** way I'd consider a build with that much as modules.
I'll clean up and build from scratch and see if I run into similar problems as you.

More to come ...

---

### Post by towsonu2003 on 2006-04-14
> **syg00]
There is ***_NO_*** way I'd consider a build with that much as modules.[/quote]
we may have a misunderstanding (not sure). I'm not complaining about the number of modules, but about the old config not configuring the new kernel so it is just like (a mirror of) the ubuntu kernel. I guess this is not a problem (both kernels are patched in different ways), but I'm clueless about how to make the new one behave the same way the old one behaves.
[QUOTE=syg00]
I'll clean up and build from scratch and see if I run into similar problems as you.
[/QUOTE]
The funny thing, when you start building from scratch (no copying old kernel), it still uses the old kernel config (check out the error messages spitted out when you hit enter to make menuconfig/xconfig. To circumvent that, I "touch"ed a new .config file (and realized there is no way I can configure that thing from scratch  said:**
> 
More to come ...
I'll be waiting :)

PS. I do show I'm clueless, don't I :)

---

### Post by syg00 on 2006-04-14
No misunderstanding - just me having a (mini-)rant.
I'm used to doing my own builds (Gentoo and Arch) - I'll have a play and see what I can generate.

---

