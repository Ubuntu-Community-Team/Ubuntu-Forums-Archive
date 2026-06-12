---
title: "[SOLVED] Brother MFC 215 scanner error"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by remy06 on 2008-11-10
Hi,

I have installed the drivers for my brother MFC-215 printer via synaptic package manager in Intrepid.I am able to print fine.

Next I downloaded and installed the driver for the scanner(my printer was off then) and installation shows no errors.I installed sane as well after that.

I switched it on and wanted to test it,I clicked on applications>graphics>xsane image scanner, it pops up an error:
```

Failed to open device `brother2:bus7;dev1`:
Error during device I/O

```

I tried followingthread #52 in the following link but /etc/udev/rules.d/45-libsane.rules does not exist.
[http://ubuntuforums.org/showthread.php?t=302960&highlight=MFC+215+210&page=6]("http://ubuntuforums.org/showthread.php?t=302960&highlight=MFC+215+210&page=6")

Have no problem installing them in hardy previously.Any suggestions??

---

### Post by remy06 on 2008-11-11
bump

---

### Post by remy06 on 2008-11-16
Thanks to TopEnder,managed to solve the issue with his suggestions.

1.Search for MFC-210 in synaptic package manager and installed the brother drivers.

2.To install the scanner driver I downloaded and used brscan2-0.2.4-0.i386.deb.
```
sudo dpkg -i brscan2-0.2.4-0.i386.deb
```

3. Install sane
```
sudo apt-get install sane
```

4.In Intrepid,45-libsane.rules does not exist so I created the file and add these entries where "MODE=666".Thanks to Matchless thread for the entry details:
```
# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="666", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="666", GROUP="scanner"
```

Switched on printer to test printing and scanning,both works fine after that.:)

Ubuntu Intrepid
Brother MFC-215C

---

