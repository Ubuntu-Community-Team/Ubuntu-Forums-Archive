---
title: "Tried to install Ubuntu and got this..."
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by Satyros on 2018-02-26
Hi, I tried installing Ubuntu on an old notebook. Everything seemed to go fine, but when I turn it on I get this very fast moving screen with lots of text info that is too quick to read: [https://streamable.com/1wei4](https://streamable.com/1wei4)

It just loops endlessly. What should I do next?


Thank you.

---

### Post by oldfred on 2018-02-26
What brand/model notebook?
How much RAM? If 2GB or less Lubuntu may be better as lighter weight gui.
What video card/chip? If nVidia, you may need nomodeset boot parameter.

You are seeing boot process with is normally hidden with boot parameter quiet splash.
But usually it stops somewhere and few lines above may be the place where the error really occurs.

       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by Satyros on 2018-05-08
Hi oldfred,
This is the pc i tried to install it in: [https://www.cnet.com/products/acer-aspire-one-happy-n55dqpp-10-1-atom-n550-windows-7-starter-1-gb-ram-250-gb-hdd-series/specs/](https://www.cnet.com/products/acer-aspire-one-happy-n55dqpp-10-1-atom-n550-windows-7-starter-1-gb-ram-250-gb-hdd-series/specs/)

It has 1 GB of memory. I will try Lubuntu today.

---

### Post by Satyros on 2018-05-08
So I tried Lubuntu today. I booted from a flash drive, got the Lubuntu menu and selected "Install Lubuntu", All seemed to be going good.

Then I get a flashing "Lubuntu" text and after a while "stdin: not a typewriter" on loop.

I checked the BIOS first for Secure Boot and I didn't see that option so I guess the problem's not there.

---

### Post by Satyros on 2018-05-08
Now I tried "nomodeset" before installing. It worked!

---

### Post by Satyros on 2018-05-08
Well it seems not. The installation was apparently successful but now when turn it on I just get a black screen and a beeping loop...

---

### Post by oldfred on 2018-05-08
If you needed nomodeset to install, you need it to boot.
And if nVidia need it until you install proprietary driver.

And you do not get grub by default if you only have one install.
If older BIOS, you hold shift key from BIOS screen until grub menu appears. Then manually edit boot stanza.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Satyros on 2018-05-15
Followed the intructions and it works perfectly, thank you!

---

### Post by Satyros on 2018-05-17
Sorry folks, it seems this is not solved yet afterall.

When I manually remove "quiet splash" from grub the everything goes well and I get access to the OS.

The problem was when I tried to permanently remove it from the kernel boot parameters. I uncommented the "quiet splash" line" updated grub and rebooted. I got the same beeping black screen that I had before messing with grub from the first time. So I rebooted again and entered grub. Quiet splash is not there, as I intended. But I also seem to remember that there was something after "quiet splash" that was there before that's not there anymore. How can this be if I only uncommented the line containing " quiet splash"? Is this that's causing the problem now?

Update: ok, this doesn't make any sense to me. If I turn on the pc normally I get the black screen and beeping sound as I told above. If I turn on the pc, go to grub, _don't change nothing_ and quit grub the OS starts normally and everything is fine.

---

### Post by oldfred on 2018-05-17
Are you getting into recovery mode which also has the nomodeset boot parameter, instead of quiet splash?
What video card/chip?

Try booting with nomodeset where you used to have quiet splash. Just manually try it when booting on linux line, not editing /etc/default/grub as permanent change. Or directly boot with recovery mode which has nomodeset.

---

