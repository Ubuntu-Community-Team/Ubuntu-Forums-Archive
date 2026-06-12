---
title: "How to edit wvdial.confg?"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by sbrick on 2005-05-13
I already posted in the Newbied area, and have not been getting much response to not being able to establish connection with my ISP.  One person did say just run wvdial application but after reading up on this in my ubuntu help files, I realize that I need to edit the wvdial.confg file for my ISP's specific details.  

First of all I don't know the proper way to "Run an application", and second, I don't know how to edit a file like wvdial.confg!  

Can anyone answer these seemingly simple questions for me?

Thank you kindly,

Steven

---

### Post by jobezone on 2005-05-13
Checkout the Dialup Modem Howto on ubuntu's website: 

[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

This will probably help you.

---

### Post by jobezone on 2005-05-13
Or easier yet!

Right-click on the top panel, and choose "add to panel", and add the "modem monitor" applet.

After it has been placed on the panel, right click it and choose "properties" . Enter your password when asked, and configure your connection and modem on the dialog that appears.

---

### Post by wwwolf on 2005-05-13
[QUOTE=sbrick]First of all I don't know the proper way to "Run an application", and second, I don't know how to edit a file like wvdial.confg!  

Can anyone answer these seemingly simple questions for me?

Thank you kindly,

Steven[/QUOTE]

To edit wvdial.conf you need to use an editor that will give you root permissions. You probably have kwrite installed so you would run this at the prompt:
sudo kwrite

If by some chance you don't have kwrite installed you can run this at the prompt:
sudo apt-get install kwrite

then open the file /etc/wvdial.conf and put your settings in and save it. /etc/wvdial.conf just means the file wvdial.conf is in the /etc directory.

Also you can run this at the command prompt to learn more:
man wvdial.conf

Then, when your ready to connect you just type:
wvdial

leave the terminal open and just minimize it. When your ready to disconnect, bring it back up and hit <CTRL> c

HTH,

---

### Post by sbrick on 2005-05-13
Ok,

I do appreciate all the suggestions, but so far they have not got me connected to the internet.  

I followed the DialupModemHowto at ubuntulinux.org/wiki/DialupModemHowto

and I thought I was finally getting somewhere but the end result was no connection to internet.

I am really uncertain as to where my modem is actually located.  I am referring to how to designate it's location.  It is an internal modem on a laptop.  Where do you go to see exactly what location the modem is configured at?

*************

I also did the suggested "right click" and added the "modem monitor" applet.

I did the suggested "properties" configuration, and still no connection obtained.

************

I can not find kwrite with any thing I tried from your suggestions.  I tried everything you said.  When you say "at the prompt", do you mean at the bottom of the Applications drop down menu, click on Run Application?

I did that route and nothing happened.  A blank white editor window opens in just a brief flash and then goes away.  Very confusing!

I don't know how to open the file/etc/wvdial.conf


Thank you for any more suggestions you might have for me,

Steven

P.S. 

I am going to try to boot from the live cd, and make a connection again.  I had to reinstall Windows XP to get back online, as I had been posting to this forum from our local library hoping to get my ubuntu ISP connection fixed without having to restore Windows.

---

### Post by jodef on 2005-05-13
[QUOTE=sbrick]Ok,

I do appreciate all the suggestions, but so far they have not got me connected to the internet.  

I followed the DialupModemHowto at ubuntulinux.org/wiki/DialupModemHowto

and I thought I was finally getting somewhere but the end result was no connection to internet.

I am really uncertain as to where my modem is actually located.  I am referring to how to designate it's location.  It is an internal modem on a laptop.  Where do you go to see exactly what location the modem is configured at?

*************

Do you have windows installed easiest way to determine what location modem is configured at is check COM port used in windows. Try typing **sudo pppconfig ** in a terminal at some stage it will try to autodetect modem if it doesn't then your modem is probably using a non standard port.

---

### Post by wwwolf on 2005-05-13
[QUOTE=sbrick]Ok,

I do appreciate all the suggestions, but so far they have not got me connected to the internet.  

I am really uncertain as to where my modem is actually located.  I am referring to how to designate it's location.  It is an internal modem on a laptop.  Where do you go to see exactly what location the modem is configured at?

*************

I can not find kwrite with any thing I tried from your suggestions.  I tried everything you said.  When you say "at the prompt", do you mean at the bottom of the Applications drop down menu, click on Run Application?

I did that route and nothing happened.  A blank white editor window opens in just a brief flash and then goes away.  Very confusing!

I don't know how to open the file/etc/wvdial.conf


Thank you for any more suggestions you might have for me,

Steven
[/QUOTE]

What I meant by "at the prompt" was to type the commands in the terminal. You should have some kind of program that says (console, konsole, terminal x-console or shell.) When you click on that you will get a window to pop up where you can type things and talk directly to your computer.

Then just follow the commands I gave you except I made one mistake: You need to use an editor you already have installed so you can try:

sudo gedit

instead of using kwrite if it is not installed.

Also, typing:

sudo pppconfig

at the prompt in your (terminal application, console, konsole or x-console) should try to autodetect your modem and tell you where it is located. It would be something like /dev/ttyS0 or something similar.

Your first priority is learning how to bring up your shell (console,terminal,konsole, x-console) so you can type commands. _Then_ your next priority should be trying to get connected to the internet.

HTH,

---

### Post by sbrick on 2005-05-14
Thank you.

I did go back into Windows and found that my modem is on COM 3.

I also went back into the Live CD boot up and in the Terminal window I ran

sudo wvdialconf ISP-Provider

The results were "modem was not detected", and it gave me a question if I had configured it correctly with setserial?

It suggested also that I read [http://open.nit.ca/wvdial](http://open.nit.ca/wvdial)

I also went through the ppp set up with the directions from 
[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

That did not get me online either, and I used the /dev/ttyS2
since Windows showed my modem on COM 3

I am lost when it comes to setserial.

Any suggestions at this point?

Thank you again for the help!

Steven

---

### Post by wwwolf on 2005-05-14
[QUOTE=sbrick]Thank you.

I did go back into Windows and found that my modem is on COM 3.

I also went back into the Live CD boot up and in the Terminal window I ran

sudo wvdialconf ISP-Provider

The results were "modem was not detected", and it gave me a question if I had configured it correctly with setserial?

Any suggestions at this point?

Thank you again for the help!

Steven[/QUOTE]

OK, you might have a winmodem (software controled) that will not work well under linux. In order to check, go back into windoze and somewhere in settings -> modem, there is a tab to querry the modem. Check the returns probably around init 3 or 4 and it should tell you the chipset that your modem uses.
This should help:

[http://linmodems.org/](http://linmodems.org/)

Hopefully your modem his hardware controlled and you won't have to go through this mess.

Since your using Gnome, I can't help much except from the command line, but there should be some kind of (system hardware information icon) or something in Gnome where you can check to see if your modem is listed in its detected hardware list.

Or from the terminal window you should be able to type:
lspci  (that's a small L and this stands for List PCI Devices)

Also:
sudo lshal ( both are small Ls )
and
sudo lshw ( again small L )

look at what that spits out and see if anything looks familiar ie your modem chipset.

HTH,

---

### Post by sbrick on 2005-05-14
Ok,

Here is the results I got with "Query Modem":

Command                   Response

ATQ0V1E0                   Success
AT+GMM                      +GMM: SoftK56 Data Fax
AT+FCLASS=?             0,1
AT#CLS=?                  COMMAND NOT SUPPORTED
AT+GCl?                     +GCl:  B5
AT+GCl=?                   +GCl:  [B5,00,20,B4,0A,0F,31,3C,3D,04  ............bla, bla, bla
ATl1                            255
ATl2                            Success
ATl3                            Sofk56V_B2.1_V3.05.38A
ATl4                            Generic SoftK56 Data Fax
ATl5                            181
ATl6                            SoftK56
                                  CModem Version 11
                                  Rksample Version 341
ATl7                           255
****************************

     This above information is really mostly greek to me!

Modem Information

Hardware ID   PCI\VEN_1106&DEV_3068&SUBSYS_80F6104D&REV_30

ModemLog_Conexant-Ambit SoftK56 Data, Fax Modem - Notepad

05-14-2005 08:49:09.428 - File: C:\WINDOWS\System32\tapisrv.dll, Version 5.1.2600   
05-14-2005 08:49:09.428 - File: C:\WINDOWS\System32\unimdm.tsp, Version 5.1.2600   
05-14-2005 08:49:09.428 - File: C:\WINDOWS\System32\unimdmat.dll, Version 5.1.2600   
05-14-2005 08:49:09.428 - File: C:\WINDOWS\System32\uniplat.dll, Version 5.1.2600   
05-14-2005 08:49:09.458 - File: C:\WINDOWS\System32\drivers\modem.sys, Version 5.1.2600   
05-14-2005 08:49:09.468 - File: C:\WINDOWS\System32\modemui.dll, Version 5.1.2600   
05-14-2005 08:49:09.729 - File: C:\WINDOWS\System32\mdminst.dll, Version 5.1.2600   
05-14-2005 08:49:09.749 - Modem type: Conexant-Ambit SoftK56 Data,Fax Modem
05-14-2005 08:49:09.749 - Modem inf path: oem4.inf
05-14-2005 08:49:09.749 - Modem inf section: ModemX_VIA
05-14-2005 08:49:09.749 - Matching hardware ID: pci\ven_1106&dev_3068&subsys_80f6104d
05-14-2005 08:49:10.390 - 115200,8,N,1, ctsfl=1, rtsctl=2
05-14-2005 08:49:10.390 - Initializing modem.
05-14-2005 08:49:10.390 - DSR is low while initializing the modem. Verify modem is turned on.
05-14-2005 08:49:10.400 - Send: AT<cr>
05-14-2005 08:49:10.400 - Recv: AT<cr>
05-14-2005 08:49:10.400 - Command Echo
05-14-2005 08:49:10.400 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.400 - Interpreted response: OK
05-14-2005 08:49:10.410 - Send: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
05-14-2005 08:49:10.550 - Recv: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
05-14-2005 08:49:10.550 - Command Echo
05-14-2005 08:49:10.550 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.550 - Interpreted response: OK
05-14-2005 08:49:10.560 - Send: ATS7=60M1+ES=3,0,2;+DS=3;+IFC=2,2;X4<cr>
05-14-2005 08:49:10.570 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.570 - Interpreted response: OK
05-14-2005 08:49:10.570 - Waiting for a call.
05-14-2005 08:49:10.580 - Send: ATS0=0<cr>
05-14-2005 08:49:10.590 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.590 - Interpreted response: OK
05-14-2005 08:49:10.630 - 115200,8,N,1, ctsfl=1, rtsctl=2
05-14-2005 08:49:10.630 - Initializing modem.
05-14-2005 08:49:10.640 - DSR is low while initializing the modem. Verify modem is turned on.
05-14-2005 08:49:10.650 - Send: AT<cr>
05-14-2005 08:49:10.660 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.660 - Interpreted response: OK
05-14-2005 08:49:10.670 - Send: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
05-14-2005 08:49:10.860 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.860 - Interpreted response: OK
05-14-2005 08:49:10.870 - Send: ATS7=60M1+ES=3,0,2;+DS=3;+IFC=2,2;X4<cr>
05-14-2005 08:49:10.880 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 08:49:10.880 - Interpreted response: OK
05-14-2005 08:49:10.880 - Dialing.
05-14-2005 08:49:10.890 - Send: ATDT#######<cr>
05-14-2005 08:49:39.301 - Recv: <cr><lf>+MCR: V34<cr><lf>
05-14-2005 08:49:39.301 - Interpreted response: Informative
05-14-2005 08:49:39.301 - Recv: <cr><lf>+MRR: 26400<cr><lf>
05-14-2005 08:49:39.301 - Interpreted response: Informative
05-14-2005 08:49:40.062 - Recv: <cr><lf>+ER: LAPM<cr><lf>
05-14-2005 08:49:40.062 - Interpreted response: Informative
05-14-2005 08:49:40.062 - Recv: <cr><lf>+DR: V42B<cr><lf>
05-14-2005 08:49:40.062 - Interpreted response: Informative
05-14-2005 08:49:40.062 - Recv: <cr><lf>CONNECT 26400<cr><lf>
05-14-2005 08:49:40.062 - Interpreted response: Connect
05-14-2005 08:49:40.062 - Connection established at 26400bps.
05-14-2005 08:49:40.062 - Error-control on.
05-14-2005 08:49:40.062 - Data compression on.
05-14-2005 08:50:10.065 - Read: Total: 579, Per/Sec: 16, Written: Total: 991, Per/Sec: 30
05-14-2005 08:52:10.068 - Read: Total: 579, Per/Sec: 0, Written: Total: 991, Per/Sec: 0
05-14-2005 08:54:10.070 - Read: Total: 35825, Per/Sec: 293, Written: Total: 8325, Per/Sec: 61
05-14-2005 08:56:10.073 - Read: Total: 37144, Per/Sec: 10, Written: Total: 9475, Per/Sec: 9
05-14-2005 08:58:10.076 - Read: Total: 169824, Per/Sec: 1105, Written: Total: 22478, Per/Sec: 108
05-14-2005 09:00:10.078 - Read: Total: 329679, Per/Sec: 1332, Written: Total: 34473, Per/Sec: 99
05-14-2005 09:02:10.081 - Read: Total: 329972, Per/Sec: 2, Written: Total: 34923, Per/Sec: 3
05-14-2005 09:04:10.083 - Read: Total: 329972, Per/Sec: 0, Written: Total: 34923, Per/Sec: 0
05-14-2005 09:06:10.086 - Read: Total: 330352, Per/Sec: 3, Written: Total: 35265, Per/Sec: 2
05-14-2005 09:08:10.088 - Read: Total: 330808, Per/Sec: 3, Written: Total: 35265, Per/Sec: 0
05-14-2005 09:09:23.474 - Hanging up the modem.
05-14-2005 09:09:23.474 - Hardware hangup by lowering DTR.
05-14-2005 09:09:25.276 - Detected CD dropped from lowering DTR
05-14-2005 09:09:25.276 - Recv: <cr><lf>NO CARRIER<cr><lf>
05-14-2005 09:09:25.276 - Interpreted response: No Carrier
05-14-2005 09:09:25.286 - Send: ATH<cr>
05-14-2005 09:09:25.376 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 09:09:25.376 - Interpreted response: OK
05-14-2005 09:09:25.376 - 115200,8,N,1, ctsfl=1, rtsctl=2
05-14-2005 09:09:25.376 - Initializing modem.
05-14-2005 09:09:25.386 - Send: AT<cr>
05-14-2005 09:09:25.386 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 09:09:25.386 - Interpreted response: OK
05-14-2005 09:09:25.396 - Send: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2<cr>
05-14-2005 09:09:25.537 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 09:09:25.537 - Interpreted response: OK
05-14-2005 09:09:25.547 - Send: ATS7=60M1+ES=3,0,2;+DS=3;+IFC=2,2;X4<cr>
05-14-2005 09:09:25.557 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 09:09:25.557 - Interpreted response: OK
05-14-2005 09:09:25.557 - Waiting for a call.
05-14-2005 09:09:25.567 - Send: ATS0=0<cr>
05-14-2005 09:09:25.577 - Recv: <cr><lf>OK<cr><lf>
05-14-2005 09:09:25.577 - Interpreted response: OK
05-14-2005 09:09:25.577 - Session Statistics:
05-14-2005 09:09:25.577 -                Reads : 24 bytes
05-14-2005 09:09:25.577 -                Writes: 86 bytes
ATQ0V1E0 - OK
AT+GMM - +GMM: SoftK56 Data Fax
AT+FCLASS=? - 0,1
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - +GCI: B5
AT+GCI=? - +GCI: (B5,00,20,B4,0A,0F,31,3C,3D,04,59,A0,8B,A5,A6,57,52,82,69,7B,46,09,7E,9C,6C,61,73,50,9F,B3,98,25,07,26)
ATI1 - 255
ATI2 - OK
ATI3 - SoftK56V_B2.1_V3.05.38A
ATI4 - Generic SoftK56 Data Fax
ATI5 - 181
ATI6 - SoftK56 
       CModem Version 11
       Rksample Version 341
ATI7 - 255
************************************

     This is the information I found on my machine using Windoze.   I thought maybe it might help you know important stuff.  I don't understand it much though.

Thank you,

Steven

---

### Post by sbrick on 2005-05-14
[QUOTE=wwwolf]OK, you might have a winmodem (software controled) that will not work well under linux. In order to check, go back into windoze and somewhere in settings -> modem, there is a tab to querry the modem. Check the returns probably around init 3 or 4 and it should tell you the chipset that your modem uses.

Answer:

I did not notice anything that resembled init 3 or 4


This should help:

[http://linmodems.org/](http://linmodems.org/)

Hopefully your modem his hardware controlled and you won't have to go through this mess.

Since your using Gnome, I can't help much except from the command line, but there should be some kind of (system hardware information icon) or something in Gnome where you can check to see if your modem is listed in its detected hardware list.

Or from the terminal window you should be able to type:
lspci  (that's a small L and this stands for List PCI Devices)

Answer:

I did find where it found the modem but it has it labled as:
communication UNCLAIMED
physical id: 7.6
bus info:  pci@00:07.6
version:  30
clock:  33MHz
capabilities:  cap_list
configuration:  irq=5



Also:
sudo lshal ( both are small Ls )
and
sudo lshw ( again small L )

look at what that spits out and see if anything looks familiar ie your modem chipset.

Answer:  I was really lost when I tried these last two commands.
I did not understand much of what it "spit out".
 :roll: 

HTH,[/QUOTE]

I hope this information helps

Thank you,

Steven

---

### Post by sbrick on 2005-05-14
I now have scanModem on a floppy in the a: drive, but when I try the 

mcopy a:scanModem.gz.

I get error message "command not recognized"

How do I run this program from the a: drive?

I wish I had a list of commands and their functions handy!

Do all linux distros use the same commands?

I am trying to follow the instructions at 

[http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

ls/mnt does not seem to work either.

Thank you,

Steven

---

### Post by sbrick on 2005-05-14
I think I am simply missing the Linux driver for my modem.

I have been to 

[www.conexant.com](www.conexant.com) 

and downloaded and used their ListModem.exe application.  My goal was to find out the modem type, but that particular information came back as unknown.  Here is the log copy from ListMdm:

 =====================================================================
=              SYSTEM INFORMATION                                   =
=====================================================================
Date         : 5/14/2005
ListMdm Ver  : 1.6
Windows OS   : Microsoft Windows XP 
Build Number : 2600 

=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
  PCI CONFIGURATION INFORMATION READ:
     VENDOR ID              : 1106
     DEVICE ID              : 3068
     SUBVENDOR ID           : 104D
     SUBDEVICE ID           : 80F6
     REVISION ID            : 30

  DEDUCED INFORMATION:
     VENDOR NAME            : VIA
     DEVICE NAME            : VIA
     SUBVENDOR NAME         : SONY -- [HTTP://WWW.SONY.COM](HTTP://WWW.SONY.COM)
     MODEM TYPE             : UNKNOWN
     WINXP INBUILD SUPPORT  : NO

*****************

I am pretty sure it is an AC97 from the information gathered so far from my machine, and also because that is the type that  Conexant said that were used in most laptop applications.  The trouble still is that they don't tell you which linux driver is supposed to be used with this AC97 type!  

Does this help any to determine what I need to do?

Lost,

Steven

---

### Post by wwwolf on 2005-05-16
Hmmm, the "soft56K" designation may indicate that it _is_ a winmodem (software controlled). I am not sure how Conexant supports it.

ScanModem should tell you which chipset the modem uses and you can look on linmodems database for configuration and settings. I think you may also be able to email them for support. I don't know but I think it is [email]support@linmodems.org[/email] or something. It should be on there website or should list a newsgroup you can post your question to.

To copy a file use "cp":

cp /source/directory/file /destination/directory/

or to copy to a place where only root has permission to write:

sudo cp file destination

Hope that helps,

---

### Post by wwwolf on 2005-05-16
I came across this link, it might help:

[http://www.ubuntuforums.org/showthread.php?t=31106&highlight=dsl](http://www.ubuntuforums.org/showthread.php?t=31106&highlight=dsl)

HTH,

---

