---
title: "How to diagnos a graphics problem?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by makitso on 2010-04-23
OK, I am on the latest release and have a ATI graphics problem.  

So, my question is, what is the best way, commands, etc. to diagnose the problem?
  
The xorg.conf file is not there by default and I can create it in recovery mode.  

I have run lspci and know the graphics model (ATI Radeon X1270)

I have tried the standard build driver, the open source version and the fglrx.  On all of them I get screen garbage with any Desktop effects other than None.

So, what can I do to diagnose the problem?

---

### Post by VMC on 2010-04-23
Someone will come along that has an ATI video an answer your question, but have you checked in your home folder the ".xsession-errors" file for any indications?

Also look at "/var/log/xorg*log" files.

---

### Post by Untitled_No4 on 2010-04-23
Could be related to this?
[http://ubuntuforums.org/showthread.php?t=1460746](http://ubuntuforums.org/showthread.php?t=1460746)

---

### Post by BrokeMahPC on 2010-04-23
RE: X1270 can we have additional info:
How much memory does that have 64mb/128mb?
What chip is it? (the command below should reveal that - RS6XX something.)
It's an older card - does it meet the requirements for lucid?
Can we have a screenshot of the screen garbage?

RE: commands - Something we really need is a command to display the video driver being used. I have found this that seems to work if it's already in the xorg. It shows everything and my driver is listed under configuration.
```
sudo lshw -C video
```just recommended it to someone with intel graphics but as he didn't have an xorg it just returned something about latency=0.

---

### Post by makitso on 2010-04-23
video RS690M, Radeon X1200, 256M memory 32 bit
Kernel driver is radeon
Running on an AMD 64 bit chip

---

