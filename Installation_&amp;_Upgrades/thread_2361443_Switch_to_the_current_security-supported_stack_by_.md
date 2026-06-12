---
title: "Switch to the current security-supported stack by running"
date: 2017-05-16
forum: Installation &amp; Upgrades
---

### Post by jeff113 on 2017-05-16
Hello,

Our production server is running 14.0.4.5 LTS. It hosts Wordpress, mediawiki, and OSTicket. I have been getting the warning:

**WARNING: Security updates for your current Hardware Enablement Stack**
**ended on 2016-08-04:**
** * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)**

**To upgrade to a supported (or longer-supported) configuration:**

*** Upgrade from Ubuntu 14.04 LTS to Ubuntu 16.04 LTS by running:**
**sudo do-release-upgrade**

**OR**

*** Switch to the current security-supported stack by running:**
[B]sudo apt-get install linux-generic-lts-xenial linux-image-generic-lts-xenial
[/B]
I would rather not upgrade to 16.0.4 yet. While I have backed up Wordpress, mediawiki, and OSTicket by copying directories and exporting databases I'm still fearful of upgrading to xenial, the currently supported stack.

1. Am I being overly cautious about upgrading to linux-generic-lts-xenial linux-image-generic-lts-xenia. Are the chances high that something could go wrong?
2. Is this the right command to run [B]sudo apt-get install linux-generic-lts-xenial linux-image-generic-lts-xenial ?
[/B]3. I would be doing this after hours remotely. Any problem there?

I realize I do have suedo backups but having to do a clean install and importing, etc. is a real pain.

Again, am I being overly paranoid about this?

Thanks,

Jeff

---

### Post by deadflowr on 2017-05-16
Do the second option and install the lts-xenial hardware stack.
Adding:
I think you only need the linux-generic-lts-xenial package.
That will bring in both the image and headers packages.

---

### Post by jeff113 on 2017-05-16
Is this a major operation or am I just paranoid? What are the chances of this failing?

Thanks,

Jeff

---

### Post by deadflowr on 2017-05-16
No more a major operation than installing a regular kernel update.
Since you will still have the currently in use kernel as a fallback, if the upgrade goes belly up, you still have the ability to boot the older kernel.
Albeit the older kernel will be the out-dated kernel, it will at least allow you to boot and figure out things if the new stack is bonked out.

I would think the chances of a failure, though, are slim.
slimmer still, on a server compared to a desktop, which can go belly up based on it also needs to upgrade the Xserver packages.

---

### Post by jeff113 on 2017-05-16
Thanks for the reassurance. I'll go ahead and run it tonight. Booting to the older kernel is accomplished by selecting it at the beginning of the boot, the menu that flashes by quickly right?

Thanks,

Jeff

---

### Post by jeff113 on 2017-05-17
Thanks deadflowr,

Ran the update last night without a hitch. Your input was truly appreciated.

Jeff

---

### Post by deadflowr on 2017-05-17
Sounds good.
Something to perhaps look into is if you require a system with minimal downtime (shutdowns, reboot, etc) 14.04 has the ability now to install the snap packages for the canonical-livepatch mechanism.
[https://www.ubuntu.com/server/livepatch]("https://www.ubuntu.com/server/livepatch")
This only works currently on the xenial kernel (4.4 series), which is what you would be running now.
It also requires installing the snap packages.

Not that you need or should do this, just something you can keep in your back pocket.

---

