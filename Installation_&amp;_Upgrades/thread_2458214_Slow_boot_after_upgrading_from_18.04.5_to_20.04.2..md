---
title: "Slow boot after upgrading from 18.04.5 to 20.04.2.."
date: 2021-02-19
forum: Installation &amp; Upgrades
---

### Post by Furycd001 on 2021-02-19
HI Guys..

Upgraded from xubuntu 18.04.5 to 20.04.2 through the terminal with **sudo do-release-upgrade --allow-third-party**.
Everything went fine apart from I'm now getting a really slow boot time & unresponsive desktop for a minute or so after logging in. Ran **systemd-analyze blame **& got [this output]("https://termbin.com/7odv"). Could someone please help me speed up my boot time & get my desktop to be more responsive after logging in, instead of having to wait around. I've already checked my auto-start & everything unessential has been unchecked already.

Many thanks in advanced....

---

### Post by ActionParsnip on 2021-02-19
If you run:
```

dmesg -T > /tmp/boot.txt; gedit /tmp/boot.txt

```
You can see the boot, look for large gaps in time and this will help identify the slowness

---

### Post by Furycd001 on 2021-02-19
Thanks for the command & for the heads up. Just ran it & got [this]("https://termbin.com/lkhp") output. The slowness appears to be around the very bottom. Looks like snap & virtualbox. The only snap I have installed in chromium, but don't really use it all that often. Was having some bother with virtualbox which I'd manually installed from a deb a while back. I uninstalled & then reinstalled from the ubuntu repos so that might fix those messages during boot (not sure tho :?).

---

### Post by oldfred on 2021-02-19
A variety of things to try.

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by Furycd001 on 2021-02-20
> **oldfred said:**
> A variety of things to try.

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

Thanks for those links. Helped a lot. Going to mark this thread as solved....

---

