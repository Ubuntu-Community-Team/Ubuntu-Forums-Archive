---
title: "Ubuntu 10.04.1 slow boot ?"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by lordmonkeyu on 2010-12-17
Hello,
Recently I have installed ubuntu 10.04.1 64 bit (as a second OS along with Win7 on the same hard drive) and as far as I have seen ubuntu booting on youtube movies or my friend's laptop I think it's a bit different a much slower.

After choosing ubuntu in grub I only see blinking cursor and black screen then aroun 50-60 seconds then purple screen with ubuntu text and finally desktop.
I have automatic login btw.

Is it caused by dual boot with win 7 ? If not how can I improve it ?

---

### Post by Quackers on 2010-12-17
If you reboot and at the grub menu make sure that Ubuntu is highlighted then press the "e" key. On the next screen navigate to the end of the line that says "quiet splash" and then remove those words and press ctrl + X to reboot.
This is a once only thing and will revert for future boots.
What it will do is show all processes on your screen during boot up. They will go quickly at first but you may see a point where it stops for a while. If you make a note of what is happening at the time of this stop it may give a you a clue as to what the problem is.
Alternatively you could look in the logs for a holdup during boot.

---

### Post by lordmonkeyu on 2010-12-17
I will change this thing in grub in a moment but where can I find these logs ?

---

### Post by Quackers on 2010-12-17
Sorry, System > Admin > Log file viewer

---

### Post by lordmonkeyu on 2010-12-17
OK I have found out, that it stops on line concerning network card :
```
eth0: dmarwctrl[76180000] dma_mask[64-bit]
```

ad second thing (but I am not sure about that) when I press e in grub then in the second or first line ( I don't remember) there is
```
insmod ext2
```

and my file system is ext4 sooo ? is it connected ?

---

### Post by lordmonkeyu on 2010-12-18
bump. anyone ?
I was trying to find something on this issue but without any effects.

---

