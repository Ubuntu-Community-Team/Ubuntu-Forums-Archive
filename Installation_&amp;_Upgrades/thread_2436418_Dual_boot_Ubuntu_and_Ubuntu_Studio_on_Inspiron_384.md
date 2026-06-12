---
title: "Dual boot Ubuntu and Ubuntu Studio on Inspiron 3847"
date: 2020-02-06
forum: Installation &amp; Upgrades
---

### Post by ChrisMacor on 2020-02-06
I've got both ubuntu 18 64 bit and Ubuntu studio 19 64 bit on an Inspiron 3847 Desktop.
The issue is I can't figure out how to boot into Studio. It's booting up into Ubuntu by default.
Thanks for your help,
Christopher

---

### Post by CelticWarrior on 2020-02-06
First thing to try: In Ubuntu open terminal and run ```
sudo update-grub
```. Reboot.

If the Grub menu still doesn't show up or hasn't an entry for Ubuntu Studio: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Use the 2nd option to install Boot Repair but DO NOT run any fix. Instead use the "Create a Bootinfo summary" button and post here the resulting URL.

---

### Post by ChrisMacor on 2020-02-08
Hi Celtic Warrior,
Thanks so much for your help! That got the boot window available.
Sorry for the delay. I suspect my account wasn't entirely verified so I got no email notification of your response.
Thanks again,
Christopher

---

### Post by CelticWarrior on 2020-02-10
You're welcome :p

Please keep in mind that the 2 Ubuntus will work concurrently with Grub. Each time one updates it takes over Grub.

---

### Post by hk42 on 2020-02-13
Hi
I installed ubuntu studio over my normal ubuntu.
At boot Grub gives you the choice between the normal kernel and the low latency one.
They both get updated at the same time.
It doesn't use much disk space as 2 partitions would.
But I'm not a great user of studio applications so there may be drawbacks.
For example if you have a CPU hungry application in the background of your normal ubuntu set up.
This could probably be solved by a script to disable such application.

---

