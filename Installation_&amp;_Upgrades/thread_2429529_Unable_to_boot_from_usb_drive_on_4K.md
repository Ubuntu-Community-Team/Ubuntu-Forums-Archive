---
title: "Unable to boot from usb drive on 4K"
date: 2019-10-19
forum: Installation &amp; Upgrades
---

### Post by manujchandra on 2019-10-19
Hi,

I am trying to install Ubuntu 19.10 on a Dell Precision 5510 which has a 4K screen. I have / am using PopOs 19.04 and Elementry Juno without problems.

When I boot from usb drive and choose "Try Ubuntu without installing", I get the error:

error: out of memory

and then nothing happens and I have to hard boot.

Upon serching I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1842320](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1842320)

Is there any solution how I can boot fom UBS drive and install Ubuntu 19.10?

Thanks.

P.S:

I tried with safe graphics today. Same error. I got an out of memory error followed by kernal panic. Had to hard reboot.
I wonder if Canonical will release a new iso with the fix. Any other suggestions are welcome.

---

### Post by Skaperen on 2019-10-21
my guess is that a device driver for some device that both Dell and HP use has a memory corruption bug.  that kind of bug can cause many kinds of misleading errors including miscalculation of memory requirements (by overwriting a number involved in the calculation).  these kinds of errors are especially difficult to solve because the symptom typically happens long after the bad code has run.  i doubt 4K is the issue (although that remains a possibility).  i can only suggest stay with 19.04.  if you need to use some software from 19.10, your options include a backport or putting 19.10 in a VM or container (as long as all 19.10 software can run in the earlier kernel).  a lot of people here are running 18.04 LTS.

---

### Post by manujchandra on 2019-10-24
Hi, thanks for responsing.

I tried Pop OS 19.10 and it worked. So I guess they have either fixed the problem, or something specifically amiss with the Ubuntu iso image. Hope Ubuntu could fix the problem soon.

Regards,

---

### Post by piotr-czarny on 2019-11-12
I had the same error on XPS 15 9550 with a 4K display.

I found a solution. After burning the Ubuntu ISO with the installer to the USB-media there is a file /boot/grub/grub.cfg on the USB media.

Open this file in a text editor and change gfxmode=auto to gfxmode=800x600

Save the file and boot from USB.

---

