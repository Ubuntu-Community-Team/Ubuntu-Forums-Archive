---
title: "End of the road for old PC?"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by ElChapulin on 2014-08-13
Dear all, just upgraded my system to 14.04 LTS and afterwards Skype and Chromium are gone. They will symply not launch.

Skype is updated to 4.3, uninstalled and reinstalled many times. Folder /.Skype has been renamed, deleted, etc.
When starting skype from terminal, nothing happens and the only visible message is: Aborted (core dumped)

Using gdb I get:

```
(gdb) run
Starting program: /usr/bin/skype 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
[New Thread 0xb1668b40 (LWP 7896)]
[New Thread 0xb0cffb40 (LWP 7897)]
[New Thread 0xb00beb40 (LWP 7898)]
[New Thread 0xaf8bdb40 (LWP 7899)]
[New Thread 0xaf0bcb40 (LWP 7900)]
[New Thread 0xae8bbb40 (LWP 7901)]
[New Thread 0xae0bab40 (LWP 7902)]
[New Thread 0xad8b9b40 (LWP 7903)]
[New Thread 0xac8b7b40 (LWP 7905)]
[New Thread 0xad0b8b40 (LWP 7904)]
[New Thread 0xac0b6b40 (LWP 7906)]
[New Thread 0xab8b5b40 (LWP 7907)]
[New Thread 0xab0b4b40 (LWP 7908)]
[New Thread 0xaa8b3b40 (LWP 7909)]

Program received signal SIGILL, Illegal instruction.
[Switching to Thread 0xad8b9b40 (LWP 7903)]
0x80c27912 in ?? ()

```

Chromium has similar symptons, after starting from terminal I get something like: Invalid command (Core dumped)

Here some info about my PC:

```
xxxx@samarkand:~$ sudo lshw -C cpu
[sudo] password for xxxx: 
  *-cpu                   
       Beschreibung: CPU
       Produkt: AMD Athlon(tm) XP 2400+
       Hersteller: Advanced Micro Devices [AMD]
       Physische ID: 4
       Bus-Informationen: cpu@0
       Version: 6.10.0
       Steckplatz: Socket A
       Größe: 1995MHz
       Kapazität: 3GHz
       Breite: 32 bits
       Takt: 133MHz
       Fähigkeiten: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow cpufreq
```

Is it worth keep trying? or should I just dump my PC and buy a new one? (it would be a shame, still working marvelously).

Thank you.

---

### Post by JDorfler on 2014-08-13
Um, if you really want to get a new computer there is nothing anyone here can say to stop you.  However, I wouldn't "dump" the older PC.  You could always install Ubuntu Server on it and create a nice headless server.  I have done something like that for my office.  Hardware too old? Make a headless server.  Nothing wrong with that.

---

### Post by sudodus on 2014-08-13
It depends what you want to do with the computer. I'm afraid, that it is or will soon be too old to browse common web-pages, that have a lot of eye-candy. But there are other things, where it will still work. Headless server is one alternative, a super light desktop is another alternative.

Have a look at this link (and links from it)
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by kansasnoob on 2014-08-13
Fresh installs quite often perform much better than upgrades ;)

---

### Post by kansasnoob on 2014-08-13
I just thought to add; I have nearly two dozen old boxes that don't play well with Trusty because of the gallium llvmpipe thing in X. I hope to find a way to blacklist or disable that feature but until then I'm using 12.04.1 with the original Precise kernel and X-stack which are supported until April 2017:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

On that older hardware I mostly use [this DE]("http://ubuntuforums.org/showthread.php?t=1966370"). The archived 12.04.1 images are here:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

Just stay away from the 12.04.2, 12.04.3, and 12.04.4 images to avoid HWE EOL:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by ElChapulin on 2014-08-13
Thanks for your ideas. I was hoping to somehow make skype work on my PC again. What I will try is to make a fresh install, we will see if that helps.

---

### Post by mörgæs on 2014-08-13
Skype should be easy to get running but as your processor does not have SSE2 there's no Flash. May or may not be a problem, as more and more web sites are dropping Flash and moving to HTML 5. Maybe you are only missing the animated ads :-) 

Another problem is that many of these old Athlons came accompanied by Nvidia Geforce 4 graphics which is slow compared to today's standards. 

Anyway, please go ahead and let us know how it proceeds.

---

### Post by ElChapulin on 2014-08-14
fresh install, latest update from today included, skype will not start.
Error the same: ABorted (core dumped)

Any ideas?


It seems it is the old hardware:

[http://community.skype.com/t5/Linux/Skype-4-3-crash-on-ubuntu-14-04/td-p/3219892/page/7](http://community.skype.com/t5/Linux/Skype-4-3-crash-on-ubuntu-14-04/td-p/3219892/page/7)

---

### Post by mörgæs on 2014-08-15
That's news to me. Googling seems to show that the new Skype 4.3 demands sse2, though it's not written in the system requirements. 

I don't remember sse2 problems for 4.2. 

I doubt that Microsoft is going to fix a bug related to old hardware, so maybe it's time to consider Google Talk or Ekiga?

---

