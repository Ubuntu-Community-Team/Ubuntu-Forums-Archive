---
title: "Computer Restarts after pressing &quot;Install Ubuntu&quot;/&quot;Try Ubuntu without Installing&quot; Opt"
date: 2017-07-04
forum: Installation &amp; Upgrades
---

### Post by prassi007 on 2017-07-04
I am trying to dual boot my laptop with Ubuntu 14.04 alongside Windows 10.
But, when i press install ubuntu on my laptop, from a live Usb.
The Ubutu loading screen with those dots pops up, and suddenly the system restarts, not even entering the setup.

My laptop:
Dell Inspiron 3543
Processor: Inter Core i5 5th gen
GPU: Nvidia 820m
OS: Windows 10
8gb Ram

Thanks in Advance.

---

### Post by yancek on 2017-07-04
The site below is the official documentation on dual booting Ubuntu with windows 10 so I would suggest reading through it before trying again.  You may have to change a setting in the BIOS so that it install UEFI which is in all likelihood what windows 10 is.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by prassi007 on 2017-07-04
Yeah, i read all that, and tried all possible ways to install. Still no luck. The computer just turns off suddenly

---

### Post by Bucky Ball on 2017-07-04
Welcome. Any reason you're not going for the newer long-term release 16.04 LTS? You might get a different result.

So, you're booting from your install media, clicking the 'Try Ubuntu' icon on the desktop and the machine turns off?

You have tried all possible ways, but which way are you trying now?

---

### Post by prassi007 on 2017-07-04
I actually want Ubuntu to run Ros-indigo. Which works only on, 14.04.

The laptop switches off when i press install ubuntu from the grub menu. I ve tried all sorts of media. Live usb and dvd. Nothing seems to work.

---

### Post by Bucky Ball on 2017-07-04
[Here you go]("http://wiki.ros.org/lunar"). Works fine on 16.04 with the latest release. [And here]("http://wiki.ros.org/lunar/Installation").

---

### Post by prassi007 on 2017-07-09
Ok, So after retrying a lot of times, i was able to Install ubuntu 14,04 and it worked properly.
But the problem is, when i want to boot ubuntu after shutting down, the same thing happens , after i choose to boot ubuntu.
It doesnot even go to the loading screen, just a purple background comes, and then laptop restarts.
Only once in lot of retries, it booted twice.
What might be the problem?? is it a hardware issue

---

