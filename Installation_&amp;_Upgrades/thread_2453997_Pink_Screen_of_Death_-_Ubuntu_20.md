---
title: "Pink Screen of Death - Ubuntu 20"
date: 2020-11-20
forum: Installation &amp; Upgrades
---

### Post by matt-claflin on 2020-11-20
Hi,

My desktop had Ubuntu 16 on it, I upgraded to Ubuntu 20, and things were working great for several weeks. Then one day I booted up my machine, got my motherboard's screen, briefly got a screen that said "Ubuntu" on it, and then immediately got a pink screen of death. I was never taken to the grub menu. Oddly enough, when I then held down the machine's power button, the machine stayed on and the power button started flashing. That action didn't return me to any sort of menu and I had to flip the power button in the back of the computer to get a system reboot.

So far, I have tried the "boot repair disk" utility, found here:

[https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

It ran through its checks, indicated that it had repaired my system boot situation, and posted a system report here:

[http://paste.ubuntu.com/p/HpBDfBF9QY/](http://paste.ubuntu.com/p/HpBDfBF9QY/)

Unfortunately, running the boot repair disk utility yielded no better result at system startup. Does anything on that report look strange? What is the next best step for diagnosing this problem?

Thanks a lot!

---

### Post by dino99 on 2020-11-21
Often due to graphic driver used, or old settings left behind: start recovery mode, activate network and select root command : there, clean the system via autoremove/autoclean

Try to boot after 'quiet splash' removal, to read booting process. 
If that still fail, try to open a terminal (ctrl+alt+F1->8) and install bleachbit; then use it 'as root' with carefully selected options.

---

### Post by CelticWarrior on 2020-11-21
Actually the first thing to do is correct this:

```
[COLOR=#000000]sda may have broken partition table.
[/COLOR][COLOR=#000000]sdc may have broken partition table.[/COLOR]
```

Assuming you have backups, just boot a live session, open GParted and then cleanup the aforementioned drives. In GParted > Device menu > New partition table... > Select GPT. This will remove all current partitions and data within, obviously.
Then proceed with a new installation.

---

