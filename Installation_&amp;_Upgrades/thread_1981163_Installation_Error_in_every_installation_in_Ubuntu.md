---
title: "Installation Error in every installation in Ubuntu 12.04"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by vj41 on 2012-05-16
I recently installed ubuntu 12.10 and whenever i try to install any software using any method, whether software center, terminal etc., i always get error message that installation unsuccessful. However, the installation is always partially successful and i found this error message at the end of every installation log:
"Errors were encountered while processing:
 crossplatformui:i386
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)"
I am a beginner at linux, please be a bit descriptive while providing solution...

---

### Post by jadtech on 2012-05-16
sounds like you system is a tad bit unstable :) 

go to a terminal try to type in  these commands see if it helps not sure it will .. 

```
 sudo apt-get update

sudo apt-get upgrade -f

configure -a


```

not all sure what the problem is but everything I can find cause for this error is unstable kernel ...
this wont help any of you install attempts 
if all you want if to atempt to fix your install try this code

```
 sudo apt-get install -f

```

---

### Post by vj41 on 2012-05-17
Your advice didn't help much, except i was able to update a few packages. The error was still there. However, i was later able to remove this error by commenting these lines in crossplatformui.postrm (at /var/lib/dpkg/info):
sudo killall -9 ...
and the three lines after that..
Then i was able to remove crossplatformui compltely. However, i had to delete remaining files in the same directory related to cross platformui. The error was solved after that! :D
Thanks for your help though...

---

### Post by mörgæs on 2012-05-17
If this solves your problem, please mark the thread so.

---

### Post by vj41 on 2012-05-17
Yeah.. I forgot... New to the forum... Sorry! :)

---

