---
title: "Help I dont want windows in my office, .sh install problems"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by whitelinux on 2013-05-08
Whilst I somehow have managed several linux web servers for many years I have a problem when trying to change from windows to linux for desktop machines in my office.

With the single exception of drivers everything works perfectly but...

I need to install several printer drivers I just fail miserably. Ill pick 1 to keep it simple.

I am trying to install a printer driver for a Xerox 8700 ColorQube. It say it supports Debian 64bit on their website and so I downloaded the .sh file. The machine is running Ubuntu 13.04 64 bit. Problem is when I run the .sh file that I download from Xerox site it launches a familer installer window which shows a Xerox screen, I hit Next and it starts the installation and then crashes out.

How do I troubleshoot an issue like this?

I have tried running the .sh file as root and makes no difference, Xerox whilst they support linux dont offer support. I dont want to run windows in the office and want to run linux but am embarresed in front of office staff that I can even get the printer driver to work :(

Any help would be much appreciated.

Thanks

---

### Post by darkod on 2013-05-08
Have you tried to let ubuntu install its own driver? Just open the Printers dialog, start Add new printer, and see if it offers a list to choose from and whether that model is in there. In most cases it can even detect the printer itself, even network printers (it did with my Epson SX510W connected on my home wi-fi network). I just pointed ubuntu to its IP.

---

### Post by whitelinux on 2013-05-08
Hi Darko,

I did try, it sees the printer and searches for the driver but doesnt find any. Then it gives me a list to choose from. I tried a few but didnt have much luck, Problem is the printers I am installing are not the most common types. They are label printers etc. It bothers me that I cant see why it is failing and dont know where to look to find why it it crashed.

I have another printer where I try to make the file and get some error about cups headers. Again ont know how to troubleshoot it.

---

### Post by darkod on 2013-05-08
I'm not sure where to look for crashed applications log. Maybe something like /var/log/messages or /var/log/dmesg. Check out different logs in /var/log. Not sure if cups has log on its own and whether the .sh script failing would be shown there at all (since it's not exactly cups).

---

### Post by whitelinux on 2013-05-08
Well, Cups has a log which just says:

[cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!

---

