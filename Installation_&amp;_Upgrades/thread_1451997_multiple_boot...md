---
title: "multiple boot.."
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by dedemith on 2010-04-11
first, this's for the first time i upgraded my ubuntu...
coz i still newbi, i just upgraded all the components that ubuntu provided for us.. after that i installed all the components..
N what made me confused's when i restarted my laptop there're 4 boot mode alternatives.. n i did'nt know why it could happen..
my question's can i delete some boot mode alternatives in order to have only one boot mode?

---

### Post by coffeecat on 2010-04-11
> **dedemith said:**
> when i restarted my laptop there're 4 boot mode alternatives.. n i did'nt know why it could happen..

After the update, there will be two versions of the kernel: the original that came with the installer and a later version that came with the upgrades. For each kernel version, there will be two grub menu options: boot in normal mode and boot in recovery mode, which will take you to a root console (text only).

This is normal. After you've been running (K)ubuntu for some time, you may collect several kernel versions with two menu entries for each. If it worries you (it doesn't do any harm), you can uninstall the older kernels with the package manager. This will remove menu entries automatically. But it's a good idea to keep the immediately preceding kernel version in case you experience problems with the latest version.

---

### Post by dedemith on 2010-04-11
do you mind if u give me instructions step by step?? coz i still newbi...

thanks before...

---

### Post by coffeecat on 2010-04-11
> **dedemith said:**
> do you mind if u give me instructions step by step?? coz i still newbi...

Do you mean to uninstall the unwanted kernel? Because I would advise you not to do that yet. You have two versions of the kernel. Keep them both - they don't take up much room on the hard drive, and unwanted files and apps don't slow Linux down. It's not Windows! :)

Anyway... you're using Kubuntu which has a different package manager from Ubuntu, which is what I'm used to. So I can't give you detailed instructions - I haven't used the Kubuntu version of Ubuntu for quite some time. What you could do is to look in the /boot folder of your filesystem. You'll see a number of files with (if you're running Karmic 9.10) numbers such as 2.6.31-14, or 2.6.31-20. These are kernel version numbers, the higher the number the later the kernel. If you wanted to uninstall the 2.6.31-14 kernel, for example, you'd simply search the package manager for all installed packages with '2.6.31-14' in the package name and mark them for uninstallation. There's usually 3 or 4, if I remember correctly.

But beware. It is quite possible to uninstall every single kernel while still running. I've done it! (On purpose :wink:) Which would make your system unbootable if you decide to reboot before reinstalling a kernel. Not for newbies! :p

---

### Post by dedemith on 2010-04-11
ok... thanks 4 giving me informations... hihi...:)

---

