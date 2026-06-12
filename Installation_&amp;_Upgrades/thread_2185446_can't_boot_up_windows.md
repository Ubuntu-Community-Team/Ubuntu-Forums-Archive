---
title: "can't boot up windows"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by Zero_Bytes on 2013-11-02
I'm a complete noob to ubuntu, but a friend gave me a cd with ubuntu 12.10 and I installed it as a dual boot but it doesn't.
I searched a bit and it they talk about "grub" wich doesn't show up on my screen: when I start my pc up it just goes staightforward to ubuntu, no questions asked.
I really need to get back on my windows xp professionel, and if someone tells me how I can I would be really gratefull. 

and here is some extra info [http://paste.ubuntu.com/6348285/](http://paste.ubuntu.com/6348285/)

---

### Post by heir4c on 2013-11-02
Open a terminal (Via Dash or via Ctrl+Alt+T) and type:
```
sudo update-grub
```
And click "Enter".
Your password will be asked. Type it in. You will see nothing when you type your password. You must type it "blind". (This is for safety).
Let do the computer his work.
After that:
Reboot the computer. Can you see now the grub menu? 
If it not show up you can use the "Shift" to see the grub menu.

---

### Post by Zero_Bytes on 2013-11-02
No, still nothing I pressed the shift button and it did nothing either just went straight to ubuntu after 10 secs black screen.

---

### Post by heir4c on 2013-11-02
It is there, and your Windows is there to, I see it in your boot-repair-log. So that is for now ok. 
I don't know for now what you can do. 
So, you have to wait till an other something can tell or I find something.

---

### Post by heir4c on 2013-11-03
I have find a tread on the Linux Mint forum:
[http://forums.linuxmint.com/viewtopic.php?f=46&t=143623&p=758416](http://forums.linuxmint.com/viewtopic.php?f=46&t=143623&p=758416)
Read it all before you do something. In post 3 you can see he has the same error.
Here something about the "Flexnet":
[http://computers-linux-other-nonsense.blogspot.be/2011/03/flexnet-sector-32.html](http://computers-linux-other-nonsense.blogspot.be/2011/03/flexnet-sector-32.html)
And here a tread from this forum about the Flexnet error:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)
Another 2 links (read them!)
[http://en.wikipedia.org/wiki/Flexnet](http://en.wikipedia.org/wiki/Flexnet)
[http://ubuntuforums.org/showthread.php?t=1976158](http://ubuntuforums.org/showthread.php?t=1976158)

Maybe other members can help explain it a little more.

---

### Post by fantab on 2013-11-03
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
**Found Microsoft Windows XP Professional on /dev/sda1**
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg
```

The Bootinfo-Summary shows that Grub has detected Windows.
However,
```
=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17df17de

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   233313694   116656816    7  HPFS/NTFS/exFAT
/dev/sda2       233314302   312580095    39632897    5  Extended
/dev/sda5       233314304   309571583    38128640   83  Linux
/dev/sda6       309573632   312580095     1503232   82  Linux swap / Solaris


[COLOR=#b22222]**Partition outside the disk detected**[/COLOR].
```

Run **[FixParts]("http://www.rodsbooks.com/fixparts/")** to correct the error. After which you wil run:
```
sudo update-grub
```
Reboot. If you still don't see Windows then re-run Boot-Repair. Let us know if that helps.

---

### Post by Zero_Bytes on 2013-11-03
This thread can be closed, I gave up on trying to fix it, I installed windows 7 and deleted ubuntu, I guess this isn't made for people like me.

---

### Post by Iowan on 2013-11-03
Best of luck with whatever OS you choose.

---

