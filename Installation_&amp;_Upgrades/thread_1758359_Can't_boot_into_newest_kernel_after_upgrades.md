---
title: "Can't boot into newest kernel after upgrades"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by nash black on 2011-05-14
Hi all, 

this is a new problem with issues that started when I upgraded to 10.10. Originally, GRUB wouldn't load after that upgrade, but that was fixed [here]("http://ubuntuforums.org/showthread.php?t=1756072"). Once GRUB was working properly, there was a problem with the 2.6.35-28 generic kernel. When I tried to boot through it, I would only get an ubuntu command line. 

Luckily the older 2.6.32-22 generic kernel worked just fine and I could log in and load my ubuntu desktop with no issues. I decided to upgrade to 11.04 to see if that would correct whatever was going on. The installation was completed without any apparent issues, GRUB works, XP Pro works, and the older 2.6.32-22 generic kernel allows me to boot into 11.04.

Unfortunately, another new kernel, 2.6.38-8 generic, is not working properly. I snaped some pictures of what happens when I try to use this kernel:

[http://imageshack.us/f/840/boot1c.jpg/](http://imageshack.us/f/840/boot1c.jpg/)

[http://img94.imageshack.us/i/boot2d.jpg/](http://img94.imageshack.us/i/boot2d.jpg/)

[http://img39.imageshack.us/i/boot3small.jpg/](http://img39.imageshack.us/i/boot3small.jpg/)

The first is GRUB/ The selection
The second is the loading graphic
The third is a command line where it freezes (note: this is not the same command line screen/environment that I was referring to with the 10.10 new kernel)

Any help would be appreciated!

Nash

---

### Post by nash black on 2011-05-14
Just tried reinstalling the kernel through synaptic package manager with no luck. arg.

---

### Post by MAFoElffen on 2011-05-14
> **nash black said:**
> Just tried reinstalling the kernel through synaptic package manager with no luck. arg.
Refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Edit /etc/defualt/grb and add this line":
```

GRUB_GFXPAYLOAD=text

```Which will tell the kerenl to ignor any graphics calls and boot as in text mode, not passing any graphics calls to xorg and letting it boot fresh, at that step.

If that works, you can leave it at that or work through the sticky's first 3 posts to correct it, get it to work as it should.  Either way, please subscribe to this bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/781445](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/781445)

---

### Post by nash black on 2011-05-14
Ahh thanks. I saw that earlier but I missed the part about the command line that I had been seeing.

I just had to create a new graphics configuration and the new kernel boots up just fine.

Thanks again

Nash

---

