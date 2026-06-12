---
title: "No such file or directory"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by graha on 2007-04-10
[http://www.knithx.net/2006/07/29/how-to-run-photoshop-cscs2-in-linux/](http://www.knithx.net/2006/07/29/how-to-run-photoshop-cscs2-in-linux/)

currently im trying to use photoshop cs2 with wine from the tutorial above but as soon as i run ~/.wine/drive_c/Program Files/Adobe/Photoshop CS2/Photoshop.exe. it gave me this /home/graha/.wine/drive_c/Program: No such file or directory 
what did i do wrong ?

---

### Post by john_spiral on 2007-04-10
have you checked if the directory exists?

---

### Post by graha on 2007-04-10
yep...i did exactly what the tutorial said 'copy the whole folder C:\Program Files\Adobe\ to the Linux folder: ~/.wine/drive_c/Program Files/'

---

### Post by taurus on 2007-04-10
Try either **"~/.wine/drive_c/Program Files/"** or **~/.wine/drive_c/Program\ Files/** since there is a space between Program and Files.

---

