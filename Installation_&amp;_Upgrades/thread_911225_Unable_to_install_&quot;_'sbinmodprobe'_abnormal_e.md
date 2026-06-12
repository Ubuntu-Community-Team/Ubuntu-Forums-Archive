---
title: "Unable to install: &quot; '/sbin/modprobe' abnormal exit&quot; at boottime"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by mahy on 2008-09-05
Hello people!

I bought a brand new notebook Toshiba Satellite A300 just today and of course, not being satisfied with Vista, I went on to installing Ubuntu, just like I did many times already.

Unfortunately, my hopes evaporated pretty fast. I insterted Ubuntu 8.04 CD, chose to boot the live session, but after a few seconds, the following message appeared:

```
udevd_event[1581]: run_program: '/sbin/modprobe' abnormal exit
```

Then it mentioned something about BusyBox, "ash" shell and initramfs. So I typed "poweroff<Enter>" and that was (so far) the end of the installation story.

My question: WTH is going on?? :confused: I never experienced such problem before. In fact, when I tried out Toshiba Satellite U400 (a very similar notebook) two days ago, everything went ok! Too bad I had to return that one, because the battery was faulty...

Alright, of course I used Google before posting this. All I found was to add the "all_generic_ide" boot option. As you can probably guess, it didn't help! ](*,)

That's why I'm asking you people to help me with issue in case you know anything more about it. I suppose it's some sort of a kernel bug caused by HW incompatibility, which is not quite my cup of tea...

THX for any advice.

---

### Post by mahy on 2008-09-06
bump

---

### Post by abrahapr on 2008-09-22
Hi,

I'm getting virtually the same problem with my new Toshiba SatellitePro L300.  

```
udevd-event[1531]:run_program sbin/modprobe abnormal exit
```

When I add all_generic_ide boot option it says:
```

(initramfs) [80.571312] Driver 'sr' needs updating - please use bus_type methods
[80.578030] sr0:scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[80.578075] Uniform CD-ROM driver Revision: 3.20
[80.578153] sr 0:0:0:0: Attached scsi CD-ROM sr0
```

Any ideas anybody?

---

### Post by trapula on 2008-10-14
Hello, I have the same problem with L300 M17. 

You'll complete the installation process if you disable LAN on-Board option in BIOS. But, then again, your system won't load if you turn it on later, so it's pointless.
The problems is related to a hardware check, it could be LAN-related but not necessarily.

---

### Post by redprag on 2008-10-25
Did you find a solution? What have you done?
I have the same problem with an A300 too.

---

### Post by Pumalite on 2008-10-25
How much memory do you guys have?
Graphics?

---

