---
title: "Mouse, keyboard isn't working"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by sakibmoon on 2011-09-17
So, I just installed ubuntu 10.10. And update was in order. After downloading, setup started. Electricity hampered and PC was off. Now when I boot, my mouse and keyboard isn't working. It works fine on boot menu, but after those two aren't responding. How to solve this problem? I need quick help. I have to send an important file to my friend immediately.

---

### Post by Hakunka-Matata on 2011-09-17
can you boot into your LiveCD/USB installation disc/usb/..........?

---

### Post by sakibmoon on 2011-09-17
Yes, I can boot from Live Usb.

---

### Post by sakibmoon on 2011-09-17
I have found a very good online resource and solved the problem.
check here for repair error or recover ubuntu from live cd: [http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/)

I think this solves problem when the problem is with update or upgrade.

I didn't run upgrade as I didn't want to upgrade. Typed apt-get update, but didn't typed the later and then rebooted and keyboard and mouse is working again.

---

### Post by Hakunka-Matata on 2011-09-17
> **sakibmoon said:**
> I have found a very good online resource and solved the problem.
check here for repair error or recover ubuntu from live cd: [http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/)

I think this solves problem when the problem is with update or upgrade.

I didn't run upgrade as I didn't want to upgrade. Typed apt-get update, but didn't typed the later and then rebooted and keyboard and mouse is working again.

sudo apt-get update
sudo apt-get upgrade

Those two commands update existing installed software, they do not upgrade the operating system to a new release.  I know, it's confusing, it says "upgrade"...........................

---

### Post by sakibmoon on 2011-09-17
Thanks for the information. I didn't know that *upgrade *command update the existing software. I was worried that I might upgrade to Ubuntu 11.04 which I don't want to.

Anyway, my problem was solved even without [I]giving

apt-get upgrade [/I]

command. When I rebooted, I installed updates manually. This command would install the updates from live cd.

---

