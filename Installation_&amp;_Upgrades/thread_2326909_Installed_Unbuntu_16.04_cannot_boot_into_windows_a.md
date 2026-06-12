---
title: "Installed Unbuntu 16.04 cannot boot into windows anymore"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by zlyspl on 2016-06-06
cann't boot into windows, does not show on bootloader, only get the ubuntu option. I run boot-info and this is what I got.. What did I do wrong and how do I fix? Thanks

[http://paste2.org/jVX4hLKJ](http://paste2.org/jVX4hLKJ)

---

### Post by yancek on 2016-06-06
If you look at the output of the boot repair script, you will see the grub.cfg file (the menu you see on boot) does not contain an entry for windows.  Boot Ubuntu, open a terminal and run the command:     

```
sudo update-grub
```

Watch the output for a windows entry and reboot to test it if you see one.

---

### Post by zlyspl on 2016-06-07
Thanks for trying to help, since I was in a rush to get this computer working (I need it for work) I reinstalled windows then reinstalled Ubuntu 15.10 which works and the bootloader works. When I have time I'll try to figure out why Ubuntu 16.04 doesn't work dual booting with Windows 10.

---

