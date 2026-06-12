---
title: "SmartLink, wvdial &quot;NO DIALTONE&quot;, Lucent Softmodem, why?"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by HilliBilly on 2007-02-01
hi, 

need help with setting up my dialup connection on my laptop (sharp pc-um10, phoenixbios, Lucent Softmodem, edgy, gnome). i think i've done everything correct but i get this "NO DIALTONE" error. i am not the only one who has trouble with this issue and i've read a lot other threads but couldn't find an explanation or solution. any ideas?

(btw: i also tried to use pon instead of wvdial but same problem)

(when i execute "sudo /etc/init.d/sl-modem-daemon restart" a window pops up "new audio playback device detected. to configure your new audio playback device (null) and possibly set it as defult service, open --> system --> preferences --> sound". is this normal? because i don't have any problems with sounds.)

this is without ATX, ATX1, ATX3, X3, which i all tried but with no success. [COLOR="black"]****[/COLOR]here we go (sorry for the long text):

:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDTphonenumber
--> Waiting for carrier.
ATDTphonenumber
NO DIALTONE
--> No dial tone.
--> Disconnecting at Thu Feb  1 13:15:26 2007


vi /etc/wvdial.conf
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = XXXXXXXXXXXXXX
Modem = /dev/ttySL0
Username = XXXXXXXXXXXXXXXX
Password = XXXXXXXXXXXXXXXX
Baud = 115200
Carrier Check = no
Stupid mode = on

what i did to get where i am:

gunzip scanModem.gz
chmod +x scanModem
sudo ./scanModem

sudo apt-get install sl-modem-daemon
sudo dpkg-reconfigure sl-modem-daemon -plow
sudo /etc/init.d/sl-modem-daemon restart
Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... snd_atiixp_modem.
Starting SmartLink Modem driver for: modem:1.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

sudo adduser USERNAME dip
sudo adduser USERNAME dialout

aplay -l |grep -i modem
card 1: Modem [Intel 440MX Modem], device 0: Intel ICH - Modem [Intel 440MX Modem - Modem]

lspci -vv | grep Modem
00:00.2 Modem: Intel Corporation 82440MX AC'97 Modem Controller (prog-if 00 [Generic])


i have windows on a dual boot, query modem shows: 
ATI3 - Lucent Softmodem V 3.1.88
ATI5 - 3.1.88, AMR Intel MB, AC97 ID:SIL REV:0x27,19

Lucent Soft Modem PCI\VEN_8086&DEV_7196&SUBSYS_102113BD&REV_00

COM3


scanModem's ModemData.txt:
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
 scanModem update of:  2007_Jan_22
The modem symbolic link is /dev/modem -> ttySL0
The slmodemd set symbolic link is /dev/ttySL0 -> /dev/pts/0

USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:00.2	8086:7196	13bd:1021	Modem: Intel Corporation 82440MX AC'97 Modem Controller

 Modem interrupt assignment and sharing: 
 10:        585          XT-PIC  Intel 440MX, Intel 440MX Modem

 --- Bootup diagnositcs for card in PCI slot 00:00.2 ----
[17179636.052000] ACPI: PCI Interrupt 0000:00:00.2[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179636.052000] PCI: Setting latency timer of device 0000:00:00.2 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

ALSAversion 1.0.11
 For candidate modem in PCI bus:  00:00.2
   Class 0703: 8086:7196 Modem: Intel Corporation 82440MX AC'97 Modem Controller
      Primary PCI_id  8086:7196
    Subsystem PCI_id  13bd:1021 
    Softmodem codec or Vendor from diagnostics: SIL27, an AgereSystems type.
                              from    Archives: 
      

 This is a NEW softmodem case!  Please send the output ModemData.txt 
 to [email]DISCUSS@linmodems.org[/email] , even if further assistance is not needed.
 It will enrich the Archive and help others!
 -------------------------------------------
 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-intel8x0m and audio drivers it depends on,
 displayed by:	lsmod | grep snd_intel8x0m
Module                  Size  Used by
-------------------------------------
snd_intel8x0m          17804  5 
snd_ac97_codec         96672  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_pcm                80520  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    55428  19 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-01: Intel ICH - MIC ADC : Intel 440MX - MIC ADC : capture 1
00-00: Intel ICH : Intel 440MX : playback 1 : capture 1
01-00: Intel ICH - Modem : Intel 440MX Modem - Modem : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
 0 snd_intel8x0
 1 snd_intel8x0m
	/proc/asound/card1/codec97#0/mc97#1-1+regs
-------------------------------
0:7c = 5349  and  0:7e = 4c27
which were translated from hexadecimal code into:  SIL27

	/proc/asound/card1/codec97#0/mc97#1-1
-------------------------------
Extended modem ID: codec=1 LIN1

and from the command:
	aplay -l | grep -i modem
card 1: Modem [Intel 440MX Modem], device 0: Intel ICH - Modem [Intel 440MX Modem - Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.1.2 and a compiler is not installed

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-4.1 make linux-headers-2.6.17-10-386


Checking pppd properties:
	-rwsr-xr-x 1 root dip 260920 2006-07-10 21:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2007-02-01 00:26 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  lrwxrwxrwx 1 root root 10 2007-02-01 00:26 /dev/ttySL0 -> /dev/pts/0
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by housam on 2007-02-01
in a terminal type:
```
sudo slmodemd -c YOUR_COUNTRY --alsa modem:1
```
Type your country in upper case and leave the terminal open 
Then open another terminal and type :
```
sudo wvdial
```
 
If it is disconnected  type it once again. and if it works leave it open also.

---

### Post by HilliBilly on 2007-02-01
housam,

tried it but ended with this error messages:

**sudo slmodemd -c MYCOUNTRYINUPPERCASE --alsa modem:1**
error: alsa setup: cannot open playback device 'modem:1': Device or resource busy
error: cannot setup device `modem:1'

why is it busy? busy with what?

-------------------------------------------------------------------------------------

i have some more information, maybe this helps:


xxx@xxx-ubuntu-laptop:~$ **fuser -v -m /dev/ttySL0**
                     USER        PID ACCESS COMMAND
/dev/ttySL0:         xxx       15210 F.... bash
                     xxx       24310 F.... bash
                     xxx       24394 F.... bash


xxx@xxx-ubuntu-laptop:~$ **sudo /etc/init.d/sl-modem-daemon restart**
Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... snd_atiixp_modem.
Starting SmartLink Modem driver for: modem:1.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


xxx@xxx-ubuntu-laptop:~$ **sudo modprobe -r snd_intel8x0m**
FATAL: Module snd_intel8x0m is in use.


xxx@xxx-ubuntu-laptop:~$ **lsmod|grep snd**
snd_atiixp_modem       16136  0 
snd_via82xx_modem      15496  0 
snd_intel8x0m          17804  5 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  19 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm


xxx@xxx-ubuntu-laptop:~$ **cat /proc/asound/cards**
 0 [I440MX         ]: ICH - Intel 440MX
                      Intel 440MX with CS4299 at 0x1800, irq 10
 1 [Modem          ]: ICH-MODEM - Intel 440MX Modem
                      Intel 440MX Modem at 0x1c00, irq 10

---

### Post by HilliBilly on 2007-02-01
**IF** my "NO DIALTONE" problem would be a result of a possible hardware conflict (sound & modem) because i could imagine that in my laptop the modem actually shares it's hardware with the sound hardware which both use the DSP in the sound chips to form the sound going to the speakers and the signal going into the modem: would there be a workaround? 

(remember: when i execute "**sudo /etc/init.d/sl-modem-daemon restart**" a window pops up "new audio playback device detected. to configure your new audio playback device (null) and possibly set it as defult service, open --> system --> preferences --> sound". is this normal? because i don't have any problems with sounds.)
[B]
lsmod |grep snd[/B]
snd_atiixp_modem       16136  0 
snd_via82xx_modem      15496  0 
snd_intel8x0m          17804  5 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  19 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm


**slmodemd -v**
SmartLink Soft Modem: version 2.9.9e-pre1 May 28 2006 17:44:44

---

### Post by housam on 2007-02-01
> **HilliBilly said:**
> housam,

tried it but ended with this error messages:

**sudo slmodemd -c [B]MYCOUNTRYINUPPERCASE** --alsa modem:1[/B]
error: alsa setup: cannot open playback device 'modem:1': Device or resource busy
error: cannot setup device `modem:1'

why is it busy? busy with what?


Kindly note that you have to write your country name ( i.e USA , GERMANY , or FRANCE  ...etc.) in upper case

---

### Post by housam on 2007-02-01
Re the SLMODEMD.gcc4 driver, I have the same driver for my dial-up modem and got it to work just fine by doing the following:
```
 cd ~/Desktop
tar zxf SLMODEMD.gcc4.tar.gz
cd SLMODEMD.gcc4
sudo - root
sudo chmod a+x slmodemd
sudo cp slmodemd /usr/bin/
sudo modprobe snd-intel8x0m
sudo slmodemd -c EGYPT --alsa hw:0,6

```

and in another terminal :
```
sudo wvdial
```

Note that hw:0,6 is modem :1 in your case.

---

### Post by HilliBilly on 2007-02-01
did that of course *smile*, just put in this as a dummy when i wrote this. any other ideas?

---

### Post by HilliBilly on 2007-02-01
do you really think i should do this? i heard about this before but didn't do it because i wasn't sure which version of my slmodemd's is the newer version. date lets suppose it's my slmodemd in use although version no lets suppose the oppsite. what do think about it?

[email]xxx@xxx-ubuntu-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ ls -ltr
total 1376
-rw-r--r-- 1 xxx xxx    1707 2004-01-31 15:06 COPYING
-rw-r--r-- 1 xxx xxx   15184 2005-08-24 14:24 Testing.txt
-rw-r--r-- 1 xxx xxx   18186 2005-08-24 14:24 slmodem.txt
-rw-r--r-- 1 xxx xxx    1214 2005-08-30 18:08 CountryList.txt
-rw-r--r-- 1 xxx xxx    7341 2005-09-22 15:05 README
-rw-r--r-- 1 xxx xxx    6481 2005-09-24 22:51 Slmodem-ALSA.txt
-rw-r--r-- 1 xxx xxx    1462 2005-10-04 19:40 wvdial.conf
-rw-r--r-- 1 xxx xxx    3555 2005-10-09 01:20 Changes
-rw-r--r-- 1 xxx xxx     946 2005-10-30 14:44 Files.txt
drwxr-xr-x 5 xxx xxx    4096 2006-01-20 03:14 scripts
-rwxr-xr-x 1 xxx xxx 1310422 2006-03-14 00:28 slmodemd
-rw-r--r-- 1 xxx xxx   13254 2006-08-02 17:01 1st_Read.txt

[email]xxx@xxx-ubuntu-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ **~/Desktop/SLMODEMD.gcc4/slmodemd --v**
SmartLink Soft Modem: **version 2.9.11 Mar 13 2006** 18:27:33
[email]xxx@xxx-ubuntu-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ slo
slocate  slogin   
[email]xxx@xxx-ubuntu-laptop:~/Desktop/SLMODEMD.gcc[/email]4$ **slmodemd --v**
SmartLink Soft Modem: v**ersion 2.9.9e-pre1 May 28 2006** 17:44:44
[email]xxx@xxx-ubuntu-laptop:~/Desktop/SLMODEMD.gcc[/email]4$

---

### Post by towsonu2003 on 2007-02-01
does it really dial? run wvdial, wait for it to dial for a little while, and pick up phone and listen to what happens. 

I have a similar NO DIALTONE problem myself but it's more of an annoyance than a problem. In my case (describing, maybe will help you), the modem dials, I hear my modem and the ISP talking when I pick up the phone (that scrambled electronic sound), than it just stays there without connecting. 

my solution; everytime I get NO DIALTONE, I kill wvdial (ctrl+c) and try again -it connects after 5 to 20 tries for me => it will take anywhere from 5 minutes to an hour to connect. I had a few days when it just wouldn't connect for like 4-5 hours and a number of reboots... some weird bug. 

also, you can try to start the [precompiled slmodemd daemon]("http://linmodems.technion.ac.il/packages/smartlink/slmodemd-2.9.9e-pre1-alsa.tar.gz") (not the one that comes from ubuntu repositories) with a nice value of -19 (which means: the most important program that is running on the computer in terms of processor priority etc): from the directory where slmodemd is installed-
```
nice -n -19 ./slmodemd -a -c USA modem:1 &
sudo wvdial
```

Also have a look [at this one]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9") on wvdial as it gives a few options that people seem to like.

---

### Post by housam on 2007-02-01
> **HilliBilly said:**
> do you really think i should do this? i heard about this before but didn't do it because i wasn't sure which version of my slmodemd's is the newer version. date lets suppose it's my slmodemd in use although version no lets suppose the oppsite. what do think about it?


In your Modem data.txt , I followed the link and found that the driver needed for your modem is the same as mine  SLMODEMD.gcc4 which I downloaded  from the same link.
I suggest to follow the steps I did , you may get connected.

towsonu2003
Using this driver gets me connected every time in less than 2 minuets from the first or second try only.

---

### Post by HilliBilly on 2007-02-02
good news: it works!!!!

really stupid, 'NO DIALTONE' was no dial tone. i can't really explain it because i am able to use a normal phone on that line but not the modem. then i tried the phone line of my fax machine and it worked. maybe because i have the adsl signal on my normal phone line? 

btw ... you know what i did *smile*: used my mobile phone number instead of the isp phone number to see if it rings. anyway, the result is what counts, thanks for your support.

last **question**: i would like to **hear the speaker**. i know this could work because i have the sound running windows on this laptop. i read already about the different AT commands like Ln (0-3) and Mn (0-3), tried a lot but no sound.

**vi wvdial.conf**
[Dialer Defaults]
Init1 = ATZ    
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = XXXXXXXXXXX
Modem = /dev/ttySL0
Username = XXXXXXXXXXXXX
Password = XXXXXXXXXXX
Baud = 115200
Carrier Check = no
#Stupid mode = yes

---

### Post by housam on 2007-02-02
Glad to here that you did it. Congratulations:)

---

