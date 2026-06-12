---
title: "Dell D600 smart card o2micro install - o2scr beid"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by gja on 2010-06-09
Hello,

Here's a small report on how I got the built-in smartcard reader of my Dell D600 to work with 10.04.
(note: the smart card reader is on the left, under the bottom of the pcmcia slot)

- check the card type with lspci
> 02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


- Install pcsd through Synaptic

- verify whether the card reader is seen by the system:
pccardctl info
> pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro"
PRODID_2="SmartCardBus Reader"
PRODID_3="V1.0"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

- verify the status of the hardware
pccardctl status
if no driver has been loaded, it will show the o2micro device as "unbound"

- download the o2 driver sources from
[http://pieleric.free.fr/o2scr/](http://pieleric.free.fr/o2scr/)

- to build this driver you need to have the header files from pcsd-lite
These header files need to be located at /usr/lib/PCSD
so best to download a copy of the pcsd-lite sources, create the PCSD folder in /usr/lib (sudo necessary) and copy the source files of pcsc-lite there.

- after building it is required to restart the pcsd daemon. For certainty I rebooted the system.
After reboot I did another
> pccardctl status
Socket 0:
  no card
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "ozscrlx_cs"

Driver bound!

- for my belgian ID card, I installed beidgui and beid-tools
At this point you can read your Belgian ID card.

- last thing to do to be able to pay my taxes online, was to register the certificates.
Check [http://users.telenet.be/mydotcom/howto/linux/ubuntubelpic.htm](http://users.telenet.be/mydotcom/howto/linux/ubuntubelpic.htm) for more pointers.
I also used a specific beid plugin for firefox.
[https://addons.mozilla.org/nl/firefox/addon/51744/](https://addons.mozilla.org/nl/firefox/addon/51744/)

If others try this, please comment in this thread if this worked for you or what you had to change.

---

### Post by MaartenM on 2010-07-15
I also have a Dell Latitude D600 with the O2 micro smartcard reader.  I have seen that there are two drivers for them:

Driver 1 => [http://download.gna.org/o2scr/](http://download.gna.org/o2scr/)  (version 1.04)
Driver 2=> [http://pieleric.free.fr/o2scr/](http://pieleric.free.fr/o2scr/)  (Version 2.03)

The first driver from gna.org compiles perfectly without problems.  A smartcard will be recognized with the pcsc_scan utility.  Unfortunately I have to use some Middleware, called AET Safesign wich doesn't work with this O2 Micro driver.  The AET safesign software does work fine with other USB smartcardreaders like the omnikey 3121.

The second driver form pieleric give problems during compiling.  I have installed build-essential, kernel source and headers and libpcsclite-dev files.  I also placed the libpcsclite header files in /usr/lib/PCSD (and some other directory's).  I have tried this on Ubuntu 9.04 and 10.04 without succes.

Can anyone help me building the driver from pieleric.free.fr ?

The output is:

ubuntu@ubuntu:~/Downloads/OZSCR_2.0.3_Kern_2.6$ sudo ./configure-debug 
Found pcsclite 1.5.3 in /usr/lib
Found kernel 2.6.32-21-generic includes directory
Building OZSCR modules...
rm -f *.o
rm -f .*.o.d
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~    
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.o
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:60:26: error: linux/config.h: No such file or directory
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:75:28: error: pcmcia/version.h: No such file or directory
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:154: error: expected ‘)’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:163: error: expected ‘)’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:205: error: unknown field ‘attach’ specified in initializer
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:205: error: ‘ozscr_attach’ undeclared here (not in a function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:206: error: unknown field ‘event’ specified in initializer
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:206: warning: excess elements in struct initializer
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:206: warning: (near initialization for ‘ozscrlx_driver’)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:207: error: unknown field ‘detach’ specified in initializer
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:207: error: ‘ozscr_detach’ undeclared here (not in a function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:207: warning: excess elements in struct initializer
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:207: warning: (near initialization for ‘ozscrlx_driver’)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:212: error: expected ‘)’ before string constant
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_interrupt’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:224: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:224: error: (Each undeclared identifier is reported only once
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:224: error: for each function it appears in.)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:224: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:225: warning: ISO C90 forbids mixed declarations and code
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:233: error: ‘dev_list’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:240: error: implicit declaration of function ‘DEV_OK’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_open’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:262: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:262: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:263: warning: ISO C90 forbids mixed declarations and code
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:269: error: ‘dev_list’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_close’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:296: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:296: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:297: warning: ISO C90 forbids mixed declarations and code
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:303: error: ‘dev_list’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:316: error: ‘DEV_STALE_CONFIG’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_ioctl’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:342: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:342: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:343: warning: ISO C90 forbids mixed declarations and code
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:352: error: ‘dev_list’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: At top level:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:515: error: expected ‘)’ before ‘handle’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:543: error: expected ‘)’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_event’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:738: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:738: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:754: error: ‘DEV_PRESENT’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:754: error: ‘DEV_CONFIG_PENDING’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:755: error: implicit declaration of function ‘ozscr_config’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:767: error: ‘DEV_STALE_CONFIG’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:768: error: ‘DEV_CONFIG’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:778: error: ‘DEV_SUSPEND’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:785: error: implicit declaration of function ‘pcmcia_release_configuration’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: At top level:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:822: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘ozscr_release’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:958: error: ‘dev_link_t’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:958: error: ‘link’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:958: error: expected expression before ‘)’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:978: error: ‘DEV_STALE_CONFIG’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:989: error: implicit declaration of function ‘pcmcia_release_io’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:990: error: implicit declaration of function ‘pcmcia_release_irq’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:991: error: ‘DEV_CONFIG’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:993: error: ‘DEV_STALE_LINK’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:994: error: implicit declaration of function ‘ozscr_detach’
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: At top level:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:1005: error: expected ‘)’ before ‘*’ token
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c: In function ‘exit_ozscrlx’:
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:1140: error: ‘dev_list’ undeclared (first use in this function)
/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:1142: error: ‘DEV_CONFIG’ undeclared (first use in this function)
make[2]: *** [/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.o] Error 1
make[1]: *** [_module_/home/ubuntu/Downloads/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [default] Error 2
cp -f ozscrlx.ko /lib/modules/`uname -r`/pcmcia
cp: cannot stat `ozscrlx.ko': No such file or directory
make: *** [install] Error 1
rm -f *.o
rm -f .*.o.d
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~    
Copying files...
cp: cannot stat `etc/reader.conf.1.5.3': No such file or directory
/etc/reader.conf updated
OZSCR installation complete.

---

