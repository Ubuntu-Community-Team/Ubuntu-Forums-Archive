---
title: "Installing grub"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by keljaden on 2010-05-01
Okay I want know if (and how) to install just grub from like a live CD or something similar.

I plan to install a lot of different OS's (as I like to test and try everything out there.)

The problem I know I will have is boot loaders.  Is there an easy way once I get everything install, just to then install grub?

(btw i am going to try, freebsd, openssuse, fedora(kde), PClinuxOS, BT4, arch, and perhaps chakra)

Sadly windows is going to be on here as well, I need on temporarily until I beat fable (doesn't work in crossover), then I am taking it off.

Hope this is enough info to explain how I need to get grub install. (like off a live CD, or a grub live CD).

---

### Post by garvinrick4 on 2010-05-01
> **keljaden said:**
> Okay I want know if (and how) to install just grub from like a live CD or something similar.

I plan to install a lot of different OS's (as I like to test and try everything out there.)

The problem I know I will have is boot loaders.  Is there an easy way once I get everything install, just to then install grub?

(btw i am going to try, freebsd, openssuse, fedora(kde), PClinuxOS, BT4, arch, and perhaps chakra)

Sadly windows is going to be on here as well, I need on temporarily until I beat fable (doesn't work in crossover), then I am taking it off.

Hope this is enough info to explain how I need to get grub install. (like off a live CD, or a grub live CD).
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by oldfred on 2010-05-01
Also this link:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I have heard that some of those installs do not play nice with others. I think it was opensuse. Some may require primary partitions like windows. So besure to leave a primary or two and install Ubuntu in logical partitions.

---

### Post by keljaden on 2010-05-01
So as long as my last distro that I install is linux I should be fine because I can just download and install grub?  Or can I just install it from any linux live CD (given I have working internet).

If I do it from the live CD will it auto detect all of my installations?

I am hoping there is a (install grub) option in some live distro...where it will just detect all your OS's and the world will be good.

I totally forgot that you can only have 4 primary partitions...are all linux distros okay with being logical?

Also can I have 4 primary on one HDD and then another 4 primary on another HDD while having all 8 OS's show up in grub??

---

### Post by oldfred on 2010-05-02
While this is older and uses old grub it shows the planning required for multiple systems.
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Ubuntu and most linux run from logical partitions without any problems.

---

