---
title: "Help me! I cant install the software.. I get errors!!"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ann pic on 2008-02-23
The output is as below. Anyone can help me what library i still need to install? Where i can find it?

ann@anndesktop:~$
cd /home/ann/desktop/
ann@anndesktop:~/
desktop$ ls
bttv0.9.15
epson31411eu.zip motion3.2.9.
tar.gz
bttv0.9.15.
tar.tar epson31411eu.zip_FILES
ann@anndesktop:~/
desktop$ tar *xvzf
/home/ann/desktop/motion3.2.9.
tar.gz
motion3.2.9/
motion3.2.9/
motion.spec.in
motion3.2.9/
picture.h
motion3.2.9/
rotate.h
motion3.2.9/
pwcioctl.
hpwc9.0.1
motion3.2.9/
alg.h
motion3.2.9/
conf.c
motion3.2.9/
pwcioctl.
hpwc8.0
motion3.2.9/
CODE_STANDARD
motion3.2.9/
README.MacOSX
motion3.2.9/
thread2.conf
motion3.2.9/
motion.initFreeBSD.
sh.in
motion3.2.9/
README
motion3.2.9/
netcam_wget.c
motion3.2.9/
FAQ
motion3.2.9/
webhttpd.h
motion3.2.9/
webcam.h
motion3.2.9/
motiondist.
conf
motion3.2.9/
INSTALL
motion3.2.9/
ffmpeg0.4.8macosx.
patch
motion3.2.9/
picture.c
motion3.2.9/
event.h
motion3.2.9/
ffmpeg.c
motion3.2.9/
netcam_wget.h
motion3.2.9/
draw.c
motion3.2.9/
track.h
motion3.2.9/
mmx.h
motion3.2.9/
conf.h
motion3.2.9/
motion.1
motion3.2.9/
video2.c
motion3.2.9/
README.axis_2100
motion3.2.9/
netcam_ftp.h
motion3.2.9/
CREDITS
motion3.2.9/
configure.in
motion3.2.9/
thread4.conf
motion3.2.9/
pwcioctl.
h
motion3.2.9/
pwcioctl.
h10.0.5
motion3.2.9/
video_common.c
motion3.2.9/
motion.h
motion3.2.9/
netcam_ftp.c
motion3.2.9/
rotate.c
motion3.2.9/
netcam.c
motion3.2.9/
video_freebsd.h
motion3.2.9/
netcam_jpeg.c
motion3.2.9/
README.FreeBSD
motion3.2.9/
Makefile.in
motion3.2.9/
video.h
motion3.2.9/
event.c
motion3.2.9/
ffmpeg.h
motion3.2.9/
video.c
motion3.2.9/
motion.c
motion3.2.9/
motion.initRH.
in
motion3.2.9/
CHANGELOG
motion3.2.9/
webhttpd.c
motion3.2.9/
COPYING
motion3.2.9/
webcam.c
motion3.2.9/
thread1.conf
motion3.2.9/
video_freebsd.c
motion3.2.9/
alg.c
motion3.2.9/
thread3.conf
motion3.2.9/
motion_guide.html
motion3.2.9/
motion.initDebian.
in
motion3.2.9/
track.c
motion3.2.9/
configure
motion3.2.9/
motion.spec
motion3.2.9/
netcam.h
ann@anndesktop:~/
desktop$ ln *s
motion3.2.9
motion
ann@anndesktop:~/
desktop$ cd motion
ann@anndesktop:~/
desktop/motion$ ./configure
checking for Darwin... no
checking for *BSD... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts *g...
yes
checking for gcc option to accept ISO C89... none needed
checking for pthread_create in *lpthread...
yes
checking for libjpegmmx...
skipping
checking for jpeg_set_defaults in *ljpeg...
no
You do not have libjpeg installed
checking how to run the C preprocessor... gcc *E
checking for grep that handles long lines and *e...
/bin/grep
checking for egrep... /bin/grep *E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking mjpegtools/jpegutils.h usability... no
checking mjpegtools/jpegutils.h presence... no
checking for mjpegtools/jpegutils.h... no
checking mjpegtools/mjpeg_types.h usability... no
checking mjpegtools/mjpeg_types.h presence... no
checking for mjpegtools/mjpeg_types.h... no
checking mjpegtools... no
checking for ffmpeg autodetecting... not found
**********************************************
* libavcodec.a or libavcodec.so or *
* libavformat.a or libavformat.so not found: *
* ALL FFMPEG FEATURES DISABLED *
* *
* Please read the Motion Guide for help: *
* [http://motion.sourceforge.net](http://motion.sourceforge.net) *
**********************************************
checking for mysql support... testing
checking autodect mysql headers... not found
Invalid MySQL directory *
unable to find mysql.h.
checking for PostgreSQL... Cannot find libpqfe.
h. Please specify the installation path of PostgreSQL
checking for ANSI C header files... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for struct v4l2_buffer... yes
checking for V42L support... yes
checking for short int... yes
checking size of short int... 2
checking for int... yes
checking size of int... 4
checking for an ANSI Cconforming
const... yes
Detected CPU: Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
CPU optimization: *march=
i686
checking for bswap instruction... yes
configure: creating ./config.status
config.status: creating motion.initFreeBSD.
sh
config.status: creating motion.initDebian
config.status: creating motion.initRH
config.status: creating motion.spec
config.status: creating Makefile
************************
* Configure status *
************************
OS : Linux
pthread Support: Yes
jpeg Support: No
**********************************************
** Fatal Error YOU MUST HAVE jpeg Support ***
**********************************************
mjpeg Support: No
V4L included: Yes
V4L2 supported: Yes
FFmpeg Support: No
MYSQL Support: No
PostgreSQL Support: No
CFLAGS: *g
*O2
*DMOTION_
V4L2 *DTYPE_
32BIT="int" *DHAVE_
BSWAP *march=
i686
LIBS: *lm
*lpthread
LDFLAGS:
Install prefix: /usr/local
ann@anndesktop:~/
desktop/motion$ make clean
Welcome to the setup procedure for Motion, the motion detection daemon! If you get
error messages during this procedure, please report them to the mailing list. The
Motion Guide contains all information you should need to get Motion up and running.
Run "make updateguide" to download the latest version of the Motion Guide.
Version: 3.2.9
Platform: Linux (if this is incorrect, please read README.FreeBSD)
Removing compiled files and binaries...
ann@anndesktop:~/
desktop/motion$ make
Welcome to the setup procedure for Motion, the motion detection daemon! If you get
error messages during this procedure, please report them to the mailing list. The
Motion Guide contains all information you should need to get Motion up and running.
Run "make updateguide" to download the latest version of the Motion Guide.
Version: 3.2.9
Platform: Linux (if this is incorrect, please read README.FreeBSD)
Generating dependencies, please wait...
In file included from motion.h:247,
from motion.c:10:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from conf.c:26:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from draw.c:13:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from video.c:12:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from video2.c:68:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from video_common.c:12:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from netcam.c:40:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from netcam_ftp.c:11:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from netcam_jpeg.c:15:
netcam.h:18:21: error: jpeglib.h: No such file or directory
netcam_jpeg.c:21:20: error: jerror.h: No such file or directory
In file included from motion.h:247,
from netcam_wget.c:26:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from track.c:11:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from alg.c:9:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from event.c:13:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from picture.h:13,
from picture.c:11:
netcam.h:18:21: error: jpeglib.h: No such file or directory
picture.c:15:20: error: jerror.h: No such file or directory
In file included from motion.h:247,
from rotate.h:14,
from rotate.c:32:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from webhttpd.c:13:
netcam.h:18:21: error: jpeglib.h: No such file or directory
In file included from motion.h:247,
from picture.h:13,
from webcam.c:21:
netcam.h:18:21: error: jpeglib.h: No such file or directory
make: *** [.depend] Error 1
ann@anndesktop:~/
desktop/motion$ make install
Installing files...
*mkdir
*p
/usr/local/bin
mkdir *p
/usr/local/share/man/man1
mkdir: cannot create directory `/usr/local/share/man/man1': Permission denied
make: *** [install] Error 1
ann@anndesktop:~/
desktop/motion$

Please i need help!

---

### Post by toa on 2008-02-23
Its a bit confusing, what was the command in geeting that list... or what are you trying to install ?

---

### Post by ann pic on 2008-02-23
I want to install motion-3.2.9.tar.gz And i got some error during the installation. It need some libraries, and i dont know how to include or get the libraries.. The motion-3.2.9.tar.gz i downloaded from [www.zorg.org](www.zorg.org) and motion is the sofware for digital video recorder.. Direct website for the motion is [http://www.lavrsen.dk/twiki/bin/view/motion/webhome](http://www.lavrsen.dk/twiki/bin/view/motion/webhome).. Anyone can help me..?

---

### Post by ShodanjoDM on 2008-02-23
I have only compiled a few programs, so someone please correct me if I'm wrong.
But this caught my eyes:

OS : Linux
pthread Support: Yes
jpeg Support: No
**********************************************
** Fatal Error YOU MUST HAVE jpeg Support ***
**********************************************

Seem like you haven't installed the necessary library. Then I searched using:

```
aptitude search libjpeg
```

and I found this:

```
$ aptitude search libjpeg
v   libjpeg-dbg                     -                                           
v   libjpeg-dev                     -                                           
i A libjpeg-progs                   - Programs for manipulating JPEG files      
i   libjpeg62                       - The Independent JPEG Group's JPEG runtime 
p   libjpeg62-dbg                   - Development files for the IJG JPEG library
p   libjpeg62-dev                   - Development files for the IJG JPEG library
```

You'll need to install the -dev libraries to compile. So maybe you should install libjpeg62-dev first, then re-try compiling (the libjpeg-dev is virtual package IIRC).

---

### Post by ann pic on 2008-02-23
Hi ShodanjoDM, i am a begineer and i am really not sure where to find all the -dev libraries. The virtual package IIRC can be found at where?

---

### Post by ShodanjoDM on 2008-02-23
About this:

checking for ffmpeg autodetecting... not found
**********************************************
* libavcodec.a or libavcodec.so or *
* libavformat.a or libavformat.so not found: *
* ALL FFMPEG FEATURES DISABLED *
* *
* Please read the Motion Guide for help: *
* [http://motion.sourceforge.net](http://motion.sourceforge.net) *
**********************************************

Have you checked this?: [http://www.lavrsen.dk/twiki/bin/view/Motion/ConfigFileOptions](http://www.lavrsen.dk/twiki/bin/view/Motion/ConfigFileOptions)

Seems like you'll also need to install libavcodec or libavformat. But you must add  medibuntu in your sources.list since they're not "legal" in some countries (IIRC again).

---

### Post by ShodanjoDM on 2008-02-23
> **ann pic said:**
> Hi ShodanjoDM, i am a begineer and i am really not sure where to find all the -dev libraries. The virtual package IIRC can be found at where?

Ok, try this:
Open terminal and type:

```
sudo aptitude install libjpeg-dev
```

It will automatically install the libjpeg-dev package and other necessary packages (if any).

Let me know how it goes.

---

### Post by ann pic on 2008-02-23
Thx shodanjoDm. By the way, to install the libavcodec or libavformat, i need to add the medibuntu, so how i wana add it in my sources? Am i need to connect to the internet?

---

### Post by ShodanjoDM on 2008-02-23
Yes, you'll need to connect to the internet.
Add medibuntu repository to your sources.list (I am assuming you're using Ubuntu 7.10):

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

And then:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

I just copied those commands from: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You might want to check the site, though. It has some more useful informations.

---

### Post by ann pic on 2008-02-24
Hi shodanjoDm, i already search my libjpeg package, but i only found that i only have i  this:-

 libjpeg62                       - The Independent JPEG Group's JPEG runtime 

i need to have libjpeg62.dev file, but in my package is not included. How i can find it? Too bad, my ubuntu linux cannot be connected to internet. I always switch to windows to find info. My internet configuration cannot be solved yet. Is there any other way to install the library without connected to the internet?

---

### Post by ann pic on 2008-02-24
i am using linux ubuntu 7.04

---

### Post by ryanhaigh on 2008-02-25
There is no need to compile this software from source it is in the ubuntu software repositories.

If you haven't enabled extra repos go to System>Administration>Software Sources and enable the universe repository, close the window. You can then install motion via System>Admin>Synaptic Package Manager. 
Press the reload button to download the new lists of available packages. Once that is done use the search button to search for motion, right click on motion select mark for installation, Synaptic will mark any other required packages automatically, then click the apply button. Once it is finished you should be done.

If you prefer the terminal, once you have added the extra repo (the GUI method is the easiest way to explain this step) you can open a terminal and do the following
sudo apt-get update
sudo apt-get install motion

For users of Ubuntu Gutsy 7.10 just click this link
[apt://motion]("apt://motion")

---

### Post by Partyboi2 on 2008-02-25
since you do not have internet access with the ubuntu box you can go [here]("http://packages.ubuntu.com/feisty/motion") to download the motion package for feisty. You will probably need to install other packages to met the dependencies.

---

### Post by ann pic on 2008-03-14
i cannot install my packages through terminal.. i really need these library so that i can install my motion software.. what should i do??? help me..

ann@ann-desktop:~$ sudo aptitude install libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libjpeg-dev"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
ann@ann-desktop:~$

---

### Post by ann pic on 2008-03-14
thanks all.. now i already install ubuntu 7.10. now i can connect to internet already. But i need to install some libraries before i can install my motion.Now i am run out of idea how i can get it through terminal. I already use sudo aptitude install or sudo apt-get install but i still cannot install the packages. What should i do? 

To ryanhaigh, you say it is easier to use GUI to install, how i can get it? tq.

---

### Post by ShodanjoDM on 2008-03-14
> **ann pic said:**
> i cannot install my packages through terminal.. i really need these library so that i can install my motion software.. what should i do??? help me..

ann@ann-desktop:~$ sudo aptitude install libjpeg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libjpeg-dev"

My bad. The libjpeg-dev is provided with libjpeg62-dev package.
Try this instead:

```
sudo aptitude install libjpeg62-dev
```

---

### Post by ryanhaigh on 2008-03-14
The software you are trying to install does not need to be compiled from source as it is already available in Ubuntus package system. You will need to enable the universe repositories so go to system>admin>software sources and enable universe by ticking the assoicated box. When you press the close button it will ask if you want to reload/refresh the package lists, say yes/ok, it will then download the new lists of software available.

You can then open system>admin>synaptic package manager, press the search button, search for motion by name rather than name and description. When you find the motion package tick the box to install it, this will also install any dependencies required automatically. Press apply and the packages will be downloaded and installed.

---

### Post by ann pic on 2008-03-14
To ShodanjoDM, seems like the package cannot be found

ann@ann-desktop:~$ sudo aptitude install libjpeg62-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libjpeg62-dev
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by ShodanjoDM on 2008-03-14
Can you post your sources.list, please?

```
gksudo gedit /etc/apt/sources.list
```

You can see in the screenshot below that the libjpeg62-dev is included inside the "main" repository. So it's a bit puzzling if it's not there.
Do you use the 32 or 64 bit Ubuntu?

---

### Post by ann pic on 2008-03-16
Thanks shodanjoDM, i have installed libjpeg. Thanks a lot. =) And i also have installed motion software. Just that now i got difficulities to run my motion. maybe i still missing something. I cannot see any image taken from my analogue camera. I connect it to my capture card Bt878. I also already installed xawtv. But still it's fails. I am really out of idea what i should do to see the image.

ann@ann-desktop:~$ motion
[0] Processing thread 0 - config file /usr/local/etc/motion.conf
[0] Motion 3.2.9 Started
[0] Thread 1 is from /usr/local/etc/motion.conf
[1] Thread 1 started
[1] cap.driver: "bttv"
[1] cap.card: "BT878 video ( *** UNKNOWN/GENER"
[1] cap.bus_info: "PCI:0000:06:00.0"
[1] cap.capabilities=0x05010015
[1] - VIDEO_CAPTURE
[1] - VIDEO_OVERLAY
[1] - VBI_CAPTURE
[1] - TUNER
[1] - READWRITE
[1] - STREAMING
[1] Supported palettes:
[1] 0: GREY (8 bpp, gray)
[1] 1: HI24 (8 bpp, dithered color)
[1] 2: RGBO (15 bpp RGB, le)
[1] 3: RGBQ (15 bpp RGB, be)
[1] 4: RGBP (16 bpp RGB, le)
[1] 5: RGBR (16 bpp RGB, be)
[1] 6: BGR3 (24 bpp RGB, le)
[1] 7: BGR4 (32 bpp RGB, le)
[1] 8: RGB4 (32 bpp RGB, be)
[1] 9: YUYV (4:2:2, packed, YUYV)
[1] 10: YUYV (4:2:2, packed, YUYV)
[1] 11: UYVY (4:2:2, packed, UYVY)
[1] 12: 422P (4:2:2, planar, Y-Cb-Cr)
[1] 13: YU12 (4:2:0, planar, Y-Cb-Cr)
[1] 14: YV12 (4:2:0, planar, Y-Cr-Cb)
[1] 15: 411P (4:1:1, planar, Y-Cb-Cr)
[1] 16: YUV9 (4:1:0, planar, Y-Cb-Cr)
[1] 17: YVU9 (4:1:0, planar, Y-Cr-Cb)
[1] Test palette YU12 (352x288)
[1] Using palette YU12 (352x288) bytesperlines 352 sizeimage 152064 colorspace 00000000
[1] found control 0x00980900, "Brightness", range 0,65535 
[1]     "Brightness", default 32768, current 32768
[1] found control 0x00980901, "Contrast", range 0,65535 
[1]     "Contrast", default 32768, current 32768
[1] found control 0x00980902, "Saturation", range 0,65535 
[1]     "Saturation", default 32768, current 32768
[1] found control 0x00980903, "Hue", range 0,65535 
[1]     "Hue", default 32768, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x00000000, "42", range 0,0 !DISABLED!
[1]     "42", default 0, current 32768
[1] found control 0x08000000, "chroma agc", range 0,1 
[1]     "chroma agc", default 0, current 0
[1] found control 0x08000001, "combfilter", range 0,1 
[1]     "combfilter", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=155648
[1] 1 length=155648
[1] 2 length=155648
[1] 3 length=155648
[1] Using V4L2

---

