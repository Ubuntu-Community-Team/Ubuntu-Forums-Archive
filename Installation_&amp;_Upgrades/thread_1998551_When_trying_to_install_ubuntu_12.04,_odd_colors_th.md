---
title: "When trying to install ubuntu 12.04, odd colors then black screen."
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by ugotboxed on 2012-06-06
So when I'm installing Ubuntu I'll click install and the screen will flash with funny colors and then the screen will go black. I know that it has to do with the drivers for my video card but I don't know how to fix this on the installation screen. Thanks for your help in advance.

---

### Post by carl4926 on 2012-06-06
During boot hit Esc. to access the menu
Something like this
[http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu%20F6%20options.jpg](http://dl.dropbox.com/u/10573557/Ubuntu/ubuntu%20F6%20options.jpg)
Hit F6 and try 'nomodeset' option

---

### Post by ugotboxed on 2012-06-07
Ok, I did this and it appears to be working. now will this still be the full os or will anything be excluded?

---

### Post by carl4926 on 2012-06-07
> **ugotboxed said:**
> Ok, I did this and it appears to be working. now will this still be the full os or will anything be excluded?
It will be fine
nomodeset just disables kernel modesetting on your graphics
Post install you may need to use F6 to apply that, wait and see. Then when you get to the desktop, install the additional drivers

---

### Post by ugotboxed on 2012-06-07
umm, now the same problem is occurring, It installed the os and told me to restart. so I did, and when it came back on the screen flashed colors and when black.

---

### Post by carl4926 on 2012-06-07
You can press e
to edit the kernel arguments and type in nomodeset

---

### Post by ugotboxed on 2012-06-07
Sorry I'm new to ubuntu or any linux distro for that matter. where do I type it in? I pressed "e"

---

### Post by carl4926 on 2012-06-07
Use the down arrow to move the cursor down and add a space on the last line and type
There should be some hints on the page too

---

### Post by carl4926 on 2012-06-07
Actually

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ugotboxed on 2012-06-07
I did this, then I pressed f10 to boot. but the same thing happened. I don't know if I did it wrong or right but that is what happened. any other ideas. Also this is 64 bit, But if ive gotten this far I dont think that has anything to do with it. Should I try 32 bit?

---

### Post by ugotboxed on 2012-06-07
Ok, I got to the desktop, now do I just go to "additional Drivers" and install my the graphics drivers? 
Edit: "sorry installation of the drivers failed" is what it told me... now what?

---

### Post by carl4926 on 2012-06-07
> **ugotboxed said:**
> I did this, then I pressed f10 to boot. but the same thing happened. I don't know if I did it wrong or right but that is what happened. any other ideas. Also this is 64 bit, But if ive gotten this far I dont think that has anything to do with it. Should I try 32 bit?

64/32 not the issue

try again

Look at that guide
Here: 
[http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png](http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png)

Note the nomodeset option added and the instruction Ctrl-x
to boot with that added

---

### Post by carl4926 on 2012-06-07
> **ugotboxed said:**
> Ok, I got to the desktop, now do I just go to "additional Drivers" and install my the graphics drivers? 
Edit: "sorry installation of the drivers failed" is what it told me... now what?
Get the system updated first
reboot
try again

---

### Post by ugotboxed on 2012-06-07
I updated, then restarted. When I got back to the desktop I went to activate the additional drivers. it says "Sorry, installation of this driver failed.
Please have a look at the log file for details:/var/log/jockey.log"

---

### Post by carl4926 on 2012-06-07
Post a link to that at
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Also, open a terminal and post the result of

```
lspci -nnk
```

---

