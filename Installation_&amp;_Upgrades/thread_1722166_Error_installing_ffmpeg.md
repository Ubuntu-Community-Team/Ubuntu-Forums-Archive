---
title: "Error installing ffmpeg"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by CrazySat on 2011-04-05
Hello,

I am using Ubuntu 10.04.
Today I run Update Manager and some files listed could not be installed, all of them where referring to ffmpeg.
I checked then in Synaptic and tryed to upgrade there ffmpeg but got error,
I unistalled it and from that moment I cannot install it anylonger.

This is the log in my terminal :
```
fabrizio@fabrizio-desktop:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libavdevice52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed
          Depends: libavfilter0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libavfilter-extra-0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed
          Depends: libavformat52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libavformat-extra-52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed
          Depends: libavutil49 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavutil-extra-49 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libpostproc51 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libpostproc-extra-51 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed
          Depends: libswscale0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed or
                   libswscale-extra-0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed
E: Broken packages
fabrizio@fabrizio-desktop:~$ 



fabrizio@fabrizio-desktop:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavcodec-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libavdevice52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavdevice-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libavfilter0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavfilter-extra-0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libavformat52 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavformat-extra-52 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libavutil49 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libavutil-extra-49 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libpostproc51 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libpostproc-extra-51 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
          Depends: libswscale0 (>= 4:0.5.1-1ubuntu1.1) but it is not going to be installed or
                   libswscale-extra-0 (>= 4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
E: Broken packages
fabrizio@fabrizio-desktop:~$ 
```Any help to solve the problem is well accepted, thank you in advance.

---

### Post by CrazySat on 2011-04-05
I selected in Synaptic --> Edit ---> Fix Broken Packages.

and Custom Filters --> Broken   and no packages are listed.

if I check ffmpeg for installation I got this message 

"ffmpeg:
 Depends: libavcodec52 but it is not going to be installed or
     libavcodec-extra-52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libavdevice52 but it is not going to be installed or
     libavdevice-extra-52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libavfilter0 but it is not going to be installed or
     libavfilter-extra-0 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libavformat52 but it is not going to be installed or
     libavformat-extra-52 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libavutil49 but it is not going to be installed or
     libavutil-extra-49 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libpostproc51 but it is not going to be installed or
     libpostproc-extra-51 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed
 Depends: libswscale0 but it is not going to be installed or
     libswscale-extra-0 (>=4:0.5.1-1ubuntu1.1) but 4:0.5.1-1ubuntu1 is to be installed"

:(

---

### Post by Joe of loath on 2011-04-05
What's the output of

```

cat /etc/apt/sources.list
```?

---

### Post by plucky on 2011-04-05
Don't do anything See [Here](http://ubuntuforums.org/showthread.php?t=1721507)

Dependency problems,give it some time.

Also [Bug Report](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114)

Good Luck

---

### Post by CrazySat on 2011-04-06
> **plucky said:**
> Don't do anything See [Here]("http://ubuntuforums.org/showthread.php?t=1721507")

Dependency problems,give it some time.

Also [Bug Report]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114")

Good Luck

Thank you plucky for your help.

I had already installed manually :

libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-0 
libavformat-extra-52
libavutil-extra-49
libpostproc-extra-51
libswscale-extra-0

and I uninstalled ffmpeg and I can't it install again ...
What can I do now that my system is messed ?
Thanks

---

### Post by CrazySat on 2011-04-07
Hi all,
I think the problem has been fixed with today's updates and I could finally install again ffmpeg.

Thank you all again for your help.

---

### Post by klausner on 2011-04-26
> **CrazySat said:**
> Hi all,
I think the problem has been fixed with today's updates and I could finally install again ffmpeg.

Thank you all again for your help.

Well it may be fixed for you, but I can't get ffmpeg, mencoder, or smplayer to install. The LCD seems to be libjack-jackd2. 

I know one poster said to be patient, but patience isn't much of an answer. ](*,)

---

### Post by CrazySat on 2011-04-27
Hello klausner,
please report here the error/s you get in your terminal log so that some expert user can help you to solve your problem.

---

### Post by klausner on 2011-04-27
ffmpeg:
>  Depends: libavdevice52 but it is not going to be installed

libavdevice52:
 > Depends: libjack-jackd2-0 (>=1.9.5~dfsg-14) but it is not installable or
 	libjack-0.116  but it is not installable

mencoder and smplayer give similar errors leading back to libjack-0. If I try to force the install of libjack-jackd2-0 from the CL, it comes up as a broken package in synaptic.

---

### Post by CrazySat on 2011-04-27
Unfortunatly I am not skilled in Linux, that's why I came here asking for help.
Anyway, did you try to install the following ?

libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-0 
libavformat-extra-52
libavutil-extra-49
libpostproc-extra-51
libswscale-extra-0

---

