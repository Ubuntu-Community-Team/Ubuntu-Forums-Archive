---
title: "unable to install or run the live cd"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by gemini30 on 2008-07-20
hello everyone..
i've been using ubuntu(7.04-8.04) for a year now and was very happy with it:).
In between there have been windows reinstallations at regular intervals. Nothing significant..everytime i formatted windows, grub could be easily installed from the live cd. But this time around the live cd just refused to run..The booting starts in the usual manner.the kernel loads and thats it..there is a blank screen which just doesn't go...the only option is reboot and the cycle continues.Even if i try to install ubuntu again the process stops at the same screen. I tried installing the grub from past releases but to no effect.Then i installed the grub from "super grub disk".
But now there is another problem..although the grub is back, when i try to start ubuntu it says " error 17. unable to mount partition"
I tried searching for ways to correct this..but they all involve entering the termional from the live cd..which i am unable to do..
PLS HELP:confused:
Can't keep workin in windows for long...:mad:

---

### Post by confused57 on 2008-07-20
> **gemini30 said:**
> hello everyone..
i've been using ubuntu(7.04-8.04) for a year now and was very happy with it:).
In between there have been windows reinstallations at regular intervals. Nothing significant..everytime i formatted windows, grub could be easily installed from the live cd. But this time around the live cd just refused to run..The booting starts in the usual manner.the kernel loads and thats it..there is a blank screen which just doesn't go...the only option is reboot and the cycle continues.Even if i try to install ubuntu again the process stops at the same screen. I tried installing the grub from past releases but to no effect.Then i installed the grub from "super grub disk".
But now there is another problem..although the grub is back, when i try to start ubuntu it says " error 17. unable to mount partition"
I tried searching for ways to correct this..but they all involve entering the termional from the live cd..which i am unable to do..
PLS HELP:confused:
Can't keep workin in windows for long...:mad:

Try pressing "c" at the grub boot menu, which should give you a grub prompt, then enter:
```
find /boot/grub/stage1
```
make a note of the results, e.g. "root (hd0,1)"...Do you have 2 hard drives or just Ubuntu/Windows on a single drive?  This might determine where to install grub.

If you receive something like "root (hd0,1)", then you could try reinstalling grub to the mbr:
```
root (hd0,1)
setup (hd0)
quit
```

Since you have SGD, you can still repair your mbr, if this doesn't work.

---

### Post by gemini30 on 2008-07-20
@ confused 57
The method you suggested does not seem to work.
The first command returned (hd0,6).
I did root (hd0,6)
Then setup (hd0)
There was some mssg regardin successful install..something that said the process had succeeded but to no avail..m still stuck..:confused:
Btw i have a single hard disk..

---

### Post by confused57 on 2008-07-20
> **gemini30 said:**
> @ confused 57
The method you suggested does not seem to work.
The first command returned (hd0,6).
I did root (hd0,6)
Then setup (hd0)
There was some mssg regardin successful install..something that said the process had succeeded but to no avail..m still stuck..:confused:
Btw i have a single hard disk..
You can also use grub's command line to investigate a computer:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)
This might tell you a little more about your partitions & give you some things to try.

I don't why the Hardy live cd won't boot...have you tried cleaning the cd drive(maybe blowing compressed air into it), or possibly burning a live cd on another computer(at the lowest speed possible)?

---

