---
title: "Dual booting: Booting into Ubuntu from grub."
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by digital_nite on 2011-02-01
Hello to all,
     I'm a newbie and can't get to linux on my external hard drive. I recently did a full install of Ubuntu 10.10 and am currenly running XP on my main drive. When I boot I can choose to go to my ext hard drive, which holds Ubuntu, but I'm stuck with a grub command line. What do I need to do to boot into Ubuntu from grub? 

Thanks for the help,
digital_nite

---

### Post by kansasnoob on 2011-02-02
With the external drive connected boot an Ubuntu Live CD and then post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by digital_nite on 2011-02-04
Hello [kansasnoob]("http://ubuntuforums.org/member.php?u=554595"),
    I just realized that i can't even get access to Ubuntu. For some reason the live CD won't let me in any longer. Should I reformat the external drive? What are your ideas?

digital_nite

---

### Post by Quackers on 2011-02-04
Hmm, you can't fix it, or re-install it without the live cd working. Maybe you could check your bios boot priority settings?

---

### Post by digital_nite on 2011-02-05
> **Quackers said:**
> Hmm, you can't fix it, or re-install it without the live cd working. Maybe you could check your bios boot priority settings?
Hi Quakers,
    I should have realized what you pointed out. I can access the "door" to Ubuntu by changing my boot priority settings; I can boot to grub. However, I don't know what to do to accesss Ubuntu from there. I'm just stuck at a "grub>" command line. What commands should I throw at grub to get into ubuntu? By the way, I tried the boot command and it said something about no kernal being loaded. I don't know anything about loading  a kernal or if loading one would help me.

Thanks,
digital_nite

---

### Post by kansasnoob on 2011-02-05
What happens when you try to boot the Live CD?

---

### Post by digital_nite on 2011-02-05
> **kansasnoob said:**
> What happens when you try to boot the Live CD?
My system hangs. I can't use the try out feature and I don't attempt to install because Ubuntu's already installed.

---

### Post by kansasnoob on 2011-02-06
It sounds to me like a possible hardware conflict issue. Have you ever been able to run any Linux Live CD/USB on that machine?

If so it would be good to see the output of these commands:

```
cat /proc/cpuinfo|head -8
```

```
lspci | grep VGA
```

```
free -m
```

That should tell us what CPU and graphics chip you have, and also how much RAM you have. Or you could boot into XP and do it the Windows way:

[http://www.computerhope.com/issues/ch000017.htm#01](http://www.computerhope.com/issues/ch000017.htm#01)

---

### Post by oldfred on 2011-02-06
Sometimes you can manually boot:

grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.

configfile (hd0,1)/boot/grub/grub.cfg

or, again change hd0,1 to whatever ls showed and change sda1 to sdaX where X is same number:

set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

---

