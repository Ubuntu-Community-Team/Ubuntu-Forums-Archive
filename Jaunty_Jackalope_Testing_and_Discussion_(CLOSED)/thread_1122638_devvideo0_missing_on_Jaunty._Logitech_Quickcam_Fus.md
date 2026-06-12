---
title: "/dev/video0 missing on Jaunty. Logitech Quickcam Fusion"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jxk7581 on 2009-04-11
I'm hoping someone can assist. I have a Dell Inspiron 530 and upgraded from 8.10 to 9.04. On 8.10 y Logitech Quickcam Fusion worked perfectly. On 9.04 however, I have had no luck. 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

My webcam is supported and the kernel is recognizing the device, but I do not have a /dev/video0 entry and therefore no programs are recognizing the webcam.

jason@ubuntu-desktop:~/trunk/trunk$ dmesg | grep uvc
[ 1216.223968] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[ 1217.220139] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[ 1218.220080] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[ 1218.220085] uvcvideo: Failed to initialize the device (-5).
[ 1218.220158] usbcore: registered new interface driver uvcvideo

jason@ubuntu-desktop:~/trunk/trunk$ ls /dev/v*
/dev/vcs   /dev/vcs3  /dev/vcs6  /dev/vcsa   /dev/vcsa3  /dev/vcsa6
/dev/vcs1  /dev/vcs4  /dev/vcs7  /dev/vcsa1  /dev/vcsa4  /dev/vcsa7
/dev/vcs2  /dev/vcs5  /dev/vcs8  /dev/vcsa2  /dev/vcsa5  /dev/vcsa8

I even performed a full reinstall of Jaunty with no luck. Any assistance is appreciated.

---

