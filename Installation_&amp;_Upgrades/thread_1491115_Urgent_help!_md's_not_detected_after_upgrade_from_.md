---
title: "Urgent help!: md's not detected after upgrade from 8.04 -&gt; 10.04"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by sean.clarke on 2010-05-23
Hi,
    I've got a problem thats making me bang my head against a  wall!

I've upgraded a P4 system from 8.04 to 10.04 and it hangs on boot saying it can't find root (/dev/md0).

ALERT: /dev/md0 does not exist

I've added rootdelay parameters in case it was a timing thing and cat /proc/modules shows raid1 etc. (although no md ??).

I noticed the md and raid1 modules weren't in the /etc/modules and /etc/initramfs-tools/modules - so i added them and did a:

mkinitramfs -o <name> 2.6.32-22-generic

and still no joy

Oddly at the initramfs prompt when I type "reboot" I see it flash up with syncing md devices (or similar) just my /dev/md0 and /dev/md1 are not in the /dev partition (although the individual devices are - /dev/sda1 etc.).

Any ideas? I am up against a deadline on this one, so any assistance would be greatly appreciated.

Many thanks
Sean

---

### Post by dino99 on 2010-05-23
cant help much but the problem seem to be "md0", maybe look for other naming

[http://www.google.com/search?client=ubuntu&channel=fs&q=raid%2Blucid&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=raid%2Blucid&ie=utf-8&oe=utf-8)

---

### Post by sean.clarke on 2010-05-23
Don't think so...

When I get to the initramfs prompt, if I do a :

mdadm --assemble --scan

it detects and builds md0 and md1

I can then do a CTRL-D and it continues...

The system is still in a poor state, I get the Ubunt splash screen, but the dots cycle forever - although if I go into another virtual terminal I can do a :

service gdm start

and I can now login and use the system.

Can't see why I cannot get it to boot....

---

