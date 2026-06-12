---
title: "Can't Install Ubuntu on My toshiba"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by Lyrik on 2011-12-29
HELP!!!
I have a Toshiba Satellite
it has an A6 Vision AMD processor 
its quad core and has a RADEON graphics card
it is running Windows 7 currently :P

I have a bootable version of ubuntu 11.04 on a flashdrive, I used the program that the ubuntu website suggested to make it.
I also have a live cd I created by burning the .iso to it.

Whenever I try to load either one it will go to a familiar screen

it has a battery logo and a little man icon at the bottom of the screen, it will then ask me if I want to install or just try it out, if I click just try it out it will begin to load and then the screen will go black and nothing will happen, even though my laptop sounds like its doing wok and loading stuff.

I have installed ubuntu on my own computer many times, but I have never encountered this problem. (This is my friends laptop).
I have tried both 32 bit and 64 bit the result is the same

---

### Post by darkod on 2011-12-29
The A6 is a new CPU and I think the driver for the video is not present yet in ubuntu. I don't know if I can find the thread, it was mentioned which parameter to use to boot correctly.

---

### Post by samigina on 2011-12-29
Isnt this one: radeon.modeset=0?

One bug about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)

---

### Post by darkod on 2011-12-29
> **samigina said:**
> Isnt this one: radeon.modeset=0?

One bug about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)

Yeah, I think it was that one.

---

### Post by fasote on 2012-03-01
Then what is the solution - have the exact same and had rather have a social disease than ANY MICROSOFT PRODUCT....have to have unbuntu or similar.....

---

### Post by darkod on 2012-03-02
> **fasote said:**
> Then what is the solution - have the exact same and had rather have a social disease than ANY MICROSOFT PRODUCT....have to have unbuntu or similar.....

According to the bug report one solution is this:
When you first boot, you have select the grub entry (press shift while  booting if it doesn't show) and press 'e', then add the word 'nomodeset'  to the end of line that has the kernel arguments. The graphical display  manager will fail to start, but you can ctrl+alt+f1 to drop to a tty.  Login and: sudo apt-get install fglrx && sudo reboot
It worked for me, but I hope it gets fixed by 12.04

Also that bug report confirms it has been solved for 12.04 LTS (although this is still in Beta 1 and is due to be released in late April).

You can try the above procedure if it works for you too.

---

