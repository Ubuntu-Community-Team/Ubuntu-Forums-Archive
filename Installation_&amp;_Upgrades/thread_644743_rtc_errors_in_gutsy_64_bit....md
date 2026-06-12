---
title: "rtc errors in gutsy 64 bit..."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Zack McCool on 2007-12-19
Since installing Gutsy on my machine, I have been getting the following errors in the syslog...

```

Dec 19 08:25:45 barada kernel: [  352.326056] printk: 241 messages suppressed.
Dec 19 08:25:45 barada kernel: [  352.326061] rtc: lost some interrupts at 512Hz.

```

I get a new one every couple of seconds.  The log fills up fast...

I also notice the following during boot:

```

Dec 19 08:21:26 barada kernel: [   47.580086] NET: Registered protocol family 1
Dec 19 08:21:26 barada kernel: [   47.580245] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Dec 19 08:21:26 barada kernel: [   47.580251] Freeing unused kernel memory: 296k freed

```

So, what is this, and how can I make it go away?

A bug report has been filed:
[https://bugs.launchpad.net/ubuntu/+bug/177807](https://bugs.launchpad.net/ubuntu/+bug/177807)

---

### Post by Elle Stone on 2007-12-21
I have the exact same message in dmesg:


[   24.332986] NET: Registered protocol family 1
[   24.333126] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.333131] Freeing unused kernel memory: 296k freed


I am running gutsy 64-bit, with AMD Oteron 252 with Nvidia nForce Professional 2200 on the mainboard.  

I am trying to figure out if my SATA (two raptors and a seagate) drive IO can be improved, so I'm checking the dmesg for things that might be not quite right.  I have a lot of "Found no ck804xrom" error messages in my dmesg output.  

As I am a complete newbie to Linux, I am still researching how to interpret dmesg output, which is how I found this thread.  Checking /var/log/syslog, I don't see any errors like you describe.

Total aside, how do you get your dmesg and log excerpts to appear in a code box?

---

### Post by Zack McCool on 2007-12-21
> **Elle Stone said:**
> 

Total aside, how do you get your dmesg and log excerpts to appear in a code box?

You can use the little # icon on the editor box, or manually type CODE (enclosed with [] Brackets) and end with /CODE in the same brackets.

---

### Post by Elle Stone on 2007-12-22
Zack, thanks! for the code info.
Elle

---

