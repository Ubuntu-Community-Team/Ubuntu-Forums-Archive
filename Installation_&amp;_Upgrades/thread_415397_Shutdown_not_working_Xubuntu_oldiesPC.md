---
title: "Shutdown not working Xubuntu oldiesPC"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by xerman on 2007-04-20
Hello there,

After installing Xubuntu on an oldie:
Pentium MMX 200MHz
13GB HD
160MB ram
Matrox Millenium 4mb Vram
20x CD
8x/4x/32x CDRW

it seems i cannot shutdown the computer:
I select shutdow and there appears de Xubuntu Splash with the progression bar going from full to empty.
The progression bar empties completely and HD parks
The computer will be like that forever unles i switch of the PowerSupply at the back of the box.

Any Idea on How to Solve this?

Thanks a lot.
Xermán

---

### Post by xerman on 2007-04-23
Hello there again:

One more thing: Going to a Console (CTRL+Alt+F1) and ```
sudo shutdown -h now
``` causes the same issue. The HD parks but the screen still keep the xubuntu logo and the progress bar empty.

Thanks again.
Xermán

---

### Post by xerman on 2007-04-23
Thanks to "jalbatros":

[http://ubuntuforums.org/showpost.php?p=2510210&postcount=7](http://ubuntuforums.org/showpost.php?p=2510210&postcount=7)

1. Edit /etc/modules with "$ sudo gedit /etc/modules" and add a new line: "apm power_off=1"

2. Edit Grub menu with "$ sudo gedit /boot/grub/menu.lst" and look for the line with the kernel option you use normally (Ubuntu, kernel 2.6.20-15-generic in my own), at the end of this line add "acpi=off apm=power_off", without quotes of course.

3. Now you have to restart your PC in order that changes take effect.

---

