---
title: "Official Ubuntu and PPA?"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2012-07-18
Hi, all:

Sorry for this naive question.
What is the relationship between current official Ubuntu 12.04 and PPA launchpad??

Well, what I want to do is actually trying to add 
[https://launchpad.net/ubuntu/precise/+source/unicap](https://launchpad.net/ubuntu/precise/+source/unicap)
or even
[https://launchpad.net/ubuntu/precise](https://launchpad.net/ubuntu/precise)
[https://launchpad.net/ubuntu/+milestone/ubuntu-12.04](https://launchpad.net/ubuntu/+milestone/ubuntu-12.04)

to my /etc/apt/sources.list
for the reason that I found the default unicap in current Ubuntu 120.4 repository doesn't work properly. I'm expecting to try launchpad Unicap here [https://launchpad.net/ubuntu/precise/+source/unicap](https://launchpad.net/ubuntu/precise/+source/unicap) .


Can anybody help ?


Cheers
Pei

---

### Post by dino99 on 2012-07-18
i have 0.9.12-2 here into quantal archives. why do you want to add a ppa then ?

if you want the latest packages, you still can download them into an empty folder, then from there, run:  sudo dpkg -i *

[https://launchpad.net/unicap](https://launchpad.net/unicap)

---

### Post by jiapei100 on 2012-07-18
Hi, Thanks dino99. Don't know why "sudo dpkg -i *" doesn't work for me. It just kept telling dpkg-deb: error: `unicap_0.9.12-2.debian.tar.gz' is not a debian format archive

Then, I downloaded the source of 0.9.12-2, and do
```

./configure 
make

```

make gives me the error

> make[3]: Entering directory `/home/pei/Downloads/unicap_0.9.12-2/libunicap-0.9.12/cpi/v4l'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../include -I../../include -I../../common    -g -O2 -MT v4l.lo -MD -MP -MF .deps/v4l.Tpo -c -o v4l.lo v4l.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../include -I../../include -I../../common -g -O2 -MT v4l.lo -MD -MP -MF .deps/v4l.Tpo -c v4l.c  -fPIC -DPIC -o .libs/v4l.o
v4l.c:52:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[3]: *** [v4l.lo] Error 1
make[3]: Leaving directory `/home/pei/Downloads/unicap_0.9.12-2/libunicap-0.9.12/cpi/v4l'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/pei/Downloads/unicap_0.9.12-2/libunicap-0.9.12/cpi'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pei/Downloads/unicap_0.9.12-2/libunicap-0.9.12'
make: *** [all] Error 2




So, now, it seems the only way for me to try my luck is to build unicap 0.9.5-1.1build1 manually. (The default unicap from Ubuntu 12.04 repository won't work fine. )


So unlucky. Thanks anyway.


Best Regards
Pei




> **dino99 said:**
> i have 0.9.12-2 here into quantal archives. why do you want to add a ppa then ?

if you want the latest packages, you still can download them into an empty folder, then from there, run:  sudo dpkg -i *

[https://launchpad.net/unicap](https://launchpad.net/unicap)

---

### Post by jiapei100 on 2012-07-18
Well, still the same for 0.9.5.
It seems a lot of people have this issue:

> v4l.c:52:28: fatal error: linux/videodev.h: No such file or directory

For example: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621954](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=621954)


Cheers
Pei

---

### Post by jiapei100 on 2012-07-18
Solution:

Modify 2 files
> ../cpi/v4l/unicap-0.9.5/cpi/v4l/v4l.c
../cpi/v4l/unicap_0.9.5/cpi/v4l2cpi/uvcvideo.h

in the following way:
```
#include <libv4l1-videodev.h>
//#include <linux/videodev.h>
```


Cheers
Pei

---

### Post by jiapei100 on 2012-07-18
Hi, Thank you dino99.

Finally, problem solved. I rebuilt unicap, with the self-built unicap, I rebuilt OpenCV2.4.2. Now, cvQueryFrame() doesn't hang any longer. 

However, before the capturing, I got several **Invalid argument** before the initialization is done.
> 
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
init done 

I myself am certain that **VIDIOC_QUERYMENU** is used by unicap. So, what for about the above 7 **VIDIOC_QUERYMENU: Invalid argument** ??


Thanks
Pei JIA

---

### Post by mastablasta on 2012-07-19
> **jiapei100 said:**
> Hi, Thanks dino99. Don't know why "sudo dpkg -i *" doesn't work for me. It just kept telling dpkg-deb: error: `unicap_0.9.12-2.debian.tar.gz' is not a debian format archive
 

 
ofcourse it's not. it should be a .deb file. .tar.gz is a compressed archive. if the .deb file is inside you need to unpack it first and then run the dpkg command.
 
if however there is no .deb file inside then it means .tar.gz is likely a source code which needs to be compiled manually.

---

### Post by mastablasta on 2012-07-19
> **jiapei100 said:**
>  
Sorry for this naive question.
What is the relationship between current official Ubuntu 12.04 and PPA launchpad??

 
PPA is a personal package archive and is not officially "supported" by cannonical.
 
th einstructions on how to install a ppa can be found on launchpad site. for example the first link you want to add is a source file which means it needs to be compiled. to do that succesfully all dependencies written below must first be met.
 
so how about this one: [https://launchpad.net/~arne-datafloater/+archive/unicap](https://launchpad.net/~arne-datafloater/+archive/unicap)
 
this one is already connected with necessary dependencies. so just add it to sources in software center, update the software center/surces and then install it. instructions for it are on the site.

---

### Post by smarty11 on 2013-07-09
I guess doing all this is not necessary. I found an easier solution. I don't know how or why it worked but I would like to tell what I did.<br><br>First I tried the C++ style coding cv::Mat and cv::VideoCapture and set the capture properties<br>```
<br>cv::VideoCapture capture(0);<br>capture.set(CV_CAP_PROP_FRAME_WIDTH, 174);<br>capture.set(CV-CAP_PROP_FRAME_HEIGHT, 144);<br>while(true){<br>&nbsp; &nbsp; capture &gt;&gt; Image;<br>&nbsp; &nbsp; cv::imshow("Video",Image);<br>&nbsp; &nbsp; cv::waitKey(100);<br>}<br>
```<br>This worked.<br><br>Then I did the same to IplImage* frame that captures the frames, I set its size by cvSize(174, 144), it also worked.<br><br>And finally I thought of checking the old code that was not working initially, but now that also started working.<br>> **jiapei100 said:**
> Hi, Thank you dino99.<br>
<br>
Finally, problem solved. I rebuilt unicap, with the self-built unicap, I rebuilt OpenCV2.4.2. Now, cvQueryFrame() doesn't hang any longer. <br>
<br>
However, before the capturing, I got several <strong>Invalid argument</strong> before the initialization is done.<br>
<br>
<br>
I myself am certain that <strong>VIDIOC_QUERYMENU</strong> is used by unicap. So, what for about the above 7 <strong>VIDIOC_QUERYMENU: Invalid argument</strong> ??<br>
<br>
<br>
Thanks<br>
Pei JIA<br>
<br>

---

