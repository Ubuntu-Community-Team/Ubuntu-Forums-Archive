---
title: "Matlab launcher help"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by srikris on 2010-04-23
I have installed matlab 7.9 in ubuntu 9.10.
I tried to launch it on the desktop using launcher
But as i double click on it it flashes but its not opening.
After seeing previous posts somewhere it is given that matlab-desktop should be used.
But iam not clear where to use it.

Help me in creating a desktop icon for matlab.


**It got solved by adding -desktop at the end of command**
Regards
Sri

---

### Post by ashokranade on 2010-05-06
[LEFT]i have installed matlab 2009 on Ubuntu  9.10 - the Karmic Koala according to [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) rules given. As i try to launch it from Application<<Programming<<MatlabR2009a it gives " Could not launch 'MATLAB R2009a' and Failed to execute child process "matlab" (No such file or directory). If i try to launch matlab by right click opening a .m file matlab screen flashes but donot go ahead.
Please give some solution to this problem
[/LEFT]

---

### Post by troll1602 on 2010-10-06
To get my launcher to work I went to System>>Preferences>>Main Menu and Selected "New Item". For "Type", I selected "Application" and for "Command" I did:
```
/path/to/MATLAB/R2010b/bin/matlab -desktop
```

---

