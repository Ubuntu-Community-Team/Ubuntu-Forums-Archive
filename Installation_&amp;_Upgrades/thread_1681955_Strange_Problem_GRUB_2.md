---
title: "Strange Problem GRUB 2"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2011-02-05
My brother has Tri boot Ubuntu ,7 and Vista ..GRUB2 is the bootloader..
 
The problem : At boot after the Lenovo splash disappears , there appears some 4 to 5 lines of error , error: syntax error GRUB or similar..
 
This is visible only for a fraction of a second before the GRUB2 menu pops up...
The OS es load properly on selection in the menu so no loss of functionality
One another problem is there is no OS highlighted by default and the timeout message 
"Automatic Boot in 10 Secs" does not appear
 
What could be the problem?
 
I tried reinstalling GRUB 2 , but same result

---

### Post by sikander3786 on 2011-02-05
Go to Applications > Accessories > Terminal and post the output of this command please.

```
sudo update-grub
```

---

### Post by vikrang on 2011-02-05
I have tried reinstalling and updating GRUB ..
 
The file grub.cfg is getting generated with all OS successfully...No errors reported

---

### Post by sikander3786 on 2011-02-05
In that case, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Unless we know the exact error message, we can't do anything.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

