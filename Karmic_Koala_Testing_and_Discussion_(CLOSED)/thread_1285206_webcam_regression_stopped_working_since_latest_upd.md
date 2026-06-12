---
title: "webcam regression: stopped working since latest updates. How do I report the problem?"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-10-07
I've tried testing it with Cheese and Skype. In both cases it shows just gray or noise. It doesn't throw any error.

Here's the output of cheese -v:
```

Cheese 2.27.5 
Probing devices with HAL...
Found device 17ef:4807, getting capabilities...
Detected v4l2 device: UVC Camera (17ef:4807)
Driver: uvcvideo, version: 256
Capabilities: 0x04000001

Probing supported video formats...

```

---

### Post by taavikko on 2009-10-07
first of all, upgrade your system, you're running outdated software.
Just to see if that fixes the issue.

"sudo aptitude update && sudo aptitude full-upgrade"
And use main-server or some other that is up-to-date

---

### Post by Giwex on 2009-10-07
[http://ubuntuforums.org/showthread.php?t=1282975](http://ubuntuforums.org/showthread.php?t=1282975)

---

### Post by andresmh on 2009-10-07
After applying the update I get the camera to work. I wasn't using the main server.

---

### Post by libihero on 2009-10-24
how do you update fromt he main server?? i'm having the same problem

---

### Post by andresmh on 2009-10-25
> **libihero said:**
> how do you update fromt he main server?? i'm having the same problem
Open "Software Sources" and  select this from the drop down menu: 
"Download from: Main server"

---

### Post by libihero on 2009-10-26
aw k well mine still wont work :(

---

