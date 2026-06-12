---
title: "Installing Gyach Enhanced"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by rvricaforte on 2005-09-28
Anybody here able to install Gyach enhanced succesfully?  Sure could used some expert advice.

---

### Post by sabitha on 2005-09-28
first u have to go to your folder download of gyach, then move couple of file to the root directory 
$sudo su
Passwd:
#mv gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 /
#mv gyachE* /

go to root directory 
#cd /
#tar xjvf gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2
#tar xjvf gyachE-Media-Package-0.2.tar.bz2
#tar xjvf gyachE-Encryption-Plugins-0.2-i586.tar.bz2
#tar xjvf gyachE-Webcam-Utilities-0.4-i586.tar.bz2
#tar xjvf gyachE-XMMS-Plugins-0.4-i586.tar.bz2

then go back to first folder where you put gyach download, for the other file
#cd /home/user/.... (up to u)

#tar xjvf libgtkhatml-2.pre-compiled-courtesy-package.i586.tar.bz2
#cd gtkhtml2
#cp libgtkhtml-2.so.0 /usr/lib
 out from the directory gtkhtml2
#cd ..

#tar xjvf gpgme-0.3.16-compiled-i586.tar.bz2
#cd usr
#cp lib/libgpgme.so.6.3.7 /usr/lib
make link to /usr/lib/libgpgme.so.6.3.7
#ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so.6
#ln -s /usr/lib/libgpgme.so.6.3.7 /usr/lib/libgpgme.so

out from directory usr
#cd ..

#tar xjvf gyach_enhanced_fonts1.tar.bz2
#tar xjvf gyach_enhanced_fonts2.tar.bz2

go to directory ttf
#cd ttf
#cp * /usr/share/fonts/truetype/

out of directory ttf
#cd ..

install debian package
#dpkg -i libltdl3_1.5.6-6_i386.deb
#dpkg -i libltdl3-dev_1.5.6-6_i386.deb

make link for libgailutil.so.16 within libgailutil.so.17.0.1
#ln -s /usr/lib/libgailutil.so.17.0.1 /usr/lib/libgailutil.so.16
this is the call trick, because if u not had libgailutil.so.16 gyach will ask that library :)

do data base update with :
#/sbin/ldconfig
#exit

then run gyach from the terminal code :
$/usr/local/bin/gyach &

finish 
now u can use gyach with webcam support for yahoo messenger
and don't forget to disable the animated smiley on gyach setup or u can try it self to see what happens if that animated smiley enable. =))

sorry my engglish not good because i spend my life time in brebes :))

pm: $sudo apt-get install libmcrypt4

have a nice try ..........

---

### Post by rvricaforte on 2005-09-28
Thank you very much Sabitha!  I really appreciate your assistance.  I'll try your advice as soon as I get back from the office and will inform you if its successful or not.  

Regards!

---

### Post by sabitha on 2005-09-28
of course it sucessfully :) but gyach enhanced is unstable, you can read about that on their website ;-)

---

### Post by mumushi on 2005-09-28
> go to root directory
#cd /
#tar xjvf gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2
#tar xjvf gyachE-Media-Package-0.2.tar.bz2
#tar xjvf gyachE-Encryption-Plugins-0.2-i586.tar.bz2
#tar xjvf gyachE-Webcam-Utilities-0.4-i586.tar.bz2
#tar xjvf gyachE-XMMS-Plugins-0.4-i586.tar.bz2

Hello Sabitha, I was reading your instructions but got confused in this area. are those files already downloaded? just wanted to clarify. Sorry i am totally a newbie so i really wanted to be clarified :) . Hope you will be patient with me.;-)

---

### Post by sabitha on 2005-09-29
ok i,m forget to tell for the first time installing gyach enhanced.
download file :
[http://sourceforge.net/project/showfile.php?group_id=57756](http://sourceforge.net/project/showfile.php?group_id=57756)
take just the binary file

gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2?donload](http://prdownload.sourceforge.net/phpaint/gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2?donload)

gyachE-Media-Package-0.2.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyachE-Media-Package-0.2.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyachE-Media-Package-0.2.tar.bz2?download)

gyachE-Encryption-Plugins-0.2.i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyachE-Encryption-Plugins-0.2.i586.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyachE-Encryption-Plugins-0.2.i586.tar.bz2?download)

gyach_enhanced_fonts1.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyach_enhanced_fonts1.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyach_enhanced_fonts1.tar.bz2?download)

gyach_enhanced_fonts2.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyach_enhanced_fonts2.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyach_enhanced_fonts2.tar.bz2?download)

gyachE-Webcam-Utilities-0.4.i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyachE-Webcam-Utilities-0.4.i586.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyachE-Webcam-Utilities-0.4.i586.tar.bz2?download)

gyachE-XMMS-Plugin-0.4.i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gyachE-XMMS-Plugin-0.4.i586.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gyachE-XMMS-Plugin-0.4.i586.tar.bz2?download)

gpgme-0.3.16-compiled-i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/gpgme-0.3.16-compiled-i586.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/gpgme-0.3.16-compiled-i586.tar.bz2?download)

libgtkhtml-2.pre-compiled-courtesy-package.i586.tar.bz2
[http://prdownload.sourceforge.net/phpaint/libgtkhtml-2.pre-compiled-courtesy-package.i586.tar.bz2?download](http://prdownload.sourceforge.net/phpaint/libgtkhtml-2.pre-compiled-courtesy-package.i586.tar.bz2?download)

libltdl3
[http://package.debian.org/cgi-bin/download.pl?arch=i386&file%2Fmain%2Flibt%2Flibltdl3_1.5.6-6_i386.deb&md5sum=040062cc0da5adc58f99ec1b9f5fd9de&arch=i386&type=main](http://package.debian.org/cgi-bin/download.pl?arch=i386&file%2Fmain%2Flibt%2Flibltdl3_1.5.6-6_i386.deb&md5sum=040062cc0da5adc58f99ec1b9f5fd9de&arch=i386&type=main)

libltdl3-dev
[http://package.debian.org/cgi-bin/download.pl?arch=i386&file%2Fmain%2Flibt%2Flibltdl3-dev_1.5.6-6_i386.deb&md5sum=a0d1b49748c80eda09509dfae02ddf54&arch=i386&type=main](http://package.debian.org/cgi-bin/download.pl?arch=i386&file%2Fmain%2Flibt%2Flibltdl3-dev_1.5.6-6_i386.deb&md5sum=a0d1b49748c80eda09509dfae02ddf54&arch=i386&type=main)

put all file on your own directory
ex:/home/client/download/

---

### Post by mumushi on 2005-09-29
:(  i can't open the links you have given. It displays an error. I just don't know whats the matter. :confused:

---

### Post by sabitha on 2005-09-29
maybe i was wrong in writing  but you also can try search on sourceforge.net with the keyword gyach
or try with this one :

[http://sourceforge.net/project/showfiles.php?group_id=57756](http://sourceforge.net/project/showfiles.php?group_id=57756)

sorry for the mistake that i made

---

### Post by mumushi on 2005-09-29
ok i will be doing that. i'll just be posting some problems regarding it. Please be patient with me :D. Thanks!

---

### Post by mumushi on 2005-09-29
[HTML]#mv gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 /
#mv gyachE* /[/HTML]

ok i downloaded the files needed except for these two files libltdl3 and libltdl3-dev. i can't find them on source forge. i tried to start installation but got confused on that part (quoted).

thanks. 


:D Please be patient with me :D

---

### Post by rvricaforte on 2005-09-29
[QUOTE=mumushi][HTML]#mv gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2 /
#mv gyachE* /[/HTML]


I found said two files by searching via yahoo and google.:razz:

---

### Post by rvricaforte on 2005-09-29
It Works!!!!!  Success!!!!! Its kinda unstable though, but who cares?  Now I can view webcams and chat with multiple windows! Thanks a lot Sabitha for your advice!

---

### Post by mumushi on 2005-09-30
ok i will be searching for these files too. thanks for the info. :D

---

### Post by mumushi on 2005-09-30
> gccservices@gccservice:~/Desktop/Gyach Enhanced$ dir
gpgme-0.3.16-compiled-i586.tar.bz2
gtkhtml2
gyach
gyachE-Encryption-Plugins-0.2-i586.tar.bz2
gyachE-Media-Package-0.2.tar.bz2
gyach_enhanced_fonts1.tar.bz2
gyach_enhanced_fonts2.tar.bz2
gyach-enhanced_pyvoice-binary-1.0.7-i586.tar.bz2
gyachE-Webcam-Utilities-0.4-source.tar.bz2
gyachE-XMMS-Plugin-0.4-i586.tar.bz2
libgtkhtml-2.pre-compiled-courtesy-package.i586.tar.bz2
libltdl3_1.5.20-2_i386.deb
libltdl3_1.5.6-6_i386.deb
libltdl3-dev_1.5.20-2_i386.deb
libltdl3-dev_1.5.6-6_i386.deb
ttf
usr
gccservices@gccservice:~/Desktop/Gyach Enhanced$ cd usr
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr$ ls
include  lib  local  share
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr$ cd local
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr/local$ ls
bin  share
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr/local$ cd bin
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr/local/bin$ ls
gyach
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr/local/bin$ gyach
bash: gyach: command not found
gccservices@gccservice:~/Desktop/Gyach Enhanced/usr/local/bin$



Hello Sabitha, this is what i did. I hope you can see what the process :D, but i got that error. i already installed it but it says there's no such file. :(


Please help me with this. Where did i go wrong?


:D Please be patient with me :D

---

### Post by sabitha on 2005-09-30
you should run from from your local direktory
ex. me : admin@ubuntu:~$ /usr/local/bin/gyach &
[1] 13787
or you just can write
admin@ubuntu:~$gyach

so i think you wrong to run gyach from that directory
or u can make your icon on desktop
right click --> create launcer --- on the command write /usr/local/bin/gyach &
then
select the icon /usr/local/share/gyach/pixmaps/gyach-icon_32.png

after that you can run gyach without terminal just double click the icon

---

### Post by mumushi on 2005-10-01
ok i did all the instructions but i stil got this error 

> gyach: error while loading shared libraries: libgailutil.so.16: cannot open shared object file: No such file or directory


:confused:  what shall i do?

---

### Post by sabitha on 2005-10-04
have'd you tried this :

make link for libgailutil.so.16 within libgailutil.so.17.0.1

#ln -s /usr/lib/libgailutil.so.17.0.1 /usr/lib/libgailutil.so.16

this is the call trick, because if u not had libgailutil.so.16 gyach will ask that library

---

### Post by jigger on 2005-10-05
Where can I download or get this ff files....

libltdl3_1.5.20-2_i386.deb
libltdl3_1.5.6-6_i386.deb
libltdl3-dev_1.5.20-2_i386.deb
libltdl3-dev_1.5.6-6_i386.deb

Tnx for the advance reply.

---

### Post by sabitha on 2005-10-06
u can use

$ sudo apt-get install libltdl3
$ sudo apt-get install libltdl3-dev

;)

---

### Post by sabitha on 2005-10-09
but i still dont know why i can use voice chat whit this gyach enhanced 
here's my error :
admin@ubuntu:~$ gyach
Use of deprecated SAXv1 function endElement
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIManager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.TreeView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints or tuples

anybody can help me with this
just for the voice in gyach

---

### Post by endangst on 2006-01-09
Hi Sabitha.  I have the same problem.

```
endangst@ubuntu:~/gyach$ gyach
shell-init: error retrieving current directory: getcwd: cannot access parent dir ectories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIM anager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.Tre eView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic  operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples
shell-init: error retrieving current directory: getcwd: cannot access parent dir ectories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIM anager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.Tre eView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic  operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples
shell-init: error retrieving current directory: getcwd: cannot access parent dir ectories: No such file or directory
/usr/local/share/gyach/pyvoice/pytsp.py:2: RuntimeWarning: Python C API version mismatch for module pytspc: This Python has API version 1012, module pytspc has version 1011.
  import pytspc
/usr/local/share/gyach/pyvoice/pyvoiceui.py:161: DeprecationWarning: use gtk.UIM anager
  itemf=ItemFactory(MenuBar, "<main>", ag)
/usr/local/share/gyach/pyvoice/pyvoiceui.py:264: DeprecationWarning: use gtk.Tre eView
  self.nmlist=CList(3,[' I ',' '+_('Name')+' ',' '+_('Alias')+' '])
/usr/local/share/gyach/pyvoice/pyvoiceui.py:298: Warning: unsupported arithmetic  operation for flags type
  prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
Traceback (most recent call last):
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1027, in ?
    runApp()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 1015, in runApp
    pyvoicegui()
  File "/usr/local/share/gyach/pyvoice/pyvoiceui.py", line 298, in __init__
    prevtable.attach( tvolbox, 1, 2, 0, 1, (EXPAND+FILL), (0), 0, 0)
TypeError: flag values must be strings, ints, longs, or tuples

(gyach:4757): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (ob ject)' failed

(gyach:4757): Gdk-CRITICAL **: gdk_draw_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf )' failed

(gyach:4757): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT ( object)' failed
Segmentation fault
endangst@ubuntu:~/gyach$

```

---

### Post by sabitha on 2006-01-09
udah di edit belom EXPAND+FILL nya ;)

---

