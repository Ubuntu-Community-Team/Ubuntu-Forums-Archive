---
title: "problems installing ies4linux in ubuntu 8.10"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by deveraux on 2008-11-18
new to ubuntu,

I tried installing ies4linux and got error in red when in terminal 

indicating that i don't have the latest version of wine..I have the latest? 

version for ubuntu 8.10 installed..so it doesn't make sense that the wine 

version i have is too old. i tried copy and pasting from terminal and saved 

screenshot, but don't know how to put it into this request.

if you could help i would greatly appreciate it

deveraux

---

### Post by deveraux on 2008-11-18
problem figured out.  i unistalled both cabextract and wine in synaptic manager and then reinstalled.  with the use of [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux), help in finishing the ies4linux install the ie explorer icon finally showed up on my desktop.  i hope it will work ok now.

thanks,
Deveraux

---

### Post by itaylor on 2008-11-19
How serendipitous to have the solution to my problem posted only 1 hour ago, and yet already findable.

The error I got following the instructions on the ies4linux website was 

Gtk:ERROR:/build/buildd/gtk+2.0-2.14.4/gtk/gtktextview.c:3425:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)

I had just installed wine and cabextract 30 seconds earlier from repositories, but doing the uninstall and then following the psychocats instructions did the trick. Who knows how much of that was necessary, but now it works (on Intrepid 64 bit).

---

### Post by c0da on 2008-11-24
I got this error message during the installation:

> ......
......
......
   100% FONTSUP.CAB
   100% VGX.CAB
   100% SCR56EN.CAB

  Downloading from macromedia.com:
   100% swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
ie_1.cab: can't find ie_3.CAB
ERROR; file "WININET.DLL" cannot be extracted, cabinet set is incomplete.
wininet.dll: error in CAB data format
[COLOR="Red"] An error occured when trying to cabextract some files[/COLOR].

---

### Post by hwang on 2008-12-19
Please check your DNS setting(/etc/resolv.conf)

I remove a server from resolv.conf, which is not accessable in my local network, then run ies4linux without modify .py file, install IE successfully.

---

### Post by nirajkeriwala on 2009-01-07
Hi,

I am facing problem while installing IEs4Linux getting the below mentioned error

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.3/threading.py", line 436, in __bootstrap
    self.run()
  File "/usr/lib/python2.3/threading.py", line 416, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/local/ies4linux-2.5beta6/ui/pygtk/ies4linux-gtk.py", line 225, in run_command
    self.process = Popen(self.command, stderr=STDOUT, stdout=PIPE)
NameError: global name 'Popen' is not defined


pls. help me to configure

Thanks,

---

### Post by teitur on 2009-01-08
If the above did not help you (like it did not help me, sorry, don't know why) I would like to refere to the following report in general
[http://ubuntuforums.org/showthread.php?t=1003201](http://ubuntuforums.org/showthread.php?t=1003201)
and the command
./ies4linux --no-gui
in particulare. That solved the problem for me.

---

### Post by noothe on 2009-01-15
> ./ies4linux --no-gui
was the solution for me as well.

the graphical installer wouldn't work on my samsung notebook with xubuntu 8.10

---

### Post by aslamsha on 2009-02-04
Hi,

I had to test my web app in IE.. tried installing ies4linux, but getting an error: 
```

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   20%  SCR56EN.CABAn error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/SCR56EN.CAB


```

Please help!

---

### Post by aslamsha on 2009-02-04
Wow!
got it working.. I followed this particular comment:
[http://www.tatanka.com.br/ies4linux/news/54#comment-10037]("http://www.tatanka.com.br/ies4linux/news/54#comment-10037")

and downloaded SCR56EN.CAB from [http://www.filewatcher.com/m/scr56en.cab.800365.0.0.html]("http://www.filewatcher.com/m/scr56en.cab.800365.0.0.html")

put this file in > ~/.ies4linux/downloads/ie6/EN-US/

then run the setup again > ./ies4linux --no-gui

works for me!

---

### Post by ydchou_69 on 2009-06-14
I am facing problems installing ies4linux on Ubuntu 8.10, Wine 1.0.1

I followed procedure enumerated earlier and ies4linux-2.99.0 folder was created in my home folder. Then using terminal I executed necessary commands for installation. Yhe terminal report is reproduced below:

[I]yogesh@yogesh-desktop:~$ cd ies4linux-2.99.0

yogesh@yogesh-desktop:~/ies4linux-2.99.0$ ./ies4linux --no-gui
[/I]
[B]mkdir: cannot create directory `/home/yogesh/.ies4linux/tmp': Permission denied
/home/yogesh/ies4linux-2.99.0/lib/functions.sh: line 418: [: =: unary operator expected
!! Needs /home/yogesh/.ies4linux/tmp for temporary files
[/B]

[COLOR="Red"]I then created a tmp folder in ies4linux-2.99.0 folder
[/COLOR]

*yogesh@yogesh-desktop:~/ies4linux-2.99.0$ ./ies4linux --no-gui*
[B]mkdir: cannot create directory `/home/yogesh/.ies4linux/tmp': Permission denied
/home/yogesh/ies4linux-2.99.0/lib/functions.sh: line 418: [: =: unary operator expected
!! Needs /home/yogesh/.ies4linux/tmp for temporary files[/B]

[COLOR="Red"]I then tried sudo which worked[/COLOR]

[I]yogesh@yogesh-desktop:~/ies4linux-2.99.0$ sudo ./ies4linux --no-gui
[sudo] password for yogesh: 
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

You are root! This is very discouraged! IE is too insecure for you to give him root access.
Want a tip from a friend? Run ies4linux as your normal user or, what's better, if you can, create a separate user just do handle your IEs.

*IEs4Linux will:*
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/yogesh/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB

  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
  Installing IE 6
  Installing DCOM98
  Installing TTF Fonts
  Installing ActiveX MFC42
  Installing RICHED20
  Installing registry
  Finalizing
[ OK ]

Installing Flash Player 9
  Extracting files
  Installing flash on ie6
  Finalizing
[ OK ]

IEs4Linux installations finished!

To run your IEs, type:
 /home/yogesh/bin/ie6[/I]

*yogesh@yogesh-desktop:~/ies4linux-2.99.0$ /home/yogesh/bin/ie6*
[B]rm: remove write-protected regular empty file `/home/yogesh/.ies4linux/ie6/.firstrun'? 
[/B]
[COLOR="Red"]I have changed the owner ship of /home/yogesh/bin and /home/yogesh/bin/ie6
 and the desktop desktop configuration file from root to yogesh[/COLOR]

yogesh@yogesh-desktop:~/ies4linux-2.99.0$ /home/yogesh/bin/ie6
rm: remove write-protected regular empty file `/home/yogesh/.ies4linux/ie6/.firstrun'? 

yogesh@yogesh-desktop:~/ies4linux-2.99.0$ /home/yogesh/bin/ie6
rm: remove write-protected regular empty file `/home/yogesh/.ies4linux/ie6/.firstrun'? ^C


Whats wrong? Please help

---

### Post by zama on 2009-06-23
Hello Could some one help me on this issue am trying to run IE on ubuntu and am getting this error when trying to install

IEs4Linux will: 
  - Install Internet Explorers: 6.0, 5.5, 5.01 
  - Using IE locale: EN-US 
  - Install Adobe Flash 9.0 
  - Install everything at: /home/zama/.ies4linux 
[ OK ] 
 
Downloading everything we need 
  Downloading from microsoft.com: 
   40%  DCOM98.EXE!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: DCOM98.EXE

---

### Post by wruslan on 2010-11-11
Bismillah.
Thu Nov 11 13:50:40 MYT 2010

root@wruslan-ub10rtai:/usr/bin# uname -a
Linux wruslan-ub10rtai 2.6.32-122-rtai #rtai SMP Tue Jul 27 12:44:07 CDT 2010 i686 GNU/Linux
root@wruslan-ub10rtai:/usr/bin# 

CREATE SOFTLINK wineprefixcreate TO wineboot
==============================================
root@wruslan-ub10rtai:/usr/bin# cp wineboot wineboot-backup
root@wruslan-ub10rtai:/usr/bin# ln -sf wineboot wineprefixcreate
root@wruslan-ub10rtai:/usr/bin# ls -al | grep wine
...
-rwxr-xr-x  1 root   root        1582 2010-11-03 03:06 wineboot
lrwxrwxrwx  1 root   root           8 2010-11-11 13:41 wineprefixcreate -> wineboot
...
root@wruslan-ub10rtai:/usr/bin# updatedb
root@wruslan-ub10rtai:/usr/bin# 

INSTALL LATEST WINE (wine1.3)
============================================
root@wruslan-ub10rtai:/usr/bin# apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@wruslan-ub10rtai:/usr/bin# 

DOWNLOAD AND EXTRACT ies4linux-latest.tar.gz
============================================
ies4linux-latest.tar.gz (332341 2008-02-06 17:49)

INSTALL ies4linux-2.99.0.1
============================================
root@wruslan-ub10rtai:~/temp/ies4linux-2.99.0.1# ./ies4linux --no-gui
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

You are root! This is very discouraged! IE is too insecure for you to give him root access.
Want a tip from a friend? Run ies4linux as your normal user or, what's better, if you can, create a separate user just do handle your IEs.

IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /root/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB

  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
  Installing IE 6
  Installing DCOM98
  Installing TTF Fonts
  Installing ActiveX MFC42
  Installing RICHED20
  Installing registry
  Finalizing
[ OK ]

Installing Flash Player 9
  Extracting files
  Installing flash on ie6
  Finalizing
[ OK ]

IEs4Linux installations finished!

To run your IEs, type:
 /root/bin/ie6

RUN IE6 ON LINUX (SUCCESS - Alhamdulillah)
=============================================
root@wruslan-ub10rtai:~/temp/ies4linux-2.99.0.1# /root/bin/ie6

DONE. THE IE6 BROWSER POPS UP. Wallah.
=============================================

---

### Post by ldcdc on 2010-12-28
Thank you wruslan! That did the trick! Perhaps editing the create_wine_prefix function in the ies4linux-2.99.0.1/lib/functions.sh file and replacing "wineprefixcreate" with "wineboot" would do the trick as well, but I didn't try it.

The other IE install methods (playonlinux,winetricks) did not have activex working, and I really needed that, hence ies4linux has been a real gem for me.

---

### Post by Thoboran on 2011-01-08
It worked just fine with ubuntu 10.10 aswell. thanks for the guide!

---

### Post by xstyr on 2011-10-13
> **ldcdc said:**
> Thank you wruslan! That did the trick! Perhaps editing the create_wine_prefix function in the ies4linux-2.99.0.1/lib/functions.sh file and replacing "wineprefixcreate" with "wineboot" would do the trick as well, but I didn't try it.

The other IE install methods (playonlinux,winetricks) did not have activex working, and I really needed that, hence ies4linux has been a real gem for me.

Trying the above I got 
ies4linux-2.99.0.1$ ./ies4linux --no-gui
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

I tried your idea and did a find-replace in ies4linux-2.99.0.1/lib/functions.sh for 'wineprefixcreate' and replaced with 'wineboot' and this worked perfectly :D
Thanks wruslan and thanks ldcdc for the tip :)

---

### Post by oldos2er on 2011-10-13
Closed, necromancy.

---

