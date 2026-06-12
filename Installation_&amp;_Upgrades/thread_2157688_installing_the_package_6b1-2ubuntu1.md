---
title: "installing the package 6b1-2ubuntu1"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by EskenderTamrat on 2013-06-26
Hi all,

I'm new to Ubuntu and when I try working on opencv, it doesn't capture my webcams. When I search for the reason, I look that maybe its because I didn't install some packages. So, when I try to install them, I got a message as follows for the package 6b1-2ubuntu1

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 6b1-2ubuntu1

Any suggestion how can I solve this problem?

My machine specification - Ubuntu 12.04, 64-bit, opencv2.4.5. 

Thanks,
Eskender

---

### Post by dino99 on 2013-06-26
opencv2.4.5 is not a genuine ubuntu package ([https://launchpad.net/ubuntu/+source/opencv](https://launchpad.net/ubuntu/+source/opencv))

all the apps you need are already inside the ubuntu archives; install them with either "apt-get" or "synaptic" or "software-center"

it can be also compile by yourself if you need the very latest release : [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

### Post by EskenderTamrat on 2013-06-27
Thanks for the reply.

So, where does that leaves me? My webcams are recognized by other packages. (eg: cheese webcam booth). But, Opencv codes to compute the capturing of cameras keeps telling me there is no camera detected. btw, they are different kinds (**INTEX IT-310WC** and **INTEX IT-309WC**). But, still opencv can't detect any of them (either individually plugged or both at a time). I was hoping to compute a pointcloud from my stereovision data.

---

### Post by steeldriver on 2013-06-27
Your title is confusing - afaik '6b1-2ubuntu1' isn't a package it's a package *version* - what actual package are you trying to locate (like libjpeg62-dev or libv4l-dev)?

What exact "Opencv codes to compute the capturing of cameras" are you using and what error does it give when it tries to connect?

---

### Post by EskenderTamrat on 2013-06-27
The package which brought unmet dependency is libjpeg62-dev
when i tried to install it with "**$ sudo apt-get install libjpeg62-dev**", it gives the error msg as follows.
[B]The following packages have unmet dependencies: Conflicts: libjpeg62-dev but 6b1-2ubuntu1 is to be installed

The opencv codes (ya, i crosscheck with other codes too) I used to know if opencv detect my webcams are written with the basic functions and they doesn't have any bugs. But, in my case it returned an output of "there are no cameras detected" while other applications got access to the cameras.

[/B][SIZE=2][FONT=courier new]// the code
int DetectCameras() {[/FONT]
[FONT=courier new]    int numOfCamera = 0;[/FONT]
[FONT=courier new]    int finished = 0;[/FONT]
[FONT=courier new]    while( !finished ) {[/FONT]
[FONT=courier new]        CvCapture* capture = cvCreateCameraCapture(numOfCamera);[/FONT]
[FONT=courier new]        if(!capture)[/FONT]
[FONT=courier new]            finished = 1;[/FONT]
[FONT=courier new]        else {[/FONT]
[FONT=courier new]            numofCamera++;[/FONT]
[FONT=courier new]            cvReleaseCapture( &capture );[/FONT]
[FONT=courier new]        }[/FONT]
[FONT=courier new]    }[/FONT]
[FONT=courier new]    return numofCamera;[/FONT]
[FONT=courier new]}[/FONT][/SIZE]
Can it be the case that the cameras aren't suitable for opencv? My Webcams version - **INTEX IT-310WC** and **INTEX IT-309WC**

---

