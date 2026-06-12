---
title: "Gournal will not run"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by vmaaxt on 2008-10-20
[Gournal ]("http://www.adebenham.com/gournal/") will not run on my computer. I have installed it from every source I know of: the creators site, Apt-get, Synaptic. Every time it installs, and then when i click on it, it asks me if I want to display or run, so I click run. The tool bar flashes "starting Gournal" and then nothing happens. After I try this several times, I uninstall, and install with the next method. The only time Gournal actually ran was the first time I tried it. Then when I closed it, it didn't work again. 

Any help would be greatly appreciated. Thank you.

I am running Ubuntu 8.04, Hardy Heron

---

### Post by Partyboi2 on 2008-10-20
Install the version from the ubuntu repos
```
sudo apt-get install gournal
``` then after it has installed try starting it from the terminal (Applications>Accessories>Terminal)  with
```
gournal
```

---

### Post by vmaaxt on 2008-10-21
Thanks for the advice, but I get the following error:

When I apt-get install, ig et the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gournal is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
XML::Mini Error MESSAGE:XML::Mini::Document::fromFile() Can't find file 

```

Any Ideas? Thanks in advance.

---

### Post by Partyboi2 on 2008-10-21
Do you have libxml-mini-perl package installed?
```
dpkg -l libxml-mini-perl
``` and if so what version.

---

### Post by vmaaxt on 2008-10-22
When I enter```
dpkg -l libxml-mini-perl

```, I get:```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libxml-mini-pe 1.2.8-3        Perl implementation of the MiniXML XML gener

```, however, when I try:```
 sudo apt-get install  libxml-mini-perl

```, I get:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxml-mini-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So I have no idea what is going on.

---

