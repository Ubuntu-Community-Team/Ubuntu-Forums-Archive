---
title: "linux-headers-2.3-23-generic Problem."
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by mrzl on 2010-12-17
Hey,
i am new to this forum and i have a big problem. Just today when i was working on my netbook with ubuntu installed it all of a sudden said the harddrive was full ( found out because i wasnt able to save files in eclipse anymore). i decided to restart the machine and since i did that i get to the login panel of ubuntu (which was actually turned to auto-login). when i login i get redirected to the login again with the message that that the gnome desktop is broken and that i should message the administrator. i tried several tutorials from the web to fix this and i got to the conclusion that there is a problem with the linux-headers-2.3-23-generic. when i try to reinstall/update it i get the message that there is a fatal error with this package saying Input/Output error. 
i could recover the system with the usbstick i got, but i have my entire uniwork on there, i would like to find out how to either save all files (which i can still access with the terminal when i boot as netboot) or get the problem with the package fixed.

hopefully one of you know anything about this problem or is willing to help me- i would appreciate this alot.

thanks in advance,
marcel

---

### Post by theozzlives on 2010-12-17
Normally if Linux says your drive is full, it means / partition is full. That can happen if you have a seperate /home and/or your log files get to big. I don't think it's a kernel issue.

---

### Post by mrzl on 2010-12-17
hi, thanks for ur quick reply. i only have one partition and everything i do concerning the old kernel package e.g. when i try to update ends up in an error says input/output error. i suspect that the harddrive just broke- i just got a message saying i/o error, dev sda, sector XXXXXXXXXX when i tried to update it again. 

actually the last two weeks, when the while system was still working, i couldnt update anything on the system and got the message that there is a problem with the kernel. but since it was still working i didnt care about this and just left it like it was. 

marcel

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

I would suggest to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would definitely help us diagnose the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by mrzl on 2010-12-23
Hello mates. i found out what the problem was. The drive was completely full- i dont know why though. via the netroot boot i deleted a few files and i was able to boot the computer as usual.

thanks alot anyway!

EDIT:
actually i still do get the input/output error at the linux headers package when i try to update anything on my ubuntu. i guess nobody needs the bootinfoscript output for that right?

cheers

---

### Post by sikander3786 on 2010-12-24
We need to see the output of apt-get.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mrzl on 2010-12-24
```
Nach dieser Operation werden 22,3MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Hole:1 http://archive.canonical.com/ubuntu/ lucid/partner adobereader-deu 9.4.1-1lucid1 [69,6MB]
Es wurden 21,0MB in 45s geholt (461kB/s)                                                                                                      
Extrahier Templates aus Paketen: 100%
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 95%dpkg: nicht behebbarer fataler Fehler, Abbruch:
 fehlgeschlagen in buffer_read(fd): Dateiliste des Paketes »linux-headers-2.6.32-26-generic«: Input/output error
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (2)
marcels@one-5xx:~$ 
```

its in german but i suppose people who know ubuntu kinda know what its meaning. if its not the case ill translate the important part here:
```

(reading database ... 95%dpkg: not solvable fatal error, aborting:
 failure in buffer_read(fd): datalist of packet »linux-headers-2.6.32-26-generic«: Input/output error
```

i really dont know how to fix this. any help is really appreciated.
M

---

### Post by sikander3786 on 2010-12-24
Try,

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get install -f
```

---

### Post by mrzl on 2010-12-24
everything is ok when i do those commands. should i update stuff again after this? thanks man.


EDIT:
when i follow ur instructions everything is ok, but the error is still not gone when i update et cetera. ahh

---

