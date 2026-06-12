---
title: "Edgy on a Promise EX8350 RAID 0"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Inuyaga on 2007-04-04
Ok as far as I can tell the only way to get the install CD to see the RAID 0 on my EX8350 is to compile the drivers from Promise as a module and load them. However thats where im stuck. Anyone got any good directions on how to get the LiveCD to a point where I can compile drivers in it?

Right now this is where I am.
Get the linux-sources package. (wrong version. How do u get a backversion?)
Get m-a which gets /usr/include/sys
attempt to do a make menuconfig.
Fails on ncurses
Attempted to get ncurses-base ncurses-bin and ncurses-term. Dosn't solve the problem.

So right now I need to figure out how to get the sources for linux 2.6.17-10 because im getting 2.6.17-11 atm, another way of getting the incluce/sys files other then m-a, and how to get make menuconfig to work so I can then configure the kernel to sources so I can then run a compile on my driver.

THEN after all that is done I figure im going to have to generate a custom kernel so it will have the Promise drivers included or have a initramfs that has the module in it. I have no good ideas on how to do either in Ubuntu. Any help on doing this would be great!

Thanks,
Inyaga

---

### Post by Inuyaga on 2007-04-04
Ha I figured it out. Problem is it doesn't seem to have helped T_T
Anyway here is the procedure to compile and install the Promise SuperTrak EX8950 source code driver for the Ubuntu 6.10 Edgy liveCD

[COLOR="Red"]NOTE: THIS IS FOR LIVED ENVIRONMENTS ONLY!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR]

1) As soon as the live cd boots BEFORE YOU DO ANTHYING ELSE.
           (Note: important DO NOT DO apt-get update IN ANY FORM)
2) run: apt-get install apt-get install linux-source-2.6.17
3) edit your /etc/apt/sources.list to include 
```
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

```You should just be able to uncomment these lines.
4) run: apt-get update
5) run: apt-get install module-assistant
6) run: m-a prepare
7) run: cp /boot/config-2.6.17-10-generic  /usr/src/linux-source-2.6.17/.config
8) run: make mrproper
9) run: make modules_prepare
10) run: cp /boot/config-2.6.17-10-generic  /usr/src/linux-headers-2.6.17-10/.config
11) run: cp /usr/src/linux-source-2.6.17/scripts/mod/modpost /usr/src/linux-headers-2.6.17-10/scripts/mod/

12) download the promise drivers from the promise website. You want the SuperTrak EX8350 -> Driver -> Other : ST EX163x0/EX83x0/EX12350/EX4350 Windows driver
13) unpack the driver
14) cd into the driver source directory.
15) If you are running a x86_64 system you need to follow these next steps
--- x86_64 ONLY
1) nano -w Makefile
2) find ```
ifeq ($(strip $(CONFIG_AMD64)),y)
       ARCH_TYPE=x86_64
else
       ARCH_TYPE=i386
endif
```
replace with
```
ARCH_TYPE=x86_64
```
3) Save
-- end x86_64 ONLY
16) run: make KERNEL_SOURCE_DIR=/usr/src/linux-headers-2.6.17-10
17) if you see errors check and make sure you completed the previous steps...
18) run insmod stex.ko

At this point you should have a successful driver load.

Now if I can figure out how to get my drives to load; I gotta figure out how to get this driver in a install so I can boot.

---

