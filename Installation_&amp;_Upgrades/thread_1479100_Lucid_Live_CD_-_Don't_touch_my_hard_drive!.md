---
title: "Lucid Live CD - Don't touch my hard drive!"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by neko1 on 2010-05-10
Hey all,

Does anyone know a way to prevent the Ubuntu 10.04 live CD from doing anything to my hard drive when it's starting up? I believe the live CD is trying to use the swap partition, which causes the bootup of the live CD to hang (my hard drive is damaged). Something like the equivalent of previous Ubuntu versions' boot options (in particular, the noswap option) would be ideal.

Thanks

Edit:
When I say "boot options", I'm referring to these: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by neko1 on 2010-05-10
Never mind. I answered my own question.

Hit escape when the "ISOLINUX" line comes up right at the start of the boot sequence.

---

### Post by doas777 on 2010-05-10
live CDs don't swap so far as I am aware. try physically disconnecting the drive if you are that worried about it, but I would give your ram a test with memtest if you are getting hangs at boot. if you have DMA enabled on your motherboard (BIOS) then a faulty hdd can send all kinds of gibberish onto the system bus even when the drive is not in use.

---

### Post by neko1 on 2010-05-10
That looks to be the problem. I'll check the BIOS setup to see if there's any way to disable DMA. After I took off the "quiet splash" options, it started spitting out a ton of errors about DMA.

Ultimately my goal is to run ddrescue on this disk, so I can't just go unplug it.

Edit:
Here are what the errors look like:
```

ata1.00 exception Emask 0x0 SAct 9x9 SErr 0x0 action 0x0
ata1.00 BMDMA stat 0x24
ata1.00 failed command: READ DMA
ata1.00 cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
        res 51/40:00:00:00:00/00:00:00:00:00 Emask 0x9 (media error)
ata1.00 status { DRDY ERR }
ata1.00 error: { UNC }
ata1.00 configured for UDMA/100
ata1.00 EH complete

```That repeats for a very long time (longer than I am patient).

Edit 2:
I already disabled the "IDE UDMA" option in the BIOS (the drive is connected with Parallel ATA/IDE).

Edit 3:
Ran across [http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837)

---

