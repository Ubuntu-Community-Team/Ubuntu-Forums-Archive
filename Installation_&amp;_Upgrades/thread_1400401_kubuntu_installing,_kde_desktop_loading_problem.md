---
title: "kubuntu installing, kde desktop loading problem"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by sathyashrayan on 2010-02-06
My system specification: 

I am using  PC(stand alone) with the following system config.. 

AMD Sempron(tm) processor 
2500+ 
704 MB RAM 
ASUS mother board.. 
ubuntu version 9.10 

Problem: 
I have ubuntu version 9.10. I went to synaptic, searched kubuntu and installed. After 2 hr with several files, around 140 installition, I rebooted my system and selected kde in the login page and looged in. But it never able to load kde env, instead it keeps coming back to login page. Then I selected gnome env, it loading the desktop. why not with kde?

---

### Post by mushwars on 2010-02-06
so you did apt-get install kubuntu-desktop and when you select it in your GDM it doesnt start but comes right back to the same screen? 

if you could hit ctl + alt + f2 and log in and type dmesg | tail and see if it gives any warnings that look like they have to do with graphics. I dont think its an X thing.

---

### Post by sathyashrayan on 2010-02-07
> **mushwars said:**
> so you did apt-get install kubuntu-desktop and when you select it in your GDM it doesnt start but comes right back to the same screen? 

if you could hit ctl + alt + f2 and log in and type dmesg | tail and see if it gives any warnings that look like they have to do with graphics. I dont think its an X thing.

I used synapitc not apt-get
```

dmesg | tail

```

output:

```

[   30.948722] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   30.948795] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   37.224022] eth0: no IPv6 routers present
[  177.243518] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 5961.509964] __ratelimit: 27 callbacks suppressed
[ 5961.509972] mail-notificati[2131]: segfault at d4 ip 0805d074 sp bfda3390 error 4 in mail-notification[8048000+4d000]
[ 5962.560539] mtrr: no MTRR for f4000000,4000000 found
[ 5963.477367] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[ 5963.477393] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[ 5963.477467] pci 0000:01:00.0: putting AGP V3 device into 8x mode

```

---

### Post by sathyashrayan on 2010-02-07
I think my monitor dose not support KDE. How to check what vga I have. I will post that information too..

---

### Post by sathyashrayan on 2010-02-09
Is it a bug?

---

### Post by sathyashrayan on 2010-02-17
bump..

---

### Post by sathyashrayan on 2010-03-13
bump..

---

### Post by sathyashrayan on 2010-04-19
I see some update in KDE but the problem still existes for me.. No one to help?

---

