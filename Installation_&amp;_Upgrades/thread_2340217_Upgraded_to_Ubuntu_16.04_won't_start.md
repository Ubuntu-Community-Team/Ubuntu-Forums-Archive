---
title: "Upgraded to Ubuntu 16.04 won't start"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by polardude1983 on 2016-10-16
I had upgraded to ubuntu 16.04.1 through the update manager and now my computer won't boot up into Ubuntu.

I believe in my franticness that I also changed my boot hard drive and repaired/installed grub on a different partition. 

Here is what is displayed on my PC. Yes I do have a Live CD of Ubuntu 16.04.1

[http://tinypic.com/r/10cknz5/9](http://tinypic.com/r/10cknz5/9)

Any help would be much appreciated.

---

### Post by oldos2er on 2016-10-16
Moved to Installation & Upgrades.

Boot from your live medium and please show us the output of both ```
sudo blkid
df -h
```

---

### Post by polardude1983 on 2016-10-16
Thank you for moving the thread into the correct one and replying as well. Here is what my terminal shows.

[http://pastebin.com/jbmxfg8P](http://pastebin.com/jbmxfg8P)

---

### Post by polardude1983 on 2016-10-20
Bumped

---

### Post by oldfred on 2016-10-20
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash) Enter 'help' for a list of built-in commands.
(initramfs)
type exit and it may load. 

If not run this from a 16.04 live installer:
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

