---
title: "How to check how much memory is used"
date: 2017-05-16
forum: Installation &amp; Upgrades
---

### Post by ubu112 on 2017-05-16
Please,I'm trying Xubuntu and Lubuntu from live USB.

With "free -m" or "free -lm",I'd like to understand which is the right number to check.

Is this "free" or "available"? and with "free -lm",what "High" and "Low" means?

Thank you

---

### Post by sp40140 on 2017-05-16
```

dell@DELL:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7915        2011        4452         239        1451        5418
Swap:          2047           0        2047
dell@DELL:~$ 

```
This is output of "free -m".
And as you see it's easy to read. It tells you "total", "used" and "available". And it's in MB (mega Bytes). 
What is your specific question.

---

### Post by Dennis N on 2017-05-16
Instead of **free** and it's possibly confusing terminology, I suggest you install and run **htop**. It runs from the terminal command **htop**. The top pane of its window clearly shows the current ram memory (Mem) in use. No confusing terminology. See attached image. 1-4 in the display are CPU information.

If you are using live media, you will probably need to install it into the live session:

```
sudo apt install htop
```

---

### Post by ubu112 on 2017-05-16
First of all,thank you for your answer.

> 
[COLOR=#000000]And as you see it's easy to read. It tells you "total", "used" and "available". And it's in MB (mega Bytes). [/COLOR]

I'm sorry,but I read "total","used" and "free".

I'd like to know _how much memory my system is using_.

The right number, to know memory used, is "Total-free" or "Total-available".

Thank you

---

### Post by Impavidus on 2017-05-16
free is the memory that's completely unused, available is the memory available for use for any application that wants it. The difference is memory used for chache or buffers, which is in use by the OS, but can be dropped whenever it's needed for something else.

---

### Post by Dennis N on 2017-05-16
FYI,
The various memory measurements are constantly changing as applications are opened or closed, or system processes start and stop. **free** (in terminal) gives you a one-time read when it is opened - it needs to be re-executed to make readings current - while other tools like **htop** (in terminal) and **system monitor** (gui) give a dynamic (changing) picture of memory usage. Users choice.

---

### Post by vasa1 on 2017-05-16
And a classic read on the subject: [Help! Linux ate my RAM!]("http://www.linuxatemyram.com/")

---

