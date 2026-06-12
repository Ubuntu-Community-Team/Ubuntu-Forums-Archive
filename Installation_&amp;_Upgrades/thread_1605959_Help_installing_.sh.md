---
title: "Help installing .sh"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by layers on 2010-10-25
I downloaded this .sh file, which I want to install but I can't. Does anybody know what to do here?

```
ibo@ibo-laptop:~$ cd Desktop
ibo@ibo-laptop:~/Desktop$ sudo sh quartus.sh
[sudo] password for ibo: 
sh: Can't open quartus.sh
ibo@ibo-laptop:~/Desktop$ sudo sh ./quartus.sh
sh: Can't open ./quartus.sh
ibo@ibo-laptop:~/Desktop$ 

```

and it is

```
-rwxr-xr-x 1 ibo ibo 3025418666 2010-10-25 22:38 quartus.sh

```

---

### Post by drdos2006 on 2010-10-26
From the terminal, 
you need to change directory to the /path/of/the/file with:
cd /path/of/the/file

then run:
 sudo bash filename.sh

regards

---

### Post by garvinrick4 on 2010-10-26
Install this it will save a bit of time:
rick@rick-HP-G71-Notebook-PC:~$ aptitude show nautilus-open-terminal
Package: nautilus-open-terminal          
State: installed
Automatically installed: no
Version: 0.18-1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 860k
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.2.5), libcairo2 (>= 1.2.4),
         libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>=
         2.27.0), libglib2.0-0 (>= 2.18.0), libgnome-desktop-2-17 (>= 1:2.29.4),
         libgtk2.0-0 (>= 2.8.0), libnautilus-extension1 (>= 1:2.29.1),
         libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), zlib1g
         (>= 1:1.1.4), gconf2 (>= 2.10.1-2)
Description: nautilus plugin for opening terminals in arbitrary local paths
 nautilus-open-terminal is a proof-of-concept Nautilus extension which allows
 you to open a terminal in arbitrary local folders.

rick@rick-HP-G71-Notebook-PC:~$ 

```
sudo apt-get install nautilus-open-terminal
```
Log off and back on.
You will now be able to right click choose open in terminal and it will do so, is a time saver from opening in path from cd commands.

---

### Post by layers on 2010-10-26
This is a linux package, downloaded from Altera's website, but it is giving me errors. Is there anything I can do?


```
ibo@ibo-laptop:~$ cd Desktop
ibo@ibo-laptop:~/Desktop$ ls -l
total 2957428
-rwxr-xr-x 1 ibo ibo        285 2010-10-09 02:07 calibre.desktop
drwxr-xr-x 3 ibo ibo       4096 2010-10-25 19:50 CppApplication_1
-rwxr-xr-x 1 ibo ibo        477 2010-10-09 01:45 gnome-terminal.desktop
-rwxr-xr-x 1 ibo ibo       4583 2010-10-11 16:21 google-chrome.desktop
-rwxr-xr-x 1 ibo ibo 3025418666 2010-10-25 22:38 quartus.sh
-rwxr-xr-x 1 ibo ibo       1381 2010-10-09 01:44 thunderbird.desktop
ibo@ibo-laptop:~/Desktop$ sudo bash quartus.sh
Creating directory 10.0sp1_quartus_free_linux
Verifying archive integrity... All good.
Uncompressing Quartus II Web Edition software (Free).................................................................................................................................................................................................
Fontconfig error: "conf.d", line 1: no element found
Fontconfig warning: line 73: unknown element "cachedir"
Fontconfig warning: line 74: unknown element "cachedir"
altera_installer/bin/altera_installer_gui: symbol lookup error: /usr/lib/libXi.so.6: undefined symbol: XESetWireToEventCookie
ibo@ibo-laptop:~/Desktop$ 


```

---

### Post by dino99 on 2010-10-26
[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D3362030](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D3362030)

---

### Post by layers on 2010-10-27
Yeah, I was supposed to install another version of Quartis. Sorry.

Now, I am stuck with this *.tar file. I ran "tar -xf q.tar", bur now, I don't know what to do. if I simply type "install", it says it needs some arguments; the included text files do not help either. Can anyone help me, please?

---

### Post by garvinrick4 on 2010-10-27
```
**Installing a Tar.Gz Archive** Hope this helps you.

 Many programs are still wrapped in a tar.gz archive folder. This is similar to a ZIP file, in that all the files are contained inside, but you can't simply extract an executable file. Installing an application from tar.gz is called install from source. To do that, follow the next instructions.
 [[IMG]http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_1.jpg[/IMG]]("http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_1.jpg")
 Download the tar.gz to your desktop, right click and choose extract here. A folder by the same name will be extracted to your desktop. Now, open the Terminal and type: cd desktop.
 [[IMG]http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_2.jpg[/IMG]]("http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_2.jpg")
 This will let your work within the Desktop directory. Now, within the same Terminal window, type: cd foldername
 [[IMG]http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_3.jpg[/IMG]]("http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_3.jpg") 
 [[IMG]http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_3.jpg[/IMG]]("http://media.laptoplogic.com/upload-images/8372/large/8372_Terminal_TAR_3.jpg")
 This will let you work from within the folder you extracted from the tar.gz. Inside this folder will be a file that says program-installer. To install this, type in the Terminal: sh program-installer
 This will install the program from within the Terminal. Simply follow the directions as they appear.  
 Page:1/1  

```

---

### Post by layers on 2010-10-27
Yeah, I did that, but then whenever I type in this, nothing happens:

```
ibo@ibo-laptop:~$ cd Desktop/quartus_free
ibo@ibo-laptop:~/Desktop/quartus_free$ ls
adm.gz        cyc_we.gz       ip.gz         maxii_we.gz  space.txt
agx_we.gz     dev_info.txt    ip_lic.txt    md5sum.txt   stub.csh
aii_we.gz     devinfo_we.gz   libraries.gz  perlsrc.gz   stx2_we.gz
common.gz     dsp_builder.gz  license.txt   qcleanup     stx3_we.gz
compare       eda.gz          linux.gz      qdesigns.gz  stx4_we.gz
cusp.gz       gpl_lic.txt     lmf.gz        qt           stx_we.gz
cyc3_we.gz    gtar            m3k_we.gz     readme.txt   sys_reqs.txt
cyc4e_we.gz   gzip            m7ka_we.gz    sgxii_we.gz  tutorial.gz
cyc4gx_we.gz  help.gz         m7k_we.gz     sgx_we.gz    version.txt
cycii_we.gz   install         manifest.txt  sopc.gz
ibo@ibo-laptop:~/Desktop/quartus_free$ install
install: missing file operand
Try `install --help' for more information.
ibo@ibo-laptop:~/Desktop/quartus_free$ install --version
install (GNU coreutils) 8.5
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.
ibo@ibo-laptop:~/Desktop/quartus_free$ 

```

---

### Post by layers on 2010-10-27
OK, I had to install csh. After that, the ./install command runs, but whenever I have to specify a directory for installation, if I say "/opt/altera", it says permission denied. I am the only user. What gives?

---

### Post by layers on 2010-10-28
i had to type "sudo ./install"

thank you guys, you helped me.

---

