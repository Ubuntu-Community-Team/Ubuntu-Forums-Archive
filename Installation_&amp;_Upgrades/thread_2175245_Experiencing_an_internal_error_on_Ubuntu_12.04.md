---
title: "Experiencing an internal error on Ubuntu 12.04"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by senuel on 2013-09-18
Hi,
 I am sorry if I am posting an old issue that's already been discussed. My problem is that when ever I am loging in to Ubuntu 12.04, I get a message in a dialog box which says 

"**Sorry, Ubuntu 12.04 has experience an internal error**"  and the error detail indicates

**ExecutablePath**
/usr/bin/Xorg
**Package**
xserver-xorg-core-lts-raring 2:1.13.3-0ubuntu6~precise2
**ProblemType**
Crash
**Title **
Xorg crashed with SIGSEGV in mieqProcessDeviceEvent()
**ApportVersion**
2.0.1-0ubuntu17.4
**Architecture**
amd64

My hardware Intel 64-bit. Just fyi, It is a newly re-installed Ubuntu-12.04. 

I am hoping if anybody can help me with the solution for this problem. I am still learning so, a detailed solution is even better. 

Regards,

---

### Post by ibjsb4 on 2013-09-18
EDIT

Nevermind, I just answered my own question :)

EDIT#2

Ok, there are several bugs filed about this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Xorg+crashed+with+SIGSEGV+in+mieqProcessDeviceEvent&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Xorg+crashed+with+SIGSEGV+in+mieqProcessDeviceEvent&sa=Search&cof=FORID:9)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:
```
uname -r
```

Please post the output (thats the kernel your currently running).

---

### Post by senuel on 2013-09-18
here is the output

3.8.0-30-generic

---

### Post by ibjsb4 on 2013-09-18
If I understand correct, even though your getting this boot error you do have a working system.  If this is so, then you may want to consider just leaving it alone until a fix comes down.

My second though is not a fix, but a possible work-a-round.  I think this problem my be kernel related and a different kernel version could resolve it.  12.04 comes with three kernel versions (3.2, 3.5 and the one you are running 3.8).  I am running the 3.2 version without issue, but that doesn't mean it will work for you.  Its just a possibility.

---

