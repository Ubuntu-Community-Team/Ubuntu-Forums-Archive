---
title: "Removed old kernels *BEFORE* upgrading"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by Freckweb on 2014-12-31
I upgraded to 14.04 yesterday. All went well until '4 minutes' from the end. During the tidy-up phase, old kernels seem to be removed one at a time. Unfortunately, I had a lot of old kernels and the process terminated after a dozen or so (it took about an hour). Following reboot, I was left with a command prompt login running an ancient kernel.
The fix is to remove all the old kernels and update grub.

Remove old kernels:

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

Update grub menu and reinstall boot sector:

update-grub
sudo grub-install /dev/sda (this installs it in the mbr)

reboot
The problem I experienced can be avoided by tidying up before the upgrade i.e. run the dpkg command before starting the upgrade.

---

### Post by bapoumba on 2014-12-31
For refs please see here : [http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648)

---

### Post by schragge on 2014-12-31
Hmm, please be aware that while this solution works as expected on older Ubuntu releases (lucid and precise), it may remove more packages than was intended on newer releases (starting from trusty). The culprit is multiarch-support (see [https://wiki.debian.org/Multiarch](https://wiki.debian.org/Multiarch)). Newer *dpkg -l* versions may include architecture in their output of package names. E.g. with
```

dpkg -l linux-\*|sed '/^ii /!d;s/^.. *\([^ 0-9]*[^ ]*\).*/\1/;/'"`uname -r`"'/d;/[0-9]/!d'

``` on my system I get
```

linux-headers-3.16.0-25
linux-headers-3.16.0-25-generic
linux-headers-3.16.0-28
linux-image-3.16.0-25-generic
linux-image-extra-3.16.0-25-generic
[COLOR=red]linux-libc-dev:i386[/COLOR]

```
Note the package I marked in [COLOR=red]red[/COLOR]. E.g. nvidia-331/nvidia-304/fglrx-core packages depend on this one. Don't forget that there are also packages named like linux-headers-3.0, linux-image-3.0, linux-source-3.16.0 that also would get selected by the sed expression above.

That's the danger of resurrecting old recipes from 2011.

But you may ask what's my solution? [post=13186077]This[/post].

---

### Post by bapoumba on 2014-12-31
Thanks schragge, updating my notes. I have an older -386 machine and have had no issue so far, but running a pure 386 install :)

---

