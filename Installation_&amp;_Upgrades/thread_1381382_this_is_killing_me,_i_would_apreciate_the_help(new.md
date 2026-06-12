---
title: "this is killing me, i would apreciate the help(newbie sh*#)"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by newkit on 2010-01-14
I am one of those unfortunate people who purchased the linksys WUSB600N v2 usb wireless, thinking it would just work on my linux os systems, but ooohh no; i was wrong. I downloaded the 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2 driver and i am having trouble unzipping and compilling it. I hope this is the right driver but better yet i can't find any clear step by step instructions of how to compile and install it. If anyone could help it would be much apreciated.

---

### Post by Leppie on 2010-01-14
to unpack cd into the folder where the archive is and issue this command:
```
tar -xvf 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2
```
to compile there should be instructions within the archive (a README file). usually there is an executable called something like configure (check the readme), then you have to issue the command "make" to start the compilation. to install you have to issue the command "sudo make install".

---

### Post by warfacegod on 2010-01-14
Do you have unzip and unrar installed? Check Synaptic.

---

### Post by newkit on 2010-01-14
tar: 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
   
 
wtf does that mean?

---

### Post by Leppie on 2010-01-14
did you change to the folder where you saved the archive?

---

### Post by warfacegod on 2010-01-14
> **newkit said:**
> tar: 2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
   
 
wtf does that mean?

You have to use command cd in Terminal to go to the folder that your package is in. Example:

```
cd /desktop
``` hit enter

---

### Post by audiomick on 2010-01-14
your probably not in the right directory.
do
```
ls
```
if you are in the right place, you will see the file.

if you are not, do
```
cd /path/to/where/the/file/is
```

"ls" again to check you are in the right place, then try the command again.

---

### Post by newkit on 2010-01-14
i have unzip and unrar installed

---

### Post by newkit on 2010-01-14
i see the directoy, it's in downloads

---

### Post by warfacegod on 2010-01-14
Then to get there in Terminal:

```
cd /home/username/downloads
``` hit Enter

---

### Post by newkit on 2010-01-14
i coppied and pasted the file directory/home/tomb/Downloads/2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2
but it says: no such file in directory. What am i doing wrong?

---

### Post by d3v1150m471c on 2010-01-14
[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

Type "tar zxf" into your terminal. You said you put the tar.gz folder in your downloads folder so drag and drop it onto your terminal screen. you will end up with something like this:

d3v11@d3v11m4ch1n3:~$ tar zxf '/home/d3v11/Downloads/kylixlibs3-borqt-3.0-2.tar.gz'

Next, press enter. It will probably spit the extracted file out in your file system, aka your home folder, at which point just move it to whatever directory you want. There are better ways to do this but I cannot remember how. It's been a while since i've touched a tar ball. I recommend google on that one.

You can then "cd" the extracted file by doing something similar. Type "cd" and space into your terminal, just like above, and then drag and drop the extracted file. I like this method because it saves me on the typing.

---

### Post by newkit on 2010-01-14
'/home/tomb/Desktop/2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2' 
bash: /home/tomb/Desktop/2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2: Permission denied

---

### Post by newkit on 2010-01-14
~$ tar zxf file.tar.gz
tar: file.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

 
sorry dudes, i still don't get it

---

### Post by d3v1150m471c on 2010-01-14
> **newkit said:**
> '/home/tomb/Desktop/2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2' 
bash: /home/tomb/Desktop/2009_1222_RT3572_LinuxSTA_V2[1].3.0.0.tar.bz2: Permission denied

use "sudo"

sudo tar zxf (leave a space after zxf, then drag an drop) It will prompt you for your password. Type in your password (you won't be able to see it), then press enter.

---

### Post by d3v1150m471c on 2010-01-14
excuse me. for "tar.bz2" use "jxf" and not "zxf"

---

### Post by newkit on 2010-01-14
i'm strrressin man, like i'm bald now, i'm f*&%'n bald.

---

### Post by d3v1150m471c on 2010-01-14
use "tar jxf" and leave a space before you drag and drop. then press enter. There are tools you can get in synaptic to just right click a package to extract it. if you give me a few i can find them. I use it on mine because i hate having to do this in the terminal. it just eats time.

---

### Post by newkit on 2010-01-14
~$ sudo tar zxf 
[sudo] password for tomb: 
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
[EMAIL="tomb@tomb-laptop:~$"]tomb@tomb-laptop:~$[/EMAIL] sudo tar zxf file.tar.gz
tar: file.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
[EMAIL="tomb@tomb-laptop:~$"]tomb@tomb-laptop:~$[/EMAIL] sudo tar jxf
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.

please help

---

### Post by d3v1150m471c on 2010-01-14
[SIZE=5]jxf, not zxf. [SIZE=2]see above. also, you are telling it to extract nothing. you have to drag and drop the folder onto your terminal after you type tar jxf.
[/SIZE][/SIZE]

---

### Post by d3v1150m471c on 2010-01-14
d3v11@d3v11m4ch1n3:~$ tar jxf '/home/d3v11/Downloads/kylixlibs3-borqt-3.0-2.tar.bz2'

---

### Post by newkit on 2010-01-15
~$ tar jxf /home/tomb/Downloads' 
> 
i don't, you know 
just trying to crawl first, sorry for the wait.

---

