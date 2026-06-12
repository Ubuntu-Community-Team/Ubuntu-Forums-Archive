---
title: "boot failure dell inspiron 530S"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by enderuub on 2007-12-15
Anyone else have this problem?

I have a fairly new Dell Inspiron 530s (intel core 2 duo).
I tried to boot the 6.06 live ubuntu CD.
I reached the point where it says mounting filesystem.... and that's it.  Nothing more happened after that.  This is quite early in the boot process from what I recall.  I also tried using the 'safe graphics mode' option, and it was the same problem.

Anyone know if it would work better with 7.10, or is it more likely a problem with my CD-drive ?

---

### Post by azimuth on 2007-12-15
Before I would suspect your cd-drive, you need to check the MD5 for your .iso. A corrupted download is more what it sounds like.

---

### Post by enderuub on 2007-12-15
actually I've used the same CD successfully on another PC recently

also I should clarify that the CD-drive seems to work fine with Windows, so I don't think there's anything wrong with the hardware

I suspect a compatibility issue

---

### Post by azimuth on 2007-12-15
> **enderuub said:**
> actually I've used the same CD successfully on another PC recently

also I should clarify that the CD-drive seems to work fine with Windows, so I don't think there's anything wrong with the hardware

I suspect a compatibility issue

I think you are on the right track. A later version (7.10), may come closer to matching the hardware in a model such as the 530s. The 16 months between 6.06 and 7.10 is a lifetime in the computer world. Atleast it's no harm, no foul to try another liveCD version.

---

### Post by k_n_murthy on 2007-12-16
I have a dell 530s inspiron. I have tried to install ubuntu-6.06-server amd64.iso and also tried ubuntu 7-04-server-i386.iso. I have seen similar problem.

Later I have tried with Ubuntu7.10-server-amd64.iso. This time installation was fine, But at the time of rebooting I saw couple of error messages on screen and finally the system got in to initRAMFS mode. If I try booting 10 times by resetting the system, one time I was successful.
Here is the information on the errors which I am seeing on the console.

when it fails to boot
loading please wait
[20.377810] irq19. Nobody cared (try booting with irq poll option]
[20.377917] handlers
[20.377947]<ffffffff88043cd07](usb-hecd-irq+0x0/0x60>(usbcore)
[20.378140]DisablingIRQ#19
[20.716188]
[50.716188]
[50.549920] ata1.00:failed to set xfer mode(err_mask=0x40)
[133611824] ata2.00 exception E mask
kernel a check root= bootarg cat /proc/cmdline
kernel dor missing modules devices:cat /proc/modules ls /dev

Alert1 /dev/disk/by-vvid/5d415acb-815d-4ad4-9ccb-107ac14395d does not exist dropping
Finally it gets into
{initRamFs}

I really appreciate help from this forum.

---

### Post by ccacioppo on 2008-04-30
Update: 8.04 fairs no better. It fails with the livecd at INITRAMFS > prompt and dies. The system is fine and runs vista and opensuse. ubuntu be broke

---

### Post by brianmoney on 2008-05-03
I have experience this as well my inspiron 530s with 8.04

---

### Post by prashanthsharma on 2008-05-20
I am facing the exact same problem. Trying 8.4 on a 530s with the Intel G33/G31 Express Chipset.

  Did anyone find a solution ?

---

### Post by prashanthsharma on 2008-05-21
Here is the solution to the problem
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

---

