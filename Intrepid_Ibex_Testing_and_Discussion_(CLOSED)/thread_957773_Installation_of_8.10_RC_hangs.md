---
title: "Installation of 8.10 RC hangs"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rozbarwinek on 2008-10-24
The ubuntu 8.10 RC installer hangs after some time of showing ubuntu orange progressbar. It's showing "starting bluetooth" and nothing happens. Any ideas?

---

### Post by ddrichardson on 2008-10-25
Edit: Withdrawn

---

### Post by rozbarwinek on 2008-10-26
> **ddrichardson said:**
> Edit: Withdrawn

???

---

### Post by Peter09 on 2008-10-26
try editing the boot command line

at the grub prompt type esc.
use the E key to edit the middle line. Remove the splash and quiet options and put in the option ```
NOAPIC
```

see if it makes a difference

---

### Post by ddrichardson on 2008-10-26
noapic mightn't help with the RC, there have been people reporting problems with bluetooth locking boot though.  The edit is because of a disagreement with someone on IRC.

---

### Post by rozbarwinek on 2008-10-26
So... what now?

---

### Post by ddrichardson on 2008-10-26
Does 8.04 work?

---

### Post by rozbarwinek on 2008-10-26
I found a solution :D
I just have to unplug all my usb devices and than installer work normally :D

---

### Post by ddrichardson on 2008-10-26
Do you have a USB bluetooth dongle?

---

### Post by rozbarwinek on 2008-10-26
> **ddrichardson said:**
> Do you have a USB bluetooth dongle?

No, I have usb modem. And new problem come up :| when I unplug modem and install ubuntu 8.10 I have to install modem drivers so I plug modem usb cable and then system won't start when there is usb device plugged :| so I don't have internet connection in ubuntu :| Any ideas?

---

### Post by ddrichardson on 2008-10-26
When Ubuntu is running, if you open a terminal and insert the USB device, then type:
```
dmesg
```
Are there any messages about USB device recognition, particularly any about being able to chose a configuration?

---

### Post by rozbarwinek on 2008-10-26
> **ddrichardson said:**
> When Ubuntu is running, if you open a terminal and insert the USB device, then type:
```
dmesg
```
Are there any messages about USB device recognition, particularly any about being able to chose a configuration?

Here you have result of dmesg:

[http://wklej.org/id/13025/](http://wklej.org/id/13025/)

My modem is Speedtouch.

---

### Post by Sef on 2008-10-26
Moved to Ibex forum.

---

### Post by ddrichardson on 2008-10-26
Do you have a printer plugged in?

---

### Post by rozbarwinek on 2008-10-26
> **ddrichardson said:**
> Do you have a printer plugged in?

No, the only usb device I got is modem.

---

### Post by ddrichardson on 2008-10-26
I don't know much about Speedtouch, hopefully a developer will pick up on this thread.

---

### Post by rozbarwinek on 2008-10-26
> **ddrichardson said:**
> I don't know much about Speedtouch, hopefully a developer will pick up on this thread.

But I was not having any problems with 8.04 :|
I think that it's caused by new kernel :/

---

### Post by asti on 2008-10-26
I can confirm this. Also, I have a usb stick which doesn't mount.
According to [this]("http://bugs.archlinux.org/task/11747") thread, the problem is in the kernel.

---

### Post by rozbarwinek on 2008-10-26
> **asti said:**
> I can confirm this. Also, I have a usb stick which doesn't mount.
According to [this]("http://bugs.archlinux.org/task/11747") thread, the problem is in the kernel.

So, what now?
I have reported it to lunchpad.

---

### Post by ddrichardson on 2008-10-26
Remember that bug reports take time, its not like support. For the time being, as unconstructive as this sounds - stick with 8.04. 8.10 is still an RC.

---

### Post by rozbarwinek on 2008-10-29
So I have to wait for 9.04? :(

---

### Post by ddrichardson on 2008-10-29
There are kernel options you can try such as acpi=noirq or irqpoll but I am not aware of significant changes in these elements between 8.04 and 8.10. There are however bluetooth changes and if 8.04 works I would stay with it until the bug you reported is addressed or someone solves the issue.

I understand your frustration, I had to skip Edgy on one of my HP machines.

---

### Post by jerrylamos on 2008-10-29
> **rozbarwinek said:**
> So, what now?
I have reported it to lunchpad.

I got a giggle out of that, sorry.  It's "launchpad".....

Jerry

---

