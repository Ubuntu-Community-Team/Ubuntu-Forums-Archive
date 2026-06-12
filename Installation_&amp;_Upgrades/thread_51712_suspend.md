---
title: "suspend"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by art on 2005-07-25
Hi forum
Has anyone gotten swsusp2 working. I patched the 2.6.12 kernel from kernel.org, then make-kpkg and finaly made mkinitrd (othewise it panics). But if I now boot into that kernel first of all CPU is at 100%, klogd takes it all, and then if I kill klogd, and do hibernate in command line, it says aborting, check dmesg, but dmesg is empty? 
Any help? I am going nuts already!

---

### Post by art on 2005-07-25
Well, I haven't figured it out yet ](*,) , very sad...
I figured people have had success installing it as a module, but the version for 2.6.12 kernel doesn't have module support, so I am stuck at this point. Any ideas?
Thanks!

---

### Post by netsyd on 2005-07-26
[QUOTE=art]Hi forum
Has anyone gotten swsusp2 working. I patched the 2.6.12 kernel from kernel.org, then make-kpkg and finaly made mkinitrd (othewise it panics). But if I now boot into that kernel first of all CPU is at 100%, klogd takes it all, and then if I kill klogd, and do hibernate in command line, it says aborting, check dmesg, but dmesg is empty? 
Any help? I am going nuts already![/QUOTE]

Hey there,

I'm not exactly sure what you were doing (make kpkg? Sorry, not much of a "Linux Guy") but I have swsusp2 working on my laptop since the default suspend/hibernate just didn't work for me. 

Also, I remember reading something in the FAQ for swsusp2 (or the instructions not sure) that it tends to freakout when you use an initrd... I know this is contrary to what you should do with a 2.6 kernel but, but I don't use an initrd and mine boots just fine.  :D

Allow me to appologize for the slowness of the following link before you even click it... it runs at my house on a cable modem... 

[http://www.netsyd.com/content.php?content.4](http://www.netsyd.com/content.php?content.4)  ** I considered posting a how-to here on the forum, but I just haven't had time. 

About halfway down is the steps I used to build my kernel. I built it twice, once to make sure my build process was good and the second to build in swsusp2. 

Hope this helps   :mrgreen:

---

### Post by art on 2005-07-28
hey Thanks a ton!
I got much further without initrd, the trick was to include IDE in the kernel, not as modules. Now I can boot allright, I can see all the software suspend messages in the boot sequence, about suspend being enabled and stuff, but when I run the hibernate script (with ath_pci removed), it doesn't do anything. It stays there for 2-3 minutes, at which point I just reboot it. How long does it take on your machine to hibernate? With ath_pci it actually spits out a kernel panic message, was it the same with you? 
Again, thanks a lot!

P.S 
I see an initrd-2.6.12.3.img in the content of the /boot directory you present on your website, why do you create that?

---

### Post by d3c3it on 2005-08-06
Did you ever figure out what was causing klogd to have a spas attack and run at 100% ? i've fallen back down to 2.6.11 as its causing to many problems

---

### Post by art on 2005-08-09
yeah, as I said it was to include IDE in kernel not as modules, when compiling kernel. 
HTH

---

