---
title: "Super slow kernel startup"
date: 2017-08-22
forum: Installation &amp; Upgrades
---

### Post by elstongunnn on 2017-08-22
[COLOR=#111111][FONT=Ubuntu]My Samsung series 5 notebook (i5, 500gb hdd, 4gb ram) has a super slow boot for Ubuntu 16.04.3 LTS (I have a dual boot Windows 10 - Ubuntu 16.04.3 LTS)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I write:
```
[FONT=Consolas]systemd-analyze[/FONT]
```

in the terminal and the output is:

> [FONT=inherit]Startup finished in 41min 44.874s (kernel) + 36.641s (userspace) = 42min 21.516s[/FONT]

What can I do?

[/FONT][/COLOR]

---

### Post by sp40140 on 2017-08-22
What are the hardware specs? All of your hardware and any peripherals (like printers, bluetooth even Wi-Fi, mouse and keyboard).
Is there any change in boot time when it's plugged into power or not?

BTW, I am really surprised that you waited 42 minutes to confirm if your laptop works or not!

---

### Post by Autodave on 2017-08-22
Did this happen all of a sudden? Did it ever boot correctly into Ubuntu?

---

### Post by elstongunnn on 2017-08-22
I installed Ubuntu last week and each time I turn it on I have to wait all that time!

I'm connected to WiFi, bluetooth is off, I don't have any external keyboard... My computer has 3 USB (two 2.0 and one 3.0), ethernet port, hdmi port.

It doesn't matter if it's plugged into power or not.

---

### Post by sp40140 on 2017-08-22
> **elstongunnn said:**
> I installed Ubuntu last week and each time I turn it on I have to wait all that time!

I'm connected to WiFi, bluetooth is off, I don't have any external keyboard... My computer has 3 USB (two 2.0 and one 3.0), ethernet port, hdmi port.

It doesn't matter if it's plugged into power or not.

Disable Wi-Fi and reboot, see if that changes anything.
Also, you mentioned the USB ports, but didn't mention what is connected to them.

Also, have you checked the logs (in /var/log) for any issues / errors?
Does screen show any errors during boot or just blank screen?
Also, what is the partition size of ubuntu install? And how many partitions on HDD?

---

### Post by elstongunnn on 2017-08-23
> **sp40140 said:**
> Disable Wi-Fi and reboot, see if that changes anything.
Also, you mentioned the USB ports, but didn't mention what is connected to them.

Also, have you checked the logs (in /var/log) for any issues / errors?
Does screen show any errors during boot or just blank screen?
Also, what is the partition size of ubuntu install? And how many partitions on HDD?

- I'm going to disable wifi and reboot, but not now because I have to work and I can't waste 1 hour haha
- Nothing is connected to the USB ports[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
- The screen is in a plain purple color for 40 minutes
- 2 partitions: 80gb for ubuntu and approximately 390gb for windows 10

---

