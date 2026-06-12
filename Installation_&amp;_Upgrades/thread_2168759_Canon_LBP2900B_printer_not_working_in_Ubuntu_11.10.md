---
title: "Canon LBP2900B printer not working in Ubuntu 11.10"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by pramodmpr on 2013-08-19
Hai,

My Canon LBP2900B printer not working in Ubuntu 11.10.  

Please give me a guide line for installing the printer

Pramod

---

### Post by Lim_Xiang_Yann on 2013-08-19
Try this driver
[http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download](http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download)

---

### Post by pramodmpr on 2013-08-20
Dear Sir,

I downloaded and installed the software but it is not working

---

### Post by Vladlenin5000 on 2013-08-20
Follow this additional instruction and report back Should be the same for 11.10):

[http://une-terre.blogspot.com.es/2012/12/install-canon-lbp2900-on-ubuntu-1204.html](http://une-terre.blogspot.com.es/2012/12/install-canon-lbp2900-on-ubuntu-1204.html)

PS - Is there any special reason for you to keep using an outdated version?

---

### Post by pdc on 2013-08-21
how is it all coming along out there, pramodmpr?

are you using 32bit ubuntu?

tell us what 

> [COLOR="#FF0000"]dpkg -l | grep Canon[/COLOR] gives you if you COPY and paste this command into a terminal?

_________________________________________________________________

the LBP 2900 will use the Canon CAPT driver

the steps are:
1) install the CAPT driver
2) install the printer in CUPS eg                     sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp ://localhost:59787 -E
3) register the printer in the ccpd daemon          eg         sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0

4)then start the ccpd daemon > [COLOR="#FF0000"]sudo service ccpd start[/COLOR]

5) then check its operation > [COLOR="#FF0000"]sudo service ccpd status[/COLOR]  ........and you should get something like > Canon Printer Daemon for CUPS: ccpd: 8956 8954

one then tests if it will print

____________________________________________________

if that works, one needs to automate the detection of the printer so the ccpd daemon starts automatically 

Sivella describes that here in section 3.3

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

one can use google translate to convert from french to your own, most favourite, language

---

### Post by pramodmpr on 2013-08-22
Dear Sir

It's not working, please help me

Pramod

---

### Post by pdc on 2013-08-22
please COPY and PASTE this command 

> [COLOR="#FF0000"]dpkg -l | grep Canon[/COLOR]

into a terminal and tell us what you get: it will tell if you have the correct drivers installed;

___________________________________

when you give us that answer, we can move forward .............

_______________________________________________

**AND** ...............[COLOR="#EE82EE"]**[SIZE=4]tell us if you have a 32bit or 64bit system[/SIZE]**[/COLOR]

---

### Post by pramodmpr on 2013-08-23
Dear Sir

I copy and paste [COLOR=#FF0000]dpkg -l | grep Canon [/COLOR][COLOR=#000000]this command but it does not work[/COLOR].   We use 64 Bit system.
Please give the correct steps one by one that is from software downloading and installation.  Where to get the correct driver for my Canon LBP2900 B Printer.

Pramod

---

### Post by pdc on 2013-08-23
> [COLOR="#800080"]I downloaded and installed the software but it is not working[/COLOR] 

...............can you tell us what software you downloaded please?

__________________________________________________________________________

I think you are going to find this all hard: have you any friends who use linux who can help you?

You need to:
1) install the CAPT drivers
2) install some libraries so it works on 64bit
.....and do what I detailed in a previous post

___________________________________________

if you want to go ahead, 

________________________________________________________________________

please tell us what 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] gives, when the printer is plugged in and turned on

__________________________________________________________________________

you need to install some things as you have 64bit

> [COLOR="#FF0000"]sudo apt-get update[/COLOR]

> [COLOR="#FF0000"]sudo apt-get install lib32asound2 lib32ffi6 lib32bz2-1.0 lib32gcc1 lib32stdc + 6 lib32z1 lib32ncurses5 lib32ncursesw5 libc6-i386[/COLOR]

> [COLOR="#FF0000"]wget [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu26_amd64.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu26_amd64.deb)[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i ia32-libs_20090808ubuntu26_amd64.deb[/COLOR]



____________________________________________________________________________

1) the software you need is the Canon CAPT driver from here

[http://support-in.canon-asia.com/contents/IN/EN/0100459601.html](http://support-in.canon-asia.com/contents/IN/EN/0100459601.html)

it comes down as Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz

commands to install it are 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_CAPT_PrinterDriver_V260_uk_EN/64-bit_Driver/Debian[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.60-1_amd64.deb[/COLOR]

then 

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-capt_2.60-1_amd64.deb[/COLOR]

_________________________________________________________________--

if you now copy and paste 

> [COLOR="#FF0000"]sudo dpkg -l | grep Canon[/COLOR]

and tell us what you get

______________________________________________

if we stop there 

if you read this

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

_____________________________________________________

we can continue when we know the drivers are installed

---

### Post by pramodmpr on 2013-08-24
It's not working

---

### Post by pdc on 2013-08-24
> It's not working 

.............I assume you mean the printer is not working;

that is because what I gave you in the last post was only the first bit of what was needed

---

### Post by pramodmpr on 2013-08-26
Dear All,

Sub: [h=2]Canon LBP2900B printer not working in Ubuntu 11.10[/h]
Please solve the issue by showing how to install and set up this type of printer

Pramod

---

### Post by pramodmpr on 2013-08-28
Dear All,

[h=2]Is there is any driver for Canon LBP2900B printer for Ubuntu 11.10.   If yes please show me the installation steps urgently[/h]Regards

Pramod

---

