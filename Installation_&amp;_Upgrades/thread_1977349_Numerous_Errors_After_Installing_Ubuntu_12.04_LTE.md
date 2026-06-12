---
title: "Numerous Errors After Installing Ubuntu 12.04 LTE"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by kensclark15 on 2012-05-10
So I just downloaded and made a fresh install on my HD of Ubuntu 12.04. First problem: When Ubuntu boots and shuts down, I cannot see the splash screen and it says resolution mismatch. Second problem: Ubuntu does not fill the screen completely, my screen goes to 1366 x 768 but Ubuntu only goes to 1234 x 768 or something like that. Third problem: ONLY if I use Ubuntu3D (doesn't happen with Ubuntu2D) I log in and go to my desktop but it flashes black a few times then it says Compiz crashed and I am not able to interact with anything. Fourth problem (minor): Whenever I install anything, I will get a message from dpkg saying that it could not install oracle-java7-install no matter what I try to install. I think there are more problems but I'll just leave you with this :)

---

### Post by alphacrucis2 on 2012-05-10
What does this say:

```
sudo lshw -C display
```

---

### Post by kensclark15 on 2012-05-10
> **alphacrucis2 said:**
> What does this say:

```
sudo lshw -C display
```
```
  *-display               
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fa000000-faffffff memory:e0000000-efffffff memory:f9000000-f9ffffff memory:fbfc0000-fbfdffff

```

---

### Post by alphacrucis2 on 2012-05-10
> **kensclark15 said:**
> ```
  *-display               
       description: VGA compatible controller
       product: C61 [GeForce 6150SE nForce 430]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fa000000-faffffff memory:e0000000-efffffff memory:f9000000-f9ffffff memory:fbfc0000-fbfdffff

```


I wonder if you have been hit by this problem per link below? I'm not sure if your particular card is one of those having problems with the version of the nvidia blob in 12.04.

[URL="http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc"]
http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc[/URL]


Edit. A quick search shows you aren't the only one with this particular issue:

[http://askubuntu.com/questions/127320/1080p-screen-resolution-problem-after-10-04-to-12-04-update](http://askubuntu.com/questions/127320/1080p-screen-resolution-problem-after-10-04-to-12-04-update)

---

### Post by kensclark15 on 2012-05-10
Yep, his problem looks like mine.

---

### Post by kensclark15 on 2012-05-10
Anyone have an idea on how to solve the problems? Any of them?

---

