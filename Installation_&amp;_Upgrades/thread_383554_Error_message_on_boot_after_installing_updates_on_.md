---
title: "Error message on boot after installing updates on 6.06"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by yves on 2007-03-13
I just reinstalled 6.06 on my Lenovo J115 AMD64 machine without any problem.
After the first boot, I got the "warning" that 119 updates were available to install. I did, but now I have a really funny error message when the splash screens shows that it's checking all filesystem :

s: command not foundhell and continue system startup.replayedal

and I did not make any typo, this is the EXACT message I have, on a full screen terminal.

If I type "exit", the system proceed and finishes it's boot process all the way...

What is wrong ?

---

### Post by zvacet on 2007-03-16
In terminal
```
sudo aptitude update
```
And if you get some error post it here.Somebody will know how to help you.

---

### Post by yves on 2007-03-16
The update was made, but I still get the same behavior with the same funny error message !

---

