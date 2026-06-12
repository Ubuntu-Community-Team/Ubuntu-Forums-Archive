---
title: "HOW TO : vmd installation and removal"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2007-10-31
Hello,

First of all I want to congratulate the developers on the production of ubuntu gutsy gibbon 7.10. Up to now is very nice. I was pleased to see gromacs in the repositories, a program that I use a lot. 

Now I will try to explain step by step the installation procedure (and uninstallment) of vmd version 1.8.6 for Gutsy Gibbon.

First you have to register to the web page of vmd before you download the tar package. 
[http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD](http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD)
I think this is the case of not finding vmd in the repositories. For all those out there who have simple computer architecture, the LINUX OpenGL version in an Intel computer will be just what you need.

Download the tar file in any folder you like and extract its contents. For gnome users it will be nice to know that they can make their life easier with nautilus-open-terminal from synaptic. That way wherever you are you will be able to open a terminal and have the same path in that terminal as that of the location you opened that terminal (I hope that that was clear). A small exception to this is when you do it from your Desktop.

Also it would be nice from synaptic to install the libstdc++5. I saw that this library might be needed.

Now go to the configure file and there you will see:

##############################################################################
# User modifiable installation parameters, can be overridden by env variables
##############################################################################
# Name of shell script used to start program; this is the name used by users
$install_name = "vmd";

# Directory where VMD startup script is installed, should be in users' paths.
$install_bin_dir="/usr/local/bin";

# Directory where VMD files and executables are installed
$install_library_dir="/usr/local/lib/$install_name";

With the above you specify how your program will be called and where it will be installed. As far as the name is concerned I keep the default.
My suggestion for the directories is to do the following 
$install_bin_dir="/usr/local/vmd/bin"; 
$install_library_dir="/usr/local//vmd/lib/$install_name";

Save and then type in terminal ```
./configure
```
Then type ```
cd src
```
and ```
sudo make install
```

Now in your /usr/local folder you have ceated a vmd folder. If you try to execute vmd with a fresh install of gutsy you will be disappointed. Your installation up to now is ok though.
If you go to /usr/local/vmd/bin and type ./vmd you will get an error as that :
bash: ./vmd: /bin/csh: bad interpreter: No such file or directory

In order to eliminate this go to synaptic and type csh. Install the package that has this name exactly. And then go back where you were and type ./vmd
You should see no error at all. The drawback with this is that you are not able to open vmd from any location you want. In order to do that we will create a soft link as follows:

go to /usr/local/bin
and type :
```
 sudo ln -s /usr/local/vmd/bin/vmd /usr/local/bin
```
That way you will be able to open vmd from every location by just typing vmd.

If someone wants also a shortcut to his or her desktop then go to your Desktop and do right click. Then choose create launcher. There for name and command type vmd. Every time you do double left click vmd will launch.

As far as the uninstallment is concerned you have to do the following :

go to the directories where you installed the VMD startup script and the VMD files and executables (the ones which we changed just above) and remove them with the command rm as root. That way you will have removed vmd from your system. 
FYI the tar file and the extracted files are not needed for the program to run.

Links which were helpful :
[http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/1400.html](http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/1400.html)
[http://www.wlug.org.nz/SoftLink](http://www.wlug.org.nz/SoftLink)
[http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/2620.html](http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/2620.html)
[http://ubuntuforums.org/showthread.php?t=397098](http://ubuntuforums.org/showthread.php?t=397098)
[http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/9576.html](http://www.ks.uiuc.edu/Research/vmd/mailing_list/vmd-l/9576.html)

Regards!

---

### Post by vancheese on 2007-11-21
Any suggestions for howto install/compile the vmd plugins?

---

### Post by Claus7 on 2007-11-26
Hello,

I do not have any idea about the plugins, because I do not use any.

What I wanted to post also is what you have to do when you will see a message in vmd such as this :
unable to create openGL window

I saw this message after I was "playing" with the resolution and the drivers of my screen and graphic card (nvidia 6200).
What I did was to type the command :
```
sudo nvidia-glx-config enable
```

and the message disappeared. This code was found from synaptic in gutsy in nvidia-glx-new. And after I typed that I saw that when I restarted my computer the logo of nvidia appeared.Just FYI.

Regards!

---

### Post by vussvillem on 2008-02-28
Thank you Claus for the great how to!

---

### Post by trexgrec on 2008-03-21
Thank you all for the important info. They were very helpfull!

---

### Post by stevieP on 2008-04-13
Very helpful thanks. Particularly the note about installation of the libstdc++5 libraries. I didn't do this at first and vmd would not open in either graphical or text mode. 

> Also it would be nice from synaptic to install the libstdc++5. I saw that this library might be needed.

-StevieP

---

### Post by davebridges on 2008-04-29
has anyone had problems with vmd since the hardy upgrade?  It was working before for me, now it blinks and crashes

---

### Post by ntsc28 on 2008-04-30
Hello,
I have installed VMD on a fresh hardy. It didn't work at all. In fact it requires libstdc++5 which is not installed by default with hardy. 

So before installing VMD, you should install csh and libstdc++5 first.

---

### Post by davebridges on 2008-05-01
for what its worth, if i go to the /vmd-1.8.6/LINUX directory and run ./vmd_LINUX it works sort of ok again, although some plugins dont seem to be recognized.  I have the new libstdc++5 and csh repos (I did an upgrade, not a fresh install).  Does someone who is familiar with the softlink command have any ideas how to get back to being able to run vmd from any location and/or have any ideas how to get the plugins to work?

---

### Post by ntlam on 2008-05-07
> **ntsc28 said:**
> Hello,
I have installed VMD on a fresh hardy. It didn't work at all. In fact it requires libstdc++5 which is not installed by default with hardy. 

So before installing VMD, you should install csh and libstdc++5 first.

I have the same problem. Thanks for your solution.

---

### Post by ehatch on 2008-06-04
I am having a problem with the installation of vmd on hardy. I have the libstdc++5 and csh packages installed, but when I launch VMD no screens appear. when I check the syslog I get "segfault at 157e0 rip 4304ce rsp 7fffeead7490 error 4" for the process.

Any ideas?

---

### Post by ehatch on 2008-06-04
I figured it out. I had the wrong package for my machine. There are 3 and the basic LINUX dist did not work. I used the AMD dist and everything came up perfect.

---

### Post by flomar on 2008-06-11
Hey,

thanks for the How-To, i spent more time on looking for a prebuilt DEB than it took me to install VMD with your guide ;)

For me (Hardy Heron 32-bit on Intel Core2Duo) it was the following package i could install sucessfully:
**LINUX OpenGL (Linux (Redhat 9 or later) with Mesa or hardware OpenGL)**

Flo

---

### Post by davebridges on 2008-06-19
how about the plugins?

---

