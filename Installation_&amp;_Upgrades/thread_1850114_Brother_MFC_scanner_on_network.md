---
title: "Brother MFC scanner on network"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by smi402 on 2011-09-25
I upgraded my AMD64 system from Ubuntu 10.10 to 11.04 a few months ago. My setup includes a network Brother MFC-8460N printer/scanner/fax at IP 192.168.1.253. Following the upgrade the printer worked fine but I have not been able to use the scanner function. Running either ***xsane*** or ***sudo xsane*** starts "**scanning for devices**" but returns "**no devices available**". Both the printer and scanner functions were working under Ubuntu 10.10.

The **brscan2** driver for this printer is installed and appears to be configured correctly:

```
frank@server:~$ dpkg  -l  |  grep  Brother
ii  brmfc8460nlpr:i386                    2.0.1-1                                            Brother MFC-8460N LPR driver
ii  brscan2                               0.2.5-1                                            Brother Scanner Driver
ii  cupswrappermfc8460n:i386              2.0.1-2                                            Brother MFC8460N CUPS wrapper driver

frank@server:~$ brsaneconfig2  -q
Devices on network
  0 SCANNER             "MFC-8460N"         I:192.168.1.253
  1 scanner             "MFC-8460N"         I:192.168.1.253
```

I would be grateful for any assistance in getting this scanning function to work again.

---

### Post by smi402 on 2011-09-26
I have now managed to fix this scanning problem by removing and reinstalling the **brscan2** driver :D. It seems that **brscan2** may not have configured correctly when I upgraded from 10.10 to 11.04. The following procedure fixed the problem and the scanner is now working well.

Firstly download the correct **brscan2** package from the Brother site:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)
and put it on the Desktop. For my amd64 installation and the MFC-8460N printer/scanner/fax the code was:

```
frank@server: sudo apt-get remove brscan2

(ignore a number of reports of "No such file or directory" during installation)

frank@server: cd /usr/local/Brother
frank@server: ls -l
and check that the directory sane no longer exists.

frank@server: cd ~/Desktop
frank@server: sudo dpkg -i brscan2-0.2.5-1.amd64.deb

```

After installation is complete you need to configure the device and its IP address.

```
frank@server: sudo brsaneconfig2 -a name=SCANNER model=MFC-8460N ip=192.168.1.253

frank@server:~$ brsaneconfig2  -q
0 "MFC-9450CDN"
  1 "DCP-9042CDN"
  2 "MFC-8670DN"
  3 "DCP-9040CN"
  4 "MFC-9440CN"
.
.
.
 87 "DCP-750CN"
 88 "MFC-860CDN"

Devices on network
  0 SCANNER             "MFC-8460N"         I:192.168.1.253
confirms the scanner is installed at the correct IP address.

```

Finally test that the scanner device is found and is working:

```
frank@server:~$ xsane
```

:D:D

---

### Post by asado on 2011-11-21
thank you so much!:D:KS
" brother scanner mfc5440cn ubuntu 11.10 solved"
it helped me with my mfc 5440, on ubuntu 11.10 32 bit: 
1. i have determined the scaner ip : in my case it was 192.168.1.3
2. than just pasted your command with mods:
Kudos!!!
sudo brsaneconfig2 -a name=SCANNER model=MFC-5440CN ip=192.168.1.3

---

