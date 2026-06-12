---
title: "Updated kernel, grub problems"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by h3r0 95 on 2009-12-17
hello my name is David, I'm Italian, I am a new member, I have a problem with ubuntu ... as I connect to the Internet using key, and Ubuntu 9.10 I did not read, I even recognize it as a USB, I was advised to upgrade the kernel .... unfortunately did not go as planned ... just completed the updates told me to reboot and start I get this in writing:
Manimal bash-like line editing is supported. For the first word, TAB lists possible command completions.anywhere else TAB lists possible device / file completions.
sh: grub >...( I enter a word or a text I think ...) ah I installed ubuntu with Wubi ... I hope you can help me ... thanks

---

### Post by darkod on 2009-12-17
At that sh:grub prompts you are getting execute this commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

Depending on which partition you have wubi installed you might need to change /dev/sda1 with /dev/sda2, /dev/sda3 (second, third partition on the drive, etc).

After you do that and you boot wubi, open terminal (in Applications-Accessories) and execute:
sudo update-grub2

That should solve it.

---

### Post by h3r0 95 on 2009-12-18
I try to type in commands but after a few seconds the computer restarts automatically and not have the time to fill it .... there's a way not to restart it so that you have the time to act?

---

### Post by darkod on 2009-12-18
I don't know, the restarting should not be related to ubuntu. If you don't have any important data on your wubi, load windows and remove wubi with add/remove programs, like any windows app.
After that either install wubi again, or the better option is to install full ubuntu on its own partition and filesystem, as dual boot with windows.

---

### Post by h3r0 95 on 2009-12-18
ok at this point the best option is to install ubuntu ... I fully explain how you could do? and then install it to completely resolve the problem?[IMG]http://www.google.com/images/cleardot.gif[/IMG]

---

### Post by darkod on 2009-12-18
Look at the tutorial here to get an idea:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by h3r0 95 on 2009-12-18
ok ok but before we do let me know if it solves the problem doing as I've recommended you ... I know that Wubi uninstalled and reinstalled but the problem persists ... still install completely resolve? thanks for you patience with me ... XD

---

### Post by darkod on 2009-12-18
Well I can't guarantee anything but as far as I know the sh:grub> error is mostly present in wubi, not in full ubuntu. There is very big chance that you will not see this error in full ubuntu.
If you decide to install full ubuntu, remove wubi first if you still have it on the computer.

---

### Post by h3r0 95 on 2009-12-18
k ... but a friend of mine told me to install ubuntu overflow, where the computer format .. (because it says that I must divide 's HD 2 partitions from there ...) I'm not sure of being able to revive the PC after it was formatted ... so there's another way to create 2 partitions?

---

### Post by darkod on 2009-12-18
It will not format the whole hdd. If you have only one drive it will just resize the windows partition to create space for the ubuntu partition. You will have the option to select how to divide it, how much space to be left for windows and how much for ubuntu.
Do not use the option Erase and use whole drive, that will erase all your data.

---

### Post by h3r0 95 on 2009-12-18
ok ... I might explain in simple terms how to do? thanks!

---

### Post by darkod on 2009-12-18
The screenshot in step 4 should look like the attached. You can slide the gray bar left/right to adjust how much space to be left for windows, and how much to be dedicated for ubuntu.
Note that you will not have so many colors on the bottom bar on your computer, this is just example. You will probably have one color for windows, then the gray slider, then one color for ubuntu.

---

### Post by h3r0 95 on 2009-12-18
well how do I take the screenshot from windows??

---

### Post by darkod on 2009-12-18
You don't need to take any screenshots. I'm just showing you an example what the screen looks like in step 4 when you are selecting how to install ubuntu next to your windows.

---

### Post by h3r0 95 on 2009-12-18
ok

---

### Post by hunterman439 on 2009-12-18
Darkod's first post worked for me, but it took a few times to type everything just right and figure out which sda the disk was in. Thanks a lot, this was really frustrating

---

