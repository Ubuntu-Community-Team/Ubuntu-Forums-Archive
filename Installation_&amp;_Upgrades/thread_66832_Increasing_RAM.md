---
title: "Increasing RAM"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by robbbert on 2005-09-18
Hi, I'm new to Ubuntu and Linux, so please be patient. I've just installed Ubuntu, and like it very much.

Nevertheless, there is a major problem with speed (this is a PIII 700 MHz, 96 MB RAM -- unfortunately, I can't change that as this is an older laptop) (BTW, Windows 2000 works much better with these settings).

I was wondering which possibilities exist to increase the speed.

+ OK, OpenOffice isn't really usable on this system, I will use AbiWord or something as an alternative.

+ "System Monitor" tells me I was using 126 of 187 MiB of RAM, and 0% swap. -- This can't be true: I'm sure there are 96 MB RAM, but not 187.

Secondly, I think there would be a possibility to increase the "virtual RAM".

-------------
Why -- do you think -- is my system relatively slow, and how could I improve this?

Thanks very much for any insight.

---

### Post by bsussman on 2005-09-18
[QUOTE=robbbert]+ "System Monitor" tells me I was using 126 of 187 MiB of RAM, and 0% swap. -- This can't be true: I'm sure there are 96 MB RAM, but not 187.
[/QUOTE]

That is strange - in a terminal window, what does 

 ```
> less /proc/meminfo
``` 

say about MEMTOTAL?  This is a direct (no app) read from a system area.

> 
Secondly, I think there would be a possibility to increase the "virtual RAM".


If it is using 0 swap, increasing it would mean that you would be using 0 out of a larger disk area - no performance gain.

---

### Post by robbbert on 2005-09-18
Thanks for your reply.

MemTotal is 191900 KB, so this might be correct, and I was wrong. -- Actually, there are two RAM sticks: 128 MB + 64 MB.

-- Well, the issue is, I like Ubuntu very much and really would like to switch from Windows 2000 (and, most likely, I will) but -- as soon I have more than, say, 10, Firefox tabs open, the system slows down. Opening OpenOffice applications then almost freezes the system. Under Windows 2000, the situation is much more relaxed: I can have -- estimatedly -- 150 Firefox tabs opened before the system slows down.

-- You're saying, increasing the swap file size wouldn't help as it isn't used anyways -- and that's sounding appropriate. -- But, which options do I really have to decrease the resources in use?

I tried to kill some processes through the "System Monitor". Those processes disappeared from the list, but the available memory didn't increase.

-- I'd just like to use any "good looking" operation system with an old computer (which is my only one, and I can't upgrade it).

Thanks again.

---

### Post by bsussman on 2005-09-18
NP - this is an important issue and deserves discussion.

Not all of us have 60 zillion megaflop PCs with Infinite drive space ;-)

---

### Post by robbbert on 2005-09-18
Hmmmm.

I think my computer is good enough to work another two or three years... Using Windows 2000 or SuSE 9.0 everything runs smart -- under Windows 2000, even the "big" server applications (like SQL Server or BizTalk Server) run smart.

Well, it's just, Ubuntu looks nice, and it feels nice (apart from I cannot have more than 3-5 applications opened).

-- My question is: Which are my options? --

I could change the window manager: Change Gnome for something else.

Is it that?

-- I tried to kill Nautilus using the Process Manager (as it used 20 MBs of RAM, and I don't seem to need it) but it re-appeared, instantly. Are there ways to customize what is loaded by default?

Thanks.

---

