---
title: "How to add Win7 to Grub2 menu"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by 007brendan on 2011-02-28
Just completed a new computer build. I installed Win7 on a 2-disk RAID0 fakeraid. I then unplugged those drives and installed linux mint on a separate drive. I did it this way because if I left the drives plugged in, linux would jack up the fakeraid for those drives and make windows upbootable, and installing linux to the fakeraid itself is just too much of a PITA. So basically, this is the disk configuration, and there's no chance of me changing it.

Right now, I can boot into either win7 or mint by pressing F12 for the boot menu, and then selecting the drive the os is installed on. It would be nice if I could just add an entry to the grub menu for win7. I've used the menu.lst file before, but apparently all that has changed with grub2.

I've checked out some of the grub2 docs and poked around in /etc/grub.d, but frankly, it seems to be orders of magnitude more complicated than it should be.

I'm hoping someone can point me in the right direction on what exactly I need to change to get this to work. Thanks.

---

### Post by kansasnoob on 2011-03-01
What happens if you just run:

```
sudo update-grub
```

---

### Post by 007brendan on 2011-03-01
Thanks, just tried it.  At first, it seemed to work, grub2 printed out that it found windows, and the grub config file was updated.  Sounds perfect, right?  Alas, my fakeraid is fubar'd again.

What I don't understand, is that Linux is still able to read from the fakeraid, even though the it's clearly broken in the raid boot menu, and Windows can't boot itself.

---

### Post by 007brendan on 2011-03-01
I lied.  After accessing the raid in linux, on reboot, the raid was functional again (weird, I know).  Now I can boot into win7, on a fakeraid, from grub2.

Thanks!

---

