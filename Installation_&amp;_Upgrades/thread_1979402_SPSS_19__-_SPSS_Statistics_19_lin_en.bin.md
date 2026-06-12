---
title: "SPSS 19  - SPSS_Statistics_19_lin_en.bin"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by e450 on 2012-05-13
Hi, i have to make some home work in SPSS 19 program. 
I got activation code from school. 
I also downloaded SPSS_Statistics_19_lin_en.bin file from our schools ftp server.

So i would like to install SPSS on my Linux machine, but i have some problems :S
```

e450@e450-1215B-1215B:~/Prejemi$ ls -l
skupno 849276
-rw-rw-r-- 1 e450 e450 869651320 maj 13 15:30 SPSS_Statistics_19_lin_en.bin
e450@e450-1215B-1215B:~/Prejemi$ sudo sh SPSS_Statistics_19_lin_en.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...


Graphical installers are not supported by the VM. The console mode will be used instead...

Preparing CONSOLE Mode Installation...

===============================================================================
Choose Locale...
----------------

    1- English
    2- Polski

CHOOSE LOCALE BY NUMBER: 1

=======================================================

Installer User Interface Mode Not Supported

The installer cannot run in this UI mode. To specify the interface mode, use the -i command-line option, followed by the UI mode identifier. The valid UI modes identifiers are GUI, Console, and Silent.

=======================================================

e450@e450-1215B-1215B:~/Prejemi$ 

```So what I'm missing? I'm using Xfce - [http://xubuntu.org/](http://xubuntu.org/)

```

e450@e450-1215B-1215B:~/Prejemi$ sudo sh SPSS_Statistics_19_lin_en.bin -i swing
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...


Graphical installers are not supported by the VM. The console mode will be used instead...

Preparing CONSOLE Mode Installation...

===============================================================================
Choose Locale...
----------------

    1- English
    2- Polski

CHOOSE LOCALE BY NUMBER: 1

=======================================================

Installer User Interface Mode Not Supported

The installer cannot run in this UI mode. To specify the interface mode, use the -i command-line option, followed by the UI mode identifier. The valid UI modes identifiers are GUI, Console, and Silent.

=======================================================

e450@e450-1215B-1215B:~/Prejemi$ sudo sh SPSS_Statistics_19_lin_en.bin -i GUI
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...


Graphical installers are not supported by the VM. The console mode will be used instead...

Preparing CONSOLE Mode Installation...

===============================================================================
Choose Locale...
----------------

    1- English
    2- Polski

CHOOSE LOCALE BY NUMBER: 1

=======================================================

Installer User Interface Mode Not Supported

The installer cannot run in this UI mode. To specify the interface mode, use the -i command-line option, followed by the UI mode identifier. The valid UI modes identifiers are GUI, Console, and Silent.

=======================================================

e450@e450-1215B-1215B:~/Prejemi$ 

```Thanks for help.

---

### Post by e450 on 2012-05-13
Hi, problem is because I have 64bit version and Java inside .bin file is 32bit.
```
locate libc.so.6
```this file should be in /lib/libc.so.6 but is in /lib/x86_64-linux-gnu/libc.so.6

So I had to execute those 2 commands.
```

sudo apt-get install libstdc++5
sudo apt-get install ia32-libs

```More info here [http://forum.ubuntued.info/viewtopic.php?f=31&t=1320](http://forum.ubuntued.info/viewtopic.php?f=31&t=1320)

Now I successfully installed SPSS.

Bye

(how to mark this solved?)

---

### Post by e450 on 2012-05-13
hi, again how to start SPSS? there is no link in menu. 
(how to add link in menu? - manually)
in /opt/IBM/SPSS/Statistics/19/ is installed SPSS,
and also in my home folder is new folder named SPSSInc.

is there any console command to run SPSS?

---

### Post by Toz on 2012-05-13
> **e450 said:**
> hi, again how to start SPSS? there is no link in menu.
I believe the terminal command to run the program is:
```
/opt/IBM/SPSS/Statistics/19/bin/stats
```
> (how to add link in menu? - manually)
Create an .desktop file:
```
sudo leafpad /usr/share/applications/spss.desktop
```
...with the following content:
```
[Desktop Entry]
Name=SPSS
GenericName=SPSS
Comment=Statistics program
Exec=/opt/IBM/SPSS/Statistics/19/bin/stats
Icon=gnome-monitor
Terminal=false
Type=Application
Categories=Application;Graphics;
```
...(feel free to change the icon to whatever you want) and save the file. Then, if it doesn't automatically show up in the menu under Graphics, try:
```
xfdesktop --reload
```
...or log out and back in again.

---

### Post by e450 on 2012-05-13
Thank you for your help. 

SPSS now works fine :)

---

