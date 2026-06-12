---
title: "Can't run live session of Feisty..."
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by IAmMe1 on 2007-08-19
First off, I'm a newbie to Linux. I've never run it before, and I'm trying to install Feisty. Anyways, here's my problem:

I have a Feisty live CD, which works perfectly well on another household computer. However, when I try to run it on mine, after selecting the default boot option, I see the Ubuntu loading bar, and then receive the following message:

/bin/sh: can't access tty; job control turned off

After this, I get the following a couple of times:

(initramfs) [ (numbers that change each time, it's not consistent at all)] ata2.01: failed to set xfermode (err_mask=0x4)

This repeats about 3-5 times, though sometimes it reads "ata2.00" and sometimes "(err_mask=0x40)", but then after that repeats a couple of times, it stops booting. The screen just doesn't change.

I've tried making it not run in quiet mode, and it usually stops at a line (that I didn't write down) that says something about my CD drive (I believe that it's a line where it has recognized my CD drive?).

Are these error messages even the important pieces of information? Am I missing something?

By the way, I'm going to be installing Ubuntu on the same HD as Windows... If that helps...

Thanks for the help.

---

### Post by jrusso2 on 2007-08-19
This appears to be a bug with some hardware in Feisty that was never resolved.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)

---

### Post by IAmMe1 on 2007-08-19
...Joy. So it basically appears that I can't run 7.04 on this machine, period.

*sigh*

---

### Post by jrusso2 on 2007-08-19
If you read the thread some people got it working but it takes some fooling around.

---

### Post by drvista on 2007-08-19
i am having the same problem

---

### Post by gigaferz on 2007-08-22
iam trying to do a clean install, and it doesnt work either....it is better to wait until the next version....

mmmhh,,,  i found a thread with a similar problem but different error messages...

i tried it and it booted on the livecd,,,now ill find out if it'll install

the " workaround" is to put a floppy  right after you press enter to start or install ubuntu, wait for about 3 minutes and  it worked....

it could help you ....

but do NOT install ubuntu if it i giving you errors, youll get them with you.....

---

### Post by deoxyna on 2007-09-03
im also a newbie but i hope this one helps. just added in boot option 'noapic nolapic' and it worked fine.

---

