---
title: "D-Link USB wireless no longer connects with lates kernels"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-07-09
Is anyone else having trouble with wireless USB sticks not connecting with the latest kernels? I can connect ok with earlier kernels but the last two kernels do not activate the usb stick properly. Wireless networks are detected but no connection is made.

---

### Post by woodbj on 2009-07-09
I'm having the same problem with a Belkin 54g USB stick, but luckily I haven't removed the old 2.6.30 kernel, so I just use that one instead until the problem is fixed

---

### Post by andyrogers2008 on 2009-07-09
This something that Iam also expericing with my Edimax USB Stick.

I have opened a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417) for my problem.

Found the same as reverting to 2.6.30 Kernel solves the problem.  Wounder if it is a problem upstream or just linked to Ubuntu.

Andy

---

### Post by budluva04 on 2009-07-09
im pretty sure its a problem wtih all usb devices and udev in the .31 kernel...no working usb cam here on .31, but works good in .30

---

### Post by gwenn on 2009-07-09
Have you tried to remove the wifi driver?
My usb stick Dlink works by default.

---

### Post by Peter09 on 2009-07-11
Was hoping the latest kernel release would fix this - but evidently not.

---

### Post by DougieFresh4U on 2009-07-11
I am having NO problems USB and D-Link.
Also, I am using 5 USB devices at the present time and all are functioning as should.

---

### Post by Peter09 on 2009-07-13
OK - to try again,
Am I the only one with this problem or is there an actual problem in there somewhere  :???:

---

### Post by andyrogers2008 on 2009-07-13
Iam still having the same problems, someone has taken note of my bug report on Launchpad, so we shall have to wait and see.

On Intrepid, Januty I did not have any problems no need to messa round with drivers.  All worked out of the box on a fresh install & upgrade.

I get this same problem on either a clean install or upgrade.

Andy

---

### Post by andyrogers2008 on 2009-07-15
Andy Whitcroft has kindly looked at this problem of mine now and posted some test kernels for me to test here:-

[http://people.ubuntu.com/~apw/lp396417-karmic/](http://people.ubuntu.com/~apw/lp396417-karmic/)

If anyone else with a similar would like to try these Kernel's then please do as I won't be able to test these until tonight.

> @Andy Rogers -- ok I have put together a patch for the semantic issue,
and build a test kernel with it applied.  If you could test this kernel
and report back here that would be very helpful.  The kernel is at the
URL below:

   [http://people.ubuntu.com/~apw/lp396417-karmic/](http://people.ubuntu.com/~apw/lp396417-karmic/)

** Changed in: linux (Ubuntu)
      Status: In Progress => Incomplete


--
Edimax Wireless USB Dongle Failure Karmic Kernel 2.6.31-X
[https://bugs.launchpad.net/bugs/396417](https://bugs.launchpad.net/bugs/396417)
You received this bug notification because you are a direct subscriber
of the bug.


Status in The Linux Kernel: New
Status in “linux” package in Ubuntu: Incomplete

---

### Post by andyrogers2008 on 2009-07-15
Test kernels work fine now for my Wireless Device.

---

