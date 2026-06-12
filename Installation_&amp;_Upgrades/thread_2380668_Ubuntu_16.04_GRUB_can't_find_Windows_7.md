---
title: "Ubuntu 16.04 GRUB can't find Windows 7"
date: 2017-12-20
forum: Installation &amp; Upgrades
---

### Post by malinchekurov on 2017-12-20
Hello everybody,

I know this is a duplicate question, but since none of the other solutions worked for me I decided to open a new thread.

Basically I had Windows 7 running and I decided to install Ubuntu 16.04 along, I followed all instructions very carefully (shrunk windows partition using windows tools, made new partitions for home and swap for ubuntu from new newly freed space, and under the "Device for boot loader installation I chose /dev/sda ATA<something here>.

Everything was going according to my plan :), until I had to restart and see the windows option was missing from the boot menu.
I have been looking for 3 days on the forums and I have tried everything. I have tried fdisk -l and checked the windows is there and then update-grub. I have ran boot-repair too and this is what it says:[https://paste.ubuntu.com/26220713/](https://paste.ubuntu.com/26220713/).
 I restored the windows boot loader and also tried to add linux entry to the windows boot loader using easyBCD, I got the Linux and Windows options in the boot menu, but then ubuntu won't boot.
So far nothing worked for me.
When I restore the windows boot loader, then only windows boots with no options, then when I repair the GRUB using boot repair I get only ubuntu in the boot menu.
I didn't imagine it will be so hard for the boot loader to find all OS and boot them.
Any help will be highly appreaciated as I am on the edge of insanity by now:).

---

### Post by mastablasta on 2017-12-20
what happens if you select the GRUB entry: FreeDOS (on /dev/sda1)  ?

it should run the windows boot loader.

---

### Post by malinchekurov on 2017-12-20
Wow I am an idiot! It really does run the windows! Thank you so much!
So end everything was working fine all that time and I had no idea :).

---

