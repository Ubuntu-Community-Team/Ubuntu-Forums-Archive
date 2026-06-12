---
title: "X server broke after an abnormal system shutdown"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by zelo on 2005-04-15
I've enjoyed wonderful Hoary for some time. 
But after today's unexpected system shutdown due to power failure, 
the X server isn't working correctly. 
The error message is like this. 
```

I cannot start the X server (your graphical
interface). It is likely that it is not set
up correctly. Would you like to view the X 
server output to diagnose the problem?

       <Yes>            <No>
```
If I choose yes, 
```

Unrecognized option: -br
use: X [:<display>] [option]
...

```
It seems that -br is an option for xfree86. 
But I have used xorg and xserver-xfree86 is not even installed in my system. 
I tried to find an answer in this site and google but failed. 
Could you give me any advice ?
(If possible, I'd like to know the cause of this problem as well as the solution...)

---

### Post by erkki70 on 2005-04-15
Hi,
Have you tried to answer no and then reconfigure X
 ```
sudo dpkg-reconfigure xserver-xorg
```

Hope this helps.

Cheers,
Erkki

---

### Post by zelo on 2005-04-15
I tried "sudo dpkg-reconfigure xserver-xorg" but I got the same error.

---

