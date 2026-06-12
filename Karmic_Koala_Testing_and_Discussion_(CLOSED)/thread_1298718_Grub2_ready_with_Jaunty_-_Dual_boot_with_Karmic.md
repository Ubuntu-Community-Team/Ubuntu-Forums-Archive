---
title: "Grub2 ready with Jaunty - Dual boot with Karmic?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JMFTheVCI on 2009-10-23
I am running Jaunty, and with Grub2, and want to install Karmic in a dual boot mode. I also have Win7 which boots fine from the Jaunty Grub2.

What problems will there be if I install karmic(rc) in another partition? Will the karmic Grub2 pick up my Jaunty(multiple kernels) and Win7? Will it just see the Win7 and ignore the Jaunty partition?

Would like to know what the recovery will be before I start.

---

### Post by philinux on 2009-10-23
> **JMFTheVCI said:**
> I am running Jaunty, and with Grub2, and want to install Karmic in a dual boot mode. I also have Win7 which boots fine from the Jaunty Grub2.

What problems will there be if I install karmic(rc) in another partition? Will the karmic Grub2 pick up my Jaunty(multiple kernels) and Win7? Will it just see the Win7 and ignore the Jaunty partition?

Would like to know what the recovery will be before I start.

Installing Karmic to a partition will result in this error, see link. It complains but it works. It might not pick up your Jaunty install first off so you might have to run sudo update-grub from karmic once it's installed. Same from the Jaunty install.

Mind you if this is all on one disk why not let the karmic install take over by installing grub to the mbr.

I'm in a different boat with two disks
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)

---

### Post by ranch hand on 2009-10-23
You should have no trouble at all if, as said by  phillinux, you run sudo update-grub when you reboot.

As far as recovery goes, if you want to continue to use your Jaunty as boot/root all you need to do is boot into it and run'
```

sudo update-grub

```
and 
```

sudo grub-install /dev/sda

```
editing the "sda" to fit you box setup.

See this thread for some info and a lot of links to grub2 stuff;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

