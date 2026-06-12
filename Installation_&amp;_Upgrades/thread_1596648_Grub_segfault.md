---
title: "Grub segfault"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by jacobandreas on 2010-10-14
Grub wasn't upgraded properly when going from 10.04 to 10.10 -- it segfaulted when trying to install. I let the installer proceed with the rest of the upgrade, but I still can't get grub to install properly and I'm worried that it's left me without a working bootloader.

I've tried purging and reinstalling grub-pc and grub-common, but whenever I run

```
sudo grub-install /dev/sda
```

or

```
sudo grub-setup /dev/sda
```

I get a segfault. Additionally, trying to run
```
sudo update-grub
```

I get

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Segmentation fault
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
done

```

I'm now afraid to restart my computer. If anybody knows what's going on I'd really appreciate it.

For reference, my hard drive is set up with:
1 real partition (with /)
1 virtual partition (with swap)

---

### Post by dabl on 2010-10-14
Here's help:

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

[http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub2)

---

### Post by jacobandreas on 2010-10-14
Was hoping I wouldn't have to make myself a new live CD to do this. Oh well....

Thanks for the help.

---

### Post by drs305 on 2010-10-14
For the update-grub problem, the error might be occurring as the 30_os-prober script is run. It's segfaulting after finding 35 so it could be faulting once os-prober is invoked. 

Possibly it's having difficulty with your virtual swap partition. As a test, you could try disabling (remove the executable bit) from /etc/grub.d/30_os-prober. That might let update-grub run, if there is 'enough' of grub-pc installed in the first place.

---

### Post by guy-rouillier on 2010-12-06
I also got a segmentation fault when upgrading from 10.4 to 10.10.  I got two, actually: one with grub and the other with Samba.  Both were asking me if I wanted to update the conf file, and offered me a drop-down list of choices.  When I clicked the arrow on the drop down list, I got the segmentation fault.

Fortunately for me, both appeared to have installed okay; my system works anyway, and claims to be running 10.10.  The only problem I'm having is with Update Manager; when I click the Check button, it hangs.

I was searching the forum for "upgrade segmentation fault" when I found your topic.

---

