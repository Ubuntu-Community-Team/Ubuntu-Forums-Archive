---
title: "Update firmware for SpeedTouch 330 modem"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by cm666 on 2007-02-11
Hello,

I have installed 6.06, and need to upgrade the firmware of my SpeedTouch 330 USB modem. I have found some info explaining how to do for a 6.10 installation. I have two questions.

1. will it still work with 6.06?
2. What effect will the firmware upgrade have on my windows system (I am dual booting)?

Any advice much appreciated.

Thanks

---

### Post by teaker1s on 2007-02-11
The firmware as I understand it is loaded every time it is initalised. so changing the firmware files in ubuntu will have zero effect in windows:popcorn:    [http://www.linux-usb.org/SpeedTouch/firmware/index.html]("http://www.linux-usb.org/SpeedTouch/firmware/index.html")

---

### Post by cm666 on 2007-02-11
Thanks for that. I'll try it out.:)

---

### Post by cm666 on 2007-02-12
It went OK until I tried splitting the firmware, then I got this

cm1@cm1-desktop:~/speedtouch/firmware-extractor$ ./configure
FIRMWARE_DIR=/lib/firmware
cm1@cm1-desktop:~/speedtouch/firmware-extractor$ make
gcc -o firmware-extractor firmware.c
firmware.c:37:19: error: stdio.h: No such file or directory
firmware.c:38:20: error: stdlib.h: No such file or directory
firmware.c:39:20: error: string.h: No such file or directory
firmware.c:40:20: error: unistd.h: No such file or directory
firmware.c:41:19: error: fcntl.h: No such file or directory
firmware.c:42:22: error: sys/stat.h: No such file or directory
firmware.c: In function ‘extract_firmware’:
firmware.c:239: error: ‘NULL’ undeclared (first use in this function)
firmware.c:239: error: (Each undeclared identifier is reported only once
firmware.c:239: error: for each function it appears in.)
firmware.c:258: warning: initialization from incompatible pointer type
firmware.c:263: warning: comparison of distinct pointer types lacks a cast
firmware.c:263: warning: return from incompatible pointer type
firmware.c:268: warning: comparison of distinct pointer types lacks a cast
firmware.c:285: warning: comparison of distinct pointer types lacks a cast
firmware.c:287: warning: return from incompatible pointer type
firmware.c:296: warning: comparison of distinct pointer types lacks a cast
firmware.c:296: warning: pointer type mismatch in conditional expression
firmware.c:297: warning: comparison of distinct pointer types lacks a cast
firmware.c: In function ‘extract_firmware_phase’:
firmware.c:320: error: ‘NULL’ undeclared (first use in this function)
firmware.c:320: warning: comparison of distinct pointer types lacks a cast
firmware.c:321: warning: return from incompatible pointer type
firmware.c:330: warning: return from incompatible pointer type
firmware.c:339: warning: return from incompatible pointer type
firmware.c:346: warning: incompatible implicit declaration of built-in function ‘malloc’
firmware.c:346: warning: comparison of distinct pointer types lacks a cast
firmware.c:348: warning: return from incompatible pointer type
firmware.c:350: warning: incompatible implicit declaration of built-in function ‘memset’
firmware.c:352: warning: comparison of distinct pointer types lacks a cast
firmware.c:355: warning: return from incompatible pointer type
firmware.c:361: warning: incompatible implicit declaration of built-in function ‘memcpy’
firmware.c: In function ‘load_file’:
firmware.c:410: error: storage size of ‘statbuf’ isn’t known
firmware.c:418: error: ‘O_RDONLY’ undeclared (first use in this function)
firmware.c:420: error: ‘NULL’ undeclared (first use in this function)
firmware.c:420: warning: return from incompatible pointer type
firmware.c:426: warning: return from incompatible pointer type
firmware.c:430: error: request for member ‘st_size’ in something not a structure or union
firmware.c:430: warning: assignment makes integer from pointer without a cast
firmware.c:433: warning: incompatible implicit declaration of built-in function ‘malloc’
firmware.c:433: warning: comparison of distinct pointer types lacks a cast
firmware.c:436: warning: return from incompatible pointer type
firmware.c:444: warning: return from incompatible pointer type
firmware.c: In function ‘free_firmware’:
firmware.c:511: error: ‘NULL’ undeclared (first use in this function)
firmware.c:511: warning: assignment from incompatible pointer type
firmware.c:516: warning: assignment from incompatible pointer type
firmware.c: In function ‘usage’:
firmware.c:531: warning: incompatible implicit declaration of built-in function ‘fprintf’
firmware.c:531: error: ‘stderr’ undeclared (first use in this function)
firmware.c:531: warning: passing argument 1 of ‘fprintf’ discards qualifiers from pointer target type
firmware.c: In function ‘main’:
firmware.c:539: error: ‘NULL’ undeclared (first use in this function)
firmware.c:539: warning: initialization from incompatible pointer type
firmware.c:540: warning: initialization from incompatible pointer type
firmware.c:554: warning: comparison of distinct pointer types lacks a cast
firmware.c:557: warning: incompatible implicit declaration of built-in function ‘printf’
firmware.c:562: error: ‘O_CREAT’ undeclared (first use in this function)
firmware.c:562: error: ‘O_WRONLY’ undeclared (first use in this function)
firmware.c:562: error: invalid operands to binary |
firmware.c:562: error: ‘O_TRUNC’ undeclared (first use in this function)
firmware.c:562: error: invalid operands to binary |
firmware.c:576: error: invalid operands to binary |
firmware.c:576: error: invalid operands to binary |
make: *** [all] Error 1
cm1@cm1-desktop:~/speedtouch/firmware-extractor$ 

:confused: 
I hope that makes some sense!
Thanks in advance.
cm

---

### Post by teaker1s on 2007-02-12
you have installed
[COLOR="Red"] gcc 
Build-essential[/COLOR]

have you tried the zipped firmware on the link I gave you?

---

### Post by philip338 on 2007-02-12
Hi 
i am also having exactly the same problems with trying to get Speedtouch 330 rev 4 working on edgy eft i get exactly the same screen dump you get. I have tried just about every way shown in every thread over the last few weeks. Please can anyone help.

---

### Post by cm666 on 2007-02-13
I downloaded the firmware from speedtouch myself, the file names look the same as the one on your link, but I'll try it again.

What should I do about gcc, build essential??

thanks
cm

---

### Post by teaker1s on 2007-02-13
edgy package links without internet-burn to cd on another pc, you will need these to build source code

build-essential[http://http://packages.ubuntu.com/edgy/devel/build-essential]("http://http://packages.ubuntu.com/edgy/devel/build-essential")

[gcc there are choices, think you need latest]("http://packages.ubuntu.com/edgy/devel/")

[latest gcc]("http://packages.ubuntu.com/edgy/devel/gcc")

---

### Post by cm666 on 2007-02-13
I could use some help to install these packages, I think I need to do it from the command line as the most of the info on package installation seems to assume an internet connection already in place. Where should I put them, extract them etc?

thanks
cm

---

### Post by teaker1s on 2007-02-14
you also need to download all the required packages that gcc and build-essential require as dependencies and burn to cd.
Then if you open cd on your ubuntu and double click on packages and click the install button.

or you may find the the alternate.iso would make it simpler by using it with synaptic,add cd feature and then searching and installing-but I'm not sure it has all you need, maybe you could try it unless anyone reading the thread knows a exactly what packages the iso has

The second method will be 700mb so depending on your connection it may be better to just try and download what you need with option one

---

### Post by cm666 on 2007-02-14
Getting closer!

"build essential" is on the installation cd for 6.10, so I used that.

I've been following this guide:

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28usbadslmodem%29](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28usbadslmodem%29)

I've got as far as trying to copy a "secrets" file to "pap" or "chap" "-secrets". I can't modify these files or change the permissions. Is there another package I'm missing??

thanks
cm

---

### Post by Aliarse on 2007-02-14
Setting this modem up is a PITA. But, it is possible. Heres how i did it for 6.10, i assume it'll work for 6.06 too, although i haven't tried it.

Firtly, follow this guide until you get to the "And that's it, reboot and you should be online." part. [http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html) - Don't reboot after you've done this because you need to add some more stuff to get it working, 

When i just did the above, it would sync with my isp, but it wouldn't assign me an ip.

Now you need to do this.

```

**In the Terminal, copy/paste:**

sudo modprobe pppoatm
sudo gedit /etc/modules

**in the editor window that opens up, add**

pppoatm

**at the bottom of the list, save and exit.**

**Create a pppd connection script to control logging on to your ISP:**

sudo cp /usr/share/doc/ppp/examples/peers-pppoe /etc/ppp/peers/adslscript 
sudo gedit /etc/ppp/peers/adslscript

**change the line:**

# user "myusername@myprovider.net"

to:

user "your-own-isp-username@yourisp"
[B]
From the same file remove:[/B]

# Load the pppoe plugin. Change the ethernet interface name if needed. plugin rp-pppoe.so eth0

**and replace with**

# These options configure pppd to talk with the kernelspace speedtch driver. 
# Don't forget to adapt the VP.VC pair to your ISP/country settings. 
# (see http://www.linux-usb.org/SpeedTouch/faq/index.html#q12) 
plugin pppoatm.so 
0.38 #UK

```

Then restart and you should be online. To check this you can either simply try browsing the web, Or open a terminal and type tail -f /var/log/syslog, which should show you your allocated ip and DNS info.

Hope this helps, i know that it took me ages to find all the correct info to get it working, but now i have, i can set this up in 5 min's tops.

---

### Post by cm666 on 2007-02-16
Thanks for that.

I've got to the point where I try the "tail" command. See the output below. I don't think I'm quite there yet! Any Ideas?


cm1@cm1-desktop:~$ tail -f /var/log/syslog
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): starting (version 2.16.0), pid 4358 user 'cm1'
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readwrite:/home/cm1/.gconf" to a writable configuration source at position 1
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 16 14:37:56 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb 16 14:37:59 cm1-desktop kernel: [  519.010862] NET: Registered protocol family 10
Feb 16 14:37:59 cm1-desktop kernel: [  519.011228] lo: Disabled Privacy Extensions
Feb 16 14:37:59 cm1-desktop kernel: [  519.011538] IPv6 over IPv4 tunneling driver
Feb 16 14:38:05 cm1-desktop gconfd (cm1-4358): Resolved address "xml:readwrite:/home/cm1/.gconf" to a writable configuration source at position 0

---

### Post by Linux-N00b on 2007-05-10
O.k. I got a bigger problem...
I can do all of that stuff, I did divide the firmare following [http://www.linux-usb.org/SpeedTouch/firmware/index.html](http://www.linux-usb.org/SpeedTouch/firmware/index.html)
But my biggest problem is that my ISP does not give us username nor password so all of my tries are non-functional because I am missing that...btw I neither have the VCI or VCP So could someone help me?
Do you know another way to install my speedtouch modem to Ubuntu?

I have noticed that the modem is connected to internet but Ubuntu does not find the Modem because of software lack....

[Just in case has someone from Cable & Wireless ISP connected their speedtouch modem?]

---

### Post by StevenHarper on 2007-05-20
I have made a Debian Package to manage USB ADSL Modems and there Configuration

I Support Speedtouch USB 330 Modems

My Page it at

[https://launchpad.net/usb-adsl-modem-manager]("https://launchpad.net/usb-adsl-modem-manager")

You can download the package at [http://www.squeezedonkey.com/svn/linux/trunk/releases/]("http://www.squeezedonkey.com/svn/linux/trunk/releases/")

And read about it at
[http://www.squeezedonkey.com/wiki/li...itle=Main_Page]("http://www.squeezedonkey.com/wiki/li...itle=Main_Page")

Hope it makes your life easier

Steve

---

