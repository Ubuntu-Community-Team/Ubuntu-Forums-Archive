---
title: "how do i upgrade 10.04 without just getting the newest distro"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by tbrownarcher on 2013-06-24
Hello:

I have linux ubuntu 10.04 .  It's a fresh install.  How do i upgrade that install without just going out and getting a newer distro?  

and also if the upgrade does not involve Java how do I get Java on the machine too.   I'm use to linux mint and synaptic (by no means fluent)  but i can't find anything similar here .

Thanks,
Nate

---

### Post by sanderj on 2013-06-24
Why did you do a fresh install of 10.04? Why not 12.04 or 13.04?

---

### Post by papibe on 2013-06-24
Hi tbrownarcher.

Is this a server edition?

If so, you just do the regular commands for an upgrade:
```
sudo apt-get update

sudo apt-get upgrade
```
In case you are upgrading the kernel (usually to pass from 10.04.3 to 10.04.4 for instance), you may need to do this instead:
```
sudo apt-get update

sudo apt-get dist-upgrade
```
Note: none of these commands would upgrade your system to another release (10.10, 12.04, etc).

Let us know how it goes.
Regards.

---

### Post by snowpine on 2013-06-24
Your simplest and cleanest option is to do a fresh reinstall of a supported release such as 12.04 following these easy 1-2-3 instructions: [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

If you are running a server and not a desktop/laptop, then see papibe's instructions above (but you might consider moving to 12.04 at some point, unless you specifically need the aging 10.04 for some reason, such as legacy application support).

---

