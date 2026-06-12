---
title: "Network Epson 4760 All-in-one for scanning"
date: 2020-06-19
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2020-06-19
I have installed the Epson .pkg from the Seiko Epson site and the printing works great over LAN. In fact, Ubuntu is faster than WIN10 sending files to the printer. I can open a terminal and ping 192.168.1.20. No joy trying to use the scanner with Ubuntu. WIN10 version of the Epson package install granted scanner functionality so I know I have a Linux configuration problem.

Invoking the program 'imagescan' brings up it can not find any scanner. Same for any other scan program installed in Ubuntu 18.04 -- SimpleScan, Insane -- none finds a scanner over my LAN. There is a lot of conflicting advice from my online researching about which .conf file to edit and which symlink to add to Ubuntu. Any help?

---

### Post by dino99 on 2020-06-20
have you used that link ? [http://support.epson.net/linux/en/imagescanv3.php#ubuntu](http://support.epson.net/linux/en/imagescanv3.php#ubuntu)

---

### Post by Unterseeboot_234 on 2020-06-20
Yes, I have used the proprietary Linux downloads for the Epson printer(s). According to my online research the drivers install and work the scanner if you have Ubuntu 20.xx but there is some missing patch for Ubuntu 18.04. Also, there is confusion on some people's part by wanting a USB-connected printer and the forums giving advice about networking the printer. The printer function of my Epson 4760 works. It is the scanner functionality of this printer that isn't linked to any Linux scanner applications.

---

### Post by Impavidus on 2020-06-20
I (or rather, my dad, but I had to do the installation on the Linux systems) recently got an Epson XP-2100 all-in-one, which may have a similar installation procedure. I made some notes (on Ubuntu 19.10) for when I want to reinstall:> Installation of the Epson XP-2100 printer/scanner

Setup the network connection of the printer using WPS. Download the software to the computer. The following packages are required:
- epson-inkjet-printer-escpr_1.7.7-1lsb3.2_amd64.deb (printer driver)
- epson-printer-utility_1.1.1-1lsb3.2_amd64.deb (additional printer software)
- imagescan-bundle-ubuntu-19.10-3.62.0.x64.deb.tar.gz (scanner software)
&#8594; Can be downloaded from [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)
- lsb
   &#8594; Can be installed from the official repos.
Change versions for the appropriate release of Ubuntu. Install the software.

Use printer settings to set up the network printer. All works automagically.

To set up the scanner, the file /etc/imagescan/imagescan.conf has to be modified. First find the IP address of the scanner:```
nmap -sn 192.168.2.0/24
```Then write the following lines in the config file:```
[devices]

net.udi = networkscan:esci://192.168.2.7:1865
net.vendor = Epson
net.model = XP-2100
```Substitute the correct IP address. Now imagescan should find the scanner.
I still have to set the scanner up to use a fixed IP address, if I can. I don't use the scanner a lot, so it hasn't got a high priority.

---

### Post by Unterseeboot_234 on 2020-06-20
Thanks Impavidus for responding. The SANE backend-compatibility website was about to lead me down a rabbit hole. After contemplating your suggestion I tried editing /etc/imagescan/imagescan.conf with my attributes and the scanner worked!

Comments for anyone following behind this via search or whatever:

1. The installation of the Epson proprietary drivers on Ubuntu 18.04 LTS did not initially create a folder /etc/imagescan/imagescan.conf. However, that folder with the one file was generated after I fired up the application ImageScan. Also, during the installation no menu shortcuts or Desktop launch icons were created. So, in my researching I recall mention some of this was fixed in Ubuntu 20.xxx.  

2. I launch the application Imagescan with a Terminal --> Ctrl-alt-t and then type imagescan

3. I had to edit imagescan.conf with my attributes and also delete the leading semi-colons which comment out the lines provided with the generated file

```
[devices]

net.udi = networkscan:esci://192.168.1.20:1865
net.vendor = Epson
net.model = ET-4760
```

---

