---
title: "Complete system"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Butcher on 2007-07-06
Hello, this is my first time installing a complete webserver/ftp-server, and I need some help doing it. As you probably understood, I am making a complete webserver/ftp-server, so I need:
- XAMPP for Linux (it includes more features than LAMP)
- FTP Server
- WPA connection

Though this might seem an easy thing to compile to most, I've never used Linux before, and don't know how to. I already figured out that I should get Ubuntu Server, but how do I make sure it has a working LAMP, FTP Server and WPA ability included?

I will mainly be using it to test out websites, scripts and similiar on it, and want to be able to move the files there via a FTP client from my main computer. Could someone please explain how I can get this all on a CD/DVD?

---

### Post by whizbaby on 2007-07-06
> **Butcher said:**
>  Could someone please explain how I can get this all on a CD/DVD?
Err, download and install perhaps?:tongue:
But serious, during install of the server CD you get the option to install LAMP and ftp, for wpa look over forum (I think its supported by default but I never needed it till now,) or perhaps someone else knows?
(btw no compiling needed at all for your services)

---

### Post by Butcher on 2007-07-06
I meant like where do I put the packages, and is LAMP the package from Apachefriends?

[quote="Apachefriends.org"]The distribution for Linux systems contains: Apache, MySQL, PHP & PEAR, Perl, ProFTPD, phpMyAdmin, OpenSSL, GD, Freetype2, libjpeg, libpng, gdbm, zlib, expat, Sablotron, libxml, Ming, Webalizer, pdf class, ncurses, mod_perl, FreeTDS, gettext, mcrypt, mhash, eAccelerator, SQLite and IMAP C-Client.[/quote]

And I found the whole "wpasupplicant", but how do I get it installed? I tried connecting using WPA on Ubuntu Desktop, but he did not manage to do it. And I am completely sure I had the right settings, copied and pasted from my router settings and sent over by USB stick.

I think there is a directory where I should put these packages or something to be able to install them from the Ubuntu Server command interface, but seeing as I never used Linux I don't know much about navigating to files or installing packages and the likes.

And when it is all in the Ubuntu Server folder, I can make a new .iso out of it and re-burn it on a new CD. Then I won't have problems getting packages over the net, as WPA will be installed and the other packages making it a completely ready webserver.

---

### Post by whizbaby on 2007-07-06
No need installing wpasupplicant, its already installed! Next thing, in linux you dont install software like that (downloading manually from the internet and installing 'by hand'), you use apt-get and apt-cache, e.g. you search a package named wpasupplicant, you type

apt-cache search wpasupplicant

and get a 'list' of packages. You could have searched for wpa, too, that would give you a longer list. Or, if you feel uncomfortable with terminal, use synaptic (though as a server op you should spend a little time learning/understanding term...).
As to the LAMP server, thats not a package, its a script installing apache, mysql, php and some apache.org mods I think. You can crosscheck on 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Butcher on 2007-07-06
So, WPA is already there? I do not need to connect to the internet in any way? Will check it out. But if I for example wanted to install LAMPP (XAMPP for Linux, not the same as LAMP), could I just download the .tar.gz file, put it on a USB stick and use "apt-chache search 'filename'"?

---

### Post by whizbaby on 2007-07-06
Sorry, no. Your apt-cache will be the one from the CD.  To explain a bit how it works:
with apt-cache you can retrieve package lists/descriptions from the url's shown in /etc/apt/sources.list. These packages can be installed via apt-get (apt-get install name_of_package). Starting from CD without internet connection will give you only the software packages on the CD. Isn't there a list of programs going with server CD that you could check to see if all you need is included? If not, you may have to download the missing (.deb) packages from the ubuntu repository and install via dpkg -i package_name. All would be a lot easyer if the machine could reach the network repositories...(e.g. temporarily)

---

### Post by Butcher on 2007-07-07
I found WPASUPPLICANT  inside **\pool\main\w\wpasupplicant** (browsing the CD in windows), but whenever I did a **sudo apt install wpasupplicant**, he said package missing. The only way I can connect to the network in my house is by WPA, but the odd thing is that when I tried connecting to it in Ubuntu-Desktop it did not work. Maybe I need drivers for my network card (the computer was originally a Windows).

And since I cannot view other networks in the area, I cannot temporarily connect to the internet either. And I do not have any free cables connected to the router, they are all in use.

But if I were for example to add the XAMPP for Linux package, where should I place it? Or if I tried it by USB stick, how would I access it? I am very used to Windows showing me Hard Disks and connected devices, but how do I determine what is where in Linux? If I put it on a USB stick, and connect it, how do I access the files from it in Ubuntu Server mode?

---

### Post by whizbaby on 2007-07-08
So, what WPA hardware do you have?
In linux you can type (e.g.) 'dmesg', that is a protocol of the 'kernel ring buffer' and will show up detected devices. If its a PCI card you could also type 'lspci -v' (if its connected via usb type  'lsusb').
To add a package. you would download a .deb package (a file ending up with .deb) and install it by 'sudo dpkg -i name_of_package'. You could also download the source and compile it (not really recommended for beginners). If theres no .deb package, maybe theres a .rpm package. This one can be turned into .deb. If theres NO package and only sources youll have to compile...

---

### Post by Butcher on 2007-07-08
It is a HP Compaq nx6325, and according to them has this card:

[quote="HP"]**Wireless Devices:**
Support for a broad range of secure, integrated wireless LAN options featuring support for the latest industry standards. Integrated Bluetooth is also an option (factory configurable only) and can be combined with any of the supported wireless LAN options.
**All integrated wireless LAN options:**
Wi-Fi certified
Cisco Compatible Extensions support (Version 3.0)
Wired Equivalent Privacy (WEP) support up to 128-bit keys
Wi-Fi Protected Access (WPA) and WPA2 support
802.1x authentication support, including EAP-TLS, EAP-TTLS, PEAP-GTC, PEAP-MSCHAPv2, and LEAP
Advanced Encryption Standard (AES) support
WiFi certified for WPA2, WMM 
Dual antennas integrated in the display enclosure
**Broadcom 4311AG WiFi Adapter:**
Integrated support for 802.11a, b and g
Up to 54-mbps data rate 
**Broadcom 4311BG WiFi Adapter:**
Integrated support for 802.11 b and g
Up to 54-mbps data rate
HP Integrated Module with Bluetooth 2.0 Wireless Technology (only available with 3-3-0 warranty)	Bluetooth Specification v2.0 compliant
[/quote]

While I ran it on windows, I could connect to WPA with it. Though now that I ran the **lspci -v** command, Ubuntu told me this:

[quote="Ubuntu Terminal Application"]30:00.0 Network Controller: Broadcom Corporation BCM4310 UART (rv 01)
Subsystem: Hewlett-Packard Company Unknown device 30b0
Flags: bus master, medium devsel, latency 64, IRQ 16
Memory at 30019000 (32-bit, non-prefetchable) [size=256]
Capabilities: [80] Power Management version 2[/quote]

And since it says "Unknown device", I am going to guess I need a driver for it, but where could I find a linux driver for it? I am now running Ubuntu Desktop to test WPA, and I can still not connect (valid credentials and settings). So a driver is needed I think, does anyone make drivers for network cards that work with Linux?

---

### Post by Butcher on 2007-07-11
I actually found a driver, from [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/), and I downloaded it (.tar.bz2 file), but how do I install it? The readme was very simple, and gave me no clue about what file to execute or where to put the files. Does anyone know how to use this driver?

---

