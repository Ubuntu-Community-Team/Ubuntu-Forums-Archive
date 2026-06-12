---
title: "[SOLVED] Thunderbird fails after todays updates"
date: 2008-07-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-07-24
As the title says, I cant fire up Thunderbird after & Thunderbird upgrade today. I have checked all the usual logs but no mention to Thunderbird or errors show! Does anyone else have any problems with Thunderbird?


Cary

---

### Post by transporter_ii on 2008-07-24
Heck yeah! Not only Thunderbird, but evolution as well. 

The same setup I have used for 6 months now, and all of the sudden my accounts won't take a password. Just to test, I tried evolution...with no luck, either. 

However, I boot up in Windows, open up Outlook Express, and all of my e-mail starts downloading. Same passwords on Ubuntu and Outlook Express. Nothing has changed anywhere.

It has to be a problem with the updates.

And really kind of annoying, because I check about 6 accounts, so once they all start failing, I have to hit each error message about 3 times to get through that account.

---

### Post by autocrosser on 2008-07-24
Time for a bug report---- I'll get one going & post back--I get this in a terminal:

dean1@linux:~/Desktop$ thunderbird
*** buffer overflow detected ***: /usr/lib/thunderbird/thunderbird-bin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7430388]
/lib/tls/i686/cmov/libc.so.6[0xb742e4b0]
/lib/tls/i686/cmov/libc.so.6[0xb742ec18]
/usr/lib/thunderbird/thunderbird-bin[0x804c8e4]
/usr/lib/thunderbird/thunderbird-bin[0x805276a]
/usr/lib/thunderbird/thunderbird-bin[0x804e550]
/usr/lib/thunderbird/thunderbird-bin[0x804ad3f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb734c685]
/usr/lib/thunderbird/thunderbird-bin[0x804ac61]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:22 4227111    /usr/lib/thunderbird/thunderbird-bin
0805b000-0805c000 r--p 00012000 08:22 4227111    /usr/lib/thunderbird/thunderbird-bin
0805c000-0805d000 rw-p 00013000 08:22 4227111    /usr/lib/thunderbird/thunderbird-bin
088ed000-0890e000 rw-p 088ed000 00:00 0          [heap]
b71fe000-b7201000 rw-p b71fe000 00:00 0 
b7201000-b7205000 r-xp 00000000 08:22 6041159    /usr/lib/libXdmcp.so.6.0.0
b7205000-b7206000 rw-p 00003000 08:22 6041159    /usr/lib/libXdmcp.so.6.0.0
b7206000-b7208000 r-xp 00000000 08:22 6041157    /usr/lib/libXau.so.6.0.0
b7208000-b7209000 rw-p 00001000 08:22 6041157    /usr/lib/libXau.so.6.0.0
b7209000-b7210000 r-xp 00000000 08:22 4415665    /lib/tls/i686/cmov/librt-2.8.90.so
b7210000-b7211000 r--p 00007000 08:22 4415665    /lib/tls/i686/cmov/librt-2.8.90.so
b7211000-b7212000 rw-p 00008000 08:22 4415665    /lib/tls/i686/cmov/librt-2.8.90.so
b7212000-b7213000 rw-p b7212000 00:00 0 
b7213000-b7214000 r-xp 00000000 08:22 6041163    /usr/lib/libxcb-xlib.so.0.0.0
b7214000-b7215000 r--p 00000000 08:22 6041163    /usr/lib/libxcb-xlib.so.0.0.0
b7215000-b7216000 rw-p 00001000 08:22 6041163    /usr/lib/libxcb-xlib.so.0.0.0
b7216000-b723e000 r-xp 00000000 08:22 4415561    /lib/libpcre.so.3.12.1
b723e000-b723f000 r--p 00027000 08:22 4415561    /lib/libpcre.so.3.12.1
b723f000-b7240000 rw-p 00028000 08:22 4415561    /lib/libpcre.so.3.12.1
b7240000-b7264000 r-xp 00000000 08:22 6041233    /usr/lib/libexpat.so.1.5.2
b7264000-b7266000 r--p 00023000 08:22 6041233    /usr/lib/libexpat.so.1.5.2
b7266000-b7267000 rw-p 00025000 08:22 6041233    /usr/lib/libexpat.so.1.5.2
b7267000-b728f000 r-xp 00000000 08:22 6041396    /usr/lib/libpixman-1.so.0.10.0
b728f000-b7291000 rw-p 00028000 08:22 6041396    /usr/lib/libpixman-1.so.0.10.0
b7291000-b72a8000 r-xp 00000000 08:22 6041161    /usr/lib/libxcb.so.1.0.0
b72a8000-b72a9000 r--p 00016000 08:22 6041161    /usr/lib/libxcb.so.1.0.0
b72a9000-b72aa000 rw-p 00017000 08:22 6041161    /usr/lib/libxcb.so.1.0.0
b72aa000-b72ab000 rw-p b72aa000 00:00 0 
b72ab000-b72b1000 r-xp 00000000 08:22 6042901    /usr/lib/libxcb-render.so.0.0.0
b72b1000-b72b2000 r--p 00005000 08:22 6042901    /usr/lib/libxcb-render.so.0.0.0
b72b2000-b72b3000 rw-p 00006000 08:22 6042901    /usr/lib/libxcb-render.so.0.0.0
b72b3000-b72b6000 r-xp 00000000 08:22 6043003    /usr/lib/libxcb-render-util.so.0.0.0
b72b6000-b72b7000 r--p 00002000 08:22 6043003    /usr/lib/libxcb-render-util.so.0.0.0
b72b7000-b72b8000 rw-p 00003000 08:22 6043003    /usr/lib/libxcb-render-util.so.0.0.0
b72b8000-b72dc000 r-xp 00000000 08:22 6041399    /usr/lib/libpng12.so.0.27.0
b72dc000-b72de000 rw-p 00023000 08:22 6041399    /usr/lib/libpng12.so.0.27.0
b72de000-b72f6000 r-xp 00000000 08:22 4415550    /lib/libselinux.so.1
b72f6000-b72f7000 r--p 00017000 08:22 4415550    /lib/libselinux.so.1
b72f7000-b72f8000 rw-p 00018000 08:22 4415550    /lib/libselinux.so.1
b72f8000-b7300000 r-xp 00000000 08:22 6041441    /usr/lib/libXcursor.so.1.0.2
b7300000-b7301000 rw-p 00007000 08:22 6041441    /usr/lib/libXcursor.so.1.0.2
b7301000-b7302000 rw-p b7301000 00:00 0 
b7302000-b7307000 r-xp 00000000 08:22 6041371    /usr/lib/libXrandr.so.2.1.0
b7307000-b7308000 rw-p 00005000 08:22 6041371    /usr/lib/libXrandr.so.2.1.0
b7308000-b730f000 r-xp 00000000 08:22 6041445    /usr/lib/libXi.so.6.0.0
b730f000-b7310000 rw-p 00006000 08:22 6041445    /usr/lib/libXi.so.6.0.0
b7310000-b7318000 r-xp 00000000 08:22 6041369    /usr/lib/libXrender.so.1.3.0
b7318000-b7319000 r--p 00007000 08:22 6041369    /usr/lib/libXrender.so.1.3.0
b7319000-b731a000 rw-p 00008000 08:22 6041369    /usr/lib/libXrender.so.1.3.0
b731a000-b7327000 r-xp 00000000 08:22 6041193    /usr/lib/libXext.so.6.4.0
b7327000-b7329000 rw-p 0000c000 08:22 6041193    /usr/lib/libXext.so.6.4.0
b7329000-b732d000 r-xp 00000000 08:22 6041167    /usr/lib/libXfixes.so.3.1.0
b732d000-b732e000 rw-p 00003000 08:22 6041167    /usr/lib/libXfixes.so.3.1.0
b732e000-b732f000 rw-p b732e000 00:00 0 
b732f000-b7331000 r-xp 00000000 08:22 6041443    /usr/lib/libXdamage.so.1.1.0
b7331000-b7332000 rw-p 00001000 08:22 6041443    /usr/lib/libXdamage.so.1.1.0
b7332000-b7334000 r-xp 00000000 08:22 6041439    /usr/lib/libXcomposite.so.1.0.0
b7334000-b7335000 r--p 00001000 08:22 6041439    /usr/lib/libXcomposite.so.1.0.0
b7335000-b7336000 rw-p 00002000 08:22 6041439    /usr/lib/libXcomposite.so.1.0.0
b7336000-b748e000 r-xp 00000000 08:22 4415646    /lib/tls/i686/cmov/libc-2.8.90.so
b748e000-b7490000 r--p 00158000 08:22 4415646    /lib/tls/i686/cmov/libc-2.8.90.so
b7490000-b7491000 rw-p 0015a000 08:22 4415646    /lib/tls/i686/cmov/libc-2.8.90.so
b7491000-b7494000 rw-p b7491000 00:00 0 
b7494000-b74a0000 r-xp 00000000 08:22 4415567    /lib/libgcc_s.so.1
b74a0000-b74a1000 r--p 0000b000 08:22 4415567    /lib/libgcc_s.so.1
b74a1000-b74a2000 rw-p 0000c000 08:22 4415567    /lib/libgcc_s.so.1
b74a2000-b7585000 r-xp 00000000 08:22 6038235    /usr/lib/libstdc++.so.6.0.10
b7585000-b7589000 r--p 000e3000 08:22 6038235    /usr/lib/libstdc++.so.6.0.10
b7589000-b758a000 rw-p 000e7000 08:22 6038235    /usr/lib/libstdc++.so.6.0.10
b758a000-b7590000 rw-p b758a000 00:00 0 
b7590000-b75b4000 r-xp 00000000 08:22 4415651    /lib/tls/i686/cmov/libm-2.8.90.so
b75b4000-b75b5000 r--p 00023000 08:22 4415651    /lib/tls/i686/cmov/libm-2.8.90.so
b75b5000-b75b6000 rw-p 00024000 08:22 4415651    /lib/tls/i686/cmov/libm-2.8.90.so
b75b6000-b75b7000 rw-p b75b6000 00:00 0 
b75b7000-b75bb000 r-xp 00000000 08:22 6037826    /usr/lib/libgthread-2.0.so.0.1704.0
b75bb000-b75bc000 r--p 00003000 08:22 6037826    /usr/lib/libgthread-2.0.so.0.1704.0
b75bc000-b75bd000 rw-p 00004000 08:22 6037826    /usr/lib/libgthread-2.0.so.0.1704.0
b75bd000-b76a8000 r-xp 00000000 08:22 6041165    /usr/lib/libX11.so.6.2.0
b76a8000-b76a9000 r--p 000ea000 08:22 6041165    /usr/lib/libX11.so.6.2.0
b76a9000-b76ab000 rw-p 000eb000 08:22 6041165    /usr/lib/libX11.so.6.2.0
b76ab000-b76ac000 rw-p b76ab000 00:00 0 
b76ac000-b7761000 r-xp 00000000 08:22 6037820    /usr/lib/libglib-2.0.so.0.1704.0
b7761000-b7762000 r--p 000b4000 08:22 6037820    /usr/lib/libglib-2.0.so.0.1704.0
b7762000-b7763000 rw-p 000b5000 08:22 6037820    /usr/lib/libglib-2.0.so.0.1704.0
b7763000-b7766000 r-xp 00000000 08:22 6037822    /usr/lib/libgmodule-2.0.so.0.1704.0
b7766000-b7767000 r--p 00002000 08:22 6037822    /usr/lib/libgmodule-2.0.so.0.1704.0
b7767000-b7768000 rw-p 00003000 08:22 6037822    /usr/lib/libgmodule-2.0.so.0.1704.0
b7768000-b77a6000 r-xp 00000000 08:22 6037824    /usr/lib/libgobject-2.0.so.0.1704.0
b77a6000-b77a7000 r--p 0003d000 08:22 6037824    /usr/lib/libgobject-2.0.so.0.1704.0
b77a7000-b77a8000 rw-p 0003e000 08:22 6037824    /usr/lib/libgobject-2.0.so.0.1704.0
b77a8000-b77d3000 r-xp 00000000 08:22 6040702    /usr/lib/libfontconfig.so.1.3.0
b77d3000-b77d4000 r--p 0002a000 08:22 6040702    /usr/lib/libfontconfig.so.1.3.0
b77d4000-b77d5000 rw-p 0002b000 08:22 6040702    /usr/lib/libfontconfig.so.1.3.0
b77d5000-b77d6000 rw-p b77d5000 00:00 0 
b77d6000-b77ea000 r-xp 00000000 08:22 6039517    /usr/lib/libz.so.1.2.3.3
b77ea000-b77ec000 rw-p 00013000 08:22 6039517    /usr/lib/libz.so.1.2.3.3
b77ec000-b785d000 r-xp 00000000 08:22 6041391    /usr/lib/libfreetype.so.6.3.17
b785d000-b7861000 r--p 00070000 08:22 6041391    /usr/lib/libfreetype.so.6.3.17
b7861000-b7862000 rw-p 00074000 08:22 6041391    /usr/lib/libfreetype.so.6.3.17
b7862000-b78a0000 r-xp 00000000 08:22 6041425    /usr/lib/libpango-1.0.so.0.2101.2
b78a0000-b78a2000 r--p 0003d000 08:22 6041425    /usr/lib/libpango-1.0.so.0.2101.2
b78a2000-b78a3000 rw-p 0003f000 08:22 6041425    /usr/lib/libpango-1.0.so.0.2101.2
b78a3000-b790b000 r-xp 00000000 08:22 6045430    /usr/lib/libcairo.so.2.17.5
b790b000-b790d000 r--p 00067000 08:22 6045430    /usr/lib/libcairo.so.2.17.5
b790d000-b790e000 rw-p 00069000 08:22 6045430    /usr/lib/libcairo.so.2.17.5
b790e000-b7975000 r-xp 00000000 08:22 6037818    /usr/lib/libgio-2.0.so.0.1704.0
b7975000-b7976000 r--p 00067000 08:22 6037818    /usr/lib/libgio-2.0.so.0.1704.0
b7976000-b7977000 rw-p 00068000 08:22 6037818    /usr/lib/libgio-2.0.so.0.1704.0
b7977000-b7980000 Aborted (core dumped)

---

### Post by autocrosser on 2008-07-24
Found two new reported bugs---

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/251657](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/251657)

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/251602](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/251602)

Both about the issue--will add to the earliest one.

---

### Post by caryb on 2008-07-24
The plot thickens! Kmail runs for about 5 mins then crashes! I have tried Evolution, it shows folders but wont suck emails from IMAP server.


Cary

---

### Post by transporter_ii on 2008-07-24
Well guys,

I don't think it is a Thunderbird or Evolution problem, but some type of TCP/IP problem.

From a Window's machine do this:

telnet pop.yourserver.com 110

user [email]username@example.net[/email]
+OK 
pass yourpassword

I get response: +OK logged in.

If I do the exact same thing from Ubuntu 8.04 w/ latest updates, and coming from the same LAN and going out through the same router, I get:

user [email]username@example.net[/email]
+OK 
pass yourpassword

I get response: -ERR authorization failed.

Now it couldn't be Thunderbird if it does it from Telnet and still fails.

Here is the weird thing,

I can still check e-mail to a Microsoft Exchange server and to gmail pop3 servers, but the pop3 servers that fail for me are hosted on FreeBSD servers.

I'm not crazy, the same ones that now fail on Ubuntu are the same ones that work on my Windows XP system. Same user names, same passwords.

I even did wireshark on the Thunderbird traffic and it is sending the correct user name and password.

I have an Ubuntu 7.10 system at work and it checked the same e-mail accounts all day with no errors.

---

### Post by caryb on 2008-07-24
Thunderbird doesn't get to connect stage! It crashes before it finishes starting up.


Cary

Just tested from Outlook/XP & connects ok!

Cary

---

### Post by transporter_ii on 2008-07-25
Ok, just a coincidence. Thunderbird did fail for me just today, but the real problem was a DNS issue for me. Sorry.

I changed my DNS to use OpenDNS servers, and they are returning the wrong IP address for some odd reason. My windows system has static DNS in it to the old DNS servers, which work. 

AHhhhhhhhhhh!

---

### Post by lithorus on 2008-07-25
These work :
[http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.16+nobinonly-0ubuntu0.8.04.1_amd64.deb)

---

### Post by andrek on 2008-07-25
Fix has been released ( [https://launchpad.net/ubuntu/+source/thunderbird/2.0.0.16+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/+source/thunderbird/2.0.0.16+nobinonly-0ubuntu2) ), successfully built but not uploaded on repositories yet.

---

### Post by andrek on 2008-07-25
Okay, the update has just showed up. Mozilla Thunderbird works great now. (finally!)

---

### Post by autocrosser on 2008-07-25
Thanks!!  I downgraded to Hardy's version til this blew over......

---

### Post by ViRMiN on 2008-07-25
> **andrek said:**
> Okay, the update has just showed up. Mozilla Thunderbird works great now. (finally!)

Hmmm... I can't get it yet... and I'm using the "Main Server" mirror... what are you using?

No matter... doing an "apt-get upgrade" instead of "apt-get dist-upgrade", and pulling it down :)

---

### Post by ViRMiN on 2008-07-25
Fixed!  Nice!  I had having to resort to webmail... yuck!

---

### Post by caryb on 2008-07-25
Well I had to find alternatives for a day, what I can say is that Kmail is a unreliable clunky pig & Evolution would be my 2nd choice behind Thunderbird.


Cary

---

