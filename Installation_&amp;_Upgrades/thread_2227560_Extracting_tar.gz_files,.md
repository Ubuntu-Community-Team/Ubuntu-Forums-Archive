---
title: "Extracting tar.gz files,"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by Nicholas_Gonzales on 2014-06-02
I just started 2 weeks ago with Linux. I have a programming class that I am taking right now and I can't run it on a regular chrome os. (I have a chromebook by the way) I found out I can't install that program because chrom os is not a full os. So I found a youtube video on how to put linux (ubuntu linux, with unity desktop, saucy, 13.04) on it. I don't know much about linux but I found out I could run Alice2.4 (the program that I need for my programming class at school) on my chromebook only if I'm running Linux, that's why I installed it. I used the commands that I found, 
```
gunzip Alice2.4.tar.gz 
```
and that one didn't work/ I used the
```
cd /home/yourusername/Desktop/program-1.2.3
```
with the command that i put was
```
cd /home/nickg90/Desktop/Alice-2.4
```
and it says that no such file exists, then when I use the
```
tar xzf Alice2.4.tar.gz
```
command, it says
```
cannot open: No such file or directory, tar (child): Error is not recoverable
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```then it says:
```
(saucy)nickg90@localhost:~$
```
what am I doing wrong? I just want to extract the file so I could then install the program after that?
I've been trying for weeks to try to do this, please if anyone could point me in the right direction.

---

### Post by papibe on 2014-06-02
Hi Nicholas_Gonzales. Welcome to the forums ):P

Try this: open the file manager (called nautilus), browse to your files, when you find the 'Alice2.4.tar.gz', right click on it, and select 'Extract here'.

Hope it helps. Let us know how that works.
Come here often and have fun.
Regards.

---

