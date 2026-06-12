---
title: "Strange error on startup"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by JC Cheloven on 2008-01-03
Hi. Just after choosing ubuntu in grub, on a black screen (before any ubuntu's logos), I ALWAYS get an error msg:

"Cannot allocate resource region 4 of device ..." (an hex number follows)

There are 4 similar lines in the message. They disappear in less than a second, so I can't read the hex numbers (it's even hard to read the text). Usually the msg disappears and Ubuntu seems to load normally. But I'm experiencing more hang-ups than normal, and the system (almost) never powers off normally. Most of the times I have to hold down the power button to force power off. 

Please, does someone know whether that error is likely to be associated to subsequent unstability? 

I have no idea about the meaning of the msg... I'm running Ubuntu 7.10 on a toshiba A50 laptop, 1Gb ram.

Thank you folks :-)
________________________________

---

### Post by Partyboi2 on 2008-01-04
You can have a look for the error by using
```
dmesg |less
```You could try using pci=routeirq as a boot option.
When grub is loading press "esc" to get to grub menu
then highlight the Kernel entry and press "e" to edit then highlight Kernel entry again and press "e" then at the end of the line add ```
pci=routeirq 
```then press "enter" then "b" to boot. If that works you need to add the option to grub menu.lst

---

### Post by JC Cheloven on 2008-01-06
Thank you for your detailed and accurate how-to. Unfortunately it didn't work. The err msgs at startup do still appear.
Nevertheless I have learned about "dmesg", and at last I was able to read the msgs completely (they were there, in the middle of the verbose :-) 
Thank you again
JC
__________________

---

